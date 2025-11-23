# Complejidad asintótica

Dado que el tiempo de ejecución exacto de un algoritmo es una expresión compleja por lo general, lo que vamos a hacer es aproximarlo con un método de análisis asintótico. 

El análisis asintótico busca busca obtener un orden de magnitud de tiempo de ejecución de un algoritmo cuando este se ejecuta con entradas de gran tamaño. Para ello, consideramos solo el término de orden más alto de la expresión sin tener el cuenta el coeficiente del termino. Para entradas de gran tamaño el termino de orden superior domina sobre el resto de términos.

## Definición

Sean $f$ y $g$ dos funciones tales que $f,g:\mathbb{N}\to \mathbb{R^{+}}$ . Decimos que $f(n) = O(g(n))$ si existen dos números enteros positivos $c$ y $n_{0}$ tales que para cada número entero $n\geq n_{0}$ entonces $f(n\leq c \cdot g(n))$

Cuando $f(n) = O(g(n))$ decimos que $g(n)$ es un límite asintótico superior para $f(n)$.

## Ejemplos

### Ejemplo 1

**Consideramos la función $f(n) =7n^4+4n^3+n^2+10n+36$.** 

Vemos que el termino de mayor orden es $7n^4$, si despreciamos el coeficiente, decimos que $f$ es asintótica como máximo en $n^4$. En notación asintóticas decimos $$f_{n} = O(n^4)$$

### Ejemplo 2

**Consideramos la función $f(n)= 3n^3+n^2+5n+6$. Calcula el límite asintótico superior para $f(n)$ y comprobar el resultado con la definición.**

Vemos que $f(n) = O(n^3)$. Para comprobar el resultado consideramos $c=4$ y $n_{0}=20$.

Vemos que $3n^3+n^2+5n+6 \leq 4n^3$ para todo $n\geq 20$.


### Ejemplo 3 - Logaritmos 

Los logaritmos son un caso interesante en notación asintótica. Cuando usamos logaritmos, debemos expresar la base, en realidad lo que estamos diciendo es:$$x=\log_{2}n \equiv 2^x = n$$
Al cambiar la base de un logaritmo, lo que estamos haciendo es cambiar el valor de ese logaritmo por un factor constante. De ahí podemos escribir:$$\log_{b}n = \frac{\log_{2}n}{\log_{2}b}$$
Por lo tanto, cuando escribimos $f(n)=O(\log n)$, en realidad no necesitamos expresar la base del logaritmo, dado que no estamos considerando factores que no sean contantes.



