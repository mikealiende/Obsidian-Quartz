# Base Fourier

En la base de Fourier la información se almacena en rotaciones alrededor del eje Z. El número que se desea almacenar determina el ángulo de la fase en la que el qubit deberá rotar alrededor del eje Z. ejemplo para representar el número 5 con 4 qubits:

* El qubit de menos peso deberá rotar $\frac{5}{2^n}2\pi=\frac{5}{16}2\pi$ radianes.
* El siguiente rotará el doble: $\frac{10}{16}2\pi$ radianes.
* El siguiente el doble que el anterior: $\frac{20}{16}2\pi$ radianes.
* El más significativo, el doble que el anterior: $\frac{40}{16}2\pi$ radianes.

Se puede observar que los qubits correspondientes al dígito menos significativo tiene la frecuencia de rotación más baja.