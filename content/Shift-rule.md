# Shift-rule

[# Gradients of parameterized quantum gates using the parameter-shift rule and gate decomposition](https://arxiv.org/abs/1905.13311)
Se trata de un método para aproximar gradientes de circuitos cuánticos respecto a sus parámetros. Se define cómo:

$$\frac{{\partial g(\vec{\theta})}}{\partial \theta_{i}} = \frac{1}{2}g(\vec{\theta}+e_{i} \frac{\pi}{2})- \frac{1}{2}g(\vec{\theta}-e_{i} \frac{\pi}{2})$$
Siendo $e_{i}$ el vector de ceros con un uno en la i-ésima posición. Ejemplo para $f(x) = sin(x)$:
\
$$f'(x) = \frac{1}{2}\sin\left( x + \frac{\pi}{2} \right) - \frac{1}{2}\sin\left( x - \frac{\pi}{2} \right) = \sin\left( \frac{\pi}{2} \right)\cos(x) = \cos(x)$$

Como podemos ver el resultado es correcto. Aunque esta función no sirve para todos los circuitos, si que sirve con aquellos en los que los parámetros se encuentren dentro de puertas de rotación $R_{X}$, $R_{Y}$ y $R_{Z}$. 
Utilicemos como ejemplo $R_{Y}$: 

$$R_{Y}(x) = \begin{pmatrix}
 \cos \frac{x}{2}  & -\sin \frac{x}{2} \\
\sin \frac{x}{2}  & \cos\ \frac{x}{2} 
\end{pmatrix}$$
A continuación, aplicamos a dicha puerta un estado arbitrario:

$$\begin{pmatrix}
 \cos \frac{x}{2}  & -\sin \frac{x}{2} \\
\sin \frac{x}{2}  & \cos\ \frac{x}{2} 
\end{pmatrix} \begin{pmatrix}
\alpha \\
\beta
\end{pmatrix} = \begin{pmatrix}
 \alpha\cos \frac{x}{2}  & -\beta\sin \frac{x}{2} \\
\alpha\sin \frac{x}{2}  & \beta\cos\ \frac{x}{2} 
\end{pmatrix}$$

Calculando el valor esperado, obtenemos nuestra función $g(x)$:
$$g(x) = \alpha\cos \frac{x}{2}   -\beta\sin \frac{x}{2} 
-\alpha\sin \frac{x}{2}   +\beta\cos\ \frac{x}{2}$$

