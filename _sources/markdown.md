# **Conclusiones y Hallazgos en los Modelados**

## **1. Logro de los Objetivos Propuestos**

El presente proyecto ha cumplido satisfactoriamente con todos los objetivos planteados inicialmente, demostrando la viabilidad de utilizar algoritmos de machine learning para la predicción temprana de diabetes y prediabetes. A través de un proceso sistemático que incluyó desde el análisis exploratorio hasta la interpretación avanzada de los modelos. Por tanto, se ha desarrollado un framework robusto capaz de identificar pacientes con alto riesgo metabólico con métricas competitivas.

## **2. Hallazgos Clínicos y Epidemiológicos Relevantes**

El análisis exploratorio y de importancia de variables reveló patrones epidemiológicos significativos que coinciden con la literatura médica existente:

- **Perfil de riesgo identificado**: Los pacientes con mayor probabilidad de diabetes presentan **edad avanzada** (categorías cat_Age_10 - cat_Age_13), **hipertensión y colesterol alto** (bin_HighBP, bin_HighChol) y **condiciones de salud general deficiente** (cat_GenHlth_4, cat_GenHlth_5).

- **Variables críticas identificadas**: Las **variables de salud general autopercibida** emergieron como los predictores más potentes acompañado de **indicadores médicos directos** (HighBP, HighChol).

- **Factores protectores consistentes**: El **consumo excesivo de alcohol** y la **pertenencia a grupos de edad jocen** se identificaron como factores protectores clave en múltiples modelos.

## **3. Análisis Comparativo de Técnicas de Balanceo por Modelo**

El análisis exhaustivo de las diferentes técnicas de balanceo reveló patrones significativos en el rendimiento de los modelos evaluados:

### **Mejor Técnica de Balanceo por Familia de Modelos**

#### **Modelos Lineales (Logistic Regression L1, L2, SVM):**
- **Class Weight ('balanced')** - Óptimo para regresión logística y SVM.
- **SMOTE** - Alternativa competitiva con buen balance general.

#### **Modelos Basados en Árboles (XGBoost, Random Forest, Decision Tree, CatBoost):**
- **scale_pos_weight (XGBoost)** - Máximo rendimiento predictivo.
- **Class Weight ('balanced')** - Excelente para Random Forest y Decision Tree.

#### **Modelos Probabilísticos (GaussianNB, BernoulliNB, MultinomialNB):**
- **SMOTE** - Superior para toda la familia Naive Bayes.
- **ADASYN** - Alternativa sólida con buena estabilidad.

#### **Modelos de Instancia (KNN):**
- **SMOTE** - Mejor rendimiento a pesar de limitaciones temporales.

### **Patrones Generales en Técnicas de Balanceo**

- **SMOTE**: Óptimo para modelos lineales, con **AUC-ROC consistentemente alto** y buen balance general. También, superior para modelos **Naive Bayes** presentando un buen balance general.

- **Class Weight y scale_pos_weight**: Superior en modelos lineales y basados en árboles, maximizando **F1-Score y AUC-ROC**.

- **Sin Balanceo**: Produjo **accuracy inflado artificialmente** con recall muy bajo, confirmando la necesidad crítica de técnicas de balanceo.

## **4. Desempeño Comparativo de los Modelos**

### **Jerarquía de Rendimiento por Métrica Clave**

#### **AUC-ROC (Capacidad Discriminativa)**
1. XGBoost (scale_pos_weight) - 0.825688.
2. Random Forest (Class Weight) - 0.822041.
3. Logistic Regression L2 (Class Weight) - 0.819243.
4. Logistic Regression L1 (Class Weight) - 0.819240.
5. Decision Tree (Class Weight) - 0.809360.
6. SVM (Class Weight) - 0.819107.
7. GaussianNB (SMOTE) - 0.789150.
8. MultinomialNB (ADASYN) - 0.787713.
9. CatBoost (SMOTE) - 0.781989.
10. BernoulliNB (SMOTE) - 0.778384.
11. KNN (SMOTE) - 0.755207.

#### **F1-Score (Balance Precision-Recall)**
1. Random Forest (Class Weight) - 0.443151.
2. Logistic Regression L1 (SMOTE) - 0.440772.
3. Logistic Regression L2 (SMOTE) - 0.440770.
4. XGBoost (scale_pos_weight) - 0.439838.
5. SVM (ADASYN) - 0.438498.
6. Decision Tree (Class Weight) - 0.427827.
7. GaussianNB (SMOTE) - 0.427725.
8. MultinomialNB (SMOTE) - 0.411253.
9. CatBoost (SMOTE) - 0.410072.
10. BernoulliNB (SMOTE) - 0.408240.
11. KNN (SMOTE) - 0.388172.

