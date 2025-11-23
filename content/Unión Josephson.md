# Unión Josephson

Utilizando este efecto, se desarrollaron los dispositivos conocidos como uniones Josephson, los cuales se tratan de dos superconductores separados por un aislante. Estos dispositivos tienen una inductancia no lineal, por lo tanto, si sustituimos por la inductancia en nuestro [[circuito LC]] que funcione como un [[Oscilador armónico cuántico]], conseguimos de esta manera romper la degeneración del espectro de energía.

![[Pasted image 20240512194011.png|500]]


Gracias a la unión Josephson, podemos usar este resonador cuántico a dos niveles como un qubit, ya que somos capaces de distinguir entre estados del espectro de energía y tener así nuestro sistema cuántico a dos niveles. 

## Espectro de energía unión Josephson

![[Pasted image 20240514185109.png| 250]]


Como hemos dicho hemos la unión Josepshon permite romper la degeneración la energía del [[Oscilador armónico cuántico]], es decir, la energía para pasar de estado $\ket{0}$ a $\ket{1}$ es distinta que la que necesitamos para pasar de $\ket{1}$ a $\ket{2}$. El Hamiltoniano del circuito se puede expresar como:

$$H = 4E_{c}n^2 - E_{j}\cos (\phi)$$
Siendo : $$\begin{align}
&E_{c} = \frac{e^2}{2(C_{s} + C_{j})} \\ \\
&E_{j} = \frac{I_{c}\Phi_{0}}{2\pi}
\end{align}$$
Donde $C$ es la capacidad total e $I_{c}$ es la corriente crítica de la unión Josephson. Con un diseño adecuado de puertas y control robusto, podemos despreciar el resto de estados de energía que no estén nuestra base computacional. De esta manera, tendríamos un [[Sistemas cuánticos de dos niveles]], asumiendo esto, podemos reducir el Hamiltoniano a 
$$H = \omega_{q}\frac{\sigma_{z}}{2}$$
