# Puertas lógicas y circuitos lógicos

Una **puerta lógica** es un modelo que implementa una función booleana, es decir, una operación lógica realizada en una o más entradas binarias que produce una única salida binaria.

Un **circuito lógico** es un modelo de computación compuesto por una secuencia de puertas lógicas, cada una de ellas computando una función y siendo el resultado del circuito una o varias salidas binarias. Su tamaño y profundidad proporcionan unos límites inferiores de los recursos necesarios para realizar una tarea computacional. Esta es la idea central para el uso de circuitos lógicos para la clasificación de los problemas por su complejidad computacional. 


**Ejemplo de circuito lógico para sumar dos bits**

A partir del concepto de suma binaria podemos construir la siguiente tabla

| A   | B   | SUMA | ACARREO |
| --- | --- | ---- | ------- |
| 0   | 0   | 0    | 0       |
| 0   | 1   | 1    | 0       |
| 1   | 0   | 1    | 0       |
| 1   | 1   | 1    | 1       |


dibujando como un diagrama de bloques tenemos:

![[Pasted image 20241216194550.png|400]]

Y en si lo construimos con puertas lógicas, el circuito que sumas dos bits sería:

![[Pasted image 20241216194640.png|300]]
