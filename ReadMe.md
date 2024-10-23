
# HENRY LABS: Proyecto Individual N°2
## Homicidios por Accidentes Viales en la Ciudad Autónoma de Buenos Aires Argentina (2016-2021)

![Portada](4.%20Imágenes/Portada.png)


## 1) INTRODUCCIÓN  Y CONTEXTO

Este proyecto se desarrolló con la simulación del rol de un analista de datos en una consultora llamada "DATAlytics" y tiene como objetivo llevar a cabo un análisis de datos solicitado por el Observatorio de Movilidad y Seguridad Vial (OMSV), que forma parte de la Secretaría de Transporte del Gobierno de la Ciudad Autónoma de Buenos Aires (CABA).

El propósito principal del proyecto es generar información que respalde la toma de decisiones en materia de prevención y mejora de la seguridad vial, así como la reducción de accidentes viales con víctimas fatales en la Ciudad de Buenos Aires.

Las tasas de mortalidad asociadas a siniestros viales son un indicador clave para evaluar la seguridad vial en una región. Estas tasas suelen calcularse como el número de muertes por cada cierta cantidad de habitantes o vehículos registrados. La disminución de estas tasas es fundamental para fortalecer la seguridad vial y proteger la vida de los ciudadanos en la ciudad.

Para lograr este objetivo, se utilizan datos provenientes de un conjunto de información sobre homicidios relacionados con siniestros viales en la Ciudad de Buenos Aires, correspondiente a los años 2016-2021. Este dataset es de acceso público y se encuentra disponible en el sitio oficial de CABA.

 **Sitio Oficial de CABA**: **[Link]( https://data.buenosaires.gob.ar/dataset/victimas-siniestros-viales)**


(Asimismo se encuentran dichos archivos dentro del apartado "1. Bases de datos" del proyecto.)


## 2) ETAPA DE ANALISIS DE DATOS (ETL & EDA)

### `DATASETS`:

Los principales datasets sobre los que trabajaremos son los siguientes:
* HECHOS: contiene una fila por hecho con id único y las variables asociadas: temporales, espaciales Y participantes.
* VICTIMAS: contiene una fila por cada víctima de los hechos junto con sus variables asociadas: edad, sexo y modo de desplazamiento . 
Se vincula a los hechos mediante el ID del hecho.

Asimismo se cuenta con dos archivos complementarios:
* DICCIONARIO_HECHOS: contiene las definiciones de cada variable de la solapa HECHOS y las definiciones de los distintos valores de cada variable.
* DICCIONARIO_VICTIMAS: contiene las definiciones de cada variable de la solapa VICTIMAS y  las definiciones de los distintos valores de cada variable

**Fuente**: [Archivo PDF con detalle](https://cdn.buenosaires.gob.ar/datosabiertos/datasets/transporte-y-obras-publicas/victimas-siniestros-viales/NOTAS_SINIESTROS_VIALES_2019-2023.pdf)

### `ETL y EDA`:
El nootbook desarrollado se estructura de la siguiente manera:
   
   * `Introducción`:
        * 1) Librerías utilizadas en el proyecto:
               * Pandas
               * Numpy
               * ydata_profiling
               * MatplotLib
               * Seaborn
               * squarify
               * folium
        * 2) Importación de datasets
        * 3) Descripción general de los datasets.
   * `HECHOS`: Se hace foco específicamente en este Dataset.
        * 4) Se realiza un análisis generalizado: Se hace uso de ProfileReport de la librería ydata_profiling (anteriormente conocida como pandas_profiling), para poder tener una visión preliminar de los datos
        * 5) Análisis univariable: Ya se analiza cada variable en mayor profundidad, analizando nulos, duplicados, outliers. Se realizan gráficas para poder reflejar de forma visual y que facilite la interpretación de los datos, para ir dando claridad a los datos y que sea factible la toma de decisiones posteriormente.
   * `VICTIMAS`: Al igual que en el Dataset anterior se divide en dos el análisis.
        * 6) Se realiza un análisis generalizado: Se hace uso de ProfileReport de la librería ydata_profiling (anteriormente conocida como pandas_profiling), para poder tener una visión preliminar de los datos
        * 7) Análisis univariable: Ya se analiza cada variable en mayor profundidad, analizando nulos, duplicados, outliers. Se realizan gráficas para poder reflejar de forma visual y que facilite la interpretación de los datos, para ir dando claridad a los datos y que sea factible la toma de decisiones posteriormente.
   * `VICTIMAS y HECHOS: Análisis y relaciones entre variables`
        * 8) Combinación de datasets y Unificación de columnas: Se combina ambos datasets para su mejor análisis y se unifican columnas que tienen los mismos datos


        *    Se considera oportuno dividir el análisis en 3 aspectos:
        * 9) Temporal: Se realiza este análisis en busca de obtener conclusiones  sobre posibles tendencias temporales y/o estacionales que nos permitan tomar medidas consistentes al resultado del mismo.
        * 10) Geográfico:  Se realiza este análisis de las variables geográficas que nos permitirá identificar patrones espaciales en la ocurrencia de accidentes de tráfico, lo cual es fundamental para diseñar estrategias de prevención y mitigación más efectivas
        * 11) Participantes:  Se realiza el presente análisis para proporcionar una comprensión integral de los factores que contribuyen a la vulnerabilidad en accidentes viales, centrándose en las víctimas y sus interacciones con los acusado

