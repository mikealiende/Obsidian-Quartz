# Tiempo de decoherencia

El tiempo de decoherencia es el conjunto de tiempos característico sde las dinámicas de un sistema cuántico en contacnto con su enterno físico. Esto incluye el resto de qubits del procesador, el entorno material, campos externos, etc.

De manera genérica puede considerarse como el tiempo en que un estado cualquiera $\ket{\psi} = a\ket{0}+\ket{1}$ se transforma en un estado mezcla con una matriz de probabilidad $\rho =  |a|^2 \ket{0}\braket{ 0}+ |b|^2 \ket{1}\bra{1}$, comportándose de manera clásica.

![[Pasted image 20240628122058.png|400]]\

El ruido en un qubit implica la decoherencia del estado cuántico y la reducción de su fiabilidad, ciertos sistemas a dos niveles son muy sensibles al ruido.

Podemos clasificar el ruido en sistemático  o aleatorio:

* **Ruido sistemático:** Depende de las características físicas del sistema, en general puede ser identificado y corregido.
* **Ruido aleatorio:** Es muy difícil de indentificar y corregir, ya que proviene de variables incontrolables del enterno del sistema y depende de parametros ajenos al sistema de control.
 