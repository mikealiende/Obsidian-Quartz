# Autómatas celulares

Modelo de computación discreto. 

Esta compuesto por una cuadricula regular de celdas, cada una de ellas en un estado "on" o "off". Los estados son finitos. Para cada celda se define un conjunto de celdas, llamado vecindario, en relación con la celda especificada. 


![[Pasted image 20241216192947.png|300]]

La evolución del autómata celular es:

* Un estado inicial (tiempo t = 0) se selecciona asignando un estado para cada celda.
* Se crea una nueva generación (t=1) de acuerdo con una regla fija (función matemática), que determina el nuevo estado de la celda en términos del estado actual de la celda y los estados de las celdas de su vecindario.

**Evolución de un autómata celular con diferentes reglas**

![[Pasted image 20241216193309.png|500]]


### Clasificación de autómatas celulares


* Clase 1: casi todos los patrones iniciales evolucionan rápidamente a un estado estable y homogéneo.

* Clase 2: casi todos los patrones iniciales evolucionan rápidamente a estructuras estables o periódicas.

* Clase 3: casi todos los patrones iniciales evolucionan de manera pseudoaleatoria o caótica. Cualquier estructura estable que aparezca es rápidamente destruida por el ruido circundante.

*  Clase 4: casi todos los patrones iniciales evolucionan hacia estructuras que interactúan de manera compleja. Se ha sugerido que los autómatas celulares de clase 4 pueden constituir un modelo de computación universal


Tienen multitud de aplicaciones en campos como la simulación de sistemas biológicos, químicos, etc...