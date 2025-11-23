# Descenso del gradiente

Algoritmo de optimización que permite encontrar mínimos locales de funciones diferenciadles.

La idea básica detrás de este algoritmo consiste en que la derivada de $\vec{\theta}$ en función de E evaluada en un punto $\vec{\theta*}$, nos da la dirección en la que la función decrece más rápido. De esta manera, el algoritmo empieza estableciendo un punto inicial, calcula la derivada en dicho punto, y se mueve en la dirección que más minimice la función una y otra vez hasta alcanzar el  mínimo de dicha función. 

## Ejemplo

Queremos minimizar: $f(x,y) = x^2+y^2$ . Tomamos el punto inicial $(x_{0}, y_{0}) = (-1,1)$, por lo tanto tenemos que:

$$[\frac{{\partial f}}{\partial x}, \frac{{\partial f}}{\partial y}]_{(-1,1)} = (2x,2y)_{(-1,1)} = (-2,2)$$

Por lo tanto la dirección en la que debemos nuestro vector será $(-2,2)$. Ahora tenemos que decidir cuánto vamos a avanza en esa dirección, pero ello, introducimos un parámetro $\lambda$ al que llamaremos coeficiente de aprendizaje, que establece la longitud del paso. Si continuamos repitiendo estos pasos, conseguiremos encontrar el mínimo de la función.