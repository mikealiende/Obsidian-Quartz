# Quantum Phase Estimation


Este algoritmo estima la fase ($\phi$) del autovalor($e^{2\pi i\phi}$) asociado a un autovector ($\ket{u}$) de un operador unitario $U$. Es decir $$U\ket{u} = e^{2\pi i\phi}\ket{u}\text{ donde } \phi \in[0,1]  $$
Para describir la fase que está entre 0 y 1 vamos a usar la representación decimal binaria donde $$\phi=0.\phi_{1}\phi_{2}\phi_{3}\dots \phi_{n} \to \phi= \sum_{k=0}^n \phi_{k}2^{-k}$$



Para conseguir este estimación el vamos a usar dos registros cuánticos.

* Registro de estimación: $n$ qubits auxiliares en los que mediante el fenómeno de [[Phase Kickback]] almacenaremos la estimación de $\phi$.
* Registro de estado: $m$ qubits necesarios para almacenar el estado $\ket{u}$.

## Ejemplo para 1 qubit en el registro de estimación 


El primer primer paso del algoritmo es tratar de transferir la fase del registro de estado al registro de estimación. Para ello vamos a usar [[Phase Kickback]]. Para entenderlo vamos a ir al ejemplo más sencillo, con un único qubit de estimación y el autoestado $\ket{\psi}$ es autovector del operador unitario $U$ con un autovalor $\lambda=e^{2\pi i0.\phi_{1}}$. Ponemos en superposición el qubit de control (condiciones para que se produzca phase kickback) y tenemos el circuito:

![[Pasted image 20250126123654.png|200]]

Más adelante veremos porque usamos $U^{2^0}$. Como $U\ket{\psi} = \lambda \ket{\psi}$, el resultado de este circuito es: $$    \begin{align}
\frac{1}{\sqrt{ 2 }}(\ket{0}\ket{\psi}+\ket{1}U\ket{\psi}) =& \frac{1}{\sqrt{ 2 }}(\ket{0}\ket{\psi}+e^{2\pi i_{0}.\phi_{1}}\ket{1}\ket{\psi} \\
=& \frac{1}{\sqrt{ 2 }}(\ket{0}+e^{2\pi i_{0}.\phi_{1}}\ket{1})\otimes \ket{\psi} 
\end{align}$$
De este resultado podemos sacar dos conclusiones importantes:

* Como resultado del [[Phase Kickback]],algo información del autovalor de $\ket{\psi}$ se ha almacenado en la fase relativa del qubit de control.
* El autoestado $\ket{\psi}$ no se ha modificado al aplicar $U$ y no lo hará por muchas veces que lo apliquemos. 

En el caso de tener un qubit en el registro de estimación bastará con aplicarle otra puerta $H$ antes de medir para poder leer esta información almacenada en la fase:
$$\begin{align}H\frac{1}{\sqrt{ 2 }}(\ket{0}+e^{2\pi i_{0}.\phi_{1}}\ket{1}) =& \frac{1}{2}((\ket{0+\ket{1}})+(e^{2\pi i_{0}.\phi_{1}}\ket{0}-e^{2\pi i_{0}.\phi_{1}}\ket{1})) \\
=&\frac{1}{2}((1+e^{2\pi i_{0}.\phi_{1}})\ket{0} +(1-e^{2\pi i_{0}.\phi_{1}})\ket{1})
\end{align}$$
Así medimos con total certeza el estado que nos dice cual es valor de la fase y por lo tanto del autovalor de $\ket{\psi}$


## Algoritmo de estimación de fase general

Si sólo contamos con un qubit en el registro de estimación la precisión con la que calculamos la fase va a ser limitada, por eso la idea de este algoritmo es utilizar un registro con $n$ qubits en superposición y aplicar $C\text{-}U^{2^k}$, ya que:$$U^{k}\ket{\psi} = e^{2\pi i\phi \cdot k}\ket{\psi}$$
Evidentemente, para que se de esto seguimos manteniendo que el autoestado $\ket{\psi}$ es un autovector de $U$ con autovalor $e^{2\pi i\phi}$. Como en el caso anterior la información de la fase de $\ket{\psi}$ se transferirá a la fase relativa de los qubits del registro de estimación, pero leerla no será tan sencillo como aplicar la puerta $H$, si no que tendremos que aplicar la [[Transformada cuántica de Fourier QFT]] inversa $QFT^{\dagger}$. De esta manera, transformaremos la información almacenada en las fases de los qubits del registro de estimación a la base computacional. 
### Ejemplo para 2 qubits. 

![[Pasted image 20250126134257.png|200]]

Después de aplicar los dos operadores controlados, tendríamos $(\ket{0}+e^{2\pi i0.\phi_{1}}\ket{1})\otimes(\ket{0}+e^{2\pi i0.\phi_{1}\phi_{2}}\ket{1})\otimes \psi$. Si aplicamos $QFT^{\dagger}$, tenemos(ignoramos los coeficientes):$$QFT^{\dagger}((\ket{0}+e^{2\pi i0.\phi_{1}}\ket{1})\otimes(\ket{0}+e^{2\pi i0.\phi_{1}\phi_{2}}\ket{1}))\otimes \psi = \ket{\phi_{2}\phi_{1}}\otimes \ket{\psi}  $$

### Ejemplo para $n$ qubits

El circuito del algoritmo de estimación de fase para $n$ qubits sería: 

![[Pasted image 20250126135508.png|500]]

Vamos a detallar cada paso de este circuito.

1. Describimos el estado inicial del circuito como $\ket\theta_{0}=\ket{0}^{\otimes n}\otimes \ket{\psi}$
2. Para poner el registro de estimación en superposición aplicamos $H$ a los $n$ qubits $$\ket{\theta_{1}}=H^{\otimes n}\ket{\theta_{0}}= \frac{1}{\sqrt{ 2^n }}\sum_{k=0}^{n}\ket{k}\otimes \ket{\psi}    $$Donde $\ket{k}$ son los estados de la base computacional de $n$ qubits. Ej para 3 qubits $\ket{000},\ket{001},\ket{010}\dots$

3. Aplicamos las puertas $C\text{-}U^{2^k}$ por cada qubit del registro de estimación y expandimos la fase en su notación binaria decimal tenemos:$$\ket{\theta_{2}}= C\text{-}U\ket{\theta_{1}} = \frac{1}{\sqrt{ 2 }}(\ket{0}+e^{2\pi i0.\theta_{1}\theta_{2}\theta_{3}\dots\theta_{n} }\ket{1})\otimes(\ket{0}+e^{2\pi i0.\theta_{2}\theta_{3}\theta_{4}\dots\theta_{n} }\ket{1})\otimes \dots \otimes(\ket{0}+e^{2\pi i0.\theta_{n}})$$
4. En este punto tenemos la representación decimal binaria de la fase almacenada en la fase relativa de los qubits del registro de estimación, por eso vamos a utilizar $QFT^{\dagger}$ para mapear estos estados de la fase a estados computacionales.$$\ket{\theta_{3}}=QFT^{\dagger}\ket{\theta_{2}} = \ket{\theta_{n}}\ket{\theta_{n-1}\ket{\theta n-2}\dots \ket{\theta_{1}}  }    $$
De esta manera conseguimos una estimación de la fase en la base computacional.

En resumen, la idea del algoritmo ha sido:

* Usar [[Phase Kickback]] con los operadores controlados $C\text{-}U^{k}$ para transferir la fase del registro de estados a la fase relativa de los qubits del registro de estimación.
* Utilizar $QFT^{\dagger}$ para mapear lso valores almacenados en la fase relativa de los qubits a estados computacionales.
