# Quantum Annealing


Las QPUs de quantum annealing están diseñadas específicamente para resolver problemas de optimización combinatoria, como nuestro TSP. En forma de [[Problemas QUBO]]

Estos sistemas simulan el proceso de enfriamiento de un material para encontrar su estado de mínima energía. Para hacer estas simulaciones, las QPUs utilizan qubits super- conductores que pueden estar en un estado de superposición cuántica. Las interconexiones entre estos qubits se consiguen mediante acoplamiento electromagnético.

El proceso comienza inicializando los qubits en un estado aleatorio de alta energía, y la función objetivo a minimizar se introduce al sistema jugando con el acoplamiento entre los qubits. En este punto comienza el proceso de annealing, dejando que la temperatura del sistema se reduzca gradualmente y los qubits se ajusten a estados de menor energía. Cuando el sistema converge a un estado de mínima energía representa una solución óptima al problema.

Enlace a documentación de D-Wave Systems: https://docs.dwavesys.com/docs/latest/c_gs_2.html