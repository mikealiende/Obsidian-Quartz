# Cota al error en la estimación EVA

Trataremos calcular la cota de del error en la estimación del algoritmo [[EVA]], la cual se puede aproximar por $\frac{{\left\|H\right\|^3}}{3!k^3}$ como vamos a demostrar a continuación:

Empezamos con dos suposiciones del Hamiltoniano:
* La norma de $H$ es menor de 1,  es decir $\left\|H\right\|:=max_{\phi}|\braket{ \phi}H\ket{\phi}\leq 1$
* H es un Hamiltoniano tipo Ising [[Modelo Ising#Definir función objetivo con Hamiltoniano]].

Partiremos de la expansión de la parte imaginaria de $e^{{iH}/{k}}$  : 
$$\Im\braket{ \phi}e^{{iH}/{k}}\ket{\phi} = \frac{\bra{\phi}H\ket{\phi}}{k}- \frac{\bra{\phi}H^3\ket{\phi}}{3!k^3} +\dots   $$

Despejamos la ecuación:

$$| \Im\braket{ \phi}e^{{iH}/{k}}\ket{\phi} - \frac{\bra{\phi}H\ket{\phi}}{k} |  = |\frac{\braket{ \phi}H^3\ket{\phi}}{3!k^3} - \frac{\bra{\phi}H^5\ket{\phi}}{5!k^5} +\dots |  $$

Como $H$ es un Hamiltoniano tipo Ising, tendrá una forma diagonal, por lo que podemos garantizar: $\bra{\phi}H^m \ket{\phi} = \bra{\phi}H\ket{\phi}^m$

Por lo tanto, podemos expresar la parte derecha de la ecuación anterior como una serie de potencias y obtener:

$$|\frac{\braket{ \phi}H^3\ket{\phi}}{3!k^3} - \frac{\bra{\phi}H^5\ket{\phi}}{5!k^5} +\dots | \leq |\frac{\bra{\phi}H\ket{\phi}}{k} - \sin\frac{\bra{\phi}H\ket{\phi}}{k} |$$
Como la función $f(x) = x-\sin x$ para $x \in(0,1)$ es siempre creciente y positiva, podemos acotar la expresión anterior por la norma:
$$|\frac{\bra{\phi}H\ket{\phi}}{k} - \sin\frac{\bra{\phi}H\ket{\phi}}{k} | \leq\frac{{\left\|H\right\|}}{k}- \sin\frac{{\left\|H\right\|}}{k} $$
Haciendo el desarrollo en serie de Taylor del seno:

$$|\frac{\braket{ \phi}H^3\ket{\phi}}{3!k^3} - \frac{\bra{\phi}H^5\ket{\phi}}{5!k^5} +\dots | \leq \frac{{\left\|H\right\|^3}}{3!k^3} - \frac{{\left\|H\right\|^5}}{5!k^5} + \dots$$
Si nos damos cuenta podemos comprobar:

$$\frac{{\left\|H\right\|^5}}{5!k^5}- \frac{{\left\|H\right\|^7}}{7!k^7}+\dots \geq 0$$

Esto es fácil de comprobar cogiendo los términos de la sucesión dos a dos y dándose cuenta de que la suma es siempre positiva. De esta manera, podemos suponer como cota $\frac{{\left\|H\right\|^3}}{3!k^3}$ al valor buscado, llegando a que:
$$\mid \Im \bra{\phi}e^{iH/k}\ket{\phi}-\frac{\bra{\phi}H\ket{\phi}}{k}     |\leq\frac{{\left\|H\right\|^3}}{3!k^3}$$
Modulando k podemos hacer el error tan pequeño como queramos.