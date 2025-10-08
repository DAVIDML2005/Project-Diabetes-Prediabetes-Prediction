# **Introducción y Contextualización**

La diabetes representa uno de los mayores desafíos de salud pública a nivel global, afectando a más de 537 millones de adultos en el mundo según la Federación Internacional de Diabetes. En Estados Unidos específicamente, aproximadamente 37.3 millones de personas padecen diabetes, lo que equivale al 11.3% de la población, mientras que 96 millones de adultos (38.0% de la población adulta) presentan prediabetes. Esta enfermedad crónica no solo impacta la calidad de vida de las personas, sino que también genera una carga económica significativa para los sistemas de salud, con un costo estimado de $327 mil millones anuales en EE. UU.

La detección temprana y la identificación de factores de riesgo modificables son cruciales para prevenir o retrasar la aparición de diabetes y sus complicaciones asociadas, como enfermedades cardiovasculares, neuropatía, retinopatía y nefropatía. En este contexto, el aprendizaje automático (Machine Learning) emerge como una herramienta poderosa para analizar patrones complejos en datos de salud y desarrollar modelos predictivos que puedan identificar individuos en riesgo.

## **Presentación del Dataset**

Este proyecto se centra en el análisis del dataset **"CDC Diabetes Health Indicators"**, recolectado por los U.S. Centers for Disease Control and Prevention (CDC) a través del sistema Behavioral Risk Factor Surveillance System (BRFSS). Este conjunto de datos representa una de las encuestas de salud más grandes a nivel mundial, con información de más de 250,000 encuestados.

El dataset incluye **21 variables** que capturan información demográfica, de comportamientos de salud, condiciones médicas y acceso a servicios de salud. La variable objetivo (`Diabetes_binary`) identifica la presencia de diabetes o prediabetes (1) versus ausencia de la condición (0).

**Dataset**: https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators  
**Codebook**: https://www.cdc.gov/brfss/annual_data/2015/pdf/codebook15_llcp.pdf

### **Clasificación de Variables**

Las variables pueden clasificarse en las siguientes categorías:

- **Variables Demográficas**: Edad (`Age`), Sexo (`Sex`), Educación (`Education`), Ingresos (`Income`).
- **Condiciones Médicas Crónicas**: Presión arterial alta (`HighBP`), Colesterol alto (`HighChol`), Antecedente de ACV (`Stroke`), Enfermedad cardíaca (`HeartDiseaseorAttack`).
- **Comportamientos de Salud**: Índice de masa corporal (`BMI`), Tabaquismo (`Smoker`), Actividad física (`PhysActivity`), Consumo de frutas (`Fruits`), Consumo de verduras (`Veggies`), Consumo de alcohol (`HvyAlcoholConsump`).
- **Acceso a Servicios de Salud**: Cobertura de salud (`AnyHealthcare`), Barreras por costo (`NoDocbcCost`), Control de colesterol (`CholCheck`).
**Mediciones de Salud Autoreportada**: Salud general (`GenHlth`), Salud mental (`MentHlth`), Salud física (`PhysHlth`), Dificultad para caminar (`DiffWalk`).

#### **Variables Demográficas**
- `Age`: Categoría de edades de 13 niveles:
    1. 18 <= AGE <= 24.
    2. 25 <= AGE <= 29. 
    3. 30 <= AGE <= 34.  
    4. 35 <= AGE <= 39. 
    5. 40 <= AGE <= 44. 
    6. 45 <= AGE <= 49. 
    7. 50 <= AGE <= 54. 
    8. 55 <= AGE <= 59. 
    9. 60 <= AGE <= 64. 
    10. 65 <= AGE <= 69.  
    11. 70 <= AGE <= 74. 
    12. 75 <= AGE <= 79. 
    13. 80 or older.
- `Sex`: (0 = female, 1 = male).
- `Education`: Nivel educativo más alto completado:
    1. Nunca asistió a la escuela o solo al jardín de infantes.
    2. Grados 1 a 8 (primaria).
    3. Grados 9 a 11 (algunos de secundaria).  
    4. Grado 12 o GED (graduado de secundaria).  
    5. Universidad 1 año a 3 años (Algunos estudios universitarios o escuelas técnicas).  
    6. Universidad 4 años o más (Graduado universitario).
- `Income`: Ingresos familiares anuales:
    1. Less than \$10,000.
    2. Less than \$15,000 (\$10,000 to less than \$15,000).
    3. Less than \$20,000 (\$15,000 to less than \$20,000). 
    4. Less than \$25,000 (\$20,000 to less than \$25,000). 
    5. Less than \$35,000 (\$25,000 to less than \$35,000). 
    6. Less than \$50,000 (\$35,000 to less than \$50,000). 
    7. Less than \$75,000 (\$50,000 to less than \$75,000). 
    8. \$75,000 or more.

#### **Condiciones Médicas Crónicas**
- `HighBP`: ¿Alguna vez un médico, enfermero u otro profesional de la salud le ha dicho que tiene presión arterial alta? (0 = no high blood pressure, 1 = high blood pressure).
- `HighChol`: ¿Alguna vez un médico, una enfermera u otro profesional de la salud le ha dicho que su colesterol en sangre es alto? (0 = no high cholesterol, 1 = high cholesterol).
- `Stroke`: ¿Alguna vez te dijeron que sufriste un derrame cerebral? (0 = no, 1 = yes).
- `HeartDiseaseorAttack`: ¿Alguna vez te dijeron que tenías angina de pecho(MI) o enfermedad cardíaca coronaria(CHD)? (0 = no, 1 = yes).