#### **Sensibilidad (Recall - Detección de Casos Positivos)**
1. XGBoost (scale_pos_weight) - 0.790918.
2. SVM (Class Weight) - 0.790494.
3. Logistic Regression L1 (ADASYN) - 0.780308.
4. Logistic Regression L2 (ADASYN) - 0.778752.
5. Random Forest (Class Weight) - 0.764747.
6. Decision Tree (Class Weight) - 0.761211.
7. GaussianNB (ADASYN) - 0.749328.
8. BernoulliNB (ADASYN) - 0.726977.
9. MultinomialNB (ADASYN) - 0.718206.
10. KNN (ADASYN) - 0.702362.
11. CatBoost (SMOTE) - 0.694582.

#### **Precision (Exactitud en Predicciones Positivas)**
1. Random Forest (Class Weight) - 0.311963.
2. Logistic Regression L2 (SMOTE) - 0.310735.
3. Logistic Regression L1 (SMOTE) - 0.310335.
4. SVM (ADASYN) - 0.305689.
5. XGBoost (scale_pos_weight) - 0.304620.
6. GaussianNB (SMOTE) - 0.304195.
7. Decision Tree (Class Weight) - 0.297523.
8. MultinomialNB (SMOTE) - 0.294308.
9. CatBoost (SMOTE) - 0.290911.
10. BernoulliNB (SMOTE) - 0.287061.
11. KNN (SMOTE) - 0.270210.

### **Análisis Detallado por Familia de Modelos**

#### **Modelos Lineales:**
- **Logistic Regression L1 vs L2**: Diferencias mínimas, L1 con ligera ventaja.
- **SVM**: **Excelente equilibrio** entre rendimiento y velocidad.

#### **Modelos Basados en Árboles:**
- **XGBoost**: **Máximo poder predictivo** con Máximo recall.
- **Random Forest**: **Mejor F1-Score** indicando balance óptimo.
- **Decision Tree**: Buen recall con simplicidad interpretativa.

#### **Modelos Probabilísticos:**
- **GaussianNB**: **Mejor rendimiento general** en la familia.
- **MultinomialNB**: **Rendimiento sólido** y velocidad excelente.
- **BernoulliNB**: **Buen recall** máximo.

#### **KNN:**
- **Limitación crítica** en tiempo lo hace impracticable.

## **5. Análisis del Caso del Paciente 30: Explicación de las Discrepancias**

### **Contexto Clínico del Paciente 30**
Mujer mayor con hipertensión, colesterol alto y dificultad para caminar, pero con comportamientos saludables (actividad física, dieta balanceada, chequeos regulares). Caso limítrofe con factores de riesgo contrapuestos.

### **Análisis de las Discrepancias entre Técnicas de Balanceo**

#### **Benchmark (Sin Balanceo):**
- **11 modelos acertaron, 1 falló**
- **Patrón**: Modelos conservadores que priorizan especificidad.
- **Razón**: Sin balanceo, los modelos aprenden a ser "cautelosos" y predecir predominantemente la clase mayoritaria (no diabetes).
- **GaussianNB falló** por su tendencia natural a sobreestimar probabilidades en clases minoritarias.

#### **SMOTE:**
- **Solo 2 modelos acertaron (XGBoost, CatBoost)**
- **Cambio radical**: La mayoría de modelos se volvieron "sensibles".
- **Explicación**: Las técnicas de sobremuestreo crean instancias sintéticas que modifican los límites de decisión.
- **XGBoost y CatBoost** mantuvieron mejor generalización por su naturaleza de ensemble robusto.

#### **Class Weight:**
- **Todos los modelos fallaron**
- **Explicación técnica**: El re-ponderación de clases hace que los modelos sean extremadamente sensibles a factores de riesgo.
- **En este paciente específico**: La combinación de HighBP=1, HighChol=1 y DiffWalk=1 superó los factores protectores.

### **Factores Clave en las Discrepancias:**

1. **HighBP y HighChol**: Variables de alto peso en todos los modelos balanceados.
2. **DiffWalk**: Indicador de comorbilidad significativa.
3. **Edad avanzada (cat_Age_10)**: Factor de riesgo consistente.
4. **Factores protectores subestimados**: Actividad física y dieta no compensaron suficientemente los riesgos.

### **Implicación Clínica:**
El paciente 30 representa exactamente el tipo de caso donde el criterio clínico humano diferiría de la predicción automatizada, destacando la necesidad de **sistemas híbridos** de decisión.

## **6. Hallazgos Clave y Patrones Identificados**

### **Patrones de Comportamiento por Tipo de Modelo**

1. **Modelos Lineales**: Responden mejor a **Class Weight**, mostrando **alta consistencia** entre validación y prueba.

