# Información del Dataset

## ¿Con qué propósito se creó el conjunto de datos?
Para comprender mejor la relación entre el estilo de vida y la diabetes en EE. UU.

## ¿Quién financió la creación del conjunto de datos?
U.S. Centers for Disease Control and Prevention (CDC)

## ¿Qué representan las instancias de este conjunto de datos?
Cada fila representa una persona que participa en este estudio.

## Información adicional
Dataset: https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators  
Codebook: https://www.cdc.gov/brfss/annual_data/2015/pdf/codebook15_llcp.pdf

## Lista de variables
- `HighBP`: ¿Alguna vez un médico, enfermero u otro profesional de la salud le ha dicho que tiene presión arterial alta? (0 = no high blood pressure, 1 = high blood pressure)
- `HighChol`: ¿Alguna vez un médico, una enfermera u otro profesional de la salud le ha dicho que su colesterol en sangre es alto? (0 = no high cholesterol, 1 = high cholesterol)
- `CholCheck`: Control de colesterol en los últimos cinco años (0 = no cholesterol check in 5 years, 1 = yes cholesterol check in 5 years)
- `BMI`: Índice de masa corporal
- `Smoker`: ¿Has fumado al menos 100 cigarrillos en toda tu vida? [Nota: 5 paquetes = 100 cigarrillos] (0 = no, 1 = yes)
- `Stroke`: ¿Alguna vez te dijeron que sufriste un derrame cerebral? (0 = no, 1 = yes)
- `HeartDiseaseorAttack`: ¿Alguna vez te dijeron que tenías angina de pecho(MI) o enfermedad cardíaca coronaria(CHD)? (0 = no, 1 = yes)
- `PhysActivity`: Durante el último mes, además de su trabajo habitual, ¿participó en alguna actividad física o ejercicio como correr, calistenia, golf, jardinería o caminar para hacer ejercicio? (0 = no, 1 = yes)
- `Fruits`: Consume fruta 1 o más veces al día (0 = no, 1 = yes)
- `Veggies`: Consume verduras 1 o más veces al día (0 = no, 1 = yes)
- `HvyAlcoholConsump`: Bebedores empedernidos (hombre adulto que consume más de 14 bebidas por semana y mujer adulta que consume más de 7 bebidas por semana) (0 = no, 1 = yes)
- `AnyHealthcare`: ¿Tiene algún tipo de cobertura de atención médica, incluido seguro médico, planes prepagos como HMO o planes gubernamentales como Medicare o el Servicio de Salud Indígena? (0 = no, 1 = yes)
- `NoDocbcCost`: ¿Hubo alguna ocasión en los últimos 12 meses en la que usted necesitó ver a un médico pero no pudo debido al costo? (0 = no, 1 = yes)
- `GenHlth`: ¿Dirías que en general tu salud es?:  
1 = excelente  
2 = muy buena  
3 = buena  
4 = regular  
5 = mala  
- `MentHlth`: Ahora, pensando en su salud mental, que incluye estrés, depresión y problemas emocionales, ¿durante cuántos días durante los últimos 30 días su salud mental no fue buena? (escala 0-30 días)
- `PhysHlth`: Ahora, pensando en su salud física, que incluye enfermedades físicas y lesiones, ¿durante cuántos días durante los últimos 30 días su salud física no fue buena? (escala 0-30 días)
- `DiffWalk`: ¿Tiene usted serias dificultades para caminar o subir escaleras? (0 = no, 1 = yes)
- `Sex`: (0 = female, 1 = male)
- `Age`: Categoría de edades de 13 niveles   
1: 18 <= AGE <= 24  
2: 25 <= AGE <= 29  
3: 30 <= AGE <= 34  
4: 35 <= AGE <= 39  
5: 40 <= AGE <= 44  
6: 45 <= AGE <= 49  
7: 50 <= AGE <= 54  
8: 55 <= AGE <= 59  
9: 60 <= AGE <= 64  
10: 65 <= AGE <= 69  
11: 70 <= AGE <= 74  
12: 75 <= AGE <= 79  
13: 80 or older
- `Education`: ¿Cuál es el grado o año de escuela más alto que completaste?  
1: Nunca asistió a la escuela o solo al jardín de infantes  
2: Grados 1 a 8 (primaria)  
3: Grados 9 a 11 (algunos de secundaria)  
4: Grado 12 o GED (graduado de secundaria)  
5: Universidad 1 año a 3 años (Algunos estudios universitarios o escuelas técnicas)  
6: Universidad 4 años o más (Graduado universitario) 
- `Income`: Ingresos familiares anuales  
1: Less than \$10,000  
2: Less than \$15,000 (\$10,000 to less than \$15,000)  
3: Less than \$20,000 (\$15,000 to less than \$20,000)  
4: Less than \$25,000 (\$20,000 to less than \$25,000)  
5: Less than \$35,000 (\$25,000 to less than \$35,000)  
6: Less than \$50,000 (\$35,000 to less than \$50,000)  
7: Less than \$75,000 (\$50,000 to less than \$75,000)  
8: \$75,000 or more
- `Diabetes_binary`: Target (0 = no diabetes, 1 = prediabetes or diabetes)