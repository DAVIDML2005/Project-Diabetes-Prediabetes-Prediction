# **Conclusiones y Hallazgos Principales**

## **1. Logro de los Objetivos Propuestos**

El presente proyecto ha cumplido satisfactoriamente con todos los objetivos planteados inicialmente, demostrando la viabilidad de utilizar algoritmos de machine learning para la predicción temprana de diabetes y prediabetes. A través de un proceso sistemático que incluyó desde el análisis exploratorio hasta la interpretación avanzada de modelos, se ha desarrollado un framework robusto capaz de identificar pacientes con alto riesgo metabólico con métricas competitivas.

## **2. Hallazgos Clínicos y Epidemiológicos Relevantes**

El análisis exploratorio y de importancia de variables reveló patrones epidemiológicos significativos que coinciden con la literatura médica existente:

- **Perfil de riesgo identificado**: Los pacientes con mayor probabilidad de diabetes presentan **edad avanzada** (categorías cat_Age_10, cat_Age_11), **consumo excesivo de alcohol** (bin_HvyAlcoholConsump), y **condiciones de salud general deficiente** (cat_GenHlth_4, cat_GenHlth_5).

- **Variables críticas identificadas**: Las **variables de edad categorizadas** emergieron como los predictores más potentes en modelos lineales, mientras que **indicadores médicos directos** (HighBP, HighChol) dominaron en modelos basados en árboles.

- **Factores protectores consistentes**: La **ausencia de consumo excesivo de alcohol** y la **pertenencia a grupos de edad media** se identificaron como factores protectores clave en múltiples modelos.

## **3. Análisis Comparativo de Técnicas de Balanceo por Modelo**

El análisis exhaustivo de las diferentes técnicas de balanceo reveló patrones significativos en el rendimiento de cada modelo:

### **Mejor Técnica de Balanceo por Modelo**

- **XGBoost**: **scale_pos_weight** - Logró el **mejor AUC-ROC global** (0.811721) con F1-Score competitivo (0.426087), demostrando superioridad sobre SMOTE y ADASYN.

- **Logistic Regression L1**: **Class Weight ('balanced')** - Alcanzó **F1-Score de 0.426976** y AUC-ROC de 0.808035, mostrando mejor balance métrico que SMOTE.

- **Logistic Regression L2**: **Class Weight ('balanced')** - Consiguió **AUC-ROC de 0.807979** con un excelente tiempo de predicción (0.068129s) para regresión logística.

- **Random Forest**: **Class Weight ('balanced')** - Obteniendo el **mejor F1-Score global** (0.427917) y AUC-ROC competitivo (0.806268).

- **SVM**: **Class Weight ('balanced')** - Alcanzó un **buen AUC-ROC para modelos lineales** (0.806949) con tiempo de predicción excelente (0.066463s).

- **BernoulliNB**: **ADASYN** - Logró **AUC-ROC de 0.790196** con precisión competitiva (29.65%).

- **Decision Tree**: **Class Weight ('balanced')** - Demostró un **excelente recall global** (0.780591) ideal para maximizar detección.

- **KNN**: **SMOTE** - Alcanzó **AUC-ROC de 0.736694**, superando a ADASYN a pesar de limitaciones temporales.

- **MultinomialNB**: **ADASYN** - Logró **AUC-ROC de 0.778285** con buen balance entre métricas.

- **GaussianNB**: **ADASYN** - Aunque con **AUC-ROC más bajo** (0.755848), mostró el **mejor recall global** (85.37%).

### **Patrones Generales en Técnicas de Balanceo**

- **SMOTE**: Óptimo para modelos lineales, con **AUC-ROC consistentemente alto** y buen balance general.

- **Class Weight y scale_pos_weight (XGBoost)**: Superior en modelos lineales y basados en árboles, maximizando **F1-Score y AUC-ROC**.

- **ADASYN**:  Superior para modelos **Naive Bayes** presentando un buen balance general.

- **Sin Balanceo**: Produjo **accuracy inflado artificialmente** con recall muy bajo, confirmando la necesidad crítica de técnicas de balanceo.

## **4. Desempeño Comparativo de Modelos**

### **Jerarquía de Rendimiento por Métrica Clave**

#### **AUC-ROC**
1. **XGBoost (scale_pos_weight)** - 0.811721.
2. **Logistic Regression L1 (Class Weight)** - 0.808035.
3. **Logistic Regression L2 (Class Weight)** - 0.807979.
4. **SVM (Class Weight)** - 0.806949.
5. **Random Forest (Class Weight)** - 0.806268.
6. **Decision Tree (Class Weight)** - 0.793718.
7. **BernoulliNB (ADASYN)** - 0.790196.
8. **MultinomialNB (ADASYN)** - 0.778285.
9. **GaussianNB (SMOTE)** - 0.756042.
10. **KNN (SMOTE)** - 0.736694.

