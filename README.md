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

Luego para buscar relaciones existentes entre las distintas variables que fueran correlativamente positivas para nuestro propósito, encontré que los resultados arrojados en la última evaluación realizada a los empleados, está altamente relacionada con su nivel de satisfacción, los cuales, a su vez, una vez asociadas mostraban relación con nuestra variable target (‘left’). 
