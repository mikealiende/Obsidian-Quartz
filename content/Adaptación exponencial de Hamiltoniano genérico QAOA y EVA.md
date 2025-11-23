# Adaptación exponencial de Hamiltoniano genérico QAOA y EVA

Vamos a plantear una manera genérica de descomponer exponenciales genérica de Hamiltonianos independientemente de sus operadores de Pauli, para usarlo en algoritmos como [[QAOA]] y [[EVA]].

Ya vimos como construir con puertas cuánticas $e^{i\sigma_{i}^z}$ usando $R_{z}$ en [[Modelo Ising#Construir $ exp(it sigma_{i} z)$]] , y $e^{i\sigma_{i}^z\sigma_{j}^{z}}$ usando $R_{z}$ y CNOT en [[Modelo Ising#Construir $ exp(it sigma_{i} z sigma_{j} z)$]]

Podemos aplicar la mismo razonamiento y la equivalencia $\sigma^x = H\sigma^zH$, de esta manera:
$$e^{it\sigma^x}= \cos(t)I+\sin(t)\sigma^x = \cos(t)I+\sin(t)H\sigma^zH = HR_{z}H = R_{x}$$

Para el caso de $e^{i\sigma_{i}^x\sigma_{j}^{x}}$ el procedimiento es igual, colocamos una puerta $H$ al principio y final de los qubits:

![[Pasted image 20240528192703.png|300]]
De esta misma manera podríamos construir la exponencial $e^{i\sigma_{i}^z\sigma_{j}^x}$ colocando las $H$ en el qubit $j$

**El problema** que tenemos es que los operadores de Pauli no conmutan entre ellos, por lo tanto no se cumple la siguiente igualdad:
$$e^{\sigma^x+\sigma^y} \neq e^{\sigma^x} e^{\sigma^y} $$
Por lo tanto a priori no podemos construir la exponencial como producto de las exponenciales sus componentes, por lo que debemos recurrir a una técnica llamada [[Trotterización]]. Esta técnica nos permitirá aproximar la exponencial de un Hamiltoniano genérico del tipo $H=\sigma^x+\sigma^z$.

