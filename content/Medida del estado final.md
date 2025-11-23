# Medida del estado final

Para poder obtener el resultado del cálculo cuántico es necesario tener la capacidad de medir el estado del registro cuántico a nivel de qubits individuales.

La matriz densidad de la probabilidad de un qubit es:
$$\rho=p\ket{0}\bra{0}+1(1-p)\ket{1}\bra{1}+\alpha \ket{0}\bra{1}+\alpha^* \ket{1}\bra{0}$$
La mediada del qubit debería resultar en $\ket{0}$ con una probabilidad $p$ y en $\ket{1}$ con una probabilidad $1-p$ , independientemente del valor $\alpha$ . Esta medida deber ser independiente del resto de qubits del sistema.