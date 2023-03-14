# Creación y descripción de modelos de clasificacio en el aprendizaje automático

## Introducción

Las salidas de los modelos de clasificación son categóricas, lo que significa que se pueden usar para etiquetar entradas o tomar decisiones. Por ejemplo, un automóvil sin conductor usa la clasificación para decidir si girar a la izquierda o a la derecha en una bifurcación de la carretera. Un modelo de clasificación difiere de los modelos de regresión clásica en que las salidas son continuas, como el tamaño de un zapato o la velocidad de un tren. Los modelos de clasificación son diversos en su forma de funcionar. Para empezar, nos centraremos en la regresión logística, que es un tipo de modelo más sencillo y popular que se usa ampliamente en muchos sectores de la ciencia y de la industria.

# ¿Qué son los modelos de clasificación?

Los modelos de clasificación se usan para tomar decisiones o asignar elementos a categorías. A diferencia de los módulos de regresión, que emiten números continuos, como alturas o pesos, los modelos de clasificación emiten valores booleanos (true o false) o decisiones categóricas, como ‘apple’, ’banana’ o ‘cherry’ ("manzana", "plátano" o "cereza").

Hay muchos tipos de modelos de clasificación. Algunos funcionan de forma similar a los modelos de regresión clásica, mientras que otras son esencialmente diferentes. Uno de los mejores modelos para aprender inicialmente se denomina regresión logística.

# ¿Qué es la regresión logística?

La regresión logística es un tipo de modelo de clasificación que funciona de forma similar a la regresión lineal. La diferencia entre esta y la regresión lineal es la forma de la curva. Mientras que la regresión lineal simple tiene forma de línea recta a los datos, los modelos de regresión logística tienen forma de curva en forma de s:

![regresion_Logistica](https://learn.microsoft.com/es-es/training/modules/understand-classification-machine-learning/media/2-logistic-regression-graph.png)

La regresión logística es mejor para estimar los resultados booleanos que la regresión lineal, porque la curva logística siempre genera un valor entre 0 (false) y 1 (true). Cualquier valor entre estos dos se puede considerar una probabilidad.

Por ejemplo, supongamos que estamos intentando predecir si se producirá una alud hoy. Si nuestro modelo de regresión logística nos proporciona el valor de 0,3, estima que la probabilidad de producirse un alud es del 30 %.

# Conversión de salidas en categorías

Dado que la regresión logística nos proporciona estas probabilidades, en lugar de valores true o false simples, es necesario realizar pasos adicionales para convertir el resultado en una categoría. La manera más sencilla de hacerlo es aplicar un umbral. Por ejemplo, en el gráfico siguiente, el umbral se establece en 0,5. Esto significa que cualquier valor de Y por debajo de 0,5 se convierte en false (cuadro inferior izquierdo) y cualquier valor situado por encima de 0,5 se convierte en true (cuadro superior derecho).

![funcion_Logistica](https://learn.microsoft.com/es-es/training/modules/understand-classification-machine-learning/media/2-logistic-function-graph.png)

Si observamos el gráfico, podemos ver que esto significa que, si la característica está por debajo de 5, la probabilidad será menor que 0,5 y, por tanto, se convertirá en false. Los valores de características superiores a 5 aquí ofrecen probabilidades superiores a 0,5, por lo que se convertirán en true.

Es importante que la regresión logística no tenga que limitarse a un resultado true o false; también se puede usar cuando hay tres o más resultados potenciales, como ‘rain’, ‘snow’ o ‘sun’ ("lluvia", "nieve" o "sol"). Esto requiere una configuración ligeramente más compleja, denominada regresión logística multinomial. Aunque no lo practicaremos durante los ejercicios siguientes, merece la pena tenerlo en cuenta en situaciones en las que es necesario realizar predicciones que no son binarias.

