# Problemas QUBO #Tema 

## Definición

Los problemas tipo QUBO: Quadratic unconstrained binary optimization 

* **Quadratic**: Este tipo de problemas tendrá una estructura polinomial donde las variables serán a lo sumo de grado 2
* **unconstrained**: A la hora de modelizar este problema no nos impondrán ninguna restricción que se deba cumplir obligatoriamente. Nos podrán orientar sobre que está bien y que está mal, pero nunca prohibir.
* **Binary** : Las variables del problema son binarias, solo pueden tomar valores 0 o 1
* **Optimization**: Se trata de un problema de optimización, donde el objetivo es encontrar el mínimo de una función dada.

Podemos representar de manera genérica cualquier problema tipo qubo de esta manera: 
$$f(\vec{x}) = \sum_{i=1}^n \alpha_{i}x_{i}+\sum_{i=1}^n\sum_{j=i}^{n}\beta_{i,j}x_{i}x_{j}$$

Donde $x_{i}$ y $x_{j}$ son variables binarias. El objetivo será encontrar el valor de $x_{i}$ y $x_{j}$ que hace mínimo la función objetivo $f(\vec{x})$. Un ejemplo de una función objetivo de un problema tipo QUBO sería:
$$f(x_{0},x_{1},x_{2})= x_{0}=3x_{2}-\frac{1}{2}x_{0}x_{2}+x_{1}x_{2}$$
Otra manera de ver los problemas QUBO es $min \quad (x^{\dagger}Qx)$, siendo:
* $x$ un vector de variables binarias.
* $Q$ es una matriz simétrica de coeficientes que define una función cuadrática.

## Restricciones 

Como por definición no podemos añadir restricciones, lo que hacemos es introducir a nuestra función objetivo una serie de condiciones multiplicadas por un parámetro conocido como el **coeficiente de Lagrange.** Por lo tanto cuando se dan estas condiciones, el coeficiente de Lagrange penalizará al función objetivo y difícilmente será el camino optimo.

### Restricciones de igualdad

Uno de los tipos de restricciones serán los de igualdad, de manera genérica los podemos plantear como:
$$\sum_{i} a_{i}x_{i} = b$$
Como no podemos introducir restricciones, lo que vamos a hacer es sumarlo a nuestra función $f(\vec{x})$ multiplicado por $\lambda$ (coeficiente de Lagrange). De forma general nuestra nueva función objetivo con restricciones será:
$$\begin{align}
f(\vec{x})' &= f(x) + \lambda \left( \sum_{i} a_{i}x_{i}-b \right)^2 \\
f(\vec{x})' &= \sum_{i=1}^n \alpha_{i}x_{i}+\sum_{i=1}^n\sum_{j=i}^{n}\beta_{i,j}x_{i}x_{j}+ \lambda \left( \sum_{i} a_{i}x_{i}-b \right)^2
\end{align}$$
Elevamos la expresión al cuadrado para que siempre sea positiva y por lo tanto perjudique a la función objetivo. 
#### Ejemplo
Rescatamos la función de antes: $f(\vec{x})= x_{0}=3x_{2}-\frac{1}{2}x_{0}x_{2}+x_{1}x_{2}$ y añadimos la siguiente restricción:
$$x_{0}+2x_{1}+3x_{2} = 4$$
La penalización en este caso será:
$$\lambda(x_{0}+2x_{1}+3x_{2} - 4)^2$$
Y nuestra nueva función objetivo:
$$f(\vec{x})'= x_{0}=3x_{2}-\frac{1}{2}x_{0}x_{2}+x_{1}x_{2}+\lambda(x_{0}+2x_{1}+3x_{2} - 4)^2$$
### Restricciones de desigualdad
De forma general este caso sería: 
$$\sum_{i} a_{i}x_{i} \leq b$$
No podemos hacer lo mismo que en la igualdad porque estaríamos penalizando los valores menores que $b$, y ese no es el objetivo. Por lo tanto lo que vamos a hacer es añadir una variable auxiliar $y$ que haga el papel de completar los sumando menores de 3 para conseguir la igualdad. Ejemplo sencillo, si $b=3$ y $\sum_{i}x_{1}=1$. Entonces, en el proceso de optimización, $y=2$ para terminar de completar el sumando.

El único inconveniente es que $y$ debe ser una variable binaria, por lo tanto debemos escribir $y$ con su desarrollo binario de $\log_{2}(b)$ términos. Por lo tanto, de forma general la restricción tendrá la forma:

$$\begin{align}
f(\vec{x})' &= f(x) + \lambda \left( \sum_{i} a_{i}x_{i} +\sum_{j=0}^{\log_{2}(b)}2^jy_{j}-b \right)^2 \\
f(\vec{x})' &= \sum_{i=1}^n \alpha_{i}x_{i}+\sum_{i=1}^n\sum_{j=i}^{n}\beta_{i,j}x_{i}x_{j}+ \lambda \left( \sum_{i} a_{i}x_{i}+\sum_{j=0}^{\log_{2}(b)}2^jy_{j}-b \right)^2
\end{align}$$

#### Ejemplo restricciones de desigualdad
Utilizando la función de antes, $f(\vec{x})= x_{0}=3x_{2}-\frac{1}{2}x_{0}x_{2}+x_{1}x_{2}$, vamos a añadir la siguiente restricción: 
$$x_{0}+x_{1}+x_{2}\leq 3$$
Por lo tanto nuestra nueva función objetivo será:

$$f(\vec{x},\vec{y})'= x_{0}=3x_{2}-\frac{1}{2}x_{0}x_{2}+x_{1}x_{2}+\lambda(x_{0}+x_{1}+x_{2}+y_{0}+2y_{1}-3)^2$$
## Ejemplo

En este trabajo vemos como podemos pasar un problema conocido de combinatoria, el problema del viajero (TSP) como un problema tipo QUBO. Estos problemas se pueden resolver usando una máquina cuántica basada en [[Quantum Annealing]]

![[Actividad 1. Miguel Aliende.pdf]]
