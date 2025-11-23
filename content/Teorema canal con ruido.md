# Teorema canal con ruido

En este sistema de comunicación, el mensaje $W$ se transmite a través de un canal con ruido, usando funciones de codificación y descodificación. 

![[Pasted image 20241215104446.png|1000]]


* El codificador mapea el mensaje $W$ en una secuencia predefinida de símbolos de longitud $n$. Esta secuencia es $X^{n}$. 
* El canal distorsiona estos símbolos, y a la salida tenemos la secuencia $Y^{n}$. Esta señal es la entrada del decodificador.
* El decodificador mapea la secuencia recibida $Y^{n}$ en una estimación de mensaje $W'$.

En este modelo, la probabilidad de error se define como $P_{e}=Pr\{W' \neq W\}$


## Formulación matemática canal discreto con ruido

Definimos:

* $p(X)$: probabilidades asociadas a la secuencia de entrada $X$. Es decir $p(x_{1}), p(x_{2}), \dots,p(x_{n})$.
* $p(Y|X)$: matriz del canal (matriz de transición del canal). Cada uno de sus elementos relaciona la probabilidad condicional de un elemento de la salida $y_{j}$, por un elemento de la entrada $x_{i}$. Por tanto esta matriz modela el efecto del ruido en el canal.
* $p(Y)$: probabilidades asociadas a las secuencias de salida $Y$.

Entonces:

$$p(Y)=p(X|Y)\cdot p(X)$$

## Teorema fundamental canal discreto con ruido

Estas son las variables que intervienen en el teorema:

* $C$: capacidad de un canal discreto y sin memoria.
* $X$: Entrada, variable discreta aleatoria.
* $Y$: Salida, variable discreta aleatoria.
* $P_{X}$: Distribución de la entrada $X$.

**Enunciado de Shannon (1948)**

Para un canal discreto y sin memoria, la capacidad $C$ del canal esta definido en términos de la información mutua $I(X;Y)$ y es: $$C = max(I(X;Y))$$

La capacidad del canal tiene la siguiente propiedad: para cada $\epsilon >0$ y ratio $R<C$ para un $N$ suficientemente grande, existe un código de longitud $N$ y $ratio \geq R$ y un algoritmo de decodificación con probabilidad máxima de error $< \epsilon$.

Si una probabilidad de error de bit $p_{b}$ es aceptable, entonces ratos de transmisión de hasta $R(p_{b})$ son conseguibles donde:$$R(p_{b})=\frac{C}{1-H_{2}(p_{b})}$$
Siendo $H_{2}(p_{b})$ es la función de entropía binaria.


**Representación gráfica**

Vamos a representar el ratio $R$ en y la probabilidad de error de bit $p_{b}$:

![[Pasted image 20241215111920.png|500]]
Podemos ver la zonas del plano $R,p_{b}$ con ratios alcanzables en función de $C$ y $p_{b}$.