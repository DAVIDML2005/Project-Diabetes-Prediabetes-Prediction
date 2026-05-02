# Predicción de Riesgo de Diabetes/Prediabetes

## Descripción

Este proyecto desarrolla y evalúa múltiples modelos de Machine Learning para predecir la presencia de diabetes o prediabetes a partir de indicadores de salud, comportamientos y variables demográficas.

La diabetes es una de las principales problemáticas de salud pública a nivel global, por lo que la detección temprana mediante modelos predictivos puede contribuir significativamente a estrategias de prevención y toma de decisiones en salud.

Este trabajo fue desarrollado como parte del curso de **Machine Learning** en la **Universidad del Norte**.

## Colaboradores

* David Marquez
* Cristian Linero

## Objetivos

### Objetivo General

Desarrollar modelos predictivos capaces de identificar factores de riesgo asociados a la diabetes utilizando datos del CDC.

### Objetivos Específicos

* Realizar un análisis exploratorio de datos (EDA) completo
* Implementar múltiples algoritmos de clasificación
* Abordar el desbalance de clases
* Optimizar el rendimiento computacional de los modelos
* Evaluar modelos con métricas robustas
* Aplicar técnicas de interpretabilidad (SHAP, LIME)
* Explorar modelos innovadores adaptados al problema

## Dataset

* **Nombre**: CDC Diabetes Health Indicators
* **Fuente**: Behavioral Risk Factor Surveillance System (BRFSS)
* **Registros**: +250,000 observaciones

- Dataset: https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators
- Codebook: https://www.cdc.gov/brfss/annual_data/2015/pdf/codebook15_llcp.pdf

### Variable Objetivo

`Diabetes_binary`:

* `0` → No diabetes
* `1` → Prediabetes o diabetes

## Modelos Implementados

Se realizó un benchmark amplio con los siguientes modelos:

* K-Nearest Neighbors (KNN)
* Naive Bayes
* Regresión Logística (L1 y L2)
* Árboles de Decisión
* Random Forest
* Gradient Boosting
* XGBoost
* LightGBM
* CatBoost
* Support Vector Machines (SVM)

## Manejo de Desbalance

Se implementaron técnicas como:

* SMOTE
* ADASYN
* Ajuste de pesos (`class_weight='balanced'`)

## Evaluación de Modelos

Se utilizaron múltiples métricas:

* Accuracy
* Precision
* Recall (especialmente importante en contexto médico)
* F1-Score
* AUC-ROC

Además:

* Matrices de confusión
* Curvas ROC

## Interpretabilidad

Para entender el comportamiento de los modelos:

* SHAP (SHapley Additive exPlanations)
* LIME
* Feature Importance

## Optimización

Se aplicaron técnicas para mejorar eficiencia:

* KD-Trees / Ball-Trees (KNN)
* Solvers optimizados (Logistic Regression)
* `hist` method (XGBoost)
* SGDClassifier (SVM)

## Impacto

Este proyecto busca:

* Mejorar la detección temprana de diabetes
* Apoyar decisiones en salud pública
* Reducir complicaciones y costos médicos
* Demostrar el potencial del Machine Learning en epidemiología
