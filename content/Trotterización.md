# Trotterización

Esta técnica nos permite aproximar exponenciales de Hamiltonianos tipo $H=\sigma^x +\sigma^z$, que como los operadores de Pauli no conmutan entre sí, no podemos expresarlos como el producto de la exponencial de sus componentes. Para conseguirlo nos vamos a basar en el producto Lie-Trotter:
$$e^{A+B} = \lim_{ N \to \infty } (e^{A/N}\cdot e^{B/N})^N $$
De esta manera cuanto más grande sea $N$, más conseguiremos acercar al valor de la exponencial A+B. La clave de esto es que los bloques $e^{A/N}$ y $e^{B/N}$ si que podemos construirlos, y por lo tanto conseguiremos la exponencial buscada concatenando estos circuitos N veces.

En caso de Hamiltonianos tipo [[Modelo Ising]], que solo están formados con puertas $\sigma^z$, con $N=1$, conseguiremos el valor exacto de la exponencial, pero para otros Hamiltonianos, tendremos que elegir un valor de $N$ que sea lo suficientemente preciso pero que no haga el circuito muy largo.