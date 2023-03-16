# Análisis de la clasificación con curvas de característica operativas del receptor

Los modelos de clasificación deben asignar un ejemplo a una categoría. Por ejemplo, debe usar características como el tamaño, el color y el movimiento para determinar si un objeto es un excursionista o un árbol.

Podemos mejorar los modelos de clasificación de muchas maneras. Por ejemplo, podemos asegurarnos de que nuestros datos están equilibrados, limpios y escalados. También podemos modificar nuestra arquitectura de modelo y usar hiperparámetros para obtener tanto rendimiento como podamos de nuestros datos y nuestra arquitectura. Finalmente, no encontramos ninguna manera mejor de mejorar el rendimiento en nuestro conjunto de pruebas (o datos de exclusión) y declarar que nuestro modelo está listo.

El ajuste del modelo a este punto puede ser complejo, pero se puede usar un sencillo paso final para mejorar aún más el buen funcionamiento de nuestro modelo. Sin embargo, para entender esto, es necesario volver a los aspectos básicos.

# Probabilidades y catergorias

Muchos modelos tienen varias fases de toma de decisiones y la última suele ser simplemente un paso de binarización. Durante la Binarización, las probabilidades y calcula que existe una probabilidad del 75 % de que se mostrara un excursionista y una probabilidad del 25 % de que se mostrara un árbol. Un objeto no puede ser 75 % excursionista y 25 % árbol, es una cosa o la otra. Como tal, el modelo aplica un umbral, que normalmente es del 50 %. Como la clase sorresponde al excursionista es mayor que el 50 %, se declara que el objeto es un excursionista.

El umbral del 50 % es lógico, lo que significa que siempre se elige la etiqueta más probable según el modelo. Sin embargo, si el modelo está sesgado, es prosible que este umbral del 50 % no sea el adecuado. Por ejemplo, si el modelo tiene una ligera tendencia a elegir árboles más que excursionistas (la frecuencia  al ahora de elegir árboles es un 10 % mayor qeu la normal), podr+iamos ajustar nuestro umbral de decisión para tener esto rn cuenta.

# Actualizar en fucnión de las matrices de decisión

Las matrices de decisión son una excelente manera de evaluar los tipos de errores qeu está cometiendo un modelo. Esto nos proporciona las tasas de verdaderos positivos (VP), verdaderos negativos (VN), falsos positivos (FP) y los falsos negativos (FN).

