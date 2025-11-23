# Demostración matemática del algoritmo de Grover

Partimos del [[Algoritmo de Grover]]:

![[Pasted image 20250216195034.png]]


## Inicialización

Empezamos en el estado $\ket{\psi_{0}} = \ket{0^{\otimes n}}$

## Aplicamos puertas Hadamard

$\ket{\psi_{1}}=H^{\otimes n}\ket{0^{\otimes n}}= \frac{1}{\sqrt{ N }}\sum_{x \in\{0,1\}^{n}}\ket{x}=\ket{s}$

Siendo $N=2^n$ la dimensión del espacio de Hilbert donde representamos los $n$ qubits.


## Aplicamos el oráculo $U_{D}$

Como hemos demostrado, $U_{D}=I-2\ket{w}\bra{w}$, siendo $\ket{w}$ el estado buscado.

$$\begin{align}
\ket{\psi_{2}}&=U_{w}\ket{\psi_{1}} = (I-2\ket{w}\bra{w})\ket{s}    \\
&=\ket{s}-2\ket{w}\braket{w|s}   
\end{align}$$
Separamos $\ket{s}$ entre $\ket{w}$ y el resto de estados $\ket{x} \neq \ket{w}$, es decir:
$$\ket{s}= \frac{1}{\sqrt{ N }}\left( \sum_{x \neq w}\ket{x} +\ket{w}   \right) $$
Volviendo a nuestra ecuación:
$$\begin{align}
\ket{\psi_{2}} &= \ket{s}-\frac{{2}}{\sqrt{ N }}\ket{w}\bra{w}\left( \sum_{x \neq w}\ket{x} +\ket{w}   \right)\\ \\
&=\ket{s}-\frac{{2}}{\sqrt{ N }}\ket{w}\left( \sum_{x \neq w}\braket{w|x}   +\braket{w|w}  \right)
\end{align}$$
Como $\ket{x}$ es ortogonal a $\ket{w} \quad\forall x \neq w$, tenemos que $\braket{w|x}=0$ y $\braket{w|w}=1$. Por lo tanto:
$$\ket{\psi_{2}} =\ket{s}-\frac{2}{\sqrt{ N }}\ket{w}  $$

## Aplicamos operador de Difusión $U_{D}$

El operador de difusión es $U_{D}=2\ket{s}\bra{s}-I$. Volviendo a nuestro estado:
$$\begin{align}
\ket{\psi_{3}}&=U_{D}\ket{\psi_{2}} =  (2\ket{s}\bra{s}-I)\left( \ket{s}-\frac{2}{\sqrt{ N }}\ket{w} \right)\\ \\
&=2\ket{s}\braket{s|s} - \frac{4}{\sqrt{ N }}\ket{s}\braket{s|w} - \ket{s} + \frac{2}{\sqrt{ N }}\ket{w}  \\ \\
&=2\ket{s} - \ket{s}  -\frac{4}{\sqrt{ N }}\ket{s}\braket{s|w} + \frac{2}{\sqrt{ N }}\ket{w}      
\end{align}$$

Como antes, separamos $\bra{s}$ entre sus componentes $\bra{x} \neq \bra{w}$ y $\bra{w}$ Tenemos:

$$\begin{align}
\ket{\psi_{3}}&=\ket{s} - \frac{4}{\sqrt{ N }}\ket{s} \cdot \frac{{1}}{\sqrt{ N }}\left( \sum_{x \neq w} \bra{x}  + \bra{w} \right)\ket{w}  +\frac{2}{\sqrt{ N }}\ket{w}\\ \\
&= \ket{s} - \frac{4}{\sqrt{ N }}\cdot \frac{{1}}{\sqrt{ N }}\ket{s} \left( \sum_{x \neq w} \braket{x|w} + \braket{w|w}\right) +\frac{2}{\sqrt{ N }}\ket{w}\\ \\
&=\ket{s}-\frac{4}{N}\ket{s}+  \frac{2}{\sqrt{ N }}\ket{w}= \frac{{N-4}}{N}\ket{s}+\frac{2}{\sqrt{ N }}\ket{w} \\ \\
&=\frac{{N-4}}{N}\cdot \frac{1}{\sqrt{ N }}\left( \sum_{x \neq w} \ket{x}   + \ket{w}  \right) + \frac{2}{\sqrt{ N }}\ket{w}\\ \\
&=\frac{{N-4}}{N\sqrt{ N }} \sum_{x \neq w} \ket{x} +\left( \frac{{N-4}}{N\sqrt{ N }}+ \frac{2}{\sqrt{ N }} \right)\ket{w} \\ \\
\ket{\psi_{3}} &=  \frac{{N-4}}{N\sqrt{ N }} \sum_{x \neq w} \ket{x} + \frac{{3N-4}}{N\sqrt{ N }}\ket{w} 
\end{align}$$
De forma más compacta nos queda:
$$\ket{\psi_{3}} = \frac{1}{N\sqrt{ N }}\left( \sum_{x \neq w}(N-4)\ket{x} + (3N-4)\ket{w}  \right) $$

Vemos la amplitud de probabilidad del elemento encontrado $\ket{w}$ se incrementa respecto a los demás. 

Si aplicamos $U_{w}$ y $U_{D}$ se va aumentado la probabilidad, aunque si nos pasamos empeorará porque es cíclico, esto lo entenderemos mejor en la [[Demostración geométrica algoritmo de Grover]]