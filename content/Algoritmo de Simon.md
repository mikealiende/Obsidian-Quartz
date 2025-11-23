# Algoritmo de Simon

El algoritmo de Simon es el primero que logra una mejora exponencial respecto a un algoritmo clásico.Utiliza un número lineal de consultas, mientras que un algoritmo clásico necesitamos un número exponencial de consultas.

## Descripción del problema.

Dada una función $f$ implementada en un oráculo, tal que: $f:\{0,1\}^n$ . El algoritmo consiste en distinguir si:

* La función es 1a1 (inyectiva), donde cada entrada distinta genera una una salida distinta.
* La función es 2a1 (no inyectiva), la función asigna dos entradas distintas a la misma salida.

El algoritmo de Simon impone también una **condición** al problema:

* Si la función es 2a1, para dos entradas distintas $x_{1}$ y $x_{2}$ con la misma salida, es decir, $f(x_{1})=f(x_{2})$. Existe un valor $s$ tal que $x_{1}\oplus x_{2} =s$, con $s \in\{0,1\}^n$
	* Si $s = 0^n \to$ La función es 1a1 (inyectiva).
	* Si $s \neq 0^n \to$ La función es 2a1.


## Circuito del algoritmo de Simon

![[Pasted image 20250212191238.png|400]]

Tenemos dos registros de $n$ qubits. Al registro principal le llamaremos $A$, y al auxiliar $B$.

* **Estado inicial**

Partimos de $\ket{\psi_{0}}= \ket{0}^{\otimes n}\otimes \ket{0}^{\otimes n}$


* **Aplicamos puertas Hadamard al registro $A$**

$$\begin{align}
\ket{\psi_{1}}&= H^{\otimes n}\otimes I^{\otimes n}\ket{\psi_{0}} = H^{\otimes n}\ket{0}^{\otimes n}\otimes \ket{0}^{\otimes n} \\ \\
\ket{\psi_{1}}&= \sum_{x \in\{0,1\}^n} \frac{1}{\sqrt{ 2^n }}\ket{x}\otimes \ket{0}^{\otimes n}
\end{align}   $$
* **Aplicamos oráculo $U_{f}$**

La expresión unitaria del oráculo aplicada a un sistema de dos qubits es: $U_{f}\ket{x}\ket{y} = \ket{x}\ket{y \oplus f(x)}$. En el caso de nuestro circuito, el registro $B$ es $\ket{0}^{\otimes n}$, tenemos que $\ket{0\oplus f(x)} = \ket{f(x)}$. Por lo tanto:
$$\ket{\psi_{2}} = U_{f}\ket{\psi_{1}} = \sum_{x \in\{0,1\}^n} \frac{1}{\sqrt{ 2^n }}\ket{x}\otimes \ket{f(x)}$$

* **Medición del registro $B$**

Al medir el registro $B$, es decir, $f(x)$. Vamos a hacer colapsar al sistema completo al subespacio asociado al valor $f(x)$ medido. Debido a la naturaleza cuántica de la medición de un sistema entrelazado, al medir el registro $B$ provocamos un colapso del registro a un autoestado, o combinación de autoestados compatibles con el resultado de la medición.

El caso más interesante en nuestro problema es el caso de que la función sea 2a1, el estado del sistema será una superposición equiprobable de los valores compatibles con la medición, llamémosles $x_{1}$ y $x_{2}$. Quiere decir entonces que $f(x_{1})=f(x_{2})$, y podemos describir el estado del sistema completo después de la medición como:

$$\ket{\psi_{3}}= \frac{1}{\sqrt{ 2 }}(\ket{x_{1}}+\ket{x_{2}})$$
* Volvemos a aplicar puertas Hadamard al registro $A$**

