# Hiperparâmetros Otimizados dos Modelos

Os hiperparâmetros para cada modelo foram otimizados utilizando GridSearchCV e Optuna, com validação cruzada.

```python
# XGBoost
best_params_xgb = {'colsample_bytree': 0.8, 'gamma': 0.3, 'reg_alpha': 0.23560905787512834, 'reg_lambda': 10.640730991765501, 'learning_rate': 0.08, 'max_depth': 11, 'n_estimators': 120, 'subsample': 1.0, 'random_state': 42, 'min_child_weight': 10}

# Extra Trees Regressor
best_params_extratree = {'n_estimators': 190, 'max_features': 0.4302785953223669, 'max_leaf_nodes': 30455}

# LightGBM
best_params_lgb = {'n_estimators': 791, 'learning_rate': 0.02055011267905208, 'num_leaves': 126, 'max_depth': 6, 'min_child_samples': 12, 'subsample': 0.7169130713979853, 'colsample_bytree': 0.9940591674448308, 'reg_alpha': 4.569350296167526, 'reg_lambda': 2.8599744711357714e-05, 'random_state':42}

# Random Forest Regressor
best_params_rf = {'n_estimators': 304, 'max_features': 0.35196173950010623, 'max_leaf_nodes': 30455, 'random_state':42}

# CatBoost Regressor
best_params_cb = {'iterations': 749, 'depth': 10, 'learning_rate': 0.018794478477941343, 'l2_leaf_reg': 0.0031107887399334008, 'border_count': 245, 'random_strength': 0.0018582007358200353, 'bagging_temperature': 0.6132451895217202, 'od_type': 'Iter', 'random_state':42}

# Decision Tree Regressor
best_params_dt = {'max_depth': 10, 'min_samples_split': 5, 'min_samples_leaf': 10, 'max_features': None, 'random_state': 42}

# MLPRegressor
best_params_mlp = {'hidden_layer_sizes': (100, 50), 'max_iter': 100, 'early_stopping': True, 'random_state': 42} # Duas camadas ocultas (100 e 50 neurônios)

# LSTM (via LSTMPipeline)
best_params_lstm = {'units': 128, 'pred_length': 1, 'epochs': 50, 'batch_size': 96} # Duas camadas LSTM com 128 unidades cada.

```

Os modelos avaliados incluem: XGBoost, LightGBM, CatBoost, Random Forest, Extra Trees, Decision Tree, Linear Regression, MLPRegressor, e LSTM. Detalhes completos das arquiteturas e código-fonte para implementação estarão disponíveis no diretório /src após a publicação do artigo.