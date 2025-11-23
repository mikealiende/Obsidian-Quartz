# Cálculo Lambda

El cálculo lambda es un lenguaje de programación muy sencillo. Consta de una única regla de transformación(transformación de variables) y un esquema de definición de función única. El concepto centra de este cálculo consiste en construir términos lambda y realizar operaciones de reducción de ellos.

Se basa en que sólo podemos hacer dos acciones: abstracción y aplicación:
* **Abstraer**: Definir una función. Por ejemplo, una función para doblar la variable $x$ sería $\lambda x. 2 * x. \lambda x$
* **Aplicar**: Usar la función en un valor específico. Si nuestra función es $\lambda x. 2*x$ y le damos el valor 3, tenemos $(\lambda x. 2*x)3 = 6$.

En esencia manipulamos funciones como si fueran datos. Se pueden pasar funciones a otras funciones, crear funciones que devuelven nuevas funciones, etc...

## Ejemplo

Una función que suma dos números $\lambda x. \lambda y. x+y$. Primero abstraemos sobre $x$ y luego sobre $y$. Si por ejemplo queremos calcular 2+3:

1. Aplicamos dos veces: $((\lambda x. \lambda y. x+y)2)3$ 
2. Esto se reduce a: $(\lambda y. 2+y)3$
3. 2+3 = 5