2. **Modelos Basados en Árboles**: Prefieren **class weight/scale_pos_weight**, logrando **máximo rendimiento predictivo**.

3. **Modelos Probabilísticos**: **SMOTE** optimiza su rendimiento, especialmente en BernoulliNB y GaussianNB.

4. **Modelos de Instancia**: **KNN** muestra limitaciones prácticas severas.

### **Trade-offs Identificados:**

- **Rendimiento vs Velocidad**: Logistic Regression ofrece el mejor balance, mientras XGBoost maximiza rendimiento con costo computacional moderado.

- **Complexidad vs Interpretabilidad**: Modelos lineales ofrecen mejor interpretabilidad, ensembles mayor poder predictivo.

## **7. Estrategias de Selección por Caso de Uso**

### **Para Screening Masivo (Maximizar Recall):**
1. **XGBoost (scale_pos_weight)** (Recall: 790%).
2. **SVM (Class Weight)** (Recall: 79.0%).
3. **Logistic Regression L1 (ADASYN)** (Recall: 78.0%).

### **Para Diagnóstico Confirmatorio (Maximizar Precisión):**
1. **Random Forest (Class Weight)** (Precision: 31.1%).
2. **Logistic Regression L2 (SMOTE)** (Precision: 31.0%).
3. **Logistic Regression L1 (SMOTE)** (Precision: 31.0%).

### **Para Balance Óptimo General:**
1. **XGBoost con scale_pos_weight** (AUC: 0.825688).
2. **Random Forest con Class Weight** (F1-Score: 0.443151).
3. **SVM con Class Weight** (Velocidad + Rendimiento).

## **8. Impacto en Práctica Clínica y Salud Pública**

### **Implicaciones Prácticas**

1. **Estratificación de Riesgo Mejorada**: Los modelos permiten seleccionar según necesidad específica.

2. **Optimización de Recursos**: Asignación más eficiente basada en el balance precisión-recall requerido.

3. **Detección Temprana Personalizada**: Selección de modelo según características de la población objetivo.

4. **Implementación Escalable**: Modelos como SVM y Logistic Regression permiten despliegue en sistemas con infraestructura limitada.

### **Consideraciones para Implementación**

- **Contexto Clínico**: Determinar si se prioriza evitar falsos negativos (alta recall) o falsos positivos (alta precisión).

- **Infraestructura Computacional**: Evaluar capacidades de procesamiento para modelos más complejos.

- **Integración con Sistemas Existentes**: Considerar tiempos de respuesta y compatibilidad.

## **9. Limitaciones y Trabajo Futuro**

### **Limitaciones Identificadas:**

1. **Precisión Moderada**: Aunque el recall mejoró significativamente, la precisión promedio alcanzada indica necesidad de mejoras adicionales.

2. **Dependencia de Preprocesamiento**: Resultados altamente dependientes de técnicas de balanceo específicas.

3. **Validación Externa**: Requerido validar con datasets independientes y diversas poblaciones.

### **Direcciones Futuras**

1. **Ensembles Híbridos**: Combinar modelos complementarios.

2. **Feature Engineering Especializado**: Desarrollo de variables específicas para diabetes.

3. **Validación Multicéntrica**: Pruebas en diferentes poblaciones y configuraciones clínicas.

## **10. Conclusiones Finales y Recomendaciones**

### **Hallazgos Fundamentales:**

1. **El balanceo es crucial**: Mejora dramáticamente el recall, manteniendo AUC-ROC competitivo.

2. **No hay solución única**: La técnica óptima de balanceo varía significativamente por familia de modelo.

3. **Trade-offs inevitables**: La elección del modelo debe alinearse con los objetivos clínicos específicos.

4. **Los modelos evaluados ofrecen ventajas complementarias** para diferentes escenarios.

### **Recomendación Final por Escenario**

**Para la mayoría de aplicaciones clínicas** en predicción de diabetes, se recomienda la **implementación de XGBoost con scale_pos_weight** como solución óptima que ofrece:
- **Máximo AUC-ROC** (0.825688).
- **Recall excelente** (79.0%).

**Para implementaciones con restricciones computacionales**, **SVM con Class Weight** constituye la alternativa ideal:
- **Alto AUC-ROC** (0.819107).
- **Excelente velocidad** (0.036883s).
- **Balance métrico sólido** (F1: 0.435101).

Este trabajo establece un precedente metodológico para la selección sistemática de técnicas de balanceo y modelos en problemas de salud pública con desbalance de clases, proporcionando un framework replicable para futuras investigaciones en predicción de enfermedades crónicas. La evaluación de los diversos modelos permite una comprensión integral del ecosistema de algoritmos disponibles y sus aplicaciones específicas en el contexto clínico.