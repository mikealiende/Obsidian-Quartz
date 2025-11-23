# Medición qubits-Proyección

## Operadores proyección para la medida

Para cualquier subespacio $S \subset V$, el subespacio $S^\bot$ esta formado por todos los vectores que son perpendiculares a los vectores en $S$. Estos subespacios satisfacen que $V =S \oplus S^\bot$ y por lo tanto, cualquier vector $\vec{v} \in V$ se puede escrbrir como suma de los vectores $\vec{s_{1}}\in S$ y $\vec{s}_{2} \in S^\bot$. Entonces definimos el operador de proyección $P_{s}$ como: $$P_{s} : V \mapsto S$$ que envía $\vec{v} \mapsto \vec{s_{1}}$ .

El operador $\ket{\Psi}\bra{\Psi}$ es el operador proyección en el subespacio generado por $\ket{\Psi}$. De forma general, para cualquier descomposición de suma directa $V = S_{1}\oplus S_{2}\oplus \dots \oplus S_{k}$ en subespacios ortogonales, existen $k$ operadores de proyección relacionados:$$P_{i}:V\mapsto S_{i} \text{ , donde }P_{i}\ket{v}= \vec{s_{1}} \text{ siendo } \ket{v} = \vec{s_{1}}+\vec{s_{2}}+\dots+\vec{s_{k}} \text{ con } s_{i} \in S_{i} $$
Usando esta terminología, un dispositivo de medición con una descomposición asociada $V = S_{1}\oplus S_{2}\oplus \dots \oplus S_{k}$ que actúa sobre el estado $\ket{\psi}$ da como resultado el estado:$$\ket{\phi} = \frac{P_{i}\ket{\psi}}{|P_{i}\ket{\psi}| }  $$
con una probabilidad $|P_{i}\ket{\psi}|^2$ . 

En el caso de un qubit, el proyector $\ket{0}\bra{0}$ aplicado sobre un estado $\ket{\psi}$, proporciona la componente de $\ket{\psi}$ en el subespacio generado por $\ket{0}$. Ejemplo, si $\ket{\psi} = a\ket{0}+b\ket{1}$, entonces:$$(\ket{0}\bra{0})\ket{\psi} = a \braket{0|0}\ket{0} + b\braket{0|1}\ket{0}= a \cdot 1 \cdot \ket{0} + b \cdot 0 \cdot \ket{1} = a\ket{0}$$
hemos utilizado propiedades del [[producto interno]] y [[Proyectores]]. Esto se puede generalizar a $n$ qubits.

## Medición mecánica cuántica

Sea $A$ un [[Observables]] con un conjunto de autovalores $\{a_{i}\}$ y autoestados $\{\ket{\phi_{i}\}}$ donde: $$A\ket{\phi_{i}} = a_{i}\ket{\phi_{}}$$
Aplicando el operador proyección $P_{i} = \sum_{k}\ket{\phi_{k}}\bra{\phi_{k}}$ donde $\ket{\phi_{k}}$ son los autoestados de $A$ correspondientes a $a_{i}$. El operador $P_{i}$, proyecta un estado arbitrario $\ket{\psi}$ sobre un subespacio asociado al autovalor $a_{i}$ así:$$P_{i}\ket{\psi}= \sum_{k}\braket{\phi_{k}|\psi}\ket{\phi_{k}} $$
Entonces podemos expresar el estado $\ket{\psi}$ como la combinación lineal de los autoestados de $A$ : $$\ket{\psi} = \sum_{i} c_{i}\ket{\phi_{i}}$$
donde $c_{i} = \braket{\phi_{i}|\psi}$ (coeficiente de expansión, número complejo)

Cuando medimos el observable, obtendremos uno de sus autovalores $a_{i}$ como resultado. la probabilidad de medir $a_{i}$ es:$$p(a_{i}) = |P_{i}\ket{\psi}|^2 = |c_{i}|^2 = |\braket{\phi_{i}|\psi}|^2$$
Después de la medición el sistema colapsará al subespacio generado por los autovalores correspondientes al autovalor $a_{i}$ resultante de la medición. Este nuevo estado en el sistema se describe como:$$\ket{\psi'} = \frac{P_{i}\ket{\psi}}{|P_{i}\ket{\psi}| }  $$
#### Ejemplo medición

Vamos a suponer un observable $A$ con tres autovalores $\{a_{1},a_{2},a_{3}\}$ con autoestados $\{\ket{\phi_{1}},\ket{\phi_{2}},\ket{\phi_{3}}\}$. El estado inicial se puede describir como:$$\ket{\psi} = c_{1}\ket{\phi_{1}}+c_{2}\ket{\phi_{2}} +c_{3}\ket{\phi_{3}}   $$
donde $c_{i} = \braket{\phi_{i}|\psi}$ al medir obtenemos el valor $a_{1}$  con una probabilidad $|c_{1}^2|$ y el estado colapsa a:$$\ket{\psi'} = \ket{\phi_{1}}  $$ Siempre y cuando $a_{1}$ no sea degenerado.