![Matriz_de_decicion](https://learn.microsoft.com/es-es/training/modules/optimize-model-performance-roc-auc/media/2-decision-matrices.png)

# Curvas ROC

Las curvas de características operativas del receptor (ROC) son un gráfico en el que se traza la tasa de verdaderos positivos frente a la tasa de falsos positivos.

Las curvas de ROC pueden resultar confusas para principiantes por dos motivos principales. El primero es que los principiantes saben que un modelo solo tiene un valor para las tasas de verdaderos positivos y verdaderos negativos. Por lo tanto, un trazado de ROC debe tener este aspecto:

![ROC1](https://learn.microsoft.com/es-es/training/modules/optimize-model-performance-roc-auc/media/roc-graph.png)

Si también piensa esto, está en lo cierto. Un modelo entrenado solo genera un punto. Sin embargo, recuerde que nuestros modelos tienen un umbral (normalmente el 50 %) que se usa para decidir si se debe utilizar la etiqueta verdadera (excursionista) o falsa (árbol). Si cambiamos este umbral al 30 % y recalculamos las tasas de verdaderos positivos y falsos positivos, obtenemos otro punto:

![ROC2](https://learn.microsoft.com/es-es/training/modules/optimize-model-performance-roc-auc/media/roc-graph-2.png)

Si lo hacemos para umbrales entre el 0 % y el 100 %, podríamos obtener un gráfico como el siguiente:

![ROC3](https://learn.microsoft.com/es-es/training/modules/optimize-model-performance-roc-auc/media/roc-graph-3.png)

que normalmente mostramos como una línea, en su lugar:

![ROC4](https://learn.microsoft.com/es-es/training/modules/optimize-model-performance-roc-auc/media/roc-graph-4.png)

El segundo motivo por el que estos gráficos pueden resultar confusos es la jerga implicada. Recuerde que queremos una tasa de verdaderos positivos alta (que identifique a los excursionistas como tales) y una tasa de falsos positivos baja (que no identifique los árboles como excursionistas).

![ROC5](https://learn.microsoft.com/es-es/training/modules/optimize-model-performance-roc-auc/media/roc-graph-5.png)

# ROC buenas, ROC malas

Comprender las curvas de ROC buenas y malas es algo que se hace en un entorno interactivo.

# Comparación y Optimización de curvas de ROC

Las curvas de características operativas del receptor (ROC) nos permiten comparar modelos entre sí y ajustar nuestro modelo seleccionado. Vamos a analizar cómo y por qué se realizan.

# Ajuste del modelo

El uso más obvio de una curva de ROC es elegir un umbral de decisión que proporcione el mejor rendimiento. Recuerde que nuestros modelos nos proporcionan probabilidades, como una probabilidad del 65 % de que la muestra sea un excursionista. El umbral de decisión es el punto por encima del cual se asigna verdadero (excursionista) a una muestra o por debajo del cual se le asigna false (árbol). Si nuestro umbral de decisión fuera del 50 %, el 65 % se asignaría a "verdadero" (excursionista). Sin embargo, si nuestro umbral de decisión fuera del 70 %, una probabilidad del 65 % sería demasiado pequeña y se asignaría a falso ("árbol").

Hemos visto en el ejercicio anterior que, al construir una curva de ROC, solo estamos cambiando el umbral de decisión y evaluando el funcionamiento del modelo. Al hacerlo, podemos encontrar el umbral que proporciona los resultados óptimos.

Por lo general, no hay un solo umbral que proporcione la mejor tasa de verdaderos positivos (TPR) y la tasa de falsos positivos (FPR) más baja. Esto significa que el umbral óptimo depende de lo que se intente lograr. Por ejemplo, en nuestro escenario, es muy importante tener una tasa de verdaderos positivos alta, ya que si no se identifica un excursionista y se produce una avalancha, el equipo no sabrá rescatarle. Sin embargo, existe un inconveniente: si la tasa de falsos positivos es demasiado alta, el equipo de rescate puede enviarse repetidamente para rescatar a personas que simplemente no existen. En otras situaciones, la tasa de falsos positivos se considera más importante. Por ejemplo, la ciencia tiene una baja tolerancia para los resultados de falsos positivos: si la tasa de falsos positivos de experimentos científicos fuera mayor, habría una oleada interminable de notificaciones contradictorias y sería imposible distinguir lo real.

# Comparación de modelos con AUC

Las curvas de ROC se pueden usar para comparar modelos entre sí, al igual que las funciones de costo. La curva de ROC de un modelo muestra lo bien que funcionará para una variedad de umbrales de decisión. Al final del día, lo más importante de un modelo es qué rendimiento tendrá en el mundo real, donde solo hay un umbral de decisión. ¿Por qué, entonces, desearíamos comparar modelos con umbrales que nunca usaremos? Existen dos respuestas para esto.

En primer lugar, comparar curvas de ROC de maneras concretas es como realizar una prueba estadística que nos indique no solo que un modelo ha funcionado mejor en este conjunto de pruebas concreto, sino si es probable que siga teniendo un mejor rendimiento en el futuro. Esto está fuera del ámbito de este material de aprendizaje, pero merece la pena tenerlo en cuenta.

En segundo lugar, la curva de ROC muestra, hasta cierto punto, cómo depende el modelo de tener el umbral perfecto. Por ejemplo, si nuestro modelo solo funciona bien cuando tenemos un umbral de decisión de 0,9, pero muy por encima o por debajo de este valor, no es un buen diseño. Probablemente preferiríamos trabajar con un modelo que funcione razonablemente bien para varios umbrales, sabiendo que si los datos reales que encontramos son ligeramente diferentes a nuestro conjunto de pruebas, el rendimiento de nuestro modelo no se contraerá necesariamente.

# ¿Cómo se comparan los ROC?

La manera más fácil de comparar las ROC numéricamente es usar el área bajo la curva (AUC). Literalmente, se trata del área del gráfico que se encuentra por debajo de la curva. Por ejemplo, nuestro modelo perfecto del último ejercicio tiene una AUC de 1:

![roc1](https://learn.microsoft.com/es-es/training/modules/optimize-model-performance-roc-auc/media/roc-auc-graph.png)

Aunque nuestro modelo cuyo rendimiento no era mejor al del simple azar tenga un área de aproximadamente 0,5:

![roc2](https://learn.microsoft.com/es-es/training/modules/optimize-model-performance-roc-auc/media/roc-auc-graph-2.png)

Cuanto más perfecto sea un modelo, mayor será esta área. Si tenemos un modelo con una AUC grande, sabemos que funciona bien para diversos umbrales, por lo que probablemente tiene una buena arquitectura y ha recibido un buen entrenamiento. Por el contrario, un modelo con una AUC pequeña (más próxima a 0,5) no funciona bien.