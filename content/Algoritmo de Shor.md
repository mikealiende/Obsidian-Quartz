# Algoritmo de Shor

El algoritmo de Shor es uno de los más importantes en la computación cuántica. Este problema resuelve de forma eficiente el problema de factorizar números enteros. Su importancia se debe a que los sistemas criptográficos que utilizan sistemas como RSA se verían comprometidos por este algoritmo ejecutado en un computador cuántico con los qubits suficientes (además de fiables).

Shor logra factorizar el número $N$ en los factores primos $p$ y $q$ en un tiempo polinómico. La clave de el algoritmo es que podemos transformar el problema de factorización de $N$ en el el problema de encontrar el período de la función $f(x) = a^{x} (\text{mod }N)$ (Este periodo debe cumplir ciertas condiciones). Y el algoritmo de Shor aprovecha que con cierto circuito cuántico que luego veremos podemos calcular estos periodos de forma eficiente.

## Equivalencia entre Factorizar $N$ y encontrar el periodo de $f(x) = a^{x} (\text{mod }N)$

Para empezar vamos a presentar las **raíces no triviales módulo $N$**. 
$$
X^2 \equiv 1\ \mod(N) \quad \text{con }X \in (2,N-2) $$
Si seguimos operando:
$$\begin{align}
X^2 &\equiv 1 \ \mod(N) \\
X^2 -1 &\equiv 0 \ \mod(N) \\
(X-1)(X+1) &\equiv 0 \mod(N)
\end{align}$$

 Esto significa que $(X-1)(X+1)$ es múltiplo de $N$, es decir:
 $$(X-1)(X+1) = k\cdot N$$
 Vamos a descomponer a $X-1$ y $X+1$ en factores más pequeños de la siguiente manera:
 $$\begin{equation}
\begin{cases}
X+1 = x_{1}\cdot x_{2}\cdot x_{3}\cdot \dots \cdot x_{n} \\
X-1 = y_{1}\cdot y_{2}\cdot y_{3}\cdot \dots \cdot y_{m}
\end{cases}
\end{equation}$$

Gracias a la condición de que $X \in (2,N-2)$, podemos asegurar que $N$ no estará enteramente contenido ni en $X+1$ ni en $X-1$. En otras palabras:
$$\begin{equation}
\begin{cases}
X+1 = x_{1}\cdot x_{2}\cdot x_{3}\cdot \dots \cdot x_{n}  <N\\
X-1 = y_{1}\cdot y_{2}\cdot y_{3}\cdot \dots \cdot y_{m} < N
\end{cases}
\end{equation}$$
Y como $N = p\cdot q$, significa que $p$ está en $X+1$ o en $X-1$ y $q$ en factor en el que no esté $p$. Por ejemplo, si $p$ está en $X+1$ y $q$ en $X-1$:
$$\begin{equation}
\begin{cases}
X+1 = x_{1}\cdot x_{2}\cdot p \cdot x_{4}\cdot \dots \cdot x_{n} \\
X-1 = y_{1}\cdot q\cdot y_{3}\cdot \cdot y_{4}\dots \cdot y_{m}
\end{cases}
\end{equation}$$
Si sustituimos en la ecuación de antes tenemos:
$$(x_{1}\cdot x_{2}\cdot p \cdot x_{4}\cdot \dots \cdot x_{n})(y_{1}\cdot q\cdot y_{3}\cdot \cdot y_{4}\dots \cdot y_{m}) = k \cdot N$$
Resulta intuitivo ver que como $p \cdot q=N$, los factores $x_{i} \neq p$ y $y_{i} \neq q$ solo aportan al factor $k$, por lo que podemos obtener $p$ y $q$ con el máximo común divisor así:
$$\begin{align}
MCD(X+1,N) =p \\
MCD(X-1,N) = q
\end{align}$$

==De momento hemos demostrado que factorizar un número es equivalente a encontrar sus raíces no triviales modulo $N$. Ahora veremos que la búsqueda de estas raíces es equivalente a encontrar el período de un función.==

Vamos a definir el orden $r$ como el número positivo más pequeño que cumple:
$$a^r \equiv 1 \mod(N)$$
Siendo a un entero positivo coprimo con $N$, tal que: $MDC(a,N)=1$.

