# Modelos, Configurações de Features e Resultados

Esta seção do repositório detalha as configurações de features utilizadas, os hiperparâmetros dos modelos de aprendizado de máquina avaliados e os resultados de desempenho obtidos no estudo "Engenharia de Features e Aprendizado de Máquina para Predição da Demanda em Estações de Troca de Baterias".

## Conteúdo:

* **[`feature_set_configurations.md`](feature_set_configurations.md)**: Descreve os seis conjuntos de configurações de features (Config_1 a Config_6) testados, conforme Tabela 5 do artigo.
* **[`model_hyperparameters.md`](model_hyperparameters.md)**: Lista os hiperparâmetros otimizados para cada um dos nove algoritmos preditivos avaliados. Os métodos GridSearchCV e Optuna foram utilizados para o ajuste fino.
* **[`model_performance_results.md`](model_performance_results.md)**: Apresenta as métricas de desempenho (R², RMSE, MAE, MAPE, Tempo de Treinamento, Tempo de Inferência) para as melhores configurações encontradas, com foco nos modelos de melhor desempenho, conforme Tabela 6 do artigo.