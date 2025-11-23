# Modelo de clasificación

Un modelo de clasificación buscamos ser capaces de predecir a que clase pertenece un objeto, en otras palabras cuál es la etiqueta de un vector de características dado.

Para este tipo de problemas partimos de que existe una función $f$ tal que $sg(f(\vec{x}))$ determinará la clase de nuestro objeto. La idea principal es establecer un candidato $g(\vec{\theta })$ a función $f$ que depende de unos parámetros $\vec{\theta}$ y, decidir cuales de estos parámetros aproximan a $f$. Una práctica habitual suele ser suponer que $g$ es una función lineal que depende de los parámetros $\vec{\theta}$
$$g(\vec{\theta})(\vec{x}) = \theta_{0}+\theta_{1}x_{1}+\theta_{2}x_{2}+\dots + \theta_{n}x_{n}$$

Una vez establecido el modelo, el siguiente paso es determinar lo bien o mal que lo estamos haciendo, a través del error, que lo definiremos como el porcentaje de puntos mal clasificados:

$$E(g(\vec{\theta})) = \frac{1}{m}\sum_{i=1}^m \frac{{1-y_{i}sg(g(\vec{\theta})(\vec{x_{i}}))}}{2}$$
siendo $m$ el número de datos de los que disponemos para ajustar nuestro modelo. Podemos ir ajustando este modelo con algoritmos de optimización.


### Ejemplo clasificación clásica

En este ejemplo ve como somos capaces de clasificar una serie de puntos separados por un hiperplano:
https://github.com/mikealiende/Algortimos_Quantum/blob/main/QML/Clasificación%20clásica.ipynb

El limite lo encontramos para clasificar modelos cuyos datos no son linealmente separables, es decir que no se pueden cortar por un hiperplano, por ejemplo:

![[Pasted image 20240618194634.png | 300]]


### Ejemplo clasificación cuántica

Para este tipo de datos que no son linealmente separables, podemos recurrir a la clasificación cuántica. El paso será crear un circuito variacional que vaya optimizando parámetros, en vez de buscar el estado de mínima energía, buscará el ansatz que mejor clasifique nuestros datos. Un posible modelo sería:

![[Pasted image 20240619180518.png|300]]

En el circuito podemos ver como estamos codificando los datos como parámetros de la propia puerta de rotación $\rightarrow$ codificación de fase. Este modelo debe dar un valor real, y en función del signo clasificarlo como elemento del tipo 1 o -1, por ello calcularemos el valor esperado sobre uno de los qubits. El valor esperado toma valores entre -1 y 1, por lo tanto es un gran candidato a función. La puerta CNOT se utiliza para pasar la información de primer qubit al segundo, porque solo medimos en el segundo.

Ejemplo de clasificador cuántico: https://github.com/mikealiende/Algortimos_Quantum/blob/main/QML/Clasificación%20cuántica.ipynb

![[Pasted image 20240619181124.png|300]]