### `CONCLUSIONES POST EDA`:
* Temporal:


![Estructura](4.%20Imágenes/Imagen1.png)
![Estructura](4.%20Imágenes/Imagen2.png)

Conclusiones:
1.	Alta Variabilidad: El número de victimas no sigue un patrón lineal o estacional claro. Existen meses con cifras muy superiores a la media y otros con cifras significativamente inferiores.
2.	Tendencia a Largo Plazo: A pesar de las fluctuaciones, se aprecia una tendencia general a la baja en los últimos 3 años, sobre todo en 2020 posiblemente a causa de la pandemia, pero con un gran sobre salto en Diciembre del mismo año.
3.	Presencia de Picos: Se identifican meses con un número de homicidios significativamente superior a la media (picos superiores), así como meses con cifras muy inferiores (picos inferiores).Sin embargo la media puede verse afectada por los valores extemos (inferiores) de la pandemia.
4. No se observan patrones repetidos sino una gran variabilidad en el número de víctimas a lo largo del tiempo, tanto a nivel mensual como anual

![Estructura](4.%20Imágenes/Imagen3.png)

![Estructura](4.%20Imágenes/Imagen4.png)

Conclusiones:
1.	Distribución por Hora: Se observa un pico en el número de homicidios durante las horas nocturnas, especialmente entre las 5 AM y las 7 AM, concentrado aún mas los Fines de semana como se puede ver en el segundo gráfico.
2.	Distribución por Día de la Semana: Los fines de semana, especialmente los sábados y domingos, muestran los índices altos de homicidios. Esto podría estar relacionado con el aumento de la actividad social y el consumo de alcohol durante estos días. Los lunes también tienen valores altos. Sin embargo, a grandes rasgos se presenta una distribución más uniforme, aunque con una ligera tendencia a la baja durante la semana en comparación con los fines de semana.
3.	Distribución por Mes: Se observa una variabilidad en el número de homicidios a lo largo de los meses del año, con un patrón estacional hacia fin de año, sobre todo Noviembre y Diciembre.
4.	Distribución por Año: Si bien hay fluctuaciones anuales, se puede apreciar una tendencia general hacia la baja, sobre todo en los últimos tres  años.


* Geográfico:

![Estructura](4.%20Imágenes/Imagen5.png)
![Estructura](4.%20Imágenes/Imagen6.png)

Conclusiones: 
1. Mediante el mapa se pueden ver de color rojo la zonas con mas de accidentes fatales. 
2. Y en el segundo podemos ver las comunas con mayor cantidad de víctimas, estando entre las más afectadas Comuna 1, 4 y 9

