# Algoritmo de Deutsch


El algoritmo de Deutsch fue el primero en demostrar la ventaja cuántica en un problema, en concreto es capaz de dado un oráculo cuántico $f(x)$, donde $x$ puede ser 0 o 1, determina con una única evaluación si $f(x)$ es:

* **Constante**: $f(0)=f(1)$
* **Balanceada**: $f(0) \neq f(1)$ 

Un algoritmo clásico para resolver este problema necesitará dos iteraciones. 

## Oráculo
Para implementar la función binaria vamos a utilizar el oráculo $U_{f}$. Si lo expresamos como un operador unitario: $$\begin{equation}
U_{f} \ket{x}\ket{y} = \ket{x}\ket{y \oplus f(x)}     
\end{equation}$$
## Descripción del algoritmo

![[Pasted image 20250117170519.png]]


### Inicialización

El algoritmo empieza en el estado $\ket{\psi_{0}}=\ket{0}_{A}\otimes \ket{1}_{B} =\ket{0_{A}1_{B}}$.
### Superposición

Para conseguir superposición vamos a aplicar una puerta Hadamard en ambos qubits.$$\begin{equation}
\ket{\psi_{1}}=H\ket{0}\otimes H\ket{1} = \left[ \frac{1}{\sqrt{ 2 }}(\ket{0}_{A}+\ket{1}_{A})   \right]\left[ \frac{1}{\sqrt{ 2 }}(\ket{0}_{B}-\ket{1}_{B})   \right] = \ket{+ -}    
\end{equation}$$
Desarrollamos el producto: $$\ket{\psi_{1}}=\frac{1}{2}(\ket{0}_{A}\ket{0}_{B}-\ket{0}_{A}\ket{1}_{B}+\ket{1}_{A}\ket{0}_{B}-\ket{1}_{A}\ket{1}_{B}        )$$
### Aplicamos el oráculo

Utilizando la expresión del oráculo y aplicando a nuestro circuito, tenemos:
$$\begin{align}
\ket{\psi_{2}}=\frac{1}{2}(\ket{0}_{A}\ket{0\oplus f(0)}_{B}-\ket{0}_{A}\ket{1\oplus f(0)}_{B}+\ket{1}_{A}\ket{0\oplus f(1)}_{B}-\ket{1}_{A}\ket{1\oplus f(1)}_{B}        ) \\ \\
\frac{1}{2}(\ket{0}_{A}(\ket{0\oplus f(0)}_{B}-\ket{1\oplus f(0)}_{B})+\ket{1}_{A}(\ket{0\oplus f(1)}_{B}-\ket{1\oplus f(1)}_{B} ))
\end{align}
$$
Aplicamos: $\ket{0\oplus a}- \ket{1\oplus a} = (-1)^a(\ket{0}-\ket{1})$ y tenemos:
$$\begin{align}
&\frac{1}{\sqrt{ 2 }}(\ket{0}_{A}(-1)^{f(0)}(\ket{0}_{B}-\ket{1}_{B}))+ \frac{1}{\sqrt{ 2 }}(\ket{1}_{A}(-1)^{f(1)}(\ket{0}_{B}-\ket{1}_{B}  ) )= \\ \\
&\frac{1}{2}((-1)^{f(0)}\ket{0}_{A}+(-1)^{f(1)}\ket{1}_{A})(\ket{0}_{B}-\ket{1}_{B})

\end{align}$$
Vemos que mediante el fenómeno [[Phase Kickback]] hemos transferido la información del qubit $B$ que hemos usando como ancilla al qubit $A$.

Sacamos $(-1)^{f(0)}$ factor común como fase global: 
$$\ket{\psi_{2}}=\frac{1}{2}(-1)^{f(0)}(\ket{0}_{A}+(-1)^{f(1)\oplus f(0)}\ket{1}_{A})(\ket{0}_{B}-\ket{1}_{B})$$
### Análisis en función de $U_f$ y medición

* Si $U_f$ es constante $\to f(0)\oplus f(1) = 0$. 
$$\begin{align}\ket{\psi_{2}}=&\frac{1}{2}(-1)^{f(0)}(\ket{0}_{A}+(-1)^{0}\ket{1}_{A})(\ket{0}_{B}-\ket{1}_{B})= \\
&\frac{1}{2}(-1)^{f(0)}(\ket{0}_{A}+\ket{1}_{A})(\ket{0}_{B}-\ket{1}_{B})= \\ \\
&(-1)^{f(0)}\ket{+}\ket{-}  
\end{align}$$
Aplicamos $H$ al primer qubit y tenemos:
$$\ket{\psi_{4}} = (-1)^{f(0)}H\ket{+}\ket{-} = (-1)^{f(0)}\ket{0}\ket{-}$$
Si medimos el primer qubit (ignoramos fase global y qubit ancilla) obtenemos $\ket{0}$ con una probabilidad del $100\%$ si $U_{f}$ es constante.


* Si $U_f$ es balanceada $\to f(0)\oplus f(1) = 1$. 
$$\begin{align}\ket{\psi_{2}}=&\frac{1}{2}(-1)^{f(0)}(\ket{0}_{A}+(-1)^{1}\ket{1}_{A})(\ket{0}_{B}-\ket{1}_{B})= \\
&\frac{1}{2}(-1)^{f(0)}(\ket{0}_{A}-\ket{1}_{A})(\ket{0}_{B}-\ket{1}_{B})= \\ \\
&(-1)^{f(0)}\ket{-}\ket{-}  
\end{align}$$
Aplicamos $H$ al primer qubit y tenemos:
$$\ket{\psi_{4}} = (-1)^{f(0)}H\ket{-}\ket{-} = (-1)^{f(0)}\ket{1}\ket{-}$$

Como antes, si medimos obtenemos $\ket{1}$ con un $100\%$ de probabilidad cuando es constante. En resumen, hemos demostrado que con el Algoritmo de Deutsch medimos:

* $\ket{0}$ si $U_{f}$ es constante.
* $\ket{1}$ si $U_{f}$ es balanceada. 