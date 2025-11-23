# Definición formal de la máquina de Turing

Podemos definir una máquina Turing como una séptupla $M =\{Q,\Sigma,T,\delta,q_{0},B,F\}$ , donde:

* $Q$ es el conjunto de estados finitos.
* $\Sigma$ Conjunto finito de símbolos de entrada.
* $T$ Conjunto de símbolos de cinta. Son los símbolos de entra más otros posibles símbolos adicionales que se pueden escribir en la cinta.
* $\delta$ Es la función de transición $\delta: Q \times T \rightarrow Q\times T\times D$ donde $D$ es una dirección $\{L,R\}$ Izquierda o derecha.
* $q_{0}$ es el estado inicial del contador.
* $B$ Símbolo especial para indicar espacios en blanco. Inicialmente la cinta debe tener estados en blanco excepto en un número finito de posiciones.
* $F$ es el conjunto de $Q$ que denota los estados finales o de aceptación del controlador.