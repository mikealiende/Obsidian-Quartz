# QAOA Quantum Aproximation Optimization Algorithm #Tema 

Con este algoritmo vamos a poder calcular la máxima energía de un Hamiltoniano tipo Ising. Utilizaremos la exponencial del Hamiltoniano debido a su relación con la evolución temporal en mecánica cuántica.

## Idea intuitiva

Partiremos del Hamiltoniano del [[Modelo Ising]]. Para este ejemplo utilizaremos:

$$H = 
\begin{pmatrix}
  1 & 0 & 0 & 0 \\
  0 & 3 & 0 & 0 \\
  0 & 0 & 4 & 0 \\ 
  0 & 0 & 0 & 0
\end{pmatrix}
$$
El objetivo de este algoritmos es encontrar el auto estado que maximiza la energía, en nuestro ejemplo concreto es fácil ver que es $\ket{10}$ con valor del Hamiltoniano 4. 

==No podemos mapear este Hamiltoniano en puertas cuánticas porque no es una matriz unitaria,== por lo tanto necesitamos introducir $e^{iH}$, que como H es una matriz diagonal tenemos:

$$e^{iH} = 
\begin{pmatrix}
  e^{i} & 0 & 0 & 0 \\
  0 & e^{i3} & 0 & 0 \\
  0 & 0 & e^{i4} & 0 \\ 
  0 & 0 & 0 & 1
\end{pmatrix}
$$
**De esta manera nuestro objetivo pasar de encontrar el mayor módulo a encontrar la mayor fase.**

Para seguir con el algoritmo tenemos que definir las [[puertas de rotación QAOA]] que son  $U(C,\gamma)$ y $U(B,\beta)$. 

1. Una vez tenemos definido nuestra función objetivo en forma de Hamiltoniano tipo Ising lo que hacemos es inicializar todos los estados con en un estado de [[superposición cuántica]] equiprobable, mediante puertas Hadamard [[Puertas cuánticas#Puerta Hadamard (H)]]. Si los representamos en una esfera, todos ellos apuntan en la misma dirección: 
	![[Pasted image 20240512115137.png|200]]



2. Primero aplicamos la puerta $U(C,\gamma)$, que es equivalente a calcular la exponencial de Hamiltoniano que hemos definido como función objetivo. Lo que hace es rotar en el eje Z los estados en función de su fase. Los estados con mayor fase más se alejarán del origen. Esta puerta no cambia las probabilidades de cada estado, sólo la fase.
	 ![[Pasted image 20240512115431.png|200]]
	

3. Por último, vamos aplicar al puerta $U(B,\beta)$, que lo que va a hacer es rotar la esfera, que después de haber aplicado la puerta $U(C,\gamma)$ lo que va a pasar es que aquellos estados más  separados del origen van a ser más probables, aplicar esta puerta sacrifica un poco de fase.
	![[Pasted image 20240512115836.png|200]]

4. Repitiendo la aplicación de estas puertas consecutivamente conseguiremos mejorar las probabilidades de los estados con mayor energía.
	![[Pasted image 20240512120015.png]]

5. Una manera de mejorar los resultados es eligiendo los valores más óptimos para $\gamma$ y $\beta$, para ello podemos utilizar algoritmos de optimización clásicos.


## Resolución genérica

La ventaja de este algoritmo es que podemos usar [[Modelo Ising#Descomponer exponencial de Hamiltoniano tipo Ising como puertas de Pauli]] para cualquier Hamiltoniano tipo Ising, e incluso [[Adaptación exponencial de Hamiltoniano genérico QAOA y EVA]] para generalizarlo a cualquier tipo de Hamiltoniano. 

## Relación con Quantum Annealing

Este algoritmo puede considerarse el equivalente del [[Quantum Annealing]] pero en computación de puertas. Este algoritmo lo que hacia era dejar evolucionar los estados influenciados por el Hamiltoniano del sistema e intentar encontrar atajos mediante el efecto túnel. 

Al hablar de dejar evolucionar el Hamiltoniano hablamos de la  [[Ecuación de Shrödinger]]:

$$i\hbar \frac{\partial \ket{\phi(t)} }{\partial t} = H \ket{\sigma(t)} $$
Resolviendo esta ecuación obtenemos como varia H a lo largo del tiempo. Lo que indicamos en QAOA con el parámetro $\gamma$ podría considerarse como el tiempo, y para simular estos saltos que pueden dar los estados podemos considerar $U(B,\beta)$ como una perturbación, donde $\beta$ sería la intensidad de esta perturbación. Por lo tanto podemos decir que estamos haciendo lo mismo que QA pero de una manera artificial. 

## Resolución de problemas con QAOA

Ejemplo de como resolver con PennyLane el problema [[minimum  vertex cover con QAOA]]