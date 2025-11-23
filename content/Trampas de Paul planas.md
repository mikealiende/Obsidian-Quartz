# Trampas de Paul planas

Las trampas de Paul planas o superficiales, se fabrican con métodos litográficos. Consisten en una serie de electrodos y guías de onda que permiten modular el campo electromagnético en la superficie de un chip generando los campos magnéticos oscilantes necesarios para crear el potencial de confinamiento necesario para atrapar los iones.

Mediante estas estructuras es posible atrapar pequeños grupos de iones sobre los que se puede operar mediante láseres de manera independiente, efectuando operaciones a partir de las técnicas descritas anteriormente. 
![[Pasted image 20240519174006.png| 400]]

Con estas trampas podemos desplazar iones de una región a otra como vemos en la imagen. Esto permite la interacción entre qubits que normalmente estarían desacoplados, así como interrelacionar diferentes registros a través de un ion mensajero que comparta la información cuántica entre ellos. Normalmente, las puertas cuánticas y las medidas se realizan en una región específica del sistema donde se realizan todas las interacciones con el láser, en la imagen sería el punto rojo.

Cuando se quiere hacer interactuar el estado del conjunto de iones de una trampa con otra, los electrodos dispuesto alrededor de la trampa permiten aplicar un campo eléctrico constante que puede desplazar y guiar a uno de los iones de una trampa a otra. De esta manera podemos tener pequeños registros cuánticos aislados y trasladar uno o varios iones desde los distintos registros a la zona de interacción con el láser para realizar las operaciones sobre los qubits que requiera el algoritmo implementar. Debemos tener en cuenta

* Desplazar un ion de una trampa a otra no suele tener efecto negativos respecto al estado del qubit, oeri el estado de movimiento del ion si puede afectar a su estado, por esto, es necesario que el movimiento de una trampa a otra no sea demasiado acelerado.
* Por otro lado, tiene que ser lo suficientemente rápida como para poder realizar el desplazamiento de ida y vuelta y aplicar las puertas cuánticas necesarias en tiempo cortos para que el qubit no pierda su coherencia. 

### Operaciones mediante desplazamiento en la trampa de iones

Las operaciones de desplazamiento se pueden realizar mediante la aplicación  de perfiles de tensión programados con un generador de forma de onda arbitraria o un procesador digital de señales. Estos instrumentos actúan como fuentes de tensión programables. Para estudiar el estado de movimiento de un ion se utilizan las **técnicas de Raman**, que permite conocer por medios ópticos el estado de movimiento de las partículas. Analizando la intensidad y frecuencia de la emisión Raman es posible determinar el número de iones en un cristal a partir de sus características vibracionales.

Estos son los tipo de operaciones que pueden realizar mediante el desplazamiento:

#### Transporte lineal
Desplazamiento de un ion o conjunto de iones de un lugar a otro del dispositivo. Se realiza mediante la aplicación de rampas de voltaje en los electrodos de continua, lo que permite desplazar el potencial de confinamiento en una dirección u otra.

#### Separación u unión
Se puede extraer un ion o un subconjunto de iones de una trampa para desplazarlos por el dispositivo o realizar la unión de dos o varios iones en un nuevo cristal ionico. 

El proceso de separación o unión de trampas es más complicado de realizar, ya que implica cambiar la forma del potencial de confinamiento durante el periodo de tiempo necesario para realizar la división o la unión. Durante el proceso de creación o destrucción de una barrera entre trampas , la interacción electroestática entre los iones será la dominante, lo que puede provocar el escape de alguno de ello o de introducir oscilaciones en la trampa. 

#### Intercambio
Es posible intercambiar las posiciones de los iones dentro de un cristal, lo que posibilita su reordenamiento. Esta operación es equivalente a una puerta SWAP. Para realizar esto se hacen oscilar electrones de la trampa en dirección paralela a esta mientras se manipulan los electrodos de continua para crear un campo eléctrico en la dirección perpendicular. Esto permite que un ion "salte" sobre todo fuera del eje de confinamiento , permitiendo que intercambien sus posiciones.


