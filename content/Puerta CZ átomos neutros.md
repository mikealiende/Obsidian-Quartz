# Puerta CZ átomos neutros

Vamos a ver como utilizando el [[Bloqueo de Rydberg]] conseguimos hacer la puerta CZ con dos qubits de átomos neutros. Para ellos vamos a usar la secuencia de pulsos de [[Puertas cuánticas con átomos neutros#Puertas de dos Qubits]]. Y diferenciaremos estos casos:

## Estado de origen: $\ket{\Psi_{0}} = \ket{0_{c}0_{o}}$

![[Pasted image 20240521193711.png|200]]

1. El primer pulso manda al qubit de control al estado $\ket{r}$ introduciendo en este una rotación de $\pi$ y creando un bloqueo de Rydberg en el qubit objetivo.
2. El segundo pulso en el qubit objetivo no no provoca ningún cambio debido a el bloqueo de Rydberg provocado por la excitación del qubit de control.
3. El tercer pulso hacer decaer al átomo del estado de $\ket{r}$ al estado $\ket{0}$ añadiéndole una rotación de $\pi$. Que junto con el primer pulso se traduce en desfase global de $2\pi$ en el qubit de control.
4. Resultado:
$$\ket{\Psi_{0}} = \ket{0_{c}0_{o}}\rightarrow \ket{\Psi} = e^{i\pi}\ket{0_{c}0_{o}}$$
##  Estado de origen: $\ket{\Psi_{0}} = \ket{0_{c}1_{o}}$

![[Pasted image 20240521232426.png|200]]

Realmente es la misma situación que el caso anterior, aunque esta vez el bloqueo de Rydberg da igual, debido a que el como el qubit objetivo parte del estado $\ket{1}$ nunca va llegar al estado $\ket{r}$ por medio del pulso 2. Resultado:
$$\ket{\Psi_{0}} = \ket{0_{c}1_{o}}\rightarrow \ket{\Psi} = e^{i\pi}\ket{0_{c}1_{o}}$$
##  Estado de origen: $\ket{\Psi_{0}} = \ket{1_{c}0_{o}}$

![[Pasted image 20240521232745.png|200]]

1. El primer pulso no consigue excitar el qubit de control debido a que este parte del estado $\ket{1}$, por lo tanto al no estar en el estado de Rydberg no provoca el bloqueo del qubit objetivo.
2. El pulso 2 esta vez es capaz de excitar el qubit objetivo al $\ket{r}$ y volverlo a $\ket{0}$ provocando una rotación de $2\pi$ en la fase.
3. Igual que en el paso 1, el tercer pulso no es capaz de excitar el qubit de control y permanece en $\ket{1}$
4. Resultado:
$$\ket{\Psi_{0}} = \ket{1_{c}0_{o}}\rightarrow \ket{\Psi} = e^{i\pi}\ket{1_{c}0_{o}}$$
##  Estado de origen: $\ket{\Psi_{0}} = \ket{1_{c}1_{o}}$
![[Pasted image 20240521233339.png|200]]

En este caso ninguno de los tres pulso es capaz de excitar ningún átomo a $\ket{r}$, debido a que ambos parten de $\ket{1}$. Por lo tanto en este caso el estado de ambos qubits permanece inalterado. Resultado:
$$\ket{\Psi_{0}} = \ket{1_{c}1_{o}}\rightarrow \ket{\Psi} = e^{i\pi}\ket{1_{c}1_{o}}$$

La matriz del operador generado por la secuencia de pulsos descrita es:
$$\begin{bmatrix}
-1 & 0 & 0 & 0\\
 0 &-1 & 0 & 0 \\
0 &0 & -1 & 0 \\
0 &0 & 0 & 1
\end{bmatrix} = e^{i\pi}\begin{bmatrix}
1 & 0 & 0 & 0\\
 0 &1 & 0 & 0 \\
0 &0 & 1 & 0 \\
0 &0 & 0 & -1
\end{bmatrix} =e^{i\pi}CZ$$
Que corresponde con la transformación CZ en un factor de fase $\pi$.

![[Pasted image 20240522182455.png| 80]]