Si definimos la función $f(x)=a^x \mod(N)$ es fácil ver que el orden $r$ coincide con el periodo de la función, ya que $f(0) = a^0 \mod(N) \equiv 1 \mod(N)$, y como $r$ es el primer entero siguiente a $0$ que cumple $a^r \equiv 1 \mod(N)$ vemos que es el periodo tal que $f(x) = f(x+k)$.

Con esto podemos asegurar que calcular el orden $r \mod(N)$   es equivalente a encontrar el periodo de $f(x)= a^x \mod(N)$. 

Si este orden $r$ es par, podemos escribirlo como:
$$\begin{align}
(a^{r/2})^2 \equiv 1 \mod(N) \\
(a^{r/2})^2 -1\equiv 0 \mod(N) \\
(a^{r/2}-1)(a^{r/2}+1)\equiv 0 \mod(N)
\end{align}$$

Vemos que tiene la misma forma que la demostración de antes de que encontrar las raíces no triviales de modulo $N$ equivale a facotorizar, por lo tanto, usando lo que hemos demostrado antes:

$$\begin{align}
MDC(a^{r/2}-1,N) = p \\
MDC(a^{r/2}+1,N) =que 
\end{align}$$

Por lo tanto hemos demostrado que factorizar $N$ es equivalente a encontrar un periodo par de la función $f(x) = a^x \mod(N)$, siendo a un entero aleatorio coprimo de $N$. [[Ejemplo equivalencia entre encontrar el periodo y factorizar]]

## Descripción detallada del algoritmo de Shor.

El algoritmo de Shor completo de trata de un algoritmo mixto, ya que aparte de la parte cuántica que utilizamos para calcular el periodo en tiempo polinomial, también requiere de un pre y post procesado clásico.

* **Pre-procesado clásico**: Básicamente comprueba que $N$ se puede factorizar de forma no trivial y escoge el valor aleatorio $a$.
* **Parte cuántica**: A partir del valor $a$ calcularemos con un algoritmo cuántico el periodo $r$ de la función $f(x) =a^x \mod(N)$.
* **Post-procesado clásico**: Veremos que del algoritmo cuántico no obtenemos directamente $r$ si no que tenemos que utilizar algoritmos como el de fracciones continuas para terminar de calcular $r$, también comprueba si $r$ es par y calcula $p$ y $q$.

### Encontrar el periodo $r$ con circuitos cuánticos.          

Tenemos dos registros cuánticos:
* Registro 1 con $t$ qubits
* Registro 2 con $n$ qubits

Todos los qubits están inicializados a $\ket{0}$, entonces partimos de $\ket{\psi_{0}}=\ket{0^{\otimes t}}\otimes\ket{0^{\otimes n}}$

**Superposición.**

Aplicamos la puerta $H^{\otimes t}$ al registro 1 para ponerlo en superposición:
$$\begin{align}
\ket{\psi_{1}}&=  H^{\otimes t}\otimes I^{\otimes n}\ket{\psi_{0}} =  \\
&=H^{\otimes t}\ket{0^{\otimes t}}\otimes\ket{0^{\otimes n}} = \\
\ket{\psi_{1}} &= \frac{1}{\sqrt{ Q }}\sum_{k=0}^{Q}\ket{x}\otimes \ket{0^{\otimes n}}    \\
\end{align}$$
Siendo $Q=2^t$.

**Exponenciación modular**

Para implementar la función $f(x) =a^x \mod(N)$ vamos a usar el oráculo $U_{f(x)}$ , que se puede implementar con el algoritmo de exponenciación modular cuántica. De forma unitaria:
$$U_{f(x)}\ket{x}\ket{y} = \ket{x}\ket{y \oplus a^x \mod(N)}    $$
Aplicándolo a nuestro estado:
$$\ket{\psi_{2}}=U_{f(x)}\ket{\psi_{1}} =  \frac{1}{\sqrt{ Q }}\sum_{k=0}^{Q}\ket{x}\otimes \ket{a^x \mod(N)}    $$
**Medición registro 2**

Al medir el registro 2, vamos a hacer colapsar a $\ket{a^x \mod(N)}$ a un valor específico $z=a^{x_{0}} \mod(N)$. Esta medición provoca que el estado en superposición del registro 1 se proyecte (colapse) en el subespacio generado por los autoestados $\ket{x}$ consistentes en el valor medido $z=a^{x_{0}} \mod(N)$. Es decir, en el registro 1 sólo nos quedamos con los valores de $x$ que sean resultado del $f(x) =z$ medido. Por lo tanto después de medir el registro 1 tenemos:
$$\ket{\psi_{3}} = \frac{1}{\sqrt{ \frac{Q}{r} }}\sum_{k=0}^{Q /r} \ket{x_{0}+k\cdot r } = \sqrt{ \frac{r}{Q } }\cdot \sum_{k=0}^{Q /r} \ket{x_{0}+k\cdot r }$$
Donde $x_{0}$ es el primer entero que da como resultado $z$. Este valor $x_{0}$, nos esta complicando el cálculo de $r$. Vamos a utilizar la [[Transformada cuántica de Fourier QFT]] para eliminar este valor.

