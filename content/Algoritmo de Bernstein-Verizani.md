# Algoritmo de Bernstein-Verizani

Se trata de una versión restringida del algoritmo de [[Algoritmo de Deutsch‐Jozsa]], en vez de distinguir entre dos tipo de funciones, intenta encontrar un valor $s$ codificado en una función.

## Problema que resuelve

Dado un oráculo que implementa la función $f:\{0,1\}^n \to \{0,1\}$, donde $f(x)$ es el producto interno binario entre $x$ y un valor secreto $s \in \{0,1\}^n$ . Es decir $f(x)= x \cdot s \quad\text{(mod2)} = x_{1}\cdot s_{1} \oplus x_{2} \cdot s_{2}\oplus\cdots\oplus x_{n}\cdot s_{n}$

El algoritmo trata de obtener el valor $s$.

Con un algoritmo clásico, necesitaremos evaluar la función $n$ veces para encontrar $s$. En cambio, con este algoritmo lo conseguimos con una única consulta.


## Circuito algoritmo de Bernstein-Verizani

![[Pasted image 20250213205007.png|500]]

Tenemos un registro principal con $n$ qubits inicializados a $\ket{0}$ y un segundo registro auxiliar inicializado a $\ket{1}$.

**Inicialización**

Comenzamos con $\ket{\psi_{0}} = \ket{0}^{\otimes n}\otimes \ket{1}$

**Aplicamos la puertas Hadamard**

$$\ket{\psi_{1}} = H^{\otimes n} \otimes H \otimes \ket{\psi_{0}} = H^{\otimes n}\ket{0}^{\otimes n}\otimes H\ket{1}   $$
Si continuamos operando: 
$$\begin{align}
\ket{\psi_{1}} &= \left(\frac{1}{\sqrt{ 2 }} \ket{0}+\frac{1}{\sqrt{ 2 }}\ket{1}  \right)^{\otimes n}\otimes \left(\frac{1}{\sqrt{ 2 }} \ket{0}+\frac{1}{\sqrt{ 2 }}\ket{1}  \right) = \\ \\  
&= \frac{1}{\sqrt{ 2^n }}\sum_{x \in\{0,1\}^n} \ket{x} \otimes \frac{1}{\sqrt{ 2 }}\left(\ket{0} -\ket{1} \right) 
\end{align}$$

Siendo $\sum_{x \in\{0,1\}^n}\ket{x}$ todos los valores que puede tomar la base computacional para $n$ qubits. 

**Aplicamos el oráculo**

Vamos a aplicar $U_{f}$ siendo su definición unitaria: $U_{f} =\ket{x}\ket{y} = \ket{x}\ket{f(x)\otimes y}$, entonces:

$$\begin{align}
\ket{\psi_{2}} = U_{f}\ket{\psi_{1}} &= U_{f}\frac{1}{\sqrt{ 2^n }}\left( \sum_{x \in\{0,1\}^n}\frac{1}{\sqrt{ 2 }}\ket{x}\ket{0} -\frac{1}{\sqrt{ 2 }}\ket{x}\ket{1}   \right) \\  \\
&=\frac{1}{\sqrt{ 2^n }}\left( \sum_{x \in\{0,1\}^n}\frac{1}{\sqrt{ 2 }}U_{f}\ket{x}\ket{0} -\frac{1}{\sqrt{ 2 }}U_{f}\ket{x}\ket{1}   \right) \\ \\
&=\frac{1}{\sqrt{ 2^n }}\left( \sum_{x \in\{0,1\}^n}\frac{1}{\sqrt{ 2 }}\ket{x}\ket{f(x)} -\frac{1}{\sqrt{ 2 }}\ket{x}\ket{!f(x)}   \right) \\  \\
\ket{\psi_{2}} &= \frac{1}{\sqrt{ 2^n }}\left( \sum_{x \in\{0,1\}^n}\frac{1}{\sqrt{ 2 }}\ket{x}\ket{f(x)} -\frac{1}{\sqrt{ 2 }}\ket{x}\ket{!f(x)}   \right) 
\end{align}$$

Si nos centramos en $\frac{1}{\sqrt{ 2 }}\ket{x}\ket{f(x)} -\frac{1}{\sqrt{ 2 }}\ket{x}\ket{!f(x)}$:

