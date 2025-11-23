# Máquinas de acceso aleatorio RAM

Son máquinas abstractas dentro de la clase de máquinas de registros. Las RAM se pueden modelar mediante dos máquinas de estados finitos síncronas, una CPU y una memoria de acceso aleatorio.

![[Pasted image 20241215181804.png|400]]


La **CPU** implementa un ciclo de búsqueda y ejecución en el que alternativamente lee una instrucción de un programa almacenado en la memoria RAM. Por lo general, las instrucciones se leen y se ejecutan desde ubicaciones consecutivas en la memoria RAM. Una CPU tiene 5 tipos básicos de instrucción:

* Instrucciones aritméticas y lógicas.
* Instrucciones de almacenamiento y carga de memoria, mover datos entre ubicaciones de memoria y registros.
* Instrucciones de salto para romper fuera de la secuencia del programa actual.
* Instrucciones de entrada/salida.
* Instrucciones de parada.

Una **memoria RAM** tiene una palabra de salida (out wrd) y tres palabras de entrada (dirección (addr), palabra de datos (en wrd) y comando (cmd))

El comando especifica una de las tres acciones:
* Leer desde una ubicación de memoria.
* Escribir desde una ubicación de memoria.
* No hace nada