# EVA Exponential Value Approximation #Tema 

En este tema veremos el algoritmos EVA (Alonso-Linaje) [[EVA.pdf]]. Que consigue aproximar el resultado con el uso único circuito. El objetivo de este algoritmo es encontrar con un único circuito el valor $\bra{\phi}H\ket{\phi}$,
para ello, vamos a hacer uso del [[Hadamard Test]], que demuestra que:
$$\mathrm{Re}(\bra{\phi}U\ket{\phi})=P(0)-P(1)$$
El problema que tenemos que solucionar es que el $H$ no tiene porque ser unitario, por lo tanto, tenemos que calcular $e^{iH}$.


## Desarrollo del Algoritmo

Como no podemos  el Hamiltoniano no tiene porque ser unitario, vamos a recurrir al operador $e^{iH}$. Con esto hacemos el desarrollo en serie de Taylor de la exponencial : $e^x = 1 +x +\frac{x^2}{2}+\dots$

Sustituyendo $x$ por $\frac{iH}{k}$, y tomando valores esperados, llegamos a:$$\bra{\phi}e^{iH/k}\ket{\phi} = \bra{\phi}I\ket{\phi}+i\frac{{\bra{\phi}H\ket{\phi}}}{k} -  \bra{\phi}H^2\ket{\phi} - \dots$$
Vamos atomar la parte imaginaria  de la expresión:$$\begin{align}
\Im(\bra{\phi}e^{iH/k}\ket{\phi}) = & \frac{\bra{\phi}H\ket{\phi}}{k} - \frac{\bra{\phi}H^3\ket{\phi}}{3!k^3}+\dots  \\
 \\
  \bra{\phi}H\ket{\phi} =  &  \Im(\bra{\phi}e^{iH/k}\ket{\phi}) +\frac{\bra{\phi}H^3\ket{\phi}}{3!k^3}- \dots
\end{align}$$

Siendo $k \geq 1$, si tomamos los limites podemos llegar a la ecuación fundamental del algoritmo:$$\bra{\phi}H\ket{\phi} = \lim_{ k \to \infty } k\Im\bra{\phi}e^{iH/k}\ket{\phi}    $$
Por lo tanto, para obtener el valor esperado del estad $\ket{\phi}$ a través del Hamiltoniano, únicamente será necesario construir la exponencial compleja de dicho Hamiltoniano y aplicar [[Hadamard Test#Hadamard test parte imaginaria]] para obtener la parte imaginaria:

![[Pasted image 20240525190311.png]]
Visto de esta manera, ejecutaremos dicho circuito y calcularemos $k(P(0)-P(1))$ como aproximación a nuestro valor buscado.

La pregunta que no podemos hacer es como de bien aproxima este método, para ello, buscaremos [[Cota al error en la estimación EVA]]. Como hemos visto, aparentemente podemos tomar un valor de $k$ tan  grande como queramos, si embargo esto no lo podemos hacer debido a [[Limitaciones EVA]]
