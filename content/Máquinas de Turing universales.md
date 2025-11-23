# Máquinas de Turing universales

Una máquina de Turing universal puede computar lo que cualquier máquina de Turing específica computa. Cualquier problema que no sea computable por la máquina de Turing universal se considera incomputable. 

El problema principal de la máquina de Turing es que se debe construir una máquina para cada computación que se realice. Son máquina de propósito específico. Para salvar esta limitación están las máquinas de Turing universales.

La máquina de Turing universal, junto a la entrada en la cinta toma la descripción de una máquina $M$. Eso permite a la máquina de Turing universal simular $M$.

![[Pasted image 20250111132624.png|300]]

Son máquinas abstractas capaces de ejecutar todos los algoritmos posibles. 

## Relación con la computación cuántica.

Una máquina de Turing cuántica contaría con: 

* **Un procesador finito**: Unidad de control, misma funcionalidad que en el modelo clásico. Tiene $P$ qubits.
* Memoria infinita: Misma función que la cinta en el modelo clásico.
* Cursor: Componente que interactua sobre el procesador y la unidad de memoria. Su posición es escaneada por una variable compleja $x$ tal que:$$x \in \mathbb{H}_{c}$$
Donde $\mathbb{H}_{c}$ es el espacio de Hilbert asociado.

No está claro para que pueden servir las máquinas de Turing cuánticas.