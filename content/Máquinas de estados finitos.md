# Máquinas de estados finitos


Un máquina de estados finitos opera sobre una entrada para producir una salida. Este modelo se puede representar como una quíntupla $M=(Q, \Sigma,q{0},\delta,F)$, esta conformado por:

* Alfabeto: $\Sigma$
* Conjunto de estados finito: $Q$. Se representan como vértices
* Función de transición: $\delta:Q\times\Sigma \rightarrow Q$. Es una transición de un estado a otro en función del valor del símbolo. Se representa como una arista que une los vértices. 
* Estado inicial: $q{0}$
* Conjunto de estados finales: $F \in Q$. Se representan mediante vértices que están encerrados por otra circunferencia. 

La función de transición recibe, a partir de un estado inicial, una cadena de caracteres perteneciente al alfabeto (entrada), y va leyendo dicha cadena a medida que la máquina se desplaza de un estado a otro. Finalmente se detiene un estado final que representa la salida. Se representan usando **Diagramas de estados:**
![[Pasted image 20241215173050.png|300]]


## Tablas de transiciones

También se pueden representar con tablas de transiciones o matrices de estados. Una posible tabla de transición para el ejemplo de arriba sería


| Salida  | Simbolo | Llegada |
| ------- | ------- | ------- |
| $S_{1}$ | 0       | $S_{2}$ |
| $S_{1}$ | 1       | $S_{1}$ |
| $S_{2}$ | 0       | $S_{1}$ |
| $S_{2}$ | 1       | $S_{2}$ |

