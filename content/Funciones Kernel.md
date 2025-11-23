# Funciones Kernel

Para solucionar el problema de que no todos los dato son linealmente separables lo que hacemos es mapear los datos a un espacio de dimensión mayor con la esperanza de que en el nuevo espacio si sean separables:

![[Pasted image 20240622104849.png]]

Definimos $\phi$ como la función que mapea cada elemento en uno de dimensión mayor. Siguiendo el ejemplo de la ilustración tendríamos $\phi : x \rightarrow (x,x^2)$, si sustituimos en la ecuación final de [[SVM Clásico]], tenemos:

$$L'= -\sum_{i=1}^m\alpha_{i}+\frac{1}{2}\sum_{i=1}^m\sum_{j=1}^m \alpha_{i}\alpha_{j}f(\vec{x_{i}})f(\vec{x_{j}})\phi(\vec{x_{i}}) \cdot \phi(\vec{x_{j}})$$
Lo que hemos hecho es sustituir el producto $\vec{x_{i}} \cdot \vec{x_{j}}$ por $\phi(\vec{x_{i}}) \cdot \phi(\vec{x_{j}})$. A esto le llamaremos función Kernel:

$$K(\vec{x_{i}}, \vec{x_{j}}) = \phi(\vec{x_{i}}) \cdot \phi(\vec{x_{j}})$$
