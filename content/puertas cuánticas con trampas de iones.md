# Puertas cuánticas con trampas de iones

## Rotaciones en la esfera de Bloch

Para poder realizar rotaciones arbitrarias en la esfera de Bloch, es necesario considerar no solo las transiciones electrónicas de los iones, sino también si estado de movimiento en el seno de la trampa.

El movimiento del ion atrapado se caracteriza por unas frecuencias de resonancia definidas por el potencial de confinamiento, que se puede aproximar al potencial de un [[Oscilador armónico cuántico]]. Los diferentes estados de movimiento del ion se pueden codificar como un estado cuántico al que denotaremos por $\ket{n}$ con  $n = 0,1,\dots$ en función del estado de movimiento.Teniendo en cuenta los estados electrónicos y los de movimiento, podemos definir el estado de un qubit en un momento dado como la combinación de ambos: $\ket{\downarrow, n}$ o $\ket{\uparrow,n}$.

Los estados de espín y de movimiento del láser se pueden acoplar modulando la frecuencia del láser $\omega_{\uparrow \rightarrow e}\pm \omega_{m}$ donde $\omega_{m}$ es la diferencia de frecuencia entre estados de movimiento. Esta excitación hará evolucionar al qubit desde el estado $\ket{\uparrow, n}$ al estado $\ket{e, n+\Delta n}$, que puede ser descrito como una rotación $R_{\Delta n(\theta,\phi)}$ en la esfera de Bloch. Usando esta técnica, $\theta$ depende de la duración del pulso del láser y $\phi$ depende de su fase en la posición de ion. 

Así representamos el acoplamiento entre los estados electrónicos del ion y el potencial armónico de la trampa

![[Pasted image 20240519164702.png|480]]

## Puertas de dos qubits

### En la misma trampa

Para generar puertas con dos qubits mediante entrelazamiento, tales como CNOT o CPHASE, también se utilizan los estados vibracionales  de movimiento de los iones. Para ello. se iluminan con la misma radiación láser simultáneamente dos iones que estén en una misma cadena. Los estados de espín de ambos iones pueden entrelazarse a través de la interacción de sus estados de movimiento.

### En distintas trampas

También se pueden entrelazar qubits que están en diferentes trampas mediante técnicas fotónicas con el uso de pulsos láser cortos que provoquen la generación de fotones individuales en los iones. Si los fotones emitidos por dos de estas trampas son enviados a un divisor de hay y detectados simultáneamente es un indicativo de la existencia de un [[estados de Bell]] entre los dos fotones y, por lo tanto, de que los iones que los han generado están entrelazados. Debido a la baja probabilidad de que dos fotones interfieran, esta técnica es muy lenta. Incluso excitando los iones de comunicación con pulsos de picosegundos a frecuencias de GHz. No obstante demuestra la posibilidad de conectar dos registros cuánticos de iones situados en diferentes trampas. 

Otra forma de operar con qubits agrupados en diferentes trampas consiste en desplazar alguno de ellos de una trampa a otra. Las distintas trampas tiene que estar a una distancia tal que se puedan considerar independientes, de manera que la única interacción entre ellas sean los iones que se han hecho viajar entre ellas. Para aplicar esta tecnica, los ordenadores basados en trampas de iones utilizan [[Trampas de Paul planas]]