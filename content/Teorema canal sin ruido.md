# Teorema canal sin ruido

Se trata de un problema de representación eficiente de los símbolos que genera una fuente.

## Enunciado

Consideramos una fuente sin memoria y entropía finita. y sea $H$ la entropía de la fuente y $\epsilon$ un número positivo. Entonces podemos codificar los símbolos que genera la fuente a un ratio $R$ tal que:$$R = H + \epsilon$$
Esta expresión indica que la entropía representa un limite fundamental en el número de bits que se necesitan para representar los símbolos de la fuente.

## Enunciado matemático

Si una fuente con entropía $H(X)$ es codificada usando un alfabeto $B$ de tamaño $b$, dado un número $\epsilon > 0$ para un número $n$ lo suficientemente grande, existe una función codificada $c(X)$ tal que:$$\frac{1}{n}E\mid c(X)\mid \leq \frac{H(X)}{\log b}+\epsilon$$
Esto implica que $$\lim_{ n \to \infty } X = \{X_{1},X_{2},\dots,X_{n}\}  = \frac{H(X)}{\log b}$$
Y por lo tanto, no se podrá codificar el mensaje que genera una fuente con una longitud inferior a $\frac{H(X)}{\log b}$

### Idea intuitiva 

De una forma más intuitiva, si $N$ si el número de variables aleatorias mutuamente independientes (independientes e idénticamente distribuidos). Estas $N$ variables, puede comprimirse en más de $N\cdot H(X)$ bits sin pérdida de información. Si $N \rightarrow \infty$, la perdida de información disminuye, pero si estas $N$ variables aleatorias se comprime en menos de $N\cdot H(X)$, se perderá información,

==De este teorema se obtiene que la entropía $H(X)$ proporciona un límite inferior y universal para la compresión de mensajes==