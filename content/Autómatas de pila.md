# Autómatas de pila

Los autómatas de pila reciben una cadena constituida por símbolos de un alfabeto, y determinan si esa cadena pertenece al lenguaje que el autómata reconoce.

Además de una cinta de entrada y un control de estados como una autómata de estados finitos, cuenta con una pila (stack) como memoria adicional. Esto le permite almacenar y recuperar información.

Para describir con una séptupla $M=(S,\Sigma, \Gamma, \delta,s,Z,F)$, donde:

* $S$: Conjunto finito de estados
* $\Gamma$ y $\Sigma$: Son alfabetos. Símbolos de la pila y símbolos de entrada respectivamente.
* $\delta: S\times(\Sigma \cup\{\epsilon\})\times  \Gamma\rightarrow P(S\times \Gamma *)$ 
* $s \in S$: Estado inicial
* $Z \in \Gamma$: Estado inicial de la pila
* $F \subseteq S$: Conjunto de estados finales

**Las transiciones** pueden describirse de la siguiente manera:

1. El autómata de pila comienza en su estado inicial, apuntando al primer símbolo de la cinta y la pila inicialmente vacía. 
2. El autómata lee el símbolo actual de la cinta.
3. Transición. En base al estado actual, el símbolo leído y el símbolo en la cima de la pila. El autómata:
	* Cambia a un nuevo estado
	* Mueve el cabezal de lectura a la siguiente posición de la cinta
	* Realiza una operación en la pila:
		* Apilar (push): Introduce un nuevo símbolo en la cima de la pila.
		* Desapilar(pop): Extrae el símbolo de la cima de la cima de la pila.
		* Nada
4. Repetición de los pasos 2 y 3
5. Aceptación o rechazo. El autómata acepta la cadena de entrada si termina un estado de aceptación y si no, la rechaza.


![[Pasted image 20241215181436.png|500]]
