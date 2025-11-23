# Adaptación Hamiltoniano genérico VQE

El objetivo es adaptar el algoritmo  [[VQE]] de la manera que podamos calcular el valor esperado de cualquier Hamiltoniano independientemente del operador de Pauli que nos encontremos, es decir, calcular $\bra{\phi}\sigma_{i}\ket{\phi}$ y $\bra{\phi}\sigma_{i}\sigma_{j}\ket{\phi}$ para cualquier operador de Pauli.

### Operador de Pauli $\sigma^z$

Para $\sigma^z$,  ya demostramos que:
$$\bra{\phi}\sigma_{i}^z\ket{\phi} = P(\ket{0}_{i})-P(\ket{1}_{i} ) $$
Siendo $P(\ket{0})$ la probabilidad de obtener el estado $\ket{0}$ al medir el qubit $i$ sobre el estado $\ket{\phi}$.

### Operador de Pauli $\sigma^x$

Para el caso de $\sigma^x$ usamos la propiedad $\sigma^x = H\sigma^zH$ siendo $H$ la [[Puerta de Hadamard]]. Siguiendo el razonamiento anterior:
$$\bra{\phi}\sigma_{i}^x\ket{\phi} = \bra{\phi}H\sigma_{i}^zH\ket{\phi}  = \bra{\phi}H^{\dagger}\sigma_{i}^zH\ket{\phi} = \bra{\phi'}\sigma_{i}^z\ket{\phi'}$$

Por lo tanto para obtener el valor esperado a través de la puerta $\sigma^x$, deberemos calcular $P(\ket{0}_{i})-P(\ket{1}_{i})$ sobre el estado $\ket{\phi'}$
Siendo:
$$\begin{align}
\ket{\phi'} =& H\ket{\phi}  \\
\bra{\phi'} =&\bra{\phi}H^{\dagger}  
\end{align}$$
### Operador de Pauli $\sigma^y$

El razonamiento es el mismo pero utilizando la puerta
$$H_{y} = \frac{1}{\sqrt{ 2 }}\begin{bmatrix}
1 & -i \\
i & -1
\end{bmatrix}$$
De esta manera $\sigma^y = H_{y}\sigma^zH_{y}$.

## Producto tensorial de puertas Pauli

Tenemos que plantear lo mismo para producto tensorial de cualquier puerta de Pauli. Recordemos que para puertas $\sigma^z$ tenemos:
$$\bra{\phi}\sigma_{i}^z\sigma_{j}^z\ket{\phi} = P(\ket{0}_{i},\ket{0}_{j})-P(\ket{1}_{i},\ket{0}_{j}) -P(\ket{0}_{i},\ket{1}_{j}) + P(\ket{1}_{i},\ket{1}_{j}) $$
Siendo por ejemplo $P(\ket{0}_{i},\ket{1}_{j})$ la probabilidad de encontrar en $\ket{0}$ al qubit $i$ y en $\ket{1}$ al qubit $j$. Para calcular $\bra{\phi}\sigma_{i}^x\sigma_{j}^x\ket{\phi}$ y $\bra{\phi}\sigma_{i}^y\sigma_{j}^y\ket{\phi}$ podemos utilizar la misma técnica que en los casos de una puerta, ejemplo:
$$\begin{align}
\bra{\phi}\sigma_{i}^x\sigma_{j}^x\ket{\phi} = & \bra{\phi}H\sigma_{i}^zHH\sigma_{j}^zH\ket{\phi} =\\
= & \bra{\phi}H^{\dagger}\sigma_{i}^zI\sigma_{j}^zH\ket{\phi} = \\
 \bra{\phi}\sigma_{i}^x\sigma_{j}^x\ket{\phi}=& \bra{\phi'}\sigma_{i}^z\sigma_{j}^z\ket{\phi'} 
\end{align}$$
También podemos estar en la situación de tener el producto tensorial de dos puertas distintas, ejemplo $\sigma_{i}^z\sigma_{j}^x$, para resolver esto recurrimos a encontrar equivalencias con única puerta de Pauli.

### Simplificación de operadores de Pauli

Gracias las siguientes reglas siempre vamos a ser capaces de simplificar productos tensoriales de operadores de Pauli.
#### Reglas de simplificación

* El producto de dos operadores de Pauli iguales es $I$
* El producto de dos operadores de Pauli distintas, da lugar al tercer operador de Pauli por un coeficiente
	* Si el orden alfabético es creciente, el coeficiente es $i$
	* Si el orden alfabético es decreciente, el coeficiente es -i
	* Ejemplo: $ZX = -iY$ 

Ejemplo:
![[Pasted image 20240528190025.png|400]]