#### **F1-Score**
1. **Random Forest (SMOTE)** - 0.435008.
2. **XGBoost (SMOTE)** - 0.430538.
3. **Logistic Regression L2 (SMOTE)** - 0.427553.
4. **Logistic Regression L1 (Class Weight)** - 0.426976.
5. **SVM (SMOTE)** - 0.426342.
6. **BernoulliNB (SMOTE)** - 0.421779.
7. **Decision Tree (ADASYN)** - 0.408646.
8. **MultinomialNB (SMOTE)** - 0.407390.
9. **KNN (SMOTE)** - 0.375550.
10. **GaussianNB (SMOTE)** - 0.350543.

#### **Precision**
1. **XGBoost (ADASYN)** - 0.447325.
2. **Random Forest (SMOTE)** - 0.339803.
3. **Decision Tree (ADASYN)** - 0.315745.
4. **BernoulliNB (SMOTE)** - 0.306038.
5. **Logistic Regression L2 (SMOTE)** - 0.298196.
6. **SVM (SMOTE)** - 0.297881.
7. **Logistic Regression L1 (SMOTE)** - 0.297523.
8. **MultinomialNB (SMOTE)** - 0.289130.
9. **KNN (SMOTE)** - 0.275120.
10. **GaussianNB (SMOTE)** - 0.221525.

#### **Recall**
1. **GaussianNB (ADASYN)** - 0.853728.
2. **XGBoost (scale_pos_weight)** - 0.781440.
3. **Decision Tree (Class Weight)** - 0.780591.
4. **Logistic Regression L1 (ADASYN)** - 0.770547.
5. **SVM (Class Weight)** - 0.769274.
6. **Logistic Regression L2 (ADASYN)** - 0.768426.
7. **Random Forest (Class Weight)** - 0.732918.
8. **MultinomialNB (ADASYN)** - 0.725421.
9. **BernoulliNB (ADASYN)** - 0.707879.
10. **KNN (SMOTE)** - 0.600368.

#### **Tiempo de Predicción**
1. **Logistic Regression L2 (SMOTE)** - 0.058025s.
2. **Decision Tree (Class Weight)** - 0.065153s.
3. **SVM (Class Weight)** - 0.066463s.
4. **MultinomialNB (SMOTE)** - 0.073863s.
5. **Logistic Regression L1 (SMOTE)** - 0.091973s.
6. **XGBoost (scale_pos_weight)** - 0.099593s.
7. **BernoulliNB (SMOTE)** - 0.115966s.
8. **GaussianNB (SMOTE)** - 0.125703s.
9. **Random Forest (SMOTE)** - 0.376555s.
10. **KNN (SMOTE)** - 26.659613s (fuera de escala).

### **Análisis Detallado por Familia de Modelos**

#### **Modelos Lineales:**
- **Logistic Regression L1 vs L2**: L1 muestra **ligera ventaja en Recall** (0.770547 vs 0.768426) mientras L2 ofrece **mejor tiempo de predicción**.
- **SVM**: **Buen equilibrio general** entre AUC-ROC (0.805641) y velocidad (0.066463s).

#### **Modelos Basados en Árboles:**
- **XGBoost**: **Máximo poder predictivo** (AUC 0.811721) con **recall excelente** (78.14%).
- **Random Forest**: **Mejor F1-Score global** (0.435008) indicando balance óptimo.
- **Decision Tree**: **Excelente Recall máximo** (78.06%) pero con buena precisión.

#### **Modelos Naive Bayes:**
- **BernoulliNB**: **Mejor rendimiento general** en la familia con AUC 0.790196.
- **MultinomialNB**: **Rendimiento sólido** (AUC 0.778285) y velocidad excelente.
- **GaussianNB**: **Especialista en recall** (85.37%) pero con precisión comprometida.

#### **KNN:**
- **Limitación crítica** en tiempo (26.66s) lo hace **impracticable** a pesar de métricas aceptables.

## **5. Hallazgos Clave y Patrones Identificados**

### **Patrones de Comportamiento por Tipo de Modelo**

1. **Modelos Lineales**: Responden mejor a **Class Weight**, mostrando **alta consistencia** entre validación y prueba.

2. **Modelos Basados en Árboles**: Prefieren **class weight**, logrando **máximo rendimiento predictivo**.

3. **Modelos Probabilísticos**: **ADASYN** optimiza su rendimiento, especialmente en BernoulliNB y MultinomialNB.

