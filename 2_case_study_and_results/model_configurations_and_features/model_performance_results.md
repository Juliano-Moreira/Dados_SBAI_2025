# Resultados de Desempenho dos Modelos (Tabela 6 do Artigo)

Esta seção resume o desempenho dos modelos preditivos para as duas melhores configurações de features encontradas (`Config_6` e `Config_5`). As métricas incluem:
* **Estatísticas:** (i) R² (Coeficiente de Determinação), (ii) RMSE (Raiz do Erro Quadrático Médio), (iii) MAE (Erro Absoluto Médio), (iv) MAPE (Erro Percentual Absoluto Médio).
* **Computacionais:** (v) Tempo de Treinamento (s), (vi) Tempo de Inferência (s)

| Configuração | Modelo        | R² (i) | RMSE (ii) | MAE (iii) | MAPE (iv) | Treinamento (s) (v) | Inferência (s) (vi) |
|--------------|---------------|-------------|-----------|-----------|-----------|-----------------------|-----------------------|
| **Config_6**  | XGBoost       | 0.99        | 0.96      | 0.56      | 0.06      | 3.57                  | 0.03                  |
|              | LightGBM      | 0.99        | 0.96      | 0.57      | 0.06      | 4.65                  | 0.18                  |
|              | CatBoost      | 0.99        | 0.96      | 0.57      | 0.06      | 36.62                 | 0.03                  |
| **Config_5**  | Random Forest | 0.78        | 14.31     | 8.31      | 0.67      | 72.55                 | 0.78                  |
|              | Extra Trees   | 0.77        | 14.45     | 8.66      | 0.72      | 30.23                 | 0.37                  |
|              | CatBoost      | 0.76        | 14.87     | 9.22      | 0.82      | 21.11                 | 0.02                  |

**Observações:**
* A Configuração 6, que inclui variáveis temporais, cíclicas, defasadas de período e defasadas de trocas acumuladas (`cumulative_swaps_t-h`), junto com o modelo XGBoost, apresentou o melhor desempenho geral.
* A inclusão de variáveis defasadas de trocas acumuladas (presentes na `Config_6`) melhorou significativamente a qualidade das previsões.
