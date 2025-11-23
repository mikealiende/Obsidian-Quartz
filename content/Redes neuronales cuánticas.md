# Redes neuronales cuánticas
#Tema 

* ### [[Introducción redes neuronales clásicas]]


Tras definir la [[Derivación en circuitos cuánticos]], podemos generalizar el concepto de redes neuronales en la computación cuántica. Nos vamos a centrar en el reemplazo de neuronas clásicas por neuronas cuánticas.

![[Pasted image 20240621190810.png|400]]

A diferencia de la neurona clásica, aquí no existe definición estándar a la hora de crear una función que trabaje con las ponderaciones. En este caso, en vez de añadir una función de activación arcotangencial, usamos el valor esperado sobre uno de los qubits. 

Podemos construir una red neuronal híbrida, por ejemplo siendo la última neurona una cuántica. La idea es que las neuronas clásicas, interpolan a la función objetivo a través de funciones polinómicas, y las neuronas cuánticas, a través de funciones trigonométricas.

### Inconvenientes

Existen varios inconvenientes de las redes neuronales, el primero que pueden ser vistas como cajas negras, y no sabemos porque se han tomado ciertas decisiones. 

Otro problema es que las funciones tiene muchos mínimos locales, por lo tanto usando el descensor de gradiente, es fácil que caigamos en un mínimo local y no en el global.

Uno de los mayores inconvenientes actuales es el [[Barren Plateaus]].