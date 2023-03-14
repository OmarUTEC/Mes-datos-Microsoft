# ¿Qué es la regresión?

La regresión es una técnica de análisis de datos sencilla, común y muy útil, que a menudo se conoce de forma coloquial como "ajustar una línea". En su forma más sencilla, la regresión se ajusta a una línea recta entre una variable (característica) y otra (etiqueta). En formas más complicadas, la regresión puede encontrar relaciones no lineales entre una sola etiqueta y varias características.

# Regresión lineal simple

La regresión lineal simple modela una relación lineal entre una sola característica y una etiqueta normalmente continua, lo que permite que la función prediga la característica. Es posible que tenga un aspecto similar a este:

![Regresion lineal simple](https://learn.microsoft.com/es-es/training/modules/understand-regression-machine-learning/media/2-simple-linear-regression.png)

La regresión lineal simple tiene dos parámetros: una intersección (c) que indica el valor de la etiqueta cuando la característica se establece en cero, y una pendiente (m) que indica cuánto aumentará la etiqueta para cada aumento de un punto de la característica.

Si le gusta pensar matemáticamente, es muy simple:

**y = mx + c**

Donde y es la etiqueta y x es la característica.

Por ejemplo, en nuestro escenario, si intentamos predecir qué pacientes tendrán una temperatura corporal elevada en función de su edad, tendríamos el modelo:

temperatura = m * edad + c

Debe buscar los valores de "m" y "c" durante el procedimiento de ajuste. Si resulta que m = 0,5 y c = 37, es posible que lo visualicemos de la siguiente forma:

![RLS](https://learn.microsoft.com/es-es/training/modules/understand-regression-machine-learning/media/2-linear-graph.png)

Esto significaría que cada año de edad está asociado con un aumento de la temperatura corporal de 0,5 °C, con un punto inicial de 37 °C.

# Ajuste de la regresión lineal

Normalmente, usamos bibliotecas existentes para ajustarnos a los modelos de regresión. La regresión normalmente pretende encontrar la línea que genera la menor cantidad de error, donde el error significa la diferencia entre el valor del punto de datos real y el valor previsto. Por ejemplo, en la imagen siguiente, la línea negra indica el error entre la predicción, la línea roja y un valor real: el punto.

![RLS2](https://learn.microsoft.com/es-es/training/modules/understand-regression-machine-learning/media/2-fitting-linear-regression.png)

Al mirar estos dos puntos en un eje Y, podemos ver que la predicción era 39,5, pero el valor real era 41.

![RLS3](https://learn.microsoft.com/es-es/training/modules/understand-regression-machine-learning/media/2-fitting-linear-regression.2.png)

Por lo tanto, el modelo estaba equivocado en 1,5 para este punto de datos.

Normalmente, ajustamos un modelo minimizando la suma residual de cuadrados. Esto significa que la función de costo se calcula de la siguiente manera:

1. Calcular la diferencia entre los valores reales y previstos (como los anteriores) para cada punto de datos
2. Eleve estos valores al cuadrado
3. Suma (o promedio) de estos valores al cuadrado

El paso de elevar al cuadrado significa que no todos los puntos contribuyen uniformemente a la línea: los valores atípicos, que son puntos que no se encuentran en el patrón esperado, tienen un error desproporcionadamente mayor, lo que puede influir la posición de la línea.

# Regresión Lineal Múltiple

La regresión lineal múltiple modela la relación entre varias características y una sola etiqueta. Matemáticamente, es lo mismo que la regresión lineal simple y normalmente se ajusta con la misma función de costo, pero con más características.

En lugar de modelar una relación única, esta técnica modela simultáneamente varias relaciones, que trata como independientes entre sí. Por ejemplo, si predecimos cuán enfermo se pone un perro en función de age y body_fat_percentage, se encuentran dos relaciones:

* Cómo age aumenta o reduce la posibilidad de enfermedad
* Cómo body_fat_percentage aumenta o reduce la posibilidad de enfermedad

Si solo estamos trabajando con dos características, podemos visualizar nuestro modelo como una superficie 2D plana, igual que podemos modelar la regresión lineal simple como una línea. Exploraremos esto en el siguiente ejercicio.

# Bondad de Ajuste: R^2

Sabemos que las funciones de costo se pueden usar para evaluar el modo en que un modelo se ajusta a los datos en los que se entrena. Los modelos de regresión lineal tienen una medida relacionada especial denominada R2 ("R cuadrado"). R2 es un valor entre 0 y 1 que nos indica cómo se ajusta un modelo de regresión lineal a los datos. Cuando se habla de que las correlaciones son sólidas, a menudo quiere decir que el valor de R2 era grande.

R2 usa las matemáticas más allá de todo aquello de lo que hablamos en este curso, pero podemos pensar en ello de forma intuitiva. Fijémonos en el ejercicio anterior en el que analizamos la relación entre age y core_temperature. Un R2 de 1 significaría que se podrían usar años para predecir perfectamente quién tenía temperatura alta y quién la tenía baja. Por el contrario, un 0 significaría simplemente que no había ninguna relación entre los años y la temperatura.

![R2](https://learn.microsoft.com/es-es/training/modules/understand-regression-machine-learning/media/4-goodness-of-fit-graph.png)

# Regresion Polimorfica

Hasta ahora, solo hemos visto modelos de regresión lineal: modelos que se pueden modelar como líneas rectas. Sin embargo, los modelos de regresión pueden funcionar con prácticamente cualquier otro tipo de relación.

# ¿En qué consiste la regresión Polimorfica?

La regresión polinómica modela las relaciones como un tipo determinado de curva. Los polinomios son una familia de curvas que abarcan desde formas simples hasta complejas. Cuantos más parámetros tenga la ecuación (modelo), más compleja puede ser la curva.

Por ejemplo, un polinomio de dos parámetros es simplemente una línea recta:

y = intersección + B1 * x

![RLP1](https://learn.microsoft.com/es-es/training/modules/understand-regression-machine-learning/media/6-polynomial-graph.png)

Mientras que un polinomio de tres parámetros tiene una única curva:

y = intersección + B1 * x + B2 * x2

![RLP2](https://learn.microsoft.com/es-es/training/modules/understand-regression-machine-learning/media/6-three-parameter-polynomial.png)

Un polinomio de cuatro parámetros puede tener dos curvas:

y = intersección + B1 * x + B2 * x2 + B3 * x3

![RLP3](https://learn.microsoft.com/es-es/training/modules/understand-regression-machine-learning/media/6-four-parameter-polynomial.png)

# Polinomio frente a otras curvas

Hay muchos tipos de curvas, como las curvas de registro y las curvas logísticas (en forma de s), que se pueden usar con regresión.

![RLP4](https://learn.microsoft.com/es-es/training/modules/understand-regression-machine-learning/media/6-polynomial-vs-curves.png)

Una ventaja importante de la regresión polinómica es que se puede usar para observar todo tipo de relaciones. Por ejemplo, la regresión polinómica se puede usar para relaciones que son negativas dentro de un determinado intervalo de valores de características, pero positivas dentro de otras. También se puede usar cuando la etiqueta (valor y) no tiene ningún límite superior teórico.

![RLP5](https://learn.microsoft.com/es-es/training/modules/understand-regression-machine-learning/media/6-example-curves.png)

La desventaja principal de las curvas polinómicas es que a menudo se extrapolan de manera errónea. En otras palabras, si intentamos predecir valores mayores o menores que nuestros datos de entrenamiento, los polinomios pueden predecir valores extremos muy poco realistas. Otra desventaja es que las curvas polinómicas son fáciles de sobreajustar. Esto significa que el ruido en los datos puede cambiar la forma de la curva mucho más que los modelos más sencillos, como la regresión lineal simple.

![RLP6](https://learn.microsoft.com/es-es/training/modules/understand-regression-machine-learning/media/6-curve.png)

# ¿Se puede usar curvas con varias característica?

Hemos visto cómo la regresión múltiple puede ajustarse a varias relaciones lineales al mismo tiempo. Sin embargo, no es necesario que se limite a las relaciones lineales. Se pueden usar curvas de todo tipo para estas relaciones cuando corresponda. Aunque se debe tener cuidado de no usar curvas, como polinomios, con varias características donde no son necesarias. Esto se debe a que las relaciones pueden acabar siendo muy complejas, lo que dificulta comprender los modelos y evaluar si realizarán predicciones que no tienen sentido desde el punto de vista del mundo real.