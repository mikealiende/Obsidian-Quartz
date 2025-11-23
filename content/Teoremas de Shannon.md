# Teoremas de Shannon #Tema 

##  Introducción

En 1948 Shannon publicó el articulo **Teoría de la matemática de la información.** Este articulo se centra en como codificar la información que un emisor desea transmitir. Aparece el concepto de [[Entropia de Shannon]], una medida de la información contenida en el mensaje. En función de como es la distribución de probabilidad de $X$, también se mencionan los conceptos de [[Entropía conjunta multivariable]] y [[Entropía condicional de dos variables]].

### Información mutua

Se define información mutua $I(X;Y)$ al número de unidades de información sobre $X$ que podemos adquirir leyendo $Y$. 

En el caso de un canal con ruido, la información mutua $I(X;Y)$ es la cantidad de información que se puede transmitir a través del canal $Y$.
$$I(X;Y)= H(X)-H(X|Y) = H(Y) - H(Y|X)$$
### Relación con la cuántica

El equivalente de la entropía de Shannon para un sistema cuántico es la [[Entropía de Von Nuemann]]

## Teoremas de canales de comunicación

Shannon clasificó sus teoremas según los canales de comunicación en dos:
* [[Teorema canal sin ruido]]
* [[Teorema canal con ruido]]


### Relación entre los teoremas de Shannon

**El primer teorema** esta enfocado a la compresión de datos, cuanto podemos comprimir un mensaje sin perder información. **El segundo teorema** contempla el efecto del ruido en el canal. Por lo tanto son complementarios y podemos implementar redundancia para mitigar los errores.

Por último, tenemos el [[Teorema de Shannon-Hartley]].

