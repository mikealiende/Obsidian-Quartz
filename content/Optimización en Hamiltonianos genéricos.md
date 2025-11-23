# Hamiltonianos Genéricos #Tema 

Hasta este punto hemos trabajado con Hamiltonianos de [[Modelo Ising]] que esta compuesto sólo por puertas de Pauli Z $\sigma^z$ el objetivo de este tema será como construir un Hamiltoniano que contenga las tres puertas de Pauli $\sigma^x, \sigma^y$ y $\sigma^z$ . De esta manera:

$$H = \sum_{k \in \{x,y,z \}}\sum_{l \in \{x,y,z \}}\sum_{i,j}\alpha_{ij}\sigma_{i}^k\sigma_{j}^l +\sum_{k \in \{x,y,z \}}\sum_{i}\beta_{i}\sigma_{i}^k$$


Empezaremos por [[Adaptación Hamiltoniano genérico VQE]] y seguiremos con [[Adaptación exponencial de Hamiltoniano genérico QAOA y EVA]] que gracias a la [[Trotterización]], seremos capaces de construir con puertas cuánticas cualquier Hamiltoniano y su exponencial.

