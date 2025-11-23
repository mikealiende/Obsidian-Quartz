#   Phase Kickback

Phase Kickback o rebote de fase, hace referencia al fenómeno por el cual las operaciones controladas, como CNOT, tienen efecto en sus qubits de control además de en los qubits objetivo.Parte de la información fase del qubit objetivo se transfiere al qubit de control y se almacena en la fase relativa. En puertas controladas, la fase del qubit objetivo esta condicionada por el estado del qubit de control, debido al entrelazamiento la fase "rebota" del qubit de objetivo al de control . Esta característica  es una ventaja de la computación cuántica y se utiliza en algoritmos como: [[Algoritmo de Deutsch]], [[Quantum Phase Estimation]], [[Transformada cuántica de Fourier QFT]](completar con más algoritmos)

Vamos a ver un ejemplo de entrelazamiento en el que no se produce phase kickback y otro en el que si.




## Entrelazamiento con Phase Kickback

### Requisitos Phase kickback

Para que se de el fenómeno de Phase kickback, se deben cumplir una serie de requisitos:

1. **Los qubits de control deben estar en superposición**. Si no es así, el "rebote" de fase afectará a la fase global que no tiene significado físico.
2. **El estado $\ket{\psi}$ del qubit objetivo, debe ser un autovector del operador controlado $U$**. Ya que de esta manera se cumple $U\ket{\psi} = e^{i\phi}\ket{\psi}$, y entonces $e^{i\phi}$ se transfiere al qubit de control.
3. **El operador $U$ se debe aplicar de forma controlada**

### Ejemplo Phase Kickback Operador general U

Vamos a considerar un sistema de 2 qubits: $\ket{c}$ el qubit de control y $\ket{t}$ el qubit objetivo. Y vamos a tener el operador unitario $U$. Si aplicamos este operador a nuestro circuito de manera controlada tenemos:
$$C\text{-}U\ket{c}\ket{ t} = \begin{cases} \ket{0}\ket{t} \text{ si } c=0 \\ \\
\ket{1}U\ket{t} \text{ si } c =1    
\end{cases}  $$
Como hemos dicho antes, para que se produzca phase kickback, el estado $\ket{t}$ debe ser un autovector del operador $U$ con el autovalor asociado $e^{i\phi}$. Es decir:$$U\ket{t} = e^{i\phi}\ket{ t}  $$
Si se cumplen estas condiciones tenemos: $$C\text{-}U\ket{c}\ket{t} = e^{i\phi c}\ket{c}\ket{t}    $$

Otra de las condiciones es que los qubits de control estén en superposición, lo que conseguimos aplicando una puerta H y mandando a $\ket{c}$ al estado $\ket{+} = \frac{1}{\sqrt{ 2 }}\ket{0}+\ket{1}$. Con esto el estado que tendríamos es:$$C\text{-}U\ket{+}\ket{t} = \frac{1}{\sqrt{ 2 }}(\ket{0}\ket{t} +e^{i\phi }\ket{1}\ket{t}   )  $$
Si factorizamos $\ket{t}$ nos queda:$$C\text{-}U\ket{+}\ket{t} = \frac{1}{\sqrt{ 2 }}(\ket{0} +e^{i\phi }\ket{1})\otimes \ket{t} = \ket{+\phi}\otimes \ket{t}$$
Siendo $\ket{+\phi}= \frac{1}{\sqrt{ 2 }}(\ket{0}+e^{i\phi}\ket{1})$, vemos claramente que la fase $e^{i\phi}$ ha "rebotado" del qubit objetivo al qubit de control. El circuito que hemos descrito sería:

![[Pasted image 20250126120739.png|400]]



### Ejemplo con C-NOT

Si colocamos también el qubit objetivo en superposición, la puerta CNOT actuaria ahora sobre $\ket{++}$ (superposición uniforme de los 4 estados estados de la base), esto no produciría ningún cambio, pero si aplicamos la CNOT al estado $\ket{+ - }$ el resultado es $\ket{--}$. Es un resultado muy interesante, dado que el qubit objetivo permanece sin cambios, pero en cambio el qubit de control tiene ahora fase negativa. De alguna manera se ha transferido la fase del qubit objetivo al qubit de control. Demostración matemática:

![[Pasted image 20250119123258.png]]

1. Partimos del estado $\ket{00}$

2. Aplicamos X al segundo qubit $I\otimes X\ket{00}\rightarrow \ket{01}$


3. Aplicamos H a ambos qubits:$$\begin{align}
&\left[ \frac{1}{\sqrt{ 2 }}(\ket{0}+\ket{1}  ) \right]\left[ \frac{1}{\sqrt{ 2 }}(\ket{0}-\ket{1}  ) \right]= \\ \\
=&\frac{1}{2}(\ket{00}-\ket{01} +\ket{10}-\ket{11}   )= \ket{+ -} 
\end{align}$$
4. Aplicamos la puerta CNOT:$$\begin{align}
&\frac{1}{2}(\ket{00}-\ket{01} +\ket{11}-\ket{10}   )+ \\ \\
&\frac{1}{2} ([\ket{0}(\ket{0}-\ket{1}) + \ket{1}(\ket{1}-\ket{0} ))= \\ \\
&\frac{1}{2} (\ket{0}\ket{-}-\ket{1}\ket{-}) = \ket{-}\ket{-} = \ket{--}   
\end{align}$$


Un aspecto clave para la aplicación es que el estado en el que se encuentra el qubit objetivo debe ser un autovector de la puerta correspondiente de la operación de control. Lo que se pretende con ello es que la aplicación de la aplicación al qubit objetivo no cambie su estado, si no que añada una fase a su estado.

Por lo tanto, aplicar el operador $U$ al qubit objetivo supondría: $U\ket{\psi} = e^{i\phi}\ket{\psi}$. Este valor $e^{i\phi}$ que multiplica al estado es el que será propagado al qubit de control.

### Entrelazamiento sin Phase Kickback


![[Pasted image 20250119122348.png]]

En este caso no se va a producir Phase kickback porque el estado del qubit objetivo no es un autovector de C-NOT 

1. Empezamos en el estado $\ket{00}$

2. Aplicamos H al primer qubit $\rightarrow \frac{1}{\sqrt{ 2 }}(\ket{0}+\ket{1})\ket{0}=\frac{1}{\sqrt{ 2}}\ket{00}+\ket{10}$

3. Aplicamos puerta CNOT $\rightarrow \frac{1}{\sqrt{ 2}}\ket{00}+\ket{11}$