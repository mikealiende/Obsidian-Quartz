# Modos fotónicos como qubits

Para poder tener un [[Computación cuántica con fotones]], lo primero que necesitamos es disponer de una base computacional $\{\ket{0}, \ket{1}\}$, sobre la cual se pueda realizar cualquier operación que pueda ser expresada como un conjunto de rotaciones parametrizadas por dos ángulos $\theta$ y $\phi$:

$$\begin{align}
\ket{0}&\rightarrow \cos \theta \ket{0} + e^{i\phi}\sin \theta \ket{1}  \\
\ket{1}&\rightarrow e^{i\phi}\sin \theta\ket{0} + \cos \theta \ket{1}   
\end{align}$$

Del fotón no podemos expresar una función de onda, pero podemos identificar distintos modos ópticos o grados de libertad que podemos usar como qubits.

## Creación y aniquilación

La absorción y emisión de fotones con un momento $k$ pueden ser descritos por las operaciones de creación y aniquilación $\hat{a}(k)$ y $\hat{a}^{\dagger}(k')$  que actúan sobre el estado cuántico de un fotón $\ket{n}$ de esta forma:
$$\begin{align}
\hat{a}\ket{n} & =\sqrt{  n}\ket{n-1} \\
\hat{a^{\dagger}}\ket{n} & =\sqrt{n+1}\ket{n+1}  
\end{align}$$
A partir de ellos se puede definir el operador $\hat{n}(k) = \hat{a}^{\dagger}(k)\hat{a}(k)$ tal que:
$$\hat{n}\ket{n}= n\ket{n}$$
Para cualquier modo dado con momento $k$

### Relaciones de conmutación operadores creación y aniquilación
Las relaciones de conmutación de los operadores de creación y aniquilación son las canónicas de este tipo de operadores:
$$\begin{align}
[\hat{a}(k),\hat{a}^{\dagger}(k')] &= \delta(k-k') \\
[\hat{a}(k),\hat{a}(k')] &= [\hat{a}^{\dagger}(k),\hat{a}^{\dagger}(k')] = 0
\end{align}$$
