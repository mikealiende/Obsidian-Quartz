# Algoritmo de Grover


El algoritmo de Grover es una algoritmo de búsqueda en una base de datos no estructurada. Para encontrar un elemento marcado en una lista de $N$ elementos, de forma clásica se necesitará una media de $N/2$ consultas. El algoritmo de Grover permite encontrar el valor en $\sqrt{ N }$ consultas. Lo que supone una ventaja cuadrática. 

El planteamiento del problema es: Dada una función $f:\{0,1\}^n \to\{0,1\}$. Siendo:
$$\begin{equation}
\begin{cases}
f(x) =1 \quad \text{si }x=w  \\
f(x) =0 \quad \text{si }x\neq w
\end{cases}
\end{equation}$$
## Elementos del algoritmo

Para comprender bien el algoritmo, vamos a detallar primero los elementos que intervienen en este algoritmo: superposición, oráculo $U_{w}$ y operador de difusión o de Grover $U_{D}$.

### Superposición equiprobable

Comenzamos poniendo  $n$ qubits inicializados a $\ket{0^{\otimes n}}$ en superposición aplicando $H^{\otimes n}$.
$$H^{\otimes n}\ket{0^{\otimes n}}= \frac{1}{\sqrt{ N }}\sum_{x \in\{0,1\}^{n}}\ket{x}=\ket{s}  $$
Siendo $N=2^n$. Hemos llamado a este estado de superposición $\ket{s}$ para simplificar. Lo que hemos hecho ha sido poner los $N$ elementos de la lista en superposición.

### Oráculo $U_{w}$

Aunque sería posible implantar el algoritmo de Grover con el oráculo estándar $U_{f}$. El oráculo $U_{w}$ lo que hace es "marcar" el estado objetivo $\ket{w}$ cambiando su signo (invirtiendo su fase) y dejando los demos inalterados. Es decir:
$$\begin{equation}
U_{w}\ket{x} = \begin{cases}
-\ket{x} \quad &\text{si } x=w \\
\ket{x} \quad &\text{si } x \neq w 
\end{cases} 
\end{equation}$$

Utilizando la función $f(x)$ que hemos usado para plantear el problema, podemos escribir el oráculo como:
$$U_{w}\ket{k} = (-1)^{f(x)}\ket{x}$$

Con la [[Demostración geométrica algoritmo de Grover]] veremos que este oráculo lo que hace es una reflexión sobre el hiperplano ortogonal a $\ket{w}$, utilizando la reflexión Householder podemos definir $U_{w}$ como:
$$U_{w}=I-2\ket{w}\bra{w}$$
Podemos observar  que $\ket{w}\bra{w}$ es el operador proyector sobre el estado $\ket{w}$.Vamos a demostrar que esta expresión invierte únicamente la fase de $\ket{w}$.

* Si $\ket{x}=\ket{w}$
	$$U_{w}\ket{w} = (I-2\ket{w}\bra{w})\ket{w} = \ket{w}-2\ket{w}\braket{w|w}= \ket{w} -2\ket{w}=-\ket{w}         $$

	Como todos los estados en superposición del estado $\ket{s}$ forman una base ortonormal, sabemos que $\braket{w|w}=1$ y $\braket{x|w}=0$.

* Si $\ket{x} \neq \ket{w}$
   $$U_{w}\ket{x} = (I-2\ket{w}\bra{w})\ket{x} = \ket{x}-2\ket{w}\braket{w|x}= \ket{x}       $$

En resumen: $U_{w} = I-2\ket{w}\bra{w}$ y su implementación dependerá del problema concreto que queramos solucionar.

### Operador de Difusión o de Grover

De forma geométrica el operador de difusión $U_{D}$ es una reflexión sobre el estado de superposición $\ket{s}$. De forma similar a como hemos hecho con el oráculo $U_{w}$, podemos utilizar la reflexión de Householder para definirlo como:
$$U_{D} = 2\ket{s}\bra{s} - I  $$

La diferencia es que $U_{w} = I-2\ket{w}\bra{w}$ refleja un vector sobre el hiperplano ortogonal a $\ket{w}$, mientras que $U_{D}=2\ket{s}\bra{s}_{I}$ es una reflexión sobre $\ket{s}$.

#### Implementación $U_{D}$ en un circuito cuántico

Como $\ket{s}=H^{\otimes n}\ket{0^{\otimes n}}$, sustituimos y tenemos:
$$U_{D} =2H^{\otimes n}\ket{0^{\otimes n}}\bra{0^{\otimes n}}H^{\otimes n} -I$$
Al ser $H^{\otimes n}$ unitario podemos escribir $I$ como $I = H^{\otimes n}\otimes H^{\otimes n}$.  Sustituyendo:
$$U_{D} =2H^{\otimes n}\ket{0^{\otimes n}}\bra{0^{\otimes n}}H^{\otimes n} -H^{\otimes n}\otimes H^{\otimes n}$$
Si sacamos factor común $H^{\otimes n}$ por la izquierda y $H^{\otimes n}$ por la derecha, tenemos:
$$U_{D} =H^{\otimes n} \otimes (2\ket{0^{\otimes n}}\bra{0^{\otimes n}} -I)\otimes H^{\otimes n}$$
Vamos a estudiar como se comporta $2\ket{0^{\otimes n}}\bra{0^{\otimes n}}-I$. 

* Vamos a empezar aplicándolo a un estado básico cualquiera $\ket{\psi}$ distinto a $\ket{0^{\otimes n}}$

$$(2\ket{0^{\otimes n}}\bra{0^{\otimes n}}-I)\ket{\psi} = 2\ket{0^{\otimes n}}\braket {0^{\otimes n}|\psi} - \ket{\psi} $$
	Como $\ket{\psi}$ y $\ket{0}^{\otimes n}$ son ortogonales $\braket {0^{\otimes n}|\psi}=0$. Tenemos:
$$(2\ket{0^{\otimes n}}\bra{0^{\otimes n}}-I)\ket{\psi} = - \ket{\psi} $$
* Ahora vamos a aplicar al estado $\ket{0^{\otimes n}}$
$$(2\ket{0^{\otimes n}}\bra{0^{\otimes n}}-I)\ket{0^{\otimes n}} = 2\ket{0^{\otimes n}}\braket {0^{\otimes n}|0^{\otimes n}} - \ket{0^{\otimes n}} = \ket{0^{\otimes n}}  $$

Es decir, $2\ket{0^{\otimes n}}\bra{0^{\otimes n}}-I$ cambia el signo a todos los estado excepto a $\ket{0^{\otimes n}}$, o visto de otro modo equivalente, deja inalterados todos los estados excepto a $\ket{0^{\otimes n}}$, que lo cambia de signo. Verlo de una forma u de otra no tiene ningún impacto en la medición. Podemos entonces representar $2\ket{0^{\otimes n}}\bra{0^{\otimes n}}-I$ como el siguiente circuito cuántico:

![[Pasted image 20250216194639.png|200]]

Y por lo tanto el operador de difusión $U_{D}$ lo podemos construir como:

![[Pasted image 20250216194758.png|300]]

El operador de difusión siempre es el mismo y no depende del problema.

Como ya hemos presentado todos los elementos del algoritmo de Grover lo podemos representar como:

![[Pasted image 20250216195034.png]]

Para entenderlo vamos a ver 3 alternativas de interpretación/demostración:

* [[Interpretación intuitiva Algoritmo de Grover]]
* [[Demostración geométrica algoritmo de Grover]]
* [[Demostración matemática del algoritmo de Grover]]