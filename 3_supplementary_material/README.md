# Definição das Variáveis (Features)

Este documento detalha as variáveis presentes nos datasets, conforme Tabela 1 (parcialmente) e Tabela 3 do artigo "Engenharia de Features e Aprendizado de Máquina para Predição da Demanda em Estações de Troca de Baterias".

A base de dados original, de Feng and Lu (2022), continha variáveis como `BSS_ID`, `Port`, `SoC (%)` e `Time`. Após o pré-processamento (Seção 3 do artigo) e engenharia de features (Seção 4 do artigo), as seguintes features foram geradas e utilizadas.

## Features nos Datasets (`*_h12.csv`)

| Variável (Feature Name) | Tipo no Dataset | Descrição (conforme artigo)                                                                                                                            | Referência no Artigo |
|-------------------------|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| `id`                    | Integer         | Identificador único da estação BSS (originalmente `BSS_ID`).                                                                                     | Tabela 1             |
| **Variáveis Temporais** |                 | Representam a estrutura cíclica do tempo.                                                                                                     | Seção 4.3            |
| `period`                | Integer         | Identificador do período do dia (1 a 96, representando intervalos de 15 minutos em 24 horas).                                     | Tabela 3             |
| `hour`                  | Integer         | Hora do dia (0-23).                                                                                                                           | Tabela 3             |
| `turn`                  | Integer         | Turno do dia: 0 (madrugada 00h-06h), 1 (manhã 06h-12h), 2 (tarde 12h-18h), 3 (noite 18h-00h).                                       | Tabela 3             |
| `hour_sin`              | Float           | Representação cíclica senoidal da hora do dia: $\sin\left(\frac{2\pi \cdot \text{hour}}{24}\right)$.                                                | Eq. 3, Tabela 3      |
| `hour_cos`              | Float           | Representação cíclica cossenoidal da hora do dia: $cos(\frac{2\pi \cdot \text{hour}}{24})$.                                                | Eq. 4, Tabela 3      |
| `turn_sin`              | Float           | Representação cíclica senoidal do turno do dia: $sin(\frac{2\pi \cdot \text{turn}}{4})$.                                                  | Eq. 5, Tabela 3      |
| `turn_cos`              | Float           | Representação cíclica cossenoidal do turno do dia: $cos(\frac{2\pi \cdot \text{turn}}{4})$.                                                 | Eq. 6, Tabela 3      |
| **Variáveis de Demanda**|                 | Capturam as transações de troca de baterias.                                                                                                 | Seção 4.3            |
| `soc_arrived`           | List (String)   | Lista com os estados de carga (SoC) das baterias entregues para troca no período. Ex: "[49.0, 69.0]" ou "[]" se não houver trocas. | Tabela 2, Tabela 3   |
| `swaps`                 | Integer         | Número de trocas (eventos de Swap) identificadas no período. Um Swap é registrado se $\|\text{SoC}_{t} - \text{SoC}_{t-1}\| \ge 10\%$.                | Eq. 2, Tabela 2      |
| `cumulative_swaps`      | Integer         | Total acumulado de trocas (`swaps`) em períodos recentes. É a **variável alvo** da predição.                                        | Tabela 3             |
| **Variáveis Defasadas (Lags)** |          | Utilizadas para modelar dependências temporais na série histórica. Para este estudo, foram criadas para os H=12 últimos períodos.  | Seção 4.3, Tabela 3  |
| `period_t-h`            | Integer         | Valores defasados do período (`period`) para $h=1,...,12$.                                                                                         | Tabela 3             |
| `cumulative_swaps_t-h`  | Integer         | Valores defasados do total acumulado de trocas (`cumulative_swaps`) para $h=1,...,12$.                                                   | Tabela 3             |


<br></br>

## Variáveis nas Fórmulas das Métricas Estatísticas (Seção 5.4)

As seguintes variáveis são utilizadas nas equações (7)-(10) para cálculo das métricas de avaliação dos modelos preditivos:

| Símbolo        | Descrição                                                                                           | Unidade/Tipo  |
|----------------|-----------------------------------------------------------------------------------------------------|---------------|
| $y_i$          | Valor real da variável alvo para a i-ésima observação.                                                | Numérico      |
| $\hat{y}_i$    | Valor predito pelo modelo para a variável alvo para a i-ésima observação.                             | Numérico      |
| $\bar{y}$      | Média dos valores reais da variável alvo ($y_i$) sobre todas as observações no conjunto de dados.     | Numérico      |
| $n$            | Número total de observações no conjunto de dados (amostras).                                        | Inteiro       |
| $\sum$         | Símbolo de somatório, indicando a soma sobre todas as observações de $i=1$ até $n$.                   | Operador      |
| $\| \cdot \|$   | Valor absoluto.                                                                                     | Operador      |
| $\sqrt{\cdot}$ | Raiz quadrada.                                                                                      | Operador      |

<br></br>

As definições detalhadas das variáveis `hour`, `turn`, `hour_sin`, etc., utilizadas nas equações (3)-(6) do artigo, correspondem às features listadas acima. O material complementar referenciado na Seção 8 do artigo aponta para estas definições.