# Ejemplo equivalencia entre encontrar el periodo y factorizar

Vamos a demostrar con un ejemplo numérico que factorizar $N$ es equivalente a encontrar un periodo par de la función $f(x) = a^x \mod(N)$, siendo a un entero aleatorio coprimo de $N$. Factorizar $N=15$ con por ejemplo $a=7$.

con $f(x) = a^x  \mod(N)\to f(x) = 7^x  \mod(15)$:

$$\begin{align}
f(0) &= 7^0  \mod(15) \equiv 1  \mod(15) \\ 
f(1) &= 7^1  \mod(15) \equiv 7  \mod(15) \\ 
f(2) &= 7^2  \mod(15)  = 49 \mod(15) \equiv  4 \mod(15) \\
f(3) &= 7^3  \mod(15)  = 7\cdot {7}^2 = 7 \cdot 4 \mod(15) \equiv  13 \mod(15) \\
f(4) &= 7^4  \mod(15)  = 7^2\cdot {7}^2 = 4 \cdot 4 \mod(15) \equiv  1 \mod(15) 
\end{align}$$
Hemos encontrado que el periodo y por lo tanto el orden es $r=4$, como es par podemos calcular $p$ y $q$ así:

$$\begin{align}
MDC(7^2+1,15) = MDC(50,15) =5 \\
MDC(7^2-1,15) = MDC(48,15) =3
\end{align}$$