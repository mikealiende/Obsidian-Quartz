# Interpretación intuitiva Algoritmo de Grover

Explicaremos de una forma intuitiva como funciona el [[Algoritmo de Grover]] con un ejemplo concreto.

Supongamos una lista de $N=4$ elementos que representamos con $n=2$ qubits. Los valores de esta tabla son $\{\ket{00},\ket{01},\ket{10},\ket{11}\}$. Suponemos que el estado que queremos buscar es $\ket{10}$.

1. Lo primero que hacemos es poner todos los estados es una superposición equiprobable, si representamos sus amplitudes de probabilidad: 

![[Pasted image 20250216195700.png|400]]

2. Aplicamos el oráculo $U_{w}$ que marca el estado buscado $\ket{10}$ invirtiendo su signo:

![[Pasted image 20250216195813.png|400]]


3. El operador difusor $U_{D}$ lo que hace es invertir respecto a al media todos los estados.

![[Pasted image 20250216195937.png|400]]

Por lo tanto, hemos conseguido aumentar la amplitud de probabilidad del estado marcado. Para conseguir resultados más óptimos debemos repetir la aplicación de $U_{w}$ y $U_{D}$ $||\frac{\pi}{4}\sqrt{ n }||$ veces.