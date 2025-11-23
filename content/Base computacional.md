# Base computacional

Es la base estándar $\{\ket{0},\ket{1}\}$ en la que se representan números en computación cuántica. De forma similar al sistema binaria en computación clásica podemos representar números enteros de la siguiente manera:

* $5\rightarrow \ket{0}\otimes \ket{1}\otimes \ket{0}\otimes \ket{1} = \ket{0101}$
* $7\rightarrow \ket{0}\otimes \ket{1}\otimes \ket{1}\otimes \ket{1} = \ket{0111}$

De forma general:$$x=\sum_{k=0}^{n-1}x_{k}2^k$$

Se puede observar que la frecuencia en la que cambian los estados es distinta, por ejemplo, si recorremos los valores del 0 al 15. Vemos que el qubit menos significativo cambia cada vez que incrementemos en 1 en valor, el siguiente cambia cada dos incrementos, el siguiente cada 4 y el más significativo cada 8. De forma general, el dígito $n$ cambia cada $2^n$ incrementos.