# Complejidad en función del tamaño de las entradas

Para decir que un algoritmo funciona mejor que otro, necesitamos cuantificar los recursos necesarios para computar.

* Tiempo
* Memoria (Espacio)
* Entradas/salidas
* Otros: circuitos, energía, etc...

El tiempo no puede ser simplemente ciclos de reloj de CPU. Para poder estudiar los algoritmos necesitamos contar con una referencia objetiva. Podemos definir el tiempo como ==*"Número de operaciones como función del tamaño de la entrada de un algoritmo"*==. Tenemos que caracterizar caracterizar el tamaño de entrada que llamaremos $n$. En función de la naturaleza del algoritmo, $n$ será:

| Tipo de algortimo | Tamaño de entrada                                    |
| ----------------- | ---------------------------------------------------- |
| Clasificación     | Número de elementos a clasificar                     |
| Grafos            | Número de vertices y aristas                         |
| Numéricos         | Número de bits necesarios para representar un número |
## Ordenes de crecimiento

Es interesante conocer el rendimiento de un algoritmo cuando el tamaño de entrada tiende a infinito. Ya que para entradas pequeñas la mayoría de algoritmos funcionan bien.

## Intratabilidad 

Los problema que solo podemos resolver con algoritmos de tiempo exponencial o superexponencial se consideran **intratables**. Significa que para tamaños de entrada grandes no pueden ejecutarse de manera eficiente, necesitan millones de años. Para resolver este tipo de problemas podemos optar por algoritmos de aproximación o randomización.

Por otro lado, los algoritmos tratables son aquellos que podemos resolver de forma eficiente, es decir, algoritmos con tiempo de ejecución polinomial. 

