# Introducción redes neuronales clásicas

Las redes neuronales son unas estructuras de datos que definirán nuestro modelo de una forma muy concreta. Las redes neuronales han ganada mucha popularidad debido a si facilidad de implementación como por la capacidad de adaptación a cualquier tipo de función.

![[Pasted image 20240621171949.png|200]]

Una neurona contará con una serie de entradas distintas, en el caso de la figura, dos entradas más in bias. Cada una de las conexiones por la que llegan los inputs están influenciadas por unos pesos $\vec{\theta}$. Una vez ponderados llegamos al cuerpo de la neurona donde se suman los valores obtenidos y finalmente se aplica una función de activación. Existen diferentes funciones de activación pero una de las más utilizadas es la arcotangente, para restringir el output entre -1 y 1. El modelo de la neurona quedaría definido de la siguiente forma:

$$g(\vec{\theta})(\vec{x}) = \arctan(x_{0}\theta_{0}+x_{1}\theta_{1}+\theta_{2})$$
Supongamos que estamos trabajando con un [[Modelo de clasificación]]. Vamos a definir el error como la suma de las distancias de $g(\vec{\theta})(\vec{x})$ a sus etiquetas:

$$E(g(\vec{\theta})) = \sqrt{ \sum_{i=1}^m \mid g(\vec{\theta})(\vec{x_{i}}) -y_{i} \mid^2}$$
La ventaja radica en que definido de esta manera, la función de error pasa a ser un  función derivable, siendo:
$$E(\vec{\theta}) = \sqrt{ \sum_{i=1}^m \mid \arctan(x_{0}\theta_{0}+x_{1}\theta_{1}+\theta_{2}) -y_{i} \mid^2}$$
De esta manera, podemos buscar el mínimo de una función derivable a través del [[Descenso del gradiente]]. 

## Red neuronal

Una red neuronal es un conjunto de neuronas distribuidas en distintas capas, que interactuan entre si con el objetivo de crear un modelo mucho más flexible. 

![[Pasted image 20240621175527.png|400]]

En la imagen vemos una red neuronal con 2 inputs, que pasarán por la primera capa de dos neuronas, posteriormente a una de 3 y acaba con una capa de 1 neurona. La idea es concretar todas las salidas de unas neuronas con las entradas de otras en la siguiente capa. Obtenemos así una función de error que dependa de cada uno de los parámetros que aparezcan dentro de todas las neuronas. 

La razón de utilizar esta función de activación es romper con la linealidad de la función neurona. En este caso el proceso de derivación es más complejo y se llama retropropagación y se caracteriza por el uso de la regla de la cadena para derivar funciones.

Ejemplo:[Clasificación con red neuronal](https://github.com/mikealiende/Algortimos_Quantum/blob/main/QML/Red%20neuronal%20clasificación.ipynb)