* Participantes (Victimas y Acusados):

![Estructura](4.%20Imágenes/Imagen7.png)
![Estructura](4.%20Imágenes/Imagen8.png)

Conclusiones:
1. Se puede observar como el rango etario con mayor concentración de víctimas es entre 21 y 40 años.
2. A su vez el género masculino es ampliamente superior al femenino, dicha brecha se acentua más entre 21 y 40 años y luego tiende a elquilibrarse despues de los 60 años.
3. Se observa que en el rol de víctima son MOTOS y PEATONES, los más afectados. Y en cuanto a acusados se destacan sobre el resto TRANSPORTES PÚBLICOS Y AUTOS.
4. Se puede observar como la mayor cantidad de víctimas se da en las siguientes relaciones ACUSADO - VICTIMA:
* PEATON-TRANSPORTE_PUBLICO    105
* MOTO-AUTO                     84
* MOTO-CARGAS                   80
* PEATON-AUTO                   79

## 3) ESTRUCTURA & PREGUNTAS CLAVES:
Se segmenta el análisis en 3 grandes grupos:
  * TEMPORAL
  * GEOGRÁFICO
  * PARTICIPANTES
Una vez organizada la estructura, se desarrollan interrogantes a reponder luego del análisis de datos, y los que nos permitiran llegar a conclusiones y recomendaciones.

![Estructura](4.%20Imágenes/Estructura.png)


## 4) DESARROLLO DE TABLERO INTERACTIVO MEDIANTE POWER BI:

### `ANÁLISIS TEMPORAL`:
 Se realiza este tablero en busca de obtener y mostrar conclusiones sobre posibles tendencias temporales y/o estacionales que nos permitan tomar medidas consistentes al resultado del mismo.

![Estructura](4.%20Imágenes/1Temporal.png)

### `ANÁLISIS GEOGRÁFICO`:
Se realiza el análisis de las variables geográficas que nos permitirá identificar patrones espaciales en la ocurrencia de accidentes de tráfico, lo cual es fundamental para diseñar estrategias de prevención y mitigación efectivas.

![Estructura](4.%20Imágenes/2Geografico.png)

### `ANÁLISIS SOBRE PARTICIPANTES`:
 Se realiza el presente análisis para proporcionar una comprensión integral de los factores que contribuyen a la vulnerabilidad en accidentes viales, centrándose en las víctimas y sus interacciones con los acusado. Identidicando perfiles de riesgo, para sectorizar correctamente las medidas a tomar.

![Estructura](4.%20Imágenes/3Participantes.png)

### `MÉTRICAS Y KPI'S`:
Se procede a medir y gráficar tres KPIs:
  - Reducir en un 10% la tasa de homicidios en siniestros viales semestralmente, en CABA, en comparación con la tasa de homicidios en siniestros viales del semestre anterior. Entendiéndose como tasa de homicidio como el número de víctimas fatales en accidentes de tránsito por cada 100,000 habitantes, en el periodo bajo análisis.
  - Reducir en un 7% la cantidad de accidentes mortales de motociclistas de forma anual, en CABA, comparada con el año anterior.
  - Reducir en un 15% la cantidad de accidentes mortales de peatones de forma anual, en CABA, comparada con el año anterior. 

![Estructura](4.%20Imágenes/4KPI.png)

## 5) CONCLUSIONES & RECOMENDACIONES:
En funcióna los principales interrogantes que se hicieron previos al análsis, se le da respuesta a cada uno de ellos y en base a los conclusiones obtenidas se procede a dar algunas recomendaciones para cada una de las áreas evaladas.

![Concluisiones](4.%20Imágenes/Conclusiones.png)

## 6) CONTACTO & CONSULTAS:
* Nombre compelto: Maillen Fiorio Espinasse
* Mail: maillenfiorio@gmail.com
* Enlace a [LINKEDIN](www.linkedin.com/in/maillen-fiorio-data)