#### **Comportamientos de Salud**
- `BMI`: Índice de masa corporal.
- `Smoker`: ¿Has fumado al menos 100 cigarrillos en toda tu vida? [Nota: 5 paquetes = 100 cigarrillos] (0 = no, 1 = yes).
- `PhysActivity`: ¿Durante cuántos días durante los últimos 30 días su salud física no fue buena? (escala 0-30 días).
- `Fruits`: Consume fruta 1 o más veces al día (0 = no, 1 = yes).
- `Veggies`: Consume verduras 1 o más veces al día (0 = no, 1 = yes).
- `HvyAlcoholConsump`: Bebedores empedernidos (Hombre adulto que consume más de 14 bebidas por semana o Mujer adulta que consume más de 7 bebidas por semana) (0 = no, 1 = yes).

#### **Acceso a Servicios de Salud**
- `AnyHealthcare`: ¿Tiene algún tipo de cobertura de atención médica, incluido seguro médico, planes prepagos como HMO o planes gubernamentales como Medicare o el Servicio de Salud Indígena? (0 = no, 1 = yes).
- `NoDocbcCost`: ¿Hubo alguna ocasión en los últimos 12 meses en la que usted necesitó ver a un médico pero no pudo debido al costo? (0 = no, 1 = yes)
- `CholCheck`: Control de colesterol en los últimos cinco años (0 = no cholesterol check in 5 years, 1 = yes cholesterol check in 5 years).

#### **Mediciones de Salud Autoreportada**
- `GenHlth`: ¿Dirías que en general tu salud es?:
    1. Excelente  
    2. Muy buena  
    3. Buena  
    4. Regular  
    5. Mala  
- `MentHlth`: ¿Durante cuántos días durante los últimos 30 días su salud mental no fue buena? (escala 0-30 días).
- `PhysHlth`: ¿Durante cuántos días durante los últimos 30 días su salud física no fue buena? (escala 0-30 días).
- `DiffWalk`: ¿Tiene usted serias dificultades para caminar o subir escaleras? (0 = no, 1 = yes).

#### **Variable Objetivo**
- `Diabetes_binary`: Target (0 = no diabetes, 1 = prediabetes or diabetes).

## **Objetivos del Proyecto**

El presente proyecto tiene como objetivo general **desarrollar y evaluar modelos predictivos de aprendizaje automático para identificar factores de riesgo asociados a diabetes y prediabetes en la población estadounidense, utilizando los indicadores de salud del CDC.**

Para alcanzar este objetivo general, se han definido los siguientes **objetivos específicos**:

1.  **Análisis Exploratorio de Datos (EDA):** Exploración exhaustiva que incluye análisis de distribuciones, valores atípicos, correlaciones y reducción de dimensionalidad exploratoria para fundamentar las decisiones de modelado.

2.  **Modelado Benchmark Comprehensivo:** Implementación y comparación de algoritmos de clasificación: K-Nearest Neighbors, Naive Bayes, Regresión Logística (con regularización L1 y L2), Árbol de Decisión, Random Forest, XGBoost y Support Vector Machines.

3.  **Técnicas de Balanceo de Clases:** Evaluación de métodos como SMOTE, ADASYN o class_weight='balanced' para abordar el desbalance inherente en datos de salud y mejorar la detección de casos positivos.

4.  **Optimización Computacional:** Implementación de técnicas especializadas por modelo (KD-Trees para KNN, solvers optimizados, entrenamiento por lotes, early stopping) para acelerar el entrenamiento sin comprometer el rendimiento predictivo.

5.  **Evaluación Rigurosa de Modelos:** Uso de métricas comprehensivas (Accuracy, Precision, Recall, F1, AUC), matrices de confusión y curvas ROC, con especial atención a la sensibilidad dado el contexto médico.

6.  **Tuning e Interpretabilidad Avanzada:** Aplicación de técnicas de optimización de hiperparámetros con validación cruzada, e implementación de métodos de interpretabilidad (LIME, SHAP, feature importance) en los mejores modelos.

## **Relevancia e Impacto Potencial**

La culminación exitosa de este proyecto tiene el potencial de identificar patrones críticos y factores de riesgo modificables asociados a la diabetes, contribuyendo al desarrollo de herramientas de proyección más efectivas. Un modelo predictivo preciso podría ser utilizado por profesionales de la salud y diseñadores de políticas públicas para:

*   Identificar poblaciones de alto riesgo para intervenciones preventivas.
*   Optimizar la asignación de recursos en programas de salud pública.
*   Desarrollar estrategias personalizadas de prevención basadas en perfiles de riesgo.
*   Reducir los costos asociados al manejo de complicaciones diabéticas.

Este proyecto demuestra la aplicabilidad del machine learning en salud pública, transformando datos epidemiológicos en conocimiento accionable para combatir una de las epidemias más significativas del siglo XXI.