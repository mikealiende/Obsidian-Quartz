# Teorema de Shannon-Hartley

A veces también denominado tercer teorema de Shannon, proporciona la velocidad máxima a la que la información puede ser transmitida por un canal con un ancho de banda dado en presencia de ruido. (Canal analógico con ruido gaussiano).

* $C$: Capacidad del canal.
* $W$: Ancho de banda (Hz).
* $N_{0}$: Densidad espectral del ruido blanco aditivo gaussiano.
* $P$: Potencia media transmitida.
$$C = W\log_{2}\left( 1+\frac{P}{N_{0}W} \right) \text{bits/s}$$
* El termino $\frac{P}{N_{0}W}$ es el ratio señal a ruido SNR.
* La capacidad del canal se alcanza cuando la fuente parece ruido, se puede demostrar que:$$C \rightarrow \frac{P}{N_{0}}\log_{2}e$$
Si escribimos esta expresión en términos de la energía por bit ($E_{b}=\frac{P}{C}$). 
Entonces obtenemos el **limite de Shannon**:
$$\frac{E_{b}}{N_{0}}\rightarrow \log_{2}e=0,693$$
