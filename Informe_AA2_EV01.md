# Actividad de aprendizaje AA2 EV01

##### Presentado por: Andrés Fernando Barona Figueroa

### Aprendizaje no supervisado K-means
#### Introducción
En el presente informe se aplica el algoritmo de aprendizaje no supervisado realizando una clusterización mediante el método **K-means** y se documentan los resultados encontrados en el dataset llamado _**Mall_Customers.csv**_ que se puede encontrar en la siguiente dirección:
https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-Python
#### Metodología
Para el agrupamiento de datos mediante la técnica de aprendizaje no supervisado **K-means** el entorno de trabajo utilizado fue la aplicación **Anaconda** con la interfaz gráfica de **Jupiterlabs** que permite la ejecución y visualización de códigos **Python** y se siguió el siguiente procedimiento:
* Preparación de datos.
* Exploración de datos.
* Aplicación de algoritmo no supervisado **K-means**.
* Conclusiones.
#### Preparación de datos
Se realizó la importación de las siguientes librerías:
* Pandas
* Seaborn
* matplotlib
* Sklearn

![Importación de librerías](https://i.postimg.cc/xTfc4y92/import-lib1.png)

![Importación de librerías2](https://i.postimg.cc/HsYVh4TC/import-lib2.png)

![Importación de librerías 3](https://i.postimg.cc/CxkMMmCn/Import-lib-3.png)

Se importó el archivo _**Mall_Customers.csv**_ y se asignó el dataframe a la variable _df_

![Cargue de datos](https://i.postimg.cc/YqTfKs0c/carguedatos.png)
![Cargue de datos 2](https://i.postimg.cc/qqTXYmLr/carguedatos2.png)

#### Exploración de los datos

Se realizó el reconocimiento de los datos contenidos en el archivo _**Mall_Customers.csv**_ y se identificó un total de 200 registros contenidos en 5 columnassiendo:
1. Cuatro (4) Variables numéricas: CustomerId, Age, Annual Income(k$) y Spending Score (1-100)
2. Una (1) variable categórica: Gender

Como se evidencia a continuación:

![Datos inicial](https://i.postimg.cc/s2kv9JSp/18-inicial.png)

Sepresenta la distribución de las variables separadas por género y la relación entre variables:

![Datos gráfica](https://i.postimg.cc/CdTBhsMD/17-expl-datos.png)

Se presenta la matriz de correlación la cual nos indica que existe una baja correlación entre las variables del dataset:

![Correlación](https://i.postimg.cc/T1W0N0H3/19-correlaci-n.png)

#### Aplicación de algoritmo no supervisado K-means

1. **Obtención de muestra de prueba**

Mediante el siguiente código una muestra de prueba aleatoria a partir del dataframe inicial:

![Muestra de prueba](https://i.postimg.cc/SQYxtSX5/datos-prueba.png)

_df_train:_ Se utilizó para entrenar el modelo.
_df_test:_ Se utilizó para probar el modelo

2. **Eliminación de variables que no aportan al modelo.**

![Eliminación variables](https://i.postimg.cc/7h59SCmk/eliminacion-variables.png)

3. **Escalamiento de datos**

En el dataset obtenido las variables no se encuentran en escalas superiores a los cientos por lo que no se considera necesario realizar este procedimiento.

4. **Obtención de valor óptimo K, entrenamiento del modelo, obtención de centroides y predicción**

Para nuestro par de variables Edad vs ingreso aplicamos el algoritmo **K-means** de la siguiente forma:

**4.1 Obtención valor K:**
Seleccionamos las variables Edad (Age) e Ingreso anual  (Annual Income(k$)) del conjunto de entrenamiento **df_train** y aplicamos el amodelo K-means para determinar el número de clústers ideal **K**.

![K edad vs ingreso](https://i.postimg.cc/3JgxC3Nf/7-edadvsingreso.png)
![Gráfica codo edad vs ingreso](https://i.postimg.cc/SRvNJttb/8-K-edad-vs-ingreso.png)

**4.2 Obtención coordenadas centroides**

Determinado valor **K=4** aplicamos el modelo **K-mean** para hallar los centroides de entrenamiento:

![centroides](https://i.postimg.cc/hvZPXPPH/9-centroides.png)

**4.3 Visualización de los clústers de entrenamiento**

![Visualización clusters entrenamiento](https://i.postimg.cc/0jXWFhcV/10-clusters-entrenamiento.png)

**4.4 Predicción sobre la muestra de prueba:**
Se aplicó el modelo K-Means previamente entrenado sobre el conjunto de prueba (df_test), utilizando las variables Edad e Ingreso anual.

El modelo asignó a cada individuo un número de clúster (Cluster_Pred) de acuerdo con la cercanía de sus características a los centroides previamente calculados durante el entrenamiento, de esta manera, se evaluó si los nuevos datos (no vistos por el modelo) presentan una distribución similar a la observada en el conjunto de entrenamiento
![Prueba edad vs ingreso](https://i.postimg.cc/QxpSp9rz/11-prueba-1.png)
![Visualización prueba edad vs ingreso](https://i.postimg.cc/63n4DZc0/12-visualizaci-n-prueba-1.png)

Al comparar las asignaciones de clúster entre el conjunto de entrenamiento y la muestra de prueba, se observa que los nuevos datos se agrupan de manera coherente con los patrones previamente identificados. Esto sugiere que el modelo generaliza adecuadamente y que los centroides definidos representan bien la estructura de los datos.

**4.5 Aplicación del modelo a la totalidad de los datos**

Una vez validado el desempeño del algoritmo, se procedió a entrenar nuevamente el modelo con el total de los datos disponibles, con el fin de obtener los centroides finales y realizar la visualización global de los clústeres, representando de manera más completa la estructura del conjunto de datos.

![Total edad vs ingresos](https://i.postimg.cc/8PbFLWZr/13-total-edad-vs-ingresos.png)

![Gráfica total edad vs ingresos](https://i.postimg.cc/BbpqP5JZ/14-edad-vs-ingreso-total.png)

**4.6 Aplicación del modelo a la totalidad de los datos**

Se aplicó el procedimiento descrito en los puntos 4.1 a 4.5 para las siguientes combinaciones de variables con el fin de analizar diferentes relaciones entre las características del conjunto de clientes:

**Edad vs Calificación**
![Gráfica edad vs calificación](https://i.postimg.cc/15HYNCwh/15-edad-vs-calif.png)

**Ingreso anual vs Calificación**

![Gráfica ingreso vs calificación](https://i.postimg.cc/KcWKfxbm/16-ingreso-vs-calificaci-n.png)

En ambos casos se determinó el valor óptimo de K mediante el método del codo, se entrenó el modelo **K-Means** y se visualizaron los clústeres resultantes.

#### Conclusiones

El análisis mediante el algoritmo ***K-Means** permitió segmentar los clientes del centro comercial a partir de las variables Edad, Ingreso anual y Calificación de gasto.

Al aplicar el modelo sobre los diferentes pares de variables se obtuvo que:

**Edad vs Ingreso anual:**
Se identificaron cuatro grupos diferenciados:
Los clústeres muestran una clara separación entre clientes jóvenes con ingresos medios, adultos con ingresos altos y grupos con ingresos bajos.

**Edad vs Calificación:**
La segmentación muestra que los clientes jóvenes tienden a presentar mayores calificaciones de gasto, lo que podría reflejar un comportamiento de consumo más activo. por otra parte, los clientes de mayor edad se concentran en clústeres con calificaciones bajas o moderadas, posiblemente por patrones de consumo más conservadores.

**Ingreso anual vs Calificación:**
En esta relación se observó una segmentación muy marcada:
1. Clientes con ingresos bajos y altos con calificación baja
2. Clientes con ingresos medios y calificación media
3. Clientes con ingresos bajos y altos con calificación alta

El modelo mostró buena capacidad de generalización al aplicarse sobre datos de prueba y sobre el conjunto completo, manteniendo coherencia en las asignaciones de clúster.

Estos resultados pueden servir como base para estrategias de marketing personalizadas, enfocadas en cada segmento de clientes según su nivel de ingreso, edad y propensión al gasto.






