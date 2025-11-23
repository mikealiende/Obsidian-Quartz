# Principio Variacional

El principio variacional es aquel que permite resolver un problema utilizando el cálculo de variaciones, que se refiere a encontrar funciones que optimicen los valores de las cantidades que dependen de esas funciones. 
## QSVM Variacional

Vamos a utilizar el principio variacional en el algoritmo [[Quantum Support Vector Machine]] para crear un circuito variacional que defina nuestro kernel. Un circuito de este tipo no es más que una serie de puertas que dependen de unos parámetros $\vec{\theta}$, los cuales se irán adaptan en función de unos resultados obtenidos con el objetivo de crear el mapa característico que mejor se adapte a nuestro problema.

Juntando todas las piezas derivadas hasta el momento llegamos a la expresión fundamental de nuestro QSVM variacional:

$$L'= -\sum_{i=1}^m\alpha_{i}+\frac{1}{2}\sum_{i=1}^m\sum_{j=1}^m \alpha_{i}\alpha_{j}f(\vec{x_{i}})f(\vec{x_{j}})\mathbb{R}(\bra{0}^{\otimes n}U^{\dagger}_{\vec{x_{j}},\vec{\theta}}U_{\vec{x_{i}},\vec{\theta}}\ket{0}^{\otimes n})$$
Siendo $U_{\vec{x_{i}},\vec{\theta}}$ nuestro nuevo mapa de características condicionado por $\vec{\theta}$ . En este caso los parámetros a optimizar son $\vec{\alpha}$ y $\vec{\theta}$, para minimizar L.

### Flujo del algoritmo
![[Pasted image 20240622165922.png]]

Primero fijamos la variable $\vec{\theta}$ para buscar el valor de $\vec{\alpha}$ para minimizar $L$, proceso que se puede hacer de manera rápida al ser esta función convexa. Tras encontrar el valor buscado, tendríamos una primera aproximación al clasificador.