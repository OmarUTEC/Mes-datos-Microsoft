# ¿Qué son los modelos de aprendizaje automático?

El modelo es el componente principal del aprendizaje automático y, en definitiva, lo que estamos intentando crear. Un modelo podría calcular la edad de una persona a partir de una foto, predecir lo que le gustaría ver en las redes sociales o decidir hacia dónde se debe mover un brazo robótico. En nuestro escenario, queremos crear un modelo que pueda calcular la talla de botas más adecuada para un perro en función de la talla de su arnés.

Los modelos se pueden crear de muchas maneras. Por ejemplo, son las personas las que crean un modelo tradicional que simula el vuelo de un avión, con conocimientos de física e ingeniería. Los modelos de aprendizaje automático son especiales, ya que en lugar de editarlos las personas para que sean eficaces, son los datos los que les dan forma, es decir, aprenden de la experiencia.

# Planteamientos sobre modelos

Un modelo puede plantearse como una función que acepta datos como entrada y genera una salida. En concreto, un modelo usa los datos de entrada para calcular otra cosa. Por ejemplo, en nuestro escenario, queremos crear un modelo al que se le proporciona una talla de arnés y calcula la talla de unas botas:

![input-output](https://learn.microsoft.com/es-es/training/modules/introduction-to-machine-learning/media/1-2-a.jpg)

Tenga en cuenta que tanto la talla del arnés como la talla de las botas para perros son datos, es decir, no forman parte del modelo. La talla del arnés es la entrada y la talla de las botas para perros es la salida.

# ¿Qué son las entradas y salidas?

El objetivo del entrenamiento es mejorar un modelo para que pueda realizar predicciones o estimaciones de alta calidad. Una vez entrenado, el modelo se puede usar en el mundo real, de forma similar al software normal.

Los modelos no se entrenan a sí mismos, se entrenan con datos y dos fragmentos de código: la función objetivo y el optimizador. A continuación, exploramos cómo funcionan estos componentes en conjunto para entrenar un modelo de manera que sea eficaz.

![inout-output2](https://learn.microsoft.com/es-es/training/modules/introduction-to-machine-learning/media/1-4-a.jpg)

# El objetivo

El objetivo es lo que queremos que el modelo pueda hacer. Por ejemplo, el objetivo de nuestro escenario es poder calcular la talla de las botas de un perro en función de la talla de su arnés.

Para que un equipo pueda comprender nuestro objetivo, debemos proporcionárselo como un fragmento de código denominado función objetivo (también conocido como función de costo). Las funciones objetivo evalúan si el modelo es eficaz (es decir, si calcula la talla correcta de las botas) o no (es decir, si se equivoca a la hora de calcular la talla de las botas). Trataremos las funciones objetivo en profundidad en el material de aprendizaje posterior.

# Datos

Los datos se refieren a la información que le proporcionamos al modelo (también denominada entrada). En nuestro escenario, se corresponde con la talla del arnés.

Los datos también se refieren a la información que la función objetivo podría necesitar. Por ejemplo, si nuestra función objetivo nos indica si el modelo ha predicho la talla correcta de las botas, necesitará saber cuál es la talla correcta de las botas. Este es el motivo por el que, en el ejercicio anterior, proporcionamos tanto las tallas de los arneses como las respuestas correctas al código de entrenamiento.

# El optimizador

Durante el entrenamiento, el modelo realiza una predicción y la función objetivo calcula la calidad de su rendimiento. El optimizador es un código que, a continuación, cambia los parámetros del modelo para que sea más eficaz la próxima vez.

El proceso que lleva a cabo el optimizador para realizar esta acción es complejo y se tratará en material posterior. Sin embargo, no se debe preocupar. No solemos escribir nuestros propios optimizadores, sino que usamos marcos de código abierto en los que ya se ha hecho el trabajo duro.

Es importante tener en cuenta que el objetivo, los datos y el optimizador son simplemente un medio para entrenar el modelo. No son necesarios una vez completado el entrenamiento. También es importante recordar que el entrenamiento solo cambia los valores de parámetro dentro del modelo, es decir, no cambia el tipo de modelo que se usa.

# Cómo usar un modelo

## Diferencias entre entrenar y usar un modelo

Es importante diferenciar el entrenamiento del uso de un modelo.

Usar un modelo significa proporcionar entradas y recibir una estimación o predicción. Lo hacemos tanto cuando entrenamos nuestro modelo como cuando nosotros, o nuestros clientes, lo usamos en el mundo real. Usar un modelo solo nos lleva unos pocos segundos.

![int-output3](https://learn.microsoft.com/es-es/training/modules/introduction-to-machine-learning/media/1-6-a.png)

Por el contrario, entrenar un modelo es el proceso de mejorar el funcionamiento de dicho modelo. El entrenamiento requiere que usemos el modelo, la función objetivo y el optimizador en un bucle específico. Esto puede tardar unos minutos o días en completarse. Solemos entrenar el modelo solo una vez. Una vez entrenado, podemos usarlo tantas veces como queramos sin realizar más cambios.

![input-output4](https://learn.microsoft.com/es-es/training/modules/introduction-to-machine-learning/media/1-6-b.png)

Por ejemplo, en nuestro escenario de la tienda para perros de rescate de avalanchas, queremos entrenar un modelo mediante un conjunto de datos públicos, que cambiará el modelo para que pueda predecir la talla de las botas de un perro en función de la talla de su arnés. Una vez entrenado, usaremos el modelo en nuestra tienda en línea para asegurarnos de que los clientes van a comprar las botas que se adaptarán mejor a sus perros.

Datos para usar, datos para entrenar
Recuerde que un conjunto de datos es una recopilación de información sobre objetos o cosas. Por ejemplo, un conjunto de datos puede contener información sobre perros:

Identificador del perro | Talla de las botas | Talla del arnés | Color del perro    | Raza                |
-----------------------|--------------------|------------------|-------------------|---------------------|
0                      | 27                 | 12               | Brown             | San bernardo        |
1                      | 26                 | 11               | Negro             | Labrador            |
2                      | 25                 | 10               | Blanco            | Labrador            |
3                      | 29                 | 14               | Negro             | Pastor alemán negro |

Cuando usamos nuestro modelo, solo necesitamos las columnas de datos que el modelo acepta como entrada. Estas columnas se denominan características. En nuestro escenario, si el modelo acepta la talla del arnés y calcula la talla de las botas, entonces nuestra característica es la talla del arnés.

Durante el entrenamiento, la función objetivo normalmente necesita saber tanto la salida del modelo como cuál era la respuesta correcta. Estas se denominan etiquetas. En nuestro escenario, si el modelo predice la talla de las botas, nuestra etiqueta será la talla de las botas.

En conjunto, esto significa que para usar un modelo solo necesitamos las características, mientras que durante el entrenamiento normalmente necesitamos tanto las características como las etiquetas. En nuestro escenario, durante el entrenamiento necesitamos tanto la característica de la talla del arnés como la etiqueta de la talla de las botas. Cuando usamos el modelo en nuestro sitio web, solo necesitamos saber la característica de la talla del arnés. A continuación, nuestro modelo calculará la talla de las botas que debemos usar.