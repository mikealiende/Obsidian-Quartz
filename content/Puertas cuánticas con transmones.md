# Puertas cuánticas con transmones

Para que nuestro sistema pueda ser considerado un computador, necesitamos un conjunto de [[Puertas cuánticas]] que nos permitan cubrir toda la esfera de Bloch y la interacción entre qubits.

El esquema utilizado en la manipulación es similar a la modulación de las ondas de radio. Una portadora, en este caso, a al frecuencia característica del qubit, es modulada por otra señal más lenta que divide sus componentes en fase $(I)$ y cuadratura $(Q)$ , es decir, retrasada $\pi / 2$.

### Rotación $X$ y $Y$

En el caso de los [[transmón]], para un pulso de duración dada en la componente $I$, produce una rotación en el eje $X$. La misma relación se da entre el eje $Y$ y la componente $Q$. De esta manera podemos aplicar una rotación de un ángulo $\theta$ al estado de los qubits en los ejes $X$ e $Y$ con un único pulso de manera simultánea.

### Rotación $Z$

Imaginemos que aplicamos un pulso, cuyas componentes $I$ y $Q$ actuan sobre un qubit aplicando la rotación $X_{\theta}Y_{\phi}$. Si retrasamos la fase en $\pi / 2$, $I$ pasaría  ser $Q$ y $Q$ pasaría a ser $-I$, lo que se traduce en la rotación $X_{\phi}Y_{-\theta}$, lo que es equivalente a una rotación $\pi$ en el eje $Z$, es decir $Z_{\pi}$.

Para hacer una rotación $\phi$ en torno al eje $Z$, basta con aplicar dos veces la misma rotación en torno a $X$ e $Y$ con un desfase $\phi$ entre los pulsos. Creamos así la puerta virtual Z que nos permite efectuar la operación $Z_{\phi]}$.

De esta manera tenemos ya definidas todas las rotaciones posibles de la esfera de Bloch. 

### Puerta CR o resonancia cruzada.

Se trata una puerta de dos qubits, a través de transmones. Para fabricar una puerta CR entre dos qubits 1 y 2, con frecuencias de resonancia $w_{q_{1}}$ y $w_{q_{2}}$, se le conecta capacitivamente mediante guías de ondas a un [[circuito LC]] resonador, que hará de intermediario entre los qubits.

Si excitamos el qubit 1 a la frecuencia de resonancia de l qubit 2, el acoplo entre ambos a través del resonador hará que el segundo qubit reciba una señal que dependa del estado del primero.  La matriz del operador CR es:

$$ U_{CR_{\phi}}= \begin{bmatrix}
\cos\left( \frac{\phi}{2} \right) & -i \cdot \sin\left( \frac{\phi}{2} \right) & 0 & 0  \\
-i \cdot \sin\left( \frac{\phi}{2} \right) & \cos\left( \frac{\phi}{2} \right)& 0 & 0  \\
 0 & 0 & \cos\left( \frac{\phi}{2} \right) & i \cdot \sin\left( \frac{\phi}{2} \right) \\
 0 & 0 & i \cdot \sin\left( \frac{\phi}{2} \right) & \cos\left( \frac{\phi}{2} \right)
\end{bmatrix}$$
Donde $[\phi]$ viene determinado por las características de duración y amplitud del pulso de frecuencia $\omega_{q2}$ aplicado al qubit 1.

![[Pasted image 20240517165729.png | 300]]

### Puerta CNOT

La puerta CR se puede combinar con los operadores de rotación de un solo qubit para crear la puerta CNOT:

![[Pasted image 20240517165853.png|400]]

