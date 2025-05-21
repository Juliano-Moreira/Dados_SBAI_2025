# Estudo do Horizonte de Predição e Número Ótimo de Lag Features

Esta seção detalha a análise realizada para determinar o tamanho ótimo do horizonte de predição (`n`) e do número de lag features (`h`) para o modelo XGBoost, que apresentou o melhor desempenho.

## Conteúdo:

* **[`figure_horizon_lag_optimization.svg`](figure_horizon_lag_optimization.svg)**: Apresenta visualmente os resultados através de heatmaps.
* **[`prediction_horizon_and_lag_features.csv`](prediction_horizon_and_lag_features.csv)**: Resultados do experimento sobre o impacto do número de lag features e do horizonte de predição na acurácia do modelo XGBoost