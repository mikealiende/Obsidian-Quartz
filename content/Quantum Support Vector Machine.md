# Quantum Support Vector Machine (QSMV)
#Tema 

Se trata de un algoritmo híbrido capaz de explotar la potencia de los ordenadores cuánticos con un número no muy elevado de qubits para tareas de clasificación.

* ## [[SVM Clásico]]

Estamos suponiendo la separabilidad lineal de los datos, hemos supuesto que existe un hiperplano que divide totalmente ambas clase. Esto no es siempre así, para solucionarlo vamos a usar las [[Funciones Kernel]]

## Idea intuitiva

La idea es utilizar los computadores como [[Funciones Kernel]], es decir, mapear los datos al espacio de Hilbert subyacente en dichos computadores.

Como hemos explicado, necesitamos calcular el producto $\phi(\vec{x_{i}}) \cdot \phi(\vec{x_{j}})$, donde $\phi(\vec{x_{i}})$ es el nuevo vector de dimensión mayor asociado al vector $\vec{x_{i}}$. En nuestro nuevo escenario el nuevo vector asociado será definido a través de una puerta $U$ aplicada a un estado inicial, por defecto el 0.

$$\phi(\vec{x_{i}}) = U_{x_{i}}\ket{0}^{\otimes n}$$\
Siendo $n$ en numero de qubits. Mostraremos diferentes mapas de características que es frecuente encontrarse. En primer lugar supondremos que los datos serán transformados a través de rotaciones en los qubits individuales. Los ángulos de rotación pueden ser elegido a través de la función no lineal: $\phi:\vec{x} \rightarrow (0,2\pi]\times(0,2\pi]\times[0,\pi]$, por lo que el mapa de características queda definido como:

$$\vec{x_{i}}\rightarrow \phi_{i}(\vec{x}) = U_{\vec{x_{i}}}\ket{0}_{i} \quad \forall i\in 1,2,\cdots, n. $$
Un ejemplo de mapa de características podría ser el caso concreto de 3 qubits, donde vamos a utilizar la puerta genérica $U_{3}$

![[Pasted image 20240622111002.png|200]]

No obstante, podemos encontrar mapas de características que jueguen con el entrelazamiento como: 

![[Pasted image 20240622111119.png|300]]


Para continuar lo que haremos es dados $\vec{x_{i}}$ y $\vec{x_{j}}$, será buscar el valor $\bra{0}^{\otimes n}U^{\dagger}_{\vec{x_{j}}}U_{\vec{x_{i}}}\ket{0}^{\otimes n}$, ya que este es el producto interno definido dentro del espacio de Hilbert, para generar la matriz de Gram y poder resolver nuestro problema. Este valor podría ser complejo y nos interesa quedarnos con el valor real, lo que podemos hacer con un [[Hadamard Test]], de esta forma:

$$\mathbb{R}(\bra{0}^{\otimes n}U^{\dagger}_{\vec{x_{j}}}U_{\vec{x_{i}}}\ket{0}^{\otimes n}) = P(0)-P(1)$$

Como la elección del mapa de características es bastante experimental y puede depender del conjunto de datos vamos a utilizar el [[Principio Variacional]] para definir nuestro Kernel.

![[Principio Variacional#QSVM Variacional]]

La ventaja cuántica de este algoritmo se conseguirá con aquellos kernels que no sean computables en ordenadores clásicos, por este motivo, frecuentemente nos encontramos con kernels que aprovechen la transformada cuántica de Fourier.

Ejemplo de implementación:[ Clasificación QSMV](https://github.com/mikealiende/Algortimos_Quantum/blob/main/QSVM.ipynb)

