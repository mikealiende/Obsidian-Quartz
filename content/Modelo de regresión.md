# Modelo de regresión

A diferencia que los modelos de clasificación, en este caso el número de posibles etiquetas es infinito.

La regresión lineal es una técnica de modela estadístico usada para describir variables continuas en funciones de unos parámetros predictores, desde un punto de vista matemático:
$$g(\vec{\theta})(\vec{x}) = \theta_{{0}}+\theta_{1}x_{1}+\theta_{2}x_{2}+\dots +\theta_{n}x_{n}$$
Suponemos la existencia de una función $f$ tal que dado un $\vec{x}$, envía dicho punto en su correspondiente $y$ buscado, la diferencia es que ahora $y$ puede tomar cualquier valor. Por lo que nuestra función $g$ con unos parámetros $\vec{\theta}$ debe aproximarse a $f$.

## Modelo de error de regresión

Lo siguiente que debemos hacer es definir un modelo de error que nos diga que tan bien está aproximando nuestra función. Lo que haremos será comprobar que tal aproxima en cada punto, ver la distancia que se lleva con el original.

$$E(g(\vec{\theta})) = \frac{1}{m}\sum_{i=1}^m \mid y_{i} -g(\vec{\theta})(\vec{x_{i}}) \mid^2$$


Disminuyendo este error conseguimos disminuir la distancia con nuestro objetivo.


## Ejemplo regresión cuántica

En este ejemplo veremos un modelo de regresión cuántica para aproximar $f(x) = 3\sin(x^2)$ a partir de varios puntos de esta función: https://github.com/mikealiende/Algortimos_Quantum/blob/main/QML/Regresión%20cuántica.ipynb

En este ejemplo usamos únicamente un qubit debido a que la dimensión del vector $\vec{x}$ es 1. Debemos tener en cuenta que el valor esperado de un qubit es un valor entre -1 y 1, pero como hemos visto $f$ puede tomar valores fuera de este intervalo, por lo tanto, utilizamos variables auxiliares para reescalar. Entremos el modelo con algoritmos de optimización y tenemos:

![[Pasted image 20240619183049.png|300]]

Los resultados comparados con una regresión clásica cuadrática del tipo $g(\vec{\theta})(x) = \theta_{0}+x\theta_{1}+x^2 \theta_{2}$ son prometedores.

### Estimar $\pi$ con un algoritmo de regresión cuántico

Utilizando un qubit, el valor esperado lo podemos definir como la probabilidad de medir $\ket{0}$ menos la probabilidad de medir $\ket{1}$. Por lo tanto si tomamos esta función como nuestra función objetivo, $f = P(\ket{0}) - P(\ket{1})$, esta función tendrá un mínimo cuando la probabilidad de medir $\ket{1}$ sea máxima. Por lo tanto partiendo de un estado $\ket{0}$ en esfera de Bloch, y deseamos llegar a $\ket{1}$, debemos aplicar una rotación en el eje X de exactamente $\pi$ radianes. Por lo tanto, nuestra nuestro circuito a optimizar será $R_{x}(\theta)$ y sabemos que será mínima cuando $\theta = \pi$, por lo tanto al minimizarlo obtendremos el valor de $\pi$.

Representando la probabilidades del qubit de manera gráfica: 
![[Pasted image 20240619185906.png|300]]
Por lo tanto si con un optimizar buscamos el valor de $\theta$ que minimice nuestra función, aproximaremos $\pi$

Código: https://github.com/mikealiende/Algortimos_Quantum/blob/main/QML/EstimarPI.ipynb

