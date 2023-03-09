# Exploración de datos con NumPy y Pandas

Los científicos de datos pueden usar diversas herramientas y técnicas para explorar, visualizar y manipular datos. Una de las formas más comunes en las que los científicos de datos trabajan con los datos es mediante el lenguaje de programación Python y algunos paquetes específicos para el procesamiento de datos.

# ¿Qué es NumPy?

NumPy es una biblioteca de Python que ofrece una funcionalidad comparable a la de herramientas matemáticas como MATLAB y R. Aunque NumPy simplifica considerablemente la experiencia del usuario, también ofrece funciones matemáticas completas.

# ¿Qué es Pandas?

Pandas es una biblioteca de Python muy conocida para el análisis y la manipulación de datos. Pandas es como el Excel de Python: proporciona una funcionalidad fácil de usar para las tablas de datos.

![Table](https://learn.microsoft.com/es-es/training/modules/explore-analyze-data-with-python/media/2-pandas-df.png)

# Exploración de datos en un cuaderno de Jupyter Notebook

Los cuadernos de Jupyter Notebooks son una forma conocida de ejecutar scripts básicos mediante el explorador web. Normalmente, estos cuadernos son una sola página web, dividida en secciones de texto y secciones de código que se ejecutan en el servidor en lugar de en la máquina local. Esto significa que puede empezar a trabajar rápidamente sin necesidad de instalar Python u otras herramientas.

# Prueba de hipótesis

La exploración y el análisis de datos suele ser un proceso iterativo en el que el científico de datos toma una muestra de los datos y realiza las siguientes tareas para analizarlos y probar una hipótesis:

* *Limpiar los datos* para controlar errores, valores que faltan y otros problemas.

* *Aplicar técnicas estadísticas para comprender mejor los datos* y cómo se puede esperar que la muestra represente la población de datos del mundo real, teniendo en cuenta la variación aleatoria.

* *Visualizar los datos* para determinar las relaciones entre variables y, en el caso de un proyecto de aprendizaje automático, identificar las características que potencialmente se pueden predecir de la etiqueta.

* *Revisión de hipótesis y repetición del proceso*.



# Visualización de datos

Los científicos de datos visualizan los datos para comprenderlos mejor. Esto puede significar examinar los datos sin procesar, las medidas de resumen, como las medias, o trazar los datos. Los gráficos son un poderoso medio de visualización de datos, ya que podemos discernir rápidamente patrones medianamente complejos sin necesidad de definir medidas matemáticas de resumen.

# Representación visual de los datos

Representar los datos visualmente normalmente significa representarlos en gráficos. Esto se hace para proporcionar una evaluación cualitativa rápida de nuestros datos, que puede ser útil para entender los resultados, encontrar valores atípicos, comprender cómo se distribuyen los números, etc.

Aunque a veces sabemos de antemano qué tipo de gráfico será más útil, otras veces utilizamos los gráficos de forma exploratoria. Para entender el poder de la visualización de datos, considere los datos siguientes: la ubicación (x,y) de un coche que se conduce automáticamente. En su forma sin procesar, es difícil ver patrones reales. La media o promedio, nos dice que su trayectoria giró en torno a x=0,2 e y=0,3, y el intervalo de números parece estar entre -2 y 2 aproximadamente.

| Time | Ubicación X | Ubicación Y |
| --- | --- | --- |
| 0 | 0 | 2 |
| 1 | 1,682942 | 1,080605 |
| 2 | 1,818595 | -0,83229 |
| 3 | 0,28224 | -1,97998 |
| 4 | -1,5136 | -1,30729 |
| 5 | -1,91785 | 0,567324 |
| 6 | -0,55883 | 1,920341 |
| 7 | 1,313973 | 1,507805 |
| 12 | 0,00001 | 0,00001 |
| 13 | 0,840334 | 1,814894 |
| 14 | 1,981215 | 0,273474 |
| 15 | 1,300576 | -1,51938 |
| 16 | -0,57581 | -1,91532 |
| 17 | -1,92279 | -0,55033 |
| 18 | -1,50197 | 1,320633 |
| 19 | 0,299754 | 1,977409 |
| 20 | 1,825891 | 0,816164 |

Si ahora trazamos la ubicación X a lo largo del tiempo, podemos ver que parece que tenemos algunos valores perdidos entre los tiempos 7 y 12.

![Image1](https://learn.microsoft.com/es-es/training/modules/explore-analyze-data-with-python/media/4-x-coordinates.png)

Si trazamos X frente a Y, terminamos con un mapa de por dónde se ha movido el coche. Es inmediatamente obvio que el coche ha estado conduciendo en círculo, pero en algún momento condujo hacia el centro de ese círculo.

![Image2](https://learn.microsoft.com/es-es/training/modules/explore-analyze-data-with-python/media/4-x-y-coordinates.png)

Los gráficos no se limitan a los diagramas de dispersión en 2D como los anteriores, sino que pueden utilizarse para explorar otros tipos de datos, como las proporciones (que se muestran a través de gráficos circulares, gráficos de barras apilados), cómo se distribuyen los datos (con histogramas, diagramas de cajas) y cómo difieren dos conjuntos de datos. A menudo, cuando intentamos comprender datos o resultados sin procesar, podemos experimentar con diferentes tipos de gráficos hasta dar con uno que explique los datos de forma visualmente intuitiva.