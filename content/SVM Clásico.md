# Support Vector Machine clásico

SVM es un clasificador binario lineal, ya que separa dos clases a través de hiperplanos. Idea del funcionamiento:

![[Pasted image 20240622094522.png|400]]

Para separar los puntos rojos y verdes, hay infinidad de planos, sin embargo para SVM no es suficiente con encontrar un plano, si no que tiene que encontrar aquel plano que maximice las distancias entre las dos clases. Contra mayor sea la diferencia entre conjuntos, mayor tolerancia tendremos a errores.

La distancia entre nuestro Hiperplano $H$ y los puntos más cercanos de ambas clases recibe el nombre de margen $d$, y los puntos más cercanos a $H$ se conocen como puntos soporte.

## Desarrollo matemático

Definimos $H$ como:

$$H = \{\vec{x} \in \mathbb{R}^n /\vec{x}\cdot \vec{w} +b =0\}$$

como el hiperplano buscado definido por $\vec{w} \in \mathbb{R}^n$ y $b\in\mathbb{R}$. Por otro lado, llamaremos $\Omega$ al conjunto de nuestros datos o vectores de características y $f(\vec{x})$ como el valor de la clase asociado a cada $\vec{x}\in \Omega$. De esta forma, será suficiente encontrar unos parámetros $\vec{w}$ y $b$ que cumplan:

$$f(\vec{x})(\vec{w} \cdot \vec{x}+b) \geq 0$$
ya que dada la ecuación de un plano de la forma $\vec{w} \cdot \vec{z} + b =0$ tendremos que $\vec{w} \cdot \vec{x} + b > 0$ si $\vec{x}$ está en un lado del plano y $\vec{w} \cdot \vec{x} + b < 0$ si está en el otro lado.

Ahora bien, si queremos maximizar la longitud del margen, podemos definir estos hiperplanos de soporte como:

$$\begin{align}
H_{1} &= \{\vec{z} \in \mathbb{R}^n /\vec{z}\cdot \vec{w} +b =1\} \\
H_{2} &= \{\vec{z} \in \mathbb{R}^n /\vec{z}\cdot \vec{w} +b =-1\} 
\end{align}$$
La distancia entre estos hiperplanos las definimos como:

$$d = \frac{2}{\mid\mid \vec{w}\mid \mid ^2}$$
Por lo tanto, el problema a minimizar es el siguiente

$$min(\frac{\mid\mid \vec{w}\mid \mid ^2}{2})$$
sujeto a $f(\vec{x_{i}})(\vec{w} \cdot \vec{x_{1}}+b) \geq 1 \quad \forall \vec{x_{i}} \in \Omega$

Este problema es equivalente a minimizar una función cuadrática convexa que podemos resolver con el uso de multiplicadores de Lagrange. 
Una de las grandes ventajas de este tipo de funciones es que existe un único mínimo local que coincide con el global, por lo tanto no tenemos el riesgo de caer en mínimos locales. En base a la función a objetivo y las restricciones definidas, el problema es equivalente a encontrar un mínimo en la siguiente función:

$$L =\frac{\mid\mid \vec{w}\mid \mid ^2}{2} + \sum_{i=1}^m \alpha_{i}[f(\vec{x_{i}})(\vec{w} \cdot \vec{x_{i}}+b) - 1] $$
siendo $\alpha_{i}$ los coeficientes de Lagrange. Si buscamos un mínimo en dicha función, a de cumplirse que la derivada con respecto a $\vec{w}$ y $b$ sea nula. Por lo tanto si derivamos respecto a estos dos parámetros y sustituimos, tenemos:

$$L'= -\sum_{i=1}^m\alpha_{i}+\frac{1}{2}\sum_{i=1}^m\sum_{j=1}^m \alpha_{i}\alpha_{j}f(\vec{x_{i}})f(\vec{x_{j}})\vec{x_{i}} \cdot \vec{x_{j}}$$
En este punto, las únicas variables son los parámetros $\vec{\alpha}$, por lo que calcularemos su valor mínimo con un [[Descenso del gradiente]] y una vez calculado $\vec{\alpha}$, recuperamos los valores de $\vec{w}$ y b. 