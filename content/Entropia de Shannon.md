# Entropía de Shannon


Una medida de la información contenida en el mensaje. 
## Valor informacional de un mensaje

La entropía también se puede considerar como la cantidad de información promedio que contienen los símbolos usados. Los símbolos con menor probabilidad son los que aportan mayor información; por ejemplo, si se considera como sistema de símbolos a las palabras en un texto, palabras frecuentes como «que», «el», «a» aportan poca información, mientras que palabras menos frecuentes como «corren», «niño», «perro» aportan más información. Si de un texto dado borramos un «que», seguramente no afectará a la comprensión y se sobreentenderá, no siendo así si borramos la palabra «niño» del mismo texto original.

Si queremos expresar estas ideas matemáticamente podemos usar la función $I$ que será el **contenido de información de un evento** $E$. De este modo:
$$\begin{align}
I(E) = -\log_{2}(p(E)) \\ \\

I(E) = \log_{2}\left( \frac{1}{p(E)} \right)
\end{align}$$
Siendo $p(E)$ la probabilidad del evento $E$.


## Formulación matemática de la entropía de Shannon


Definimos la entropía de una variable discreta aleatoria $X$ cuyos posibles valores pueden ser $x_{1},x_{2},..,x_{n}$ como
$$H(X)= E[I(X)]$$

Siendo $E$ el valor esperado y $I(X)$ el contenido de información de $X$, de esta manera:

$$\begin{align}
I(X) &= -\log_{b}(P(X)) \\
H(X) &= E[-\log_{b}(P(X))]
\end{align}$$

Si definimos el valor esperado de una variable discreta $X$ con valores $x_{1},x_{2},..,x_{n}$ con probabilidades $p_{1},p_{2},..,p_{n}$ como $$E[X]=\sum_{i=1}^n x_{i}p_{i}$$
Sustituyendo esta expresión en la definición de entropía de $X$ tenemos $$H(X) = -\sum_{i=1}^{n}P(x_{i})\log_{b}P(x_{i})$$
Para el caso de la teoría de la información hablamos de bits y $b=2$.

También podemos hablar de [[Entropía conjunta multivariable]] y[[Entropía condicional de dos variables]]

## Propiedades de la entropía de Shannon

* H debe ser continua $\rightarrow$ Pequeños cambios en las probabilidades originan pequeños cambios en la entropía.
* H es simétrica $\rightarrow$ La entropía no cambia si los valores de $X$ cambian de orden.
* H es máxima cuando todas la probabilidades son iguales y aumenta con el número de posibilidades

