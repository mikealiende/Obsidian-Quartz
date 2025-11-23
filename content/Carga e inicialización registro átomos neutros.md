# Carga e inicialización registro átomos neutros

Una vez tenemos la [[Trampas de átomos]], debemos cargarla con átomo neutros e inicializarlos para poder operar con ellos como qubits. Para ello, se hace pasar un gas por la trampa y parte de sus átomos serán atrapados en el potencial óptico.

Al observar la fluorescencia de los átomos es posible saber que partes de la trampa se han ocupado con átomos y cuales han quedado vacías.

Mediante esta técnica, la probabilidad de que un punto de la trampa esté ocupada por un átomo es del 50% aprox. Por esto, es necesario definir un subconjunto de punto como el registro cuántico que vamos a utilizar. Para esto, cambiamos parámetros de la trampa así podemos desplazar los átomos a esta zona de interés:

![[Pasted image 20240520175154.png | 550]]


### Sistema a dos niveles
Los átomos así cargados estarán en su estado fundamental o decaerán rápidamente a este. Para las operaciones cuánticas podemos utilizar:

* Dos estados electrónicos del átomo $\rightarrow$ Accedemos a ellos mediante transiciones ópticas.
* Estados del espín de la estructura hiperfina $\rightarrow$ Accedemos a ellos mediante pulsos de microondas.
### Reutilización de los registros

En los ordenadores de átomos atrapados, a diferencia de otras tecnologías, los registros no pueden ser reutilizados, **cada vez que se inicializa un registro se carga con átomos nuevos.**

La ventaja de esto es que podemos realizar el mismo algoritmo en la misma trampa varias veces, pero cada vez con átomos nuevos. Lo que permite garantizar la ausencia de ciertos errores relacionados con la implementación física del qubit.

### Átomos de Rydberg

En muchos ordenadores cuánticos se utilizan [[átomos de Rydberg]]. Debido a su momento dipolar relativamente grande, su respuesta a campos eléctricos y magnéticos es exagerada. Lo que facilita su integración en las trampas ópticas.