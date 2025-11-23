# La máquina de Turing #Tema 

La máquina de Turing aparece por primera vez en el artículo de Turing «Sobre los números computables, y su aplicación al Entscheidungsproblem» (1937).

Nos vamos a centrar en la máquina de Turing determinista. Para el caso de un máquina de Turing de memoria acotada, la máquina esta formada por:
* Cabezal
* Unidad de control
* Unidad de cinta

![[Pasted image 20250111120154.png|300]]


El funcionamiento a alto nivel sería:
* Para cada unidad de tiempo, la unidad de control acepta una entrada de la unidad de la cinta y proporciona una salida.
* La unidad de cinta proporciona el valor de la salida en la celda bajo el cabezal. Este valor es una palabra de b-bits. La unidad de cinta acepta y escribe esta palabra de b-bits en la celda
* La unidad de cinta también puede recibir y aceptar instrucciones para mover el cabezal a una celda a la izquierda o derecha.
* La unidad de cinta es una matriz de celdas y tiene una capacidad de almacenamiento de $S = m \cdot b$ bits.

De forma más detallada, vamos a explicar los [[Componentes de la máquina de Turing]].

[[Definición formal de la máquina de Turing]]

Podemos representar el funcionamiento de estas máquina con [[Diagramas de estados de la máquina de Turing]].

Para terminar vamos a explicar las [[Máquinas de Turing universales]]