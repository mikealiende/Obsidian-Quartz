# Postulados de la mecánica cuántica #Tema 

## Indice
### [[Principio de incertidumbre]]
### [[Ecuación de Shrödinger]]
### [[Interpretaciones de la mecánica cuántica]]

### [[Paradoja EPR]]


## Postulados

#### Postulado 1. Estado cuántico

El estado de un sistema físico cerrado S se describe totalmente mediante un vector unitario |ψ⟩, que denominamos vector de estado o función de onda. Este vector forma parte de un espacio de Hilbert separable HS asociado al sistema.

A cada sistema físico descrito en el marco de la Mecánica Cuántica le corresponde un espacio de Hilbert complejo y separable. Por tanto, cada sistema cuántico lleva aso- ciado un Espacio de Hilbert en el que se definen todos los posibles estados que puede adoptar dicho sistema. La forma en la que se definen los estados del sistema en el Espacio de Hilbert es mediante un vector complejo, es decir, cada vector complejo del Espacio de Hilbert es posible estado del sistema al que está asociado.

En el campo de la computación cuántica, el sistema cuántico con el que se trata es el denominado qubit (quantum bit), y por tanto, el espacio de Hilbert asociado es de dos dimensiones. Esto significa que el espacio de Hilbert está formado por dos vectores base y que cualquier estado se puede representar como una combinación lineal de estos dos vectores base. Si los vectores base se representan mediante |v1⟩ y |v2⟩, entonces, cualquier estado general |ψ⟩ del sistema se puede representar como:
![[Pasted image 20240217185523.png]]

#### Postulado 2. [[Observables]]

Cualquier variable dinámica del sistema que es susceptible de ser medida, se denomina observable, y se representa mediante un operador, por ejemplo O. Si en un sistema descrito por el vector de estado |ψ⟩ se realiza una medida del observable O y se obtiene el resultado an, entonces, después de la medida, el estado del sistema viene dado por:
![[Pasted image 20240217185617.png]]
donde Pn es el operador proyección sobre el subespacio correspondiente a an.


El valor medio de una variable dinámica O (que puede representar un observable) en
el conjunto de estados igualmente preparados representados por el operador ρ es:
![[Pasted image 20240217185709.png]]
Cuando se realiza la medida del observable, el sistema (según la interpretación de Copenhagen) se proyecta sobre uno de los autoestados posibles y proporciona el autovalor asociado a ese autoestado.

En Mecánica Cuántica, el valor de un observable es incierto, se cree que un estado se encuentra en un estado de superposición coherente de todos los autoestados posibles del observable.

#### Postulado 3. Evolución

Cada observable A tiene asociado un operador auto-adjunto A en el espacio de Hilbert HS, y el único valor posible que se puede obtener al realizar una medida del observable A es alguno de los autovalores del operador A.

La evolución de un sistema cuántico cerrado viene descrita por una transformación unitaria. Esto quiere decir que, el estado |ψ⟩ del sistema en el instante t1 está relacio- nado con el estado |ψ′⟩ del sistema en el instante t2 mediante un operador U que solo depende de los instantes t1 y t2.

Un estado del espacio de Hilbert se representa por un operador ρ, también llamado [[operador densidad]], no negativo, autoadjunto y de traza unidad. Los observables también serán operadores autoadjuntos, y sus autovalores serán los posibles valores de las magnitudes físicas.

La [[Ecuación de Shrödinger]] es una ecuación diferencial que proporciona una descripción de un sistema cuántico aislado y da cuenta de su evolución temporal.

#### Postulado 4. Medidas

Si un operador 𝐴 asociado a un observable físico 𝔸 tiene una base propia 𝛼 y valores propios {ai } y el estado del sistema es Ψ 𝑥 antes de realizar una medida.

Solo podemos predecir la probabilidad de que el valor de la medida de 𝐴 sea el valor propio ak

![[Pasted image 20240217190630.png]]

#### Tema 5. Descomposición espectral
![[Pasted image 20240217190806.png]]
