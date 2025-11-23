# Algoritmo de Deutsch‐Jozsa

Se trata de una generalización del [[Algoritmo de Deutsch]] para $n$ qubits. Determina si una función $f:\{0,1\}^n \to\{0,1\}$ es constante o balanceada en una única evaluación. Un algoritmo clásico necesitaría $2^{n-1}+1$ evaluaciones. 

* Si $f$ es constante: Devuelve todo 0s o todo 1s para cualquier entrada
* Si $f$ es balanceada: Devuelve la 0s para la mitad de las entradas y 1s para la otra mitad.

Cualquier otra combinación, como que para una entrada de un 0 y el resto de entradas 1, no está contemplada en el contexto del algoritmo de Deutsch‐Jozsa.


## Desarrollo del Algoritmo

![[Pasted image 20250209184456.png]]


Partimos de $\ket{\psi_{0}}= \ket{0}^{\oplus n}\ket{1}$.

Aplicamos las $n+1$ puertas $H$:
$$\ket{\psi_{1}}= H^{\oplus n}\ket{\psi_{0}} = \sum_{x \in\{0,1\}^{n}} \frac{1}{\sqrt{ 2^n }}\ket{x} \frac{\ket{0}-\ket{1} }{\sqrt{ 2 }}     $$
Donde $\ket{x}$ toma cualquier valor posible de la base computacional de $n$ qubits. Ejemplo para $n=2$: $\ket{x} = \{00,01,10,11\}$. Si continuamos operando:
$$\ket{\psi_{1}}= \sum_{x \in\{0,1\}^{n}} \frac{1}{\sqrt{ 2^n }}\frac{\ket{x} \ket{0}-\ket{x} \ket{1} }{\sqrt{ 2 }}     $$
Aplicamos el oráculo $U_{f}$, que en su forma de operador unitario es $U_{f} \to U_{f}\ket{x}\ket{y} = \ket{x}\ket{f(x)\oplus y}$. Si lo aplicamos a $\ket{\psi_{1}}$:
$$\ket{\psi_{2}} = U_{f}\ket{\psi_{1}}  = \sum_{x \in\{0,1\}^{n}} \frac{1}{ 2^n }\ket{x} \ket{f(x)}-\ket{x} \ket{!f(x)}$$
En el segundo termino tenemos $!f(x)$, ya que a $f(x)$ se le suma 1 en módulo 2. $f(x)\oplus 1= !f(x)$.

Sacando factor común $\ket{x}$:
$$\ket{\psi_{2}}= \sum_{x \in\{0,1\}^{n}} \frac{1}{\sqrt{ 2^n }}\ket{x} \cdot\frac{\ket{f(x)}-\ket{!f(x)} }{\sqrt{ 2 }}    $$
Podemos reformular la expresión $\ket{f(x)}-\ket{!f(x)}= (-1)^{f(x)}(\ket{0}-\ket{1})$. Bastaría con evaluar $f(x) =0$ y $f(x)=1$ para comprobar que se cumple. Entonces:
$$\ket{\psi_{2}}= \sum_{x \in\{0,1\}^{n}} \frac{1}{\sqrt{ 2^n }}(-1)^{f(x)}\ket{x} \cdot\frac{\ket{0}-\ket{1} }{\sqrt{ 2 }}$$

Antes de aplicar las $H^{\oplus n}$, vamos a dar la siguiente igualdad:
$$H\ket{x}= \sum_{z \in\{0,1\}}\frac{(-1)^{x\cdot z}\ket{z}}{\sqrt{2}}  $$
Generalizamos para $H^{\oplus n}$:
$$H^{\oplus n}\ket{x} = \sum_{z_{1},\dots,z_{n}\in\{0,1\}} \frac{1}{\sqrt{ 2^n }}(-1)^{x_{1}\cdot z_{1}+\dots+x_{n}\cdot z_{n}}\ket{z_{1},\dots,z_{n}}=   \sum_{z \in\{0,1\}^n} \frac{1}{\sqrt{ 2^n }}(-1)^{x\cdot z}\ket{z} $$
Aplicando esto a nuestro estado $\ket{\psi_{2}}$, tenemos:
$$\ket{\psi_{3}} = H^{\oplus n}\ket{\psi_{2}} = \sum_{x \in\{0,1\}^{n}} \frac{(-1)^{f(x)}}{\sqrt{ 2^n }}\sum_{z \in\{0,1\}^n} \frac{(-1)^{x\cdot z}}{\sqrt{ 2^n }}\ket{z} \cdot\frac{\ket{0}-\ket{1} }{\sqrt{ 2 }}$$
Vemos que la información del qubit ancilla ha pasado al resto de qubits gracias al fenómeno de [[Phase Kickback]]. 
$$\ket{\psi_{3}} =\sum_{x \in\{0,1\}^{n}}\sum_{z \in\{0,1\}^n}  \frac{(-1)^{f(x)}}{\sqrt{ 2^n }}\frac{(-1)^{x\cdot z}}{\sqrt{ 2^n }}\ket{z} \cdot\frac{\ket{0}-\ket{1} }{\sqrt{ 2 }}$$
Por último, si simplificamos nos queda:
$$\ket{\psi_{3}}  = \sum_{x,z \in\{0,1\}^{n}}\frac{(-1)^{f(x)+x\cdot z}\ket{z} }{2^n}\cdot \frac{\ket{0}-\ket{1}  }{\sqrt{ 2 }} $$
**Medición**

Vamos a analizar las amplitudes de probabilidad para el estado $\ket{0}^{\oplus n}$, es decir, medir $\ket{0}$ en todos los qubits. La amplitud es:
$$\sum_{x \in\{0,1\}^{n}} \frac{1}{2^n}(-1)^{f(x)}$$
* Si $f$ es constante, el valor de la amplitud es $+1$ o $-1$, en función del valor constante que tome $f(x)$. Como la amplitud nos indica la probabilidad, en caso de ser constante mediremos $\ket{0}$ en todos los qubits.
* Si $f$ es balanceada, las contribuciones positivas y negativas de $f(x)$ a la amplitud de probabilidad del estado $\ket{0}$ se cancelan, dando lugar a una amplitud de probabilidad de $0$ al estado $\ket{0}^{\oplus n}$. Por lo tanto, si es balanceada es imposible medir $\ket{0}$ en todos los qubits, mediríamos con total seguridad algún $\ket{1}$.