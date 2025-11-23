# Hadamard Test

El test de Hadamard es capaz de calcular $\Re\bra{\phi}U\ket{\phi}$ para cualquier operador unitario $U$. También en posible calcular la parte imaginaria con modificaciones en el test, por lo tanto, relacionándolo con el algoritmo [[EVA]] podríamos pensar que sustituyendo $H$ por $U$ podríamos llegar a la solución deseada, el problema es que $H$ no tiene porque ser unitario.

![[Pasted image 20240525105958.png| 400]]

A partir de este circuito podemos asegurar que:
$$\Re(\bra{\phi}H\ket{\phi}) = P(0)-P(1)$$
Siendo $P(0)$ y $P(1)$ la probabilidad de obtener $\ket{0}$ y $\ket{1}$ respectivamente al medir sobre el primer qubit.

## Demostración Hadamard Test

1. Empezamos por el estado $\ket{\phi}\ket{0}$, tras aplicar la puerta Hadamard sobre el primer qubit tenemos:
$$\ket{\phi}\frac{{\ket{0}+\ket{1}}}{\sqrt{ 2 }} $$
2. Tras aplicar la puerta controlada tenemos:

$$\frac{U\ket{\phi}\ket{1}}{\sqrt{ 2 }}+\frac{\ket{\phi}\ket{0}}{\sqrt{ 2 }}    $$
4. Volvemos a aplicar la Hadamard:
$$\frac{{U\ket{\phi}\ket{0}-U\ket{\phi}\ket{1}}}{2} + \frac{{\ket{\phi}\ket{0}+\ket{\phi}\ket{1}}}{2}$$

Si agrupamos respecto al qubit de medición tenemos: 
$$\frac{{(U\ket{\phi}+\ket{\phi})\ket{0}-(U\ket{\phi}-\ket{\phi})\ket{1}}}{2}$$
Vamos a calcular primero $P(0)$:
$$\begin{align}
P(0) &=  \left\| \displaystyle\frac{(U\ket{\phi}+\ket{\phi})}{2} \right\|^2 = \frac{{(\bra{ {\phi}}U^{\dagger} +  \bra{\phi})(U\ket{\phi}+\ket{\phi})}}{4} = \\ \\

&= \frac{{2+\bra{\phi}U^{\dagger}\ket{\phi}+\bra{\phi}U\ket{\phi}}}{4} 
\end{align}$$
Y ahora calcularemos $P(1)$:
$$\begin{align}
P(1) &=  \left\| \displaystyle\frac{(U\ket{\phi}-\ket{\phi})}{2} \right\|^2 = \frac{{(\bra{ {\phi}}U^{\dagger} - \bra{\phi})(U\ket{\phi}-\ket{\phi})}}{4} = \\ \\

&= \frac{{2-\bra{\phi}U^{\dagger}\ket{\phi}-\bra{\phi}U\ket{\phi}}}{4} 
\end{align}$$

Si restamos ambas probabilidades tenemos: 
$$P(0)-P(1) = \frac{{\bra{\phi}U^{\dagger}\ket{\phi}+\bra{\phi}U\ket{\phi}}}{2}$$
Sabiendo que la suma de un número complejo con su conjugado nos da el doble de su parte real $z^* +z = 2 \Re(z)$, por lo tanto:
$$P(0)-P(1) = \Re(\bra{\phi}U\ket{\phi})$$
Queda así demostrado.

## Hadamard test parte imaginaria

De la misma manera podemos usar este circuito para obtener $P(0)-P(1) = \Im(\bra{\phi}U\ket{\phi})$


![[Pasted image 20240525115308.png|450]]

