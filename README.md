**Movilidad urbana y desempeño económico en Latinoamérica (2024)**

Análisis exploratorio de datos | Python · Pandas · Seaborn · Matplotlib

**Descripción del proyecto**

En este proyecto exploro la relación entre la movilidad urbana y los indicadores económicos de **15 ciudades latinoamericanas durante 2024**. Me interesa identificar diferencias en las condiciones del tráfico y examinar si el PIB per cápita presenta alguna asociación con los retrasos asociados a la congestión.

El análisis se plantea como un ejercicio de evaluación de infraestructura urbana, tomando como referencia un escenario de interés para el Banco Interamericano de Desarrollo (BID). No es un estudio encargado ni avalado por el BID.

**Objetivo**

Preparar e integrar información de movilidad y economía para responder a la siguiente pregunta:
¿Qué relación se observa entre el PIB per cápita y el indicador de retrasos por congestión (jams_delay) en las ciudades de la muestra?

**Datos y alcance**

Utilicé dos conjuntos de datos identificados en el Notebook como:
- **TomTom Traffic Index:** registros de movilidad, congestión y tiempos de desplazamiento.
- **OECD Cities:** indicadores económicos y sociodemográficos, como PIB per cápita, desempleo, población y PM2.5.
  
El conjunto original de movilidad contiene **1,004,464 registros** y el económico **30 registros**. Después de filtrar el año 2024, quedaron **886,779 registros de movilidad** y **15 registros económicos**. Resumí los datos de tráfico a nivel ciudad-país-año, obteniendo **387 registros**, y los integré con el conjunto económico.

El conjunto integrado final contiene **15 registros y 14 columnas**, sin valores nulos en la comprobación realizada. Los resultados se refieren únicamente a las ciudades incluidas en esa muestra; no representan a todas las ciudades de Latinoamérica.

**Herramientas y habilidades aplicadas**

- **Python y Pandas:** exploración de DataFrames, limpieza de tipos de datos, manejo de fechas, groupby(), agregaciones, merge() y exportación de CSV.
- **Matplotlib y Seaborn:** diagramas de caja, histogramas y gráficos de dispersión.
- **Estadística descriptiva:** promedios, análisis de distribuciones, identificación de valores atípicos y correlación de Pearson.
- **Comunicación analítica:** interpretación de resultados y reconocimiento de limitaciones.

**Metodología**

1. **Exploración inicial:** revisé la estructura y los tipos de datos de los dos conjuntos.
2. **Limpieza y estandarización:** normalicé los nombres de columnas a snake_case, convertí fechas e indicadores económicos y preparé la población en habitantes.
3. **Selección temporal:** filtré los registros correspondientes a 2024.
4. **Resumen de movilidad:** calculé promedios de siete indicadores por ciudad, país y año.
5. **Integración:** realicé un inner join por ciudad y año, comprobando dimensiones, valores faltantes y coincidencias de claves.
6. **Exploración visual y estadística:** analicé las distribuciones de jams_delay y del PIB per cápita, elaboré un gráfico de dispersión y calculé la correlación de Pearson.
7. **Exportación:** guardé y volví a leer un CSV con el conjunto integrado para comprobar su estructura.

**Principales hallazgos**

- **Retrasos por congestión:** Ciudad de México presentó el valor medio más alto de jams_delay dentro de las 15 ciudades integradas, aproximadamente 2,833. El promedio de este indicador en la muestra fue 629.52, con una distribución asimétrica influida por valores elevados.
- **Diferencias económicas:** el histograma del PIB per cápita mostró una concentración de observaciones aproximadamente entre 10,000 y 14,000, junto con diferencias considerables entre ciudades.
- **Asociación débil:** la correlación de Pearson entre city_gdp_capita y jams_delay fue r = 0.283. El resultado indica una asociación lineal positiva débil en la muestra, pero no establece causalidad ni permite afirmar que las ciudades con mayor PIB per cápita tengan necesariamente mayor congestión.

**Conclusión y siguientes pasos**

La relación entre PIB per cápita y retrasos por congestión **no presenta un patrón lineal fuerte** en estas 15 ciudades. El análisis es exploratorio: conviene ampliar la muestra, examinar la influencia de observaciones extremas e incorporar variables como densidad poblacional, oferta de transporte público e infraestructura vial antes de formular recomendaciones de inversión específicas.

También sería útil analizar varios años y verificar que las unidades y definiciones de cada indicador de movilidad sean comparables entre ciudades.

**Archivos del repositorio**

Archivo	Contenido
[`mobility_economy_project_analysis.ipynb`](mobility_economy_project_analysis.ipynb)	Notebook con preparación, integración, gráficos y conclusiones.
[`ladb_mobility_economy_2024_clean.csv`](ladb_mobility_economy_2024_clean.csv)	Conjunto integrado de 2024: 15 registros y 14 columnas.


**Reproducción del análisis**

El Notebook original se ejecutó en el entorno de **TripleTen/JupyterHub**, donde los archivos de entrada se leen desde estas rutas:

traffic = pd.read_csv('/datasets/tomtom_traffic.csv')
eco = pd.read_csv('/datasets/oecd_city_economy.csv')

Para reproducir **todo el procesamiento desde cero** en otro entorno, es necesario contar con los dos CSV originales y modificar esas rutas a su ubicación local. Estos archivos de entrada **no forman parte del repositorio actual**. También se requieren Python, Pandas, NumPy, Matplotlib y Seaborn en versiones compatibles.

El archivo CSV integrado incluido en este repositorio permite consultar los datos preparados para la etapa de análisis, aunque **no sustituye los archivos originales** para reproducir la limpieza y la integración.

**Limitaciones**

- La muestra integrada contiene solo **15 ciudades**.
- El análisis corresponde a **2024**; no permite evaluar cambios a lo largo del tiempo.
- La correlación observada no implica causalidad y puede verse afectada por valores atípicos.
- El cruce de fuentes se realizó con "city" y "year"; se recomienda verificar también las correspondencias de país en futuros refinamientos.
- Las unidades exactas de "jams_delay" deben corroborarse en la documentación de origen antes de interpretarlo como minutos u otra unidad temporal.
  
*Proyecto de portafolio de análisis de datos. Elaborado con fines de aprendizaje y demostración de habilidades técnicas y analíticas.*
