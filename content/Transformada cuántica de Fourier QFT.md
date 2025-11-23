# Transformada cuántica de Fourier QFT

Es la versión cuántica de la transformada discreta de Fourier, una transformación lineal que transforma del dominio del tiempo a la frecuencia. La transformada cuántica de Fourier es una transformación unitaria que transforma de la [[Base computacional]]  a [[Base Fourier]].

La transformada de Fourier se define como: $$QFT\ket{x}\rightarrow \frac{{1}}{\sqrt{ N }}\sum_{y=0}^{N-1}e^{2\pi i\cdot \frac{xy}{N}} \ket{k} $$
Siendo $N =2^n$, donde $n$ es el número de qubits, vamos a estudiar en detalle la siguiente demostración para el caso general de $n$ qubits.$$$$$$\frac{{1}}{\sqrt{ N }}\sum_{y=0}^{N-1}e^{2\pi i\cdot \frac{xy}{N}} \ket{k} = \frac{1}{\sqrt{ N }}(\ket{0}+e^{2\pi i \frac{x}{2}} \ket{1} )\otimes(\ket{0}+e^{2\pi i \frac{x}{4}}\ket{1}  )\otimes \cdots \otimes(\ket{0}+e^{2\pi i \frac{x}{2^n}} \ket{1} )$$

### Demostración caso general $n$ qubits.
![[Demostración QFT.pdf]]



### Implementación QFT en un circuito cuántico

Vamos a trasladar la expresión anterior a un circuito cuántico.Puesto que:
$$
\frac{1}{\sqrt{2}}(\ket{0}  + e^{i\pi x_k}\ket{1} ) =
\begin{cases} 
\frac{1}{\sqrt{2}}(\ket{0}  + e^0\ket{1} ) = \frac{1}{\sqrt{2}}(\ket{0}  + \ket{1} ), & x_k = 0 \\ 
\frac{1}{\sqrt{2}}(\ket{0}  + e^{\pi i}\ket{1} ) = \frac{1}{\sqrt{2}}(\ket{1}  - \ket{1} ), & x_k = 1
\end{cases}
$$

Corresponde con el comportamiento de la puerta Hadamard sobre $x_{k}$: $$\frac{1}{\sqrt{2}}(\ket{0}  + e^{i\pi x_k}\ket{1} ) =
\begin{cases} 
\frac{1}{\sqrt{2}}(\ket{0}  + \ket{1} ) = \ket{+} , & x_k = 0 \\ 
\frac{1}{\sqrt{2}}(\ket{1}  - \ket{1} ) = \ket{-} , & x_k = 1
\end{cases}$$
Por otro lado, podemos utilizar la puerta de fase $P(\theta)$: $$P(\theta) = \begin{bmatrix}
1 & 0  \\
0 & e^{i\theta}
\end{bmatrix}$$
Que lo que hace es: 

* $\ket{0}\rightarrow \ket{0}$
* $\ket{1}\rightarrow e^{i\theta}\ket{1}$

#### Ejemplo para 3 qubits

Siendo entonces $\ket{x} = \ket{x_{2},x_{1},x_{0}}$ la QFT sería: 
$$
QFT_8\ket{x} = \frac{1}{\sqrt{8}} \big(\ket{0} + e^{2\pi i \frac{x_0}{2}} \ket{1}\big) 
\otimes \big(\ket{0} + e^{2\pi i \big(\frac{x_0}{2^2} + \frac{x_1}{2}\big)} \ket{1}\big) 
\otimes \big(\ket{0} + e^{2\pi i \big(\frac{x_0}{2^3} + \frac{x_1}{2^2} + \frac{x_2}{2}\big)} \ket{1}\big)
$$
Nos fijamos en el último término y aplicamos $e^{A+B} = e^Ae^B$: $$(\ket{0} + e^{2\pi i \large(\frac{x_0}{2^3} + \frac{x_1}{2^2} + \frac{x_2}{2}\large)} \ket{1}) = \ket{0}+e^{\pi i\frac{x_{0}}{2^2}}e^{\pi i\frac{x_{1}}{2}} e^{\pi ix_{2}} \ket{1}  $$

Desgranado esta expresión tenemos sobre el qubit $x_{2}$ tenemos:

* Debe rotar $\pi$ radianes si el vale $\ket{1}$. Corresponde con el comportamiento de la puerta $H$ (revisar esto)
* Debe rotar adicionalmente $\frac{\pi}{2}$ si el qubit $x_{1}$ es $\ket{1}$. Corresponde con la puerta $P\left( \frac{\pi}{2} \right)$ controlada por $x_{1}$
* Por último, deberá rotar adicionalmente $\frac{\pi}{4}$ si el qubit $x_{0}$ es $\ket{1}$. Corresponde con la puerta $P\left( \frac{\pi}{4} \right)$ controlada por $x_{0}$

Si construimos este circuito para el qubit $x_{2}$ tenemos:

![[Pasted image 20250121204123.png|300]]

Completando el circuito pera los otros 2 términos siguiendo la misma lógica tenemos el circuito completo que proporciona la transformada de Fourier para 3 qubits.

![[Pasted image 20250121204238.png]]