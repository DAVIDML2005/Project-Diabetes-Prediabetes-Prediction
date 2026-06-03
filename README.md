# Predicción de Riesgo de Diabetes/Prediabetes

## Descripción

Este proyecto desarrolla y evalúa múltiples modelos de Machine Learning para predecir la presencia de diabetes o prediabetes a partir de indicadores de salud, comportamientos y variables demográficas.

La diabetes es una de las principales problemáticas de salud pública a nivel global, por lo que la detección temprana mediante modelos predictivos puede contribuir significativamente a estrategias de prevención y toma de decisiones en salud.

Este trabajo fue desarrollado como parte del curso de **Machine Learning** en la **Universidad del Norte**.

## Colaboradores

* David Ricardo Marquez Luna (https://github.com/DAVIDML2005)
* Cristian Camilo Linero Cantillo (https://github.com/cristianclc)

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
* Explorar y adaptar modelos provenientes de otros dominios al problema de predicción de diabetes

## Modelo Original: Ensemble con Simulated Annealing

### Contexto del Enfoque

Como aporte diferencial del proyecto, se diseñó un modelo original basado en ensemble learning optimizado mediante Simulated Annealing (SA), inspirado en metodologías recientes aplicadas en problemas de *churn prediction* y adaptado al dominio de la salud.

El objetivo de este modelo es superar el rendimiento de modelos individuales mediante la combinación óptima de múltiples clasificadores.

### ¿Por qué Ensemble Learning?

El uso de ensembles se fundamenta en:

* **Diversidad estadística**: distintos modelos capturan diferentes patrones en los datos
* **Robustez**: reducción de overfitting y menor dependencia de un solo modelo
* **Complementariedad**: mejor cobertura del espacio de características

### Arquitectura del Sistema

El modelo propuesto sigue un enfoque de **ensemble heterogéneo en tres fases**:

#### Modelos Base

Se entrenaron 12 modelos diversos, incluyendo:

* Regresión Logística (L1 y L2)
* Árboles de Decisión
* Naive Bayes
* Random Forest
* XGBoost
* LightGBM
* CatBoost
* AdaBoost
* Gradient Boosting
* Bagging
* Extra Trees

Esta diversidad permite capturar relaciones lineales y no lineales en los datos.

#### Optimización con Simulated Annealing

Se implementó el algoritmo de Simulated Annealing (SA) para:

* Seleccionar subconjuntos óptimos de modelos
* Ajustar los pesos de cada modelo dentro del ensemble
* Evitar óptimos locales mediante exploración controlada del espacio de soluciones

La función objetivo utilizada se basa en la maximización del AUC-ROC.

#### Combinación de Predicciones

Las predicciones finales se obtienen mediante una media ponderada optimizada, donde cada modelo contribuye según su peso aprendido durante el proceso de optimización.


### Valor del Modelo Propuesto

Este enfoque aporta:

* Mejora potencial en métricas clave (especialmente Recall y AUC)
* Mayor estabilidad frente a datos desbalanceados
* Exploración de técnicas avanzadas de optimización
* Un enfoque innovador aplicado al problema de salud

**Referencia**: https://www.researchgate.net/publication/368868896_Ensemble_Methods_in_Customer_Churn_Prediction_A_Comparative_Analysis_of_the_State-of-the-Art

## Dataset

* **Nombre**: CDC Diabetes Health Indicators
* **Fuente**: Behavioral Risk Factor Surveillance System (BRFSS)
* **Registros**: +250,000 observaciones

**Dataset**: https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators

**Codebook**: https://www.cdc.gov/brfss/annual_data/2015/pdf/codebook15_llcp.pdf

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