$$\begin{equation}
\begin{cases}
 \frac{1}{\sqrt{ 2 }}\ket{x}\ket{0} -\frac{1}{\sqrt{ 2 }}\ket{x}\ket{1} \quad \text{si} \quad f(x)=0 \\ \\
 \frac{1}{\sqrt{ 2 }}\ket{x}\ket{1} -\frac{1}{\sqrt{ 2 }}\ket{x}\ket{0}\quad \text{si} \quad f(x)=1
\end{cases}
\end{equation}$$
que es lo mismo que:
$$\begin{equation}
\begin{cases}
\ket{x}\ket{-}  \quad \text{si} \quad f(x)=0 \\ \\
-\ket{x}\ket{-}  \quad \text{si} \quad f(x)=1
\end{cases}
\end{equation}$$

Es decir:
$$\frac{1}{\sqrt{ 2 }}\ket{x}\ket{f(x)} -\frac{1}{\sqrt{ 2 }}\ket{x}\ket{!f(x)} = (-1)^{f(x)}\ket{x}\otimes \ket{-}  $$
Volviendo a nuestro estado, lo podemos reescribir como:
$$\ket{\psi_{2}} = \frac{1}{\sqrt{ 2^n }} \sum_{x \in\{0,1\}^n}(-1)^{f(x)}\ket{x}\otimes \ket{-}  $$
Observamos que $\ket{-}$ no se ha modificado, pero hemos codificado la información de $f(x)$ de este registro auxiliar en nuestro registro principal gracias al fenómeno de [[Phase Kickback]].

**Aplicar Hadamards al registro principal**

Para volver a aplicar las puertas $H^{\otimes n}$ vamos a utilizar la transformada de Hadamard:
$$H^{\otimes n}\ket{x} =  \sum_{z \in\{0,1\}^n} \frac{1}{\sqrt{ 2^n }}(-1)^{x \cdot z}\ket{z} $$

En nuestro sistema:
$$\begin{align}
\ket{\psi_{3}}&= H^{\otimes n}\ket{\psi_{2}}= \frac{1}{\sqrt{ 2^n }} \sum_{x \in\{0,1\}^n} (-1)^{f(x)}\sum_{z \in\{0,1\}^n} \frac{1}{\sqrt{ 2^n }}(-1)^{x \cdot z}\ket{z}=\\ \\
&=\frac{1}{2^n}\sum_{x,z \in\{0,1\}^n}(-1)^{f(x)}\cdot (-1)^{x \cdot z}\ket{z}\\ \\
\ket{\psi_{3}} &=  \frac{1}{2^n}\sum_{x,z \in\{0,1\}^n}(-1)^{f(x)+x \cdot z}
\end{align}$$
Como hemos dicho al plantear el problema, $f(x)= x \cdot s \quad\text{(mod2)}$ 
$$\ket{\psi_{3}} =  \frac{1}{2^n}\sum_{x,z \in\{0,1\}^n}(-1)^{x\cdot s+x \cdot z}\ket{z} \to \frac{1}{2^n}\sum_{x,z \in\{0,1\}^n}(-1)^{x\cdot(s\oplus z)}\ket{z} $$

Finalmente si medimos $\ket{\psi_{3}}$, podemos demostrar que obtenemos el estado $\ket{s}$, siendo $s$ la cadena buscada.

El término clave de $\ket{\psi_{3}}$ en la medición es:
$$\sum_{x \in\{0,1\}^n}(-1)^{x\cdot(s\oplus z)}$$
* si $s\oplus z=0$ , es decir, $z=s$ entonces $(-1)^{x\cdot(s\oplus z)}=1$ para todo $x$. Y el resultado del los dos sumatorios es $2^n$.
* si $s\oplus z \neq 0$, la suma alterna entre $-1$ y $1$ cancelándose, interferencia cuántica destructiva.

De este modo, nunca mediremos los estados en los que $s \neq z$. Gracias a que la segunda aplicación $H ^{\otimes n}$ interfiere constructivamente en las amplitudes de probabilidad en las que $\ket{z} = \ket{s}$ y destruye todos los estados $\ket{z} \neq \ket{s}$. Sustituyendo entonces $\sum_{x,z \in\{0,1\}^n}(-1)^{x\cdot(s\oplus z)}=2^n$ cuando $z=s$, tenemos:
$$\ket{\psi_{3}} = \frac{1}{2^n}\cdot 2^n \ket{s} = \ket{s}  $$

Siendo $s$ la cadena buscada.