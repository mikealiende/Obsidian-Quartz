# Puertas de cuánticas fotónicas un qubit

## Rotaciones en la esfera de Bloch
Veremos como los [[Elementos de óptica cuántica lineal]] somos capaces de aplicar todas las rotaciones en la esfera de Bloch.

### Mediante [[Láminas plano-paralelas]]

Si un fotón atraviesa una lámina con un índice de refracción diferente al de su entorno, se producirá un cambio en su fase mediante el operador:
$$\hat{a}^{\dagger}_{salida} = e^{i\phi}\hat{a}^{\dagger}_{entrada}$$
Lo que da lugar al **Hamiltoniano** de la interacción que es proporcional al operador número $n$, por lo que el número de fotones se conserva
$$H_{\phi} =  \phi \hat{a}^{\dagger}_{entrada}\hat{a}_{entrada}$$

La **matriz unitaria asociada** a este operador se puede escribir cómo:

$$U_{CF} = \begin{bmatrix}
 e^{i\phi} & 0 \\
0 & 1
\end{bmatrix}$$
### Mediante [[Divisores de haz]]

Si consideramos un divisor de haz con una amplitud en la transmisión parametrizada por $\theta$ tal que $T =\cos^2\theta$, con unas intensidades de entrada $\hat{a}^{\dagger}_{e}$ y $\hat{b}^{\dagger}_{e}$ en las posibles direcciones y una fase relativa $\phi$ podemos expresar las intensidades de salida a través de los siguientes operadores:
$$\begin{align}
\hat{a}^{\dagger}_{s} &= \cos \theta \cdot\hat{a}^{\dagger}_{e} +ie^{-i\phi}\sin \theta \cdot \hat{b}^{\dagger}_{e} \\
\hat{b}^{\dagger}_{s} &= ie^{i\phi}\sin \theta \cdot\hat{a}^{\dagger}_{e} +\cos \theta \cdot \hat{b}^{\dagger}_{e}
\end{align}$$
Los coeficientes de transmisión $T$ y reflexión $R$ son:
$$
\begin{align}
R &= \sin^2\theta \\
T&= 1-R = \cos^2\theta 
\end{align}$$
Mientras que el cambio de fase relativo $e^{\pm i\phi}$ mantiene la transformación como unitaria.

**El Hamiltoniano del divisor de haz** puede expresarse como:
$$H_{DH} = \theta e^{i\phi}\cdot\hat{a}^{\dagger}_{e}\hat{b}_{e} + \theta e^{-i\phi}\hat{a}_{e}\hat{b}^{\dagger}_{e}$$
Como conmuta con el operador número $n$, conserva el número de fotones.
La matriz unitaria asociada al divisor de haz es por lo tanto:
$$U_{DH} = \begin{bmatrix}
 \cos \theta & ie^{-i\phi}\cdot \sin\theta \\
ie^{i\phi}\cdot \sin \theta & \cos \theta
\end{bmatrix}$$

### Mediante [[Láminas de onda]]

La descripción matemática de una lámina de ondas es equivalente a la del divisor de haz, solo se cambian los dos modos espaciales por los modos de polarización:
$$\begin{align}
\hat{a}^{\dagger}_{e} &\rightarrow \hat{a}^{\dagger}_{x} \\
\hat{b}^{\dagger}_{e} &\rightarrow \hat{b}^{\dagger}_{y}
\end{align}$$
Siendo $x$ e $y$ dos ejes de polarización ortogonales elegidos arbitrariamente, los operadores quedarían de la forma:
$$\begin{align}
\hat{a}^{\dagger}_{x'} &= \cos \theta \cdot\hat{a}^{\dagger}_{x} +ie^{-i\phi}\sin \theta \cdot \hat{b}^{\dagger}_{y} \\
\hat{b}^{\dagger}_{y'} &= ie^{i\phi}\sin \theta \cdot\hat{a}^{\dagger}_{x} +\cos \theta \cdot \hat{b}^{\dagger}_{y}
\end{align}$$
El hamiltoniano es igual al del divisor de haz pero cambiando las direcciones espaciales por los ejes de polarización.

## Circuito óptico

Las transformaciones vistas anteriormente son suficientes para implementar cualquier operación de un solo qubit, con lo que vamos a poder fabricar circuitos ópticos para tareas de computación.

Un circuito óptico con $N$ entradas realiza una transformación unitaria sobre los $N$ modos posibles. A la salida detectamos estos modos mediante detectores ópticos, que dan lugar al estado cuántico.

El operador unitario de un circuito óptico de $N$ entradas puede ser descrito como:
$$\begin{align}
\hat{b}^{\dagger}_{k} \rightarrow \sum_{j=1}^N U^{*}_{jk}\cdot \hat{a}^{\dagger}_{j} \\
\hat{b}_{k} \rightarrow \sum_{j=1}^N U_{jk}\cdot \hat{a}^{\dagger}_{j}
\end{align}$$

Tenemos dos opciones para codificar el qubit:
* **Dirección espacial:** $$\begin{align}
\ket{0}_{L} &=\ket{1}\otimes \ket{0} \\
 \ket{1}_{L} &=\ket{0}\otimes \ket{1}   
\end{align}$$
* **Polarización**: $$\begin{align}
\ket{0}_{L} &=\ket{H} \\
\ket{1}_{L} &=\ket{V}  
\end{align} $$
Estas dos representaciones del qubit son equivalentes y podemos alternar entre ellas mediante un divisor de haces polarizado. 