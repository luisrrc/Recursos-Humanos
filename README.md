![Python](https://img.shields.io/badge/Python-blue)


# Análisis de Recursos Humanos

## Introducción / Problema de Negocio
       
Una empresa solicita ayuda debido a que muchos empleados han ido abandonando la compañía, por lo tanto, se quiere saber el por que sus empleados se van. Dado el conjunto de datos disponibles, se debe determinar un plan para utilizar el modelado de datos y así proporcionar una visión empresarial impactante.
Teniendo esto en cuenta, si se pudiera predecir las probabilidades de que un empleado renuncie, la empresa podría seleccionar a esos empleados para que reciban un trato especial.

## Data

El departamento de recursos humanos de la empresa ha compilado un conjunto de datos que creen que serán útiles para tratar con el problema. Incluye detalles de los niveles de satisfacción de los empleados, evaluaciones, tiempo de trabajo, departamento y salario.
     La empresa comparte sus datos enviando un archivo llamado hr_data.csv. Este conjunto de datos contiene las siguientes propiedades:
     
    • Filas: 15.000 muestras (registros) que representan a los empleados anteriores o actuales.
    
Columnas:  

    • left: si el empleado abandonó o no la empresa.
    
    • satisfaction_level: representa el nivel de satisfacción de cada empleado. 
    
    • last_evaluation: indica la última evaluación realizada al empleado.
    
    • average_montly_hours:  promedio de horas trabajadas al mes.
    
    • time_spend_company:  tiempo que tiene en la compañía. 
    
    • number_project:  número de proyectos realizados por cada empleado.
    
    • work_accident:  si el empleado ha tenido algún accidente en el trabajo o no.
    
    • promotion_last_5years: muestra si el empleado ha sido ascendido de cargo en los últimos cinco (5) años o no.
    
    • is_smoker: indica si el empleado es fumador o no.
    
    • department:  departamento de la empresa en el cual trabaja el empleado.
    
    • salary:  el salario que devenga cada empleado.

## Preparación de los datos

El primer paso que se utilizo fue cargar los datos usando la librería Pandas, mostrando las primeras filas para así verificar que están estructurados los datos en una tabla con sus respectivas columnas (las cuales están conformadas por cada variable necesaria para realizar el estudio) y sus filas las cuales representa a cada uno de los empleados.

Como el problema a resolver consiste en poder predecir que empleados se van a ir o no de la compañía, necesitamos revisar la columna(variable) **‘left’**, sabiendo que está compuesta por solo dos (2) clases: si el empleado se fue o no se fue. 

![image](https://user-images.githubusercontent.com/58336896/140763915-798a19df-b2d5-45bf-ba42-df8000158323.png)

La variable a predecir ‘left’ presentaba un desbalance en sus clases ya que 11428 registros pertenecen a la clase ‘no’ y 3571 registros a la clase ‘yes’. Como indica la gráfica de la imagen 1.3, esto nos dice que se tenía que tratar con un problema de clasificación desbalanceado, lo cual implica que se tendría que tomar medidas especiales para contar cada clase cuando se calcule su precisión.

Luego para buscar relaciones existentes entre las distintas variables que fueran correlativamente positivas para nuestro propósito, encontré que los resultados arrojados en la última evaluación realizada a los empleados, está altamente relacionada con su nivel de satisfacción, los cuales, a su vez, una vez asociadas mostraban relación con nuestra variable target (**‘left’**). 

## Modelado de datos

Se entrenaron varios modelos de machine learning para problemas de clasificación binarias. Para el modelo final que se eligió para producción se seleccionó un modelo de ensamble Random Forest:

![how-random-forest-classifier-work](https://user-images.githubusercontent.com/58336896/140766991-1c8212ea-2744-4df2-968a-cb0fff61a477.png)

El algoritmo **Random Forest** funciona completando los siguientes pasos:

Paso 1: El algoritmo selecciona muestras en forma aleatoria de la base de datos proporcionada.

Paso 2: El algoritmo creará un árbol de decisión para cada muestra seleccionada. Luego obtendrá un resultado de predicción de cada árbol creado.

Paso 3: A continuación, se realizará la votación para cada resultado previsto. Para un problema de clasificación, usará la moda, y para un problema de regresión, usará la media.

Paso 4: Y finalmente, el algoritmo seleccionará el resultado de predicción más votado como predicción final.

Luego de evaluar el desempeño con los datos de prueba, el modelo obtuvo una precisión del 99.59% para la clase 0 y 97.22% para la clase 1.

## Conclusión

Retomando al problema original, el cual era que la empresa quiere reducir el número de empleados que abandonan, se ha logrado crear un herramienta la cual permite con una alta precisión el poder predecir la probabilidad de que un trabajador renuncie, teniendo así la empresa la posibilidad de tener un trato especial con dicho empleado, estudiando las causas, bien sea por el salario, las horas de trabajo al mes o demás variables que estén incidiendo en el descontento del empleado, como lo vimos en el ejemplo de “María” que su promedio de horas de trabajo al mes, era muy elevado.

Luego de haber realizado varios modelos predictivos con los datos suministrados por el departamento de recursos humanos de la empresa, se logró crear una herramienta (‘rh-analisis-pca-forest.pkl’) que les permitirá a las personas encargadas teniendo prudencia y ética profesional llevar un seguimiento de todos los empleados, observando las posibles causas que les esté produciendo un descontento con la empresa y así tomar una decisión oportuna con ese empleado para evitar que abandone la compañía.
