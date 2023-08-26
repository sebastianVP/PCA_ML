# ANALISIS DE COMPONENTE PRINCIPAL - PCA
***
Este es un metodo estadistico cuya utilidad radica en la reduccion de la dimensionalidad de la base de datos(BDD) con la que estamos trabajando
Esta tecnica se tuiliza cuando queremos simplificar la base de datos ya sea para elegir un menor numero de predictores para pronosticar una variable objetivo, o para comprender una BDD de una forma mas simple.

Por lo general este caso seria aplicable para cualquier problema  que tengamos con un dataset y se recomendaria
analizar las variables disponibles antes de utilizar algoritmos de CLUSTERING(Kmeans, jerarquico, DBSCAN..)

La tecnica PRINCIPAL COMPONENTE ANALYSIS forma parte de los algortimos de aprendizaje no supervisado de MACHINE LEARNING,
y se utilizaria con aquellas variables numericas disponibles.

## COMO USAR UN PCA?

PARA poder utilizar PCA, se requiere del uso del algebra lineal, algo que la mayoria de softwares como R y Python tienen implementado en sus librerias. En el caso que nos ocupa, Google Cloud Platform nos permite realizar PCA en BigQuery mediante unas sencillas consultas gracias a la potencia de BigQuery Machine Learning(Bigquery ML)

## EXPLICACION MATEMATICA DE PCA

Matematicamente se necesitarian Vectores propios(eigenvectores) y valores propios(eigenvalues) de la matriz de correlaciones o de la matriz de varianzas-covarianas de las variables.
Los eigenvectores de una matriz son todos aquellos vectores que, al multiplicarlos por dicha matriz, resultan en el mismo vector o en un multimo entero del mismo.
Los eingenvalues son el resultado de multiplicar la matriz por cada eigenvector..
En definitiva a todo eigenvecto le corresponde un eigenvalue y viceversa.

## Los eigenvalues y el comportamiento de variables

Con los eigenvalues obtendriamos la proporcion de varianza explicada por cada componente. Sabiendo que la suma de los eigenvalues es el total de varianza explicada, se busca siempre maximizar este % con la suma de los componente. 
Es importante que en este proceso se seleccionen solo aquellos componente que mas aporten al total de la varianza explicada. Normalmente se aconseja llegar al menos al 80% del total de vairanza explicada.
LLegar al 80% significa reduccion de dimensionalidad y del conjunto de datos original.

Con los eigenvectores analizariamos como se comportan las variables en los distintos componentes y aportariamos una definicipin a los mismo.
Cabe decir que la definicion de los componente en base a los eigenvectores se vuelve mas dificil cuanto menos son los eigenvalues, es decirm cuanto menos explique el componente concreto.

## COMO SE IMPLEMENTA PCA EN GOOGLE BigQuery?
Para llevar a cabo este experimento en GoogleCloud, se ha utilizado el proyecto BigQuery gratuido biquery-publica-data, del cual hemos utilizado la tabla natality perteneciente al dataset samples.

###DISPONIBILIDAD DEL DATO
La tabla natality contiene las caracteristicas de una gran cantidad de nacimientos, combinando 
variables continuas(año, peso,edad de los progenitores...) y variables discretas(ubicacion, raza del bebe y los padres...)

*Supongamos* que nuestro objetivo es determinar si el sexo del recien nacido(variable is_male)
viene motivado por alguna causa explicable con los datos disponibles.

*Planteamos que el sexo depende de la edad de los padres, el perso, las semanas de gestacion y los hijos totales de la madre*. Para ello vamo a crear una tablad  ad hoc con estas variables en nuestro dataset de pruebas.