**QFT registro 1**

Antes de empezar tenemos que tener en cuanta lo siguiente:

* $Q$ es multiplo de r
* $QFT\ket{x} = \frac{1}{\sqrt{ Q }}\sum_{y=0}^{Q}e^{2\pi i {x\cdot y}/Q}\ket{y}$

Aplicamos $QFT$ a $\ket{\psi_{3}} =$

$$\begin{align}
\ket{\psi_{4}}=QFT\ket{\psi_{3}}=  \sqrt{ \frac{r}{Q } }\cdot \sum_{k=0}^{Q /r} \frac{1}{Q}\cdot \sum_{y=0} ^{Q}e^{2\pi i(x_{0}+k\cdot r)y/Q}\ket{y} \\ \\
\ket{\psi_{4}} =\frac{\sqrt{ r }}{Q }\sum_{k=0}^{Q /r} \sum_{y=0} ^{Q}e^{2\pi ix_{0}y/Q}\cdot e^{2\pi i+k\cdot r\cdot y/Q} \ket{y} 
\end{align}$$

Vamos a analizar el factor $e^{2\pi i+k\cdot r\cdot y/Q}$ de la expresión de arriba, si se da el caso que $y$ es múltiplo de $\frac{Q}{r}$ entonces $e^{2\pi i+k\cdot r\cdot y/Q}=1$, y entonces, el coeficiente del estado que cumple este caso sería:
$$\frac{\sqrt{ r }}{Q} \cdot \frac{Q}{r}e^{2\pi i x_{o}\cdot y /Q} \cdot 1 = \frac{1}{\sqrt{ r }}\phi_{y}$$
Siendo $^{2\pi i x_{o}\cdot y /Q} =\phi_{y}$, pero al ser una fase global no afecta en el resultado de la medición. Entonces el coeficiente de los estados $\ket{y}$ cuando $y$ es múltiplo de $\frac{Q}{r}$ es $\frac{1}{\sqrt{ r }}$.

Teniendo en cuenta que en $Q$ hay $r$ múltiplos de $\frac{Q}{r}$, cuando $y$ recorra todos los valores se dará el caso de que $y$ es múltiplo de $\frac{Q}{r}$ un total de $r$ veces, lo que nos permite calcular la probabilidad de que $y$ sea múltiplo de $\frac{Q}{r}$.

$$P\left( y=k \cdot\frac{Q}{r} \right) = |\frac{{1}}{\sqrt{r  }}|^2+ \dots \text{ n veces } \cdot |\frac{{1}}{\sqrt{r  }}|^2 = \sum^r |\frac{{1}}{\sqrt{r  }}|^2 =1$$

Que la probabilidad de que $y$ sea múltiplo de $\frac{Q}{r}$ sea 1, significa entonces que la probabilidad de que no lo sea es entonces 0. Es decir, siempre que midamos un $\ket{y}$, este será múltiplo de $\frac{Q}{r}$. Asi que podemos decir:
$$\sqrt{ \frac{r}{Q } }\cdot \sum_{k=0}^{Q /r} \ket{x_{0}+k\cdot r }\rightarrow^{QFT}\rightarrow \frac{1}{\sqrt{ r }}\sum_{k=0}^{r}\ket{k \cdot \frac{Q}{r}} $$
Por lo que al medir en el registro 1 mediremos siempre $k \cdot \frac{Q}{r}$ 

Con una etapa final de post-procesado clásico en el que podemos usar el algoritmo de fracciones continuas para obtener $r$ a partir de $k \cdot \frac{Q}{r}$. Y después calcularíamos $p$ y $q$ así:
$$\begin{align}
MCD(a^{r/2}+1,N) = p \\
MCD(a^{r/2}-1,N) = q
\end{align}$$

Este post-procesado cuántico también comprueba que $r$ es par, si no empezamos el ciclo desde el principio con otro valor de $a$.
