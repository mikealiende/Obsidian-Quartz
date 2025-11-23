# Puntos cuánticos semiconductores

## Fabricación

Los puntos cuánticos semiconductores se fabrican mediante técnicas litográficas a partir de un diseño complejo pero reproducible.
Parten de un pozo cuántico bidimensionales, que puede ser de un material semiconductor como el silicio.

![[Pasted image 20240602122935.png]]
* (a): Representación esquemática de la geometría de las bandas
* (b): Pozo cuántico de potencial 
* (c): Estructura de electrodos
* (d): Esquema del perfil de densidad de estado de un punto cuántico fabricado a partir de un pozo cuántico.

Para pasar de un pozo cuántico a un punto, se hace mediante técnicas litográficas y una serie de electrodos de control que pueden modificar las propiedades electrónicas del material mediante la aplicación de tensión.

Como partimos de un pozo cuántico, el confinamiento en una de las direcciones ya viene determinado por la geometría del pozo, mientras que los electrodos de control nos permiten crear barreras de potencial de manera localizada en las otras dos dimensiones espaciales, dando control sobre el lugar e intensidad del confinamiento. Gracias a esto, podemos cargar y descargar el punto cuántico, conectarlo con otros puntos o simplemente hacerlo desaparecer y devolverlo al pozo original.

## Puntos cuánticos semiconductores como qubits

* Los electrodos que están directamente enfrentados a la región de confinamiento carga permiten modular la profundidad del pozo $\rightarrow$ Alterando la posición de los niveles energéticos del electrón confinado.
* Los electrodos de puerta situados a sus lados, permiten cambiar la altura de la barrera potencial $\rightarrow$ Modula la intensidad de la interacción entre puntos cuánticos adyacentes.

### Protocolo inicialización punto cuántico en superposición

Una de las posibilidades para inicializar un qubit en superposición es considerar el estado de carga de dos puntos cuánticos interconectados separados por una barrera potencial controlable. Es posible cargar uno de los puntos con un electrón y jugando con la modulación de la altura de la barrera, creamos un estado en superposición

![[Pasted image 20240602224158.png]]

* a) Estado inicial con el qubit descargado
* b) Carga del qubit con un electrón e inicialización al estado con la carga en el punto cuántico izquierdo $\ket{I}$
* c) Modulación de la barrera de potencial entre puntos mediante el electrodo de puerta.
* d) Estado de superposición entre los dos estados de carga: $\alpha \ket{I}+\beta \ket{D}$

### Puertas cuánticas un solo qubit

La intensidad de interacción entre los puntos cuánticos, también pede ser controlada mediante los electrodos de puerta., lo que permite cambiar entre un estado u otro incluso superposiciones de ambos. Mediante pulsos de corriente de una duración determinada se puede establecer la relación entre ambos, lo que permite recorrer toda la esfera de Bloch con su elección adecuada. Podemos constituir así todas la puertas cuánticas sobre un solo qubit.

![[Pasted image 20240602225451.png|500]]

Esto sería un ejemplo de como podemos realizar rotaciones en un solo qubit mediante pulsos de corriente.

### Medidas de qubits de puntos cuánticos

La medida de el estado de un qubit de este tipo, se puede realizar con un sensor capacitivo de carga situado cerca de uno de los puntos cuánticos. Esto nos indicará si la carga está presente en él.

Mediante el mismo tipo de interacci
