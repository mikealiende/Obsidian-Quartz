# Demostración geométrica algoritmo de Grover

Aunque la representación de los estados del problema se hace en un hiperplano (Espacio de Hilbert de dimensión $N$). Lo podemos transfirmar en un plano $2D$ generado por los 2 estados que nos interesan: 
$$\begin{equation}
\begin{cases}
\ket{w} \to \text{Estado objetivo} \\
\ket{s} \to \text{Estado de superposición uniforme}  
\end{cases}
\end{equation}$$

Puesto que $\ket{w} \in \ket{s}$ no van a ser ortogonales, por lo que vamos a considerar el estado $\ket{s'}$ que si es es ortogonal a $\ket{w}$, es decir, $\braket{w|s'}=0$.

El estado $\ket{s'}$ no es otra cosa que eliminar el estado objetivo $\ket{w}$ de la superposición $\ket{s}$. Con esto 3 elementos vamos a representar $\ket{s}$ en el plano ortonormal que forman $\ket{w}$ y $\ket{s'}$:

![[Pasted image 20250217195335.png|300]]

Siendo $\ket{s} = \sin \theta \ket{w}+\cos \theta \ket{s'}$, siendo $\sin \theta=\frac{1}{\sqrt{ N }}$.


Aplicando el oráculo $U_{w}= I-2\ket{w}\bra{w}$ como hemos dicho en [[Algoritmo de Grover]], esto corresponde a una reflexión sobre el hiperplano ortogonal a $\ket{w}$, es decir, una reflexión sobre $\ket{s'}$.

$$\begin{align}
U_{w}\ket{s} &= U_{w}(\sin \theta \ket{w} +\cos \theta \ket{s'} ) =  \\
U_{w}\ket{s} &= -\sin \theta \ket{w} + \cos \theta \ket{s'}    
\end{align}$$
En el plano:

![[Pasted image 20250217195718.png|300]]


Ahora vamos a aplicar el operador de difusión $U_{D} = 2\ket{s}\bra{s}-I$ sobre $U_{w}\ket{s}$.

Este operador lo que hace es una reflexión sobre el estado $\ket{s}$. Lo que hace es rotar $2\theta$ sobre el vector que representa $\ket{s}$, amplificando así la amplitud de $\ket{w}$. Es decir:
$$\begin{align}
U_{D}U_{w}\ket{s} &= U_{D}(-\sin \theta \ket{w}+\cos \theta \ket{s'}  )= \\\\
&=\sin(3\cdot \theta)\ket{w} + \cos(3\cdot \theta)\ket{s'}   
\end{align}$$
![[Pasted image 20250217200217.png|300]]

Vemos gráficamente que aumentamos la amplitud de probabilidad de $\ket{w}$. Si seguimos aplicando $U_{w}$ y $U_{D}$ consecutivamente aumentaremos aún más la probabilidad de $\ket{w}$. Pero si nos pasamos del número de veces que aplicamos estos dos operadores, $U_{D}U_{w}\ket{s}$, "dará la vuelta"y la amplitud de probabilidad de $\ket{w}$ disminuirá.


El número optimo de aplicaciones de estos dos operadores es: $||\frac{{\pi}}{4}\sqrt{ N }||$ veces.

