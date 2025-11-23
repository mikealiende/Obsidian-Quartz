# Entropía condicional de dos variables

La entropía condicional es la cantidad de información en una variable aleatoria suponiendo que conocemos la otra.

Si $X$ e $Y$ son variables discretas aleatorias tales que sus posibles valores son $$\begin{align}
X&:\{x_{1},x_{2},\dots,x_{n}\} \\
Y&:\{y_{1},y_{2},\dots,y_{n}\}
\end{align}$$
La entropía condicional de $X$ e $Y$ se define como:
$$H(X|Y)=-\sum_{i,j}^{n,m}p(x_{i,y_{j}})\cdot \log_{b}\frac{p(x_{i},y_{i})}{p(y_{j})}$$


