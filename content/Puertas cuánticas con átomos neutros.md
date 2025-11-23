# Puertas cuánticas con átomos neutros

### Puertas de un sólo qubit

Para producir rotaciones en los qubits de átomos neutros, se utilizan las [[Oscilaciones de Rabi]] típicas de un sistema de dos niveles. De esta manera, al iluminar un átomo estaremos pasando periódicamente entre el estado fundamental y el excitado, efectuando una rotación en la esfera de Bloch en un tiempo finito.

Si controlamos el desajuste, la duración y la fase de láser, podemos situar al qubits en el cualquier punto de la esfera de Bloch, implementando las rotaciones en $X$, $Y$ y $Z$. 

Las características del láser se pueden controlar con esta dos técnicas:

* Los moduladores **acusto-ópticos**: Son cristales piezoeléctricos, sus propiedades mecánicas pueden ser moduladas mediante un campo eléctrico, por lo cuales se hace pasar el haz de luz. Al aplicar un campo eléctrico variable a ambos extremos del piezoeléctrico se produce una vibración acústica del cristal, lo que provoca la difracción del haz en distintas direcciones. Con el uso de uno de estos haces difractados es posible modular la amplitud de la luz con gran precisión.
* Los moduladores **electro-ópticos** actúan de manera similar, pero, en lugar de cristales se utilizan materiales con distintas propiedades eletro-ópticas, como cristales birrefringentes, en los que la relación de los indices de refracción de los ejes rápido y lento puede ser modulada con un campo eléctrico.

Al controlar este tipo de moduladores con un generador digital de señales, podemos diseñar pulsos de luz a medida para realizar todas las rotaciones posibles sobre la esfera de Bloch.

![[Pasted image 20240521182144.png ]]

En la figura podemos ver oscilaciones de Rabi de frecuencia $\Omega$ entre los estados $\ket{0}$ y $\ket{1}$. Si añadimos el desajuste $\Delta$ a la frecuencia de excitación, podemos modular la respuesta para una pulsación de pulso fija.

Por lo tanto con tenemos los siguientes parámetros:
* Duración de los pulsos del láser: $\tau$
* Desajuste de la frecuencia del láser con respecto a la frecuencia de excitación: $\Delta$
* Fase: $\phi$
* Frecuencia de Rabi: $\Omega$

Podemos realizar las siguientes rotaciones respecto a la esfera de Bloch:
$$(x,y,z) \rightarrow (\Omega \tau \cos(\phi)),(\Omega \tau \cos(\phi),\Delta \tau)$$
### Puertas de dos Qubits

Para realizar puertas de dos qubits, vamos tomar dos átomos, uno control y otro objetivo y vamos a utilizar un tercer estado de Rydberg auxiliar $\ket{r}$ para realizar las operaciones, partiendo de $\ket{0}$ en ambos qubits, la secuencia es:

![[Pasted image 20240521190811.png]]

1. Pulso 1 $\rightarrow$ Pasa de $\ket{0}$ al estado de Rydberg $\ket{r}$, lo que provoca una rotación de $\pi$ en el qubit de control.
2. Pulso 2 $\rightarrow$ Pasa del estado $\ket{0}$ a $\ket{r}$ y vuelve a $\ket{0}$, lo que provoca una rotación de $2\pi$ en el qubit objetivo.
3. Pulso 3 $\rightarrow$ Pasa del estado $\ket{r}$ a $\ket{0}$. Añadiendo una rotación $\pi$ al qubit de control, sumando una rotación total de $2\pi$.

Para construir estas puertas cuánticas nos vamos a aprovechar de la propiedad de [[Bloqueo de Rydberg]]. En el siguiente ejemplo vamos a ver como podemos construir la [[Puerta CZ átomos neutros]] aprovechado este mecanismo. 

Como hemos ya tenemos la puerta CZ, vamos a construir la CNOT añadiendo una puerta Hadamard antes y después del de aplicar la rotación Z en el qubit objetivo, de esta manera:

![[Pasted image 20240522182846.png|380]]

Con la posibilidad de efectuar todas las rotaciones posibles sobre qubits individuales y puertas de dos qubits con entrelazamiento tenemos un conjunto de puertas universales.