4. **Modelos de Instancia**: **KNN** muestra limitaciones prácticas severas a pesar de métricas teóricas aceptables.

### **Trade-offs Identificados:**

- **Precisión vs Recall**: Claramente demostrado en GaussianNB (alta recall, baja precisión) vs XGBoost (balance óptimo).

- **Rendimiento vs Velocidad**: Logistic Regression ofrece el mejor balance, mientras XGBoost maximiza rendimiento con costo computacional moderado.

- **Complexidad vs Interpretabilidad**: Modelos lineales ofrecen mejor interpretabilidad, ensembles mayor poder predictivo.

## **6. Estrategias de Selección por Caso de Uso**

### **Para Screening Masivo (Maximizar Recall):**
- **GaussianNB con ADASYN** (Recall: 85.37%).
- **XGBoost con scale_pos_weight** (Recall: 78.14%).
- **Decision Tree con Class Weight** (Recall: 78.06%).

### **Para Diagnóstico Confirmatorio (Maximizar Precisión):**
- **XGBoost con ADASYN** (Precision: 44.73%).
- **Random Forest con SMOTE** (Precision: 33.98%).
- ***Decision Tree con ADASYN** (Precision: 31.57%).

## **7. Impacto en Práctica Clínica y Salud Pública**

### **Implicaciones Prácticas**

1. **Estratificación de Riesgo Mejorada**: Capacidad de identificar diferentes perfiles de riesgo según el modelo seleccionado.

2. **Optimización de Recursos**: Asignación más eficiente basada en el balance precisión-recall requerido.

3. **Detección Temprana Personalizada**: Selección de modelo según características de la población objetivo.

4. **Implementación Escalable**: Modelos como SVM y Logistic Regression permiten despliegue en sistemas de salud con infraestructura limitada.

### **Consideraciones para Implementación**

- **Contexto Clínico**: Determinar si se prioriza evitar falsos negativos (alta recall) o falsos positivos (alta precisión).

- **Infraestructura Computacional**: Evaluar capacidades de procesamiento para modelos más complejos.

- **Integración con Sistemas Existentes**: Considerar tiempos de respuesta y compatibilidad.

## **8. Limitaciones y Trabajo Futuro**

### **Limitaciones Identificadas:**

1. **Precisión Moderada**: Aunque el recall mejoró significativamente, la precisión promedio alcanzada indica necesidad de mejoras adicionales.

2. **Dependencia de Preprocesamiento**: Resultados altamente dependientes de técnicas de balanceo y preprocesamiento específico.

3. **Complexidad Operacional**: La necesidad de múltiples pipelines según el modelo seleccionado.

4. **Validación Externa**: Requerido validar con datasets independientes y diversas poblaciones.

### **Direcciones Futuras**

1. **Ensembles Híbridos**: Combinar modelos complementarios (ej: GaussianNB para recall + Random Forest para precisión).

2. **Optimización Avanzada**: Técnicas como Bayesian Optimization para hiperparámetros.

3. **Feature Engineering Especializado**: Desarrollo de variables específicas para diabetes.

4. **Validación Multicéntrica**: Pruebas en diferentes poblaciones y configuraciones clínicas.

## **9. Conclusiones Finales y Recomendaciones**

### **Hallazgos Fundamentales:**

1. **El balanceo es crucial**: Mejora dramáticamente el recall, manteniendo AUC-ROC competitivo.

2. **No hay solución única**: La técnica óptima de balanceo varía significativamente por familia de modelo.

3. **Trade-offs inevitables**: La elección del modelo debe alinearse con los objetivos clínicos específicos.

4. **Velocidad vs Rendimiento**: SVM y Logistic Regression emergen como el mejor balance para aplicaciones prácticas.

### **Recomendación Final**

Para la mayoría de aplicaciones clínicas en predicción de diabetes, se recomienda la **implementación de SVM con class weigh** como solución balanceada que ofrece:
- **Alto AUC-ROC** (0.806949).
- **Excelente velocidad** (0.066463s).
- **Balance métrico sólido** (F1: 0.424811).
- **Interpretabilidad razonable**.
- **Facilidad de implementación**.

Para casos donde se priorice el **máximo rendimiento predictivo**, **XGBoost con scale_pos_weight** constituye la alternativa óptima, aceptando un modesto incremento en complejidad computacional.

Este trabajo establece un precedente metodológico para la selección sistemática de técnicas de balanceo y modelos en problemas de salud pública con desbalance de clases, proporcionando un framework replicable para futuras investigaciones en predicción de enfermedades crónicas.