Para volver a aplicar las puertas $H^{\otimes n}$ vamos a aprovecharnos de la **transformada de Hadamard**:
$$H^{\otimes n}\ket{x} =  \sum_{z \in\{0,1\}^n} \frac{1}{\sqrt{ 2^n }}(-1)^{x \cdot z}\ket{z} $$
Aplicando en nuestro estado:

$$\begin{align}
\ket{\psi_{4}} &= H^{\otimes n}\ket{\psi_{3}} = \frac{1}{\sqrt{ 2 }}(H^{\otimes n}\ket{x_{1}} +H^{\otimes n}\ket{x_{2}} ) = \\ \\
&= \frac{1}{\sqrt{2 }}\left( \sum_{z \in\{0,1\}^n} \frac{1}{\sqrt{ 2^n }}(-1)^{x_{1} \cdot z}\ket{z} + \sum_{z \in\{0,1\}^n} \frac{1}{\sqrt{ 2^n }}(-1)^{x_{2} \cdot z}\ket{z}  \right) =\\ \\
&= \frac{1}{\sqrt{ 2 }}\left( \frac{1}{\sqrt{ 2^n }} \sum_{z \in\{0,1\}^n}(-1)^{x_{1} \cdot z}+(-1)^{x_{2} \cdot z}\ket{z} \right) = \\ \\
\ket{\psi_{4}}&=  \frac{1}{\sqrt{ 2^{n+1} }}\sum_{z \in\{0,1\}^n}(-1)^{x_{1} \cdot z}+(-1)^{x_{2} \cdot z}\ket{z}
\end{align} $$

Si medimos ahora, vamos a obtener un estado $\ket{z}$, por ejemplo, $\ket{z_{1}}$ en función de sus amplitudes de probabilidad. El hecho de haber medido $\ket{z_{1}}$ significa que que para este autoestado se cumple: $$(-1)^{x_{1} \cdot z_{1}}=(-1)^{x_{2}\cdot z_{1}} $$
Ya que, en caso contrario estos valores se hubieran anulado y nunca hubiéramos medido $\ket{z_{1}}$, por lo tanto, el mero hecho de haberlo medido justifica la igualdad de arriba. Entonces:
$$\begin{align}
(-1)^{x_{1} \cdot z_{1}}&=(-1)^{x_{2}\cdot z_{1}}  \\
x_{1}\cdot z_{1} &= x_{2}\cdot z_{1}
\end{align}$$

Ahora vamos a hacer uso de la condición que hemos impuesto al problema para funciones 2a1, donde $f(x_{1})=f(x_{2})$ (precisamente lo que hemos conseguido) se debe cumplir: $x_{1}\oplus x_{2} =s \to x_{2} = x_{1}\oplus s$. 
Si sustituimos:

$$\begin{align}
x_{1}\cdot z_{1} &= (x_{1}\oplus s)\cdot z_{1}  =  \\
x_{1}\cdot z_{1} &= (x_{1}\cdot z_{1} \oplus s\cdot z_{1})  =   \\
s \cdot z_{1} &=0
\end{align}$$
Hemos obtenido un vector $z_{1}$ tal que $s \cdot z_{1} = 0$ (mod2). Vamos a repetir este paso $O(n)$ veces hasta conseguir un conjunto de vectores $\{z_{1},z_{2},\dots,z_{n}\}$ que formen un sistema de ecuaciones linealmente independientes del tipo:
$$\begin{align} 
z_{1}\cdot s &= 0 \quad \text{mod 2} \\
z_{2}\cdot s &= 0 \quad \text{mod 2} \\ \\
\vdots \\
z_{n}\cdot s &= 0 \quad \text{mod 2} \\
\end{align}$$

==Resolviendo el sistema de forma clásica para encontrar $s \neq0$ que satisfaga $z_{n}\cdot s = 0 \quad \text{mod 2} \quad\forall i$ . Si la única solución es $s =0$, entonces la función es 1a1 o inyectiva, en cambio si hemo encontrado ese valor $s \neq 0$, entonces la función es 2a1.==


