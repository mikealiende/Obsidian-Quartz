# Entropia de Von Nuemann 

Se trata de la extensión del concepto de entropía para estados cuánticos. La entropía de Von Nuemann para sistemas descritos por el [[operador densidad]] es: 

Sea $\rho$ el operador densidad de un sistema cuántica, entonces definimos como la entropía de este sistema como $S$ :
$$S(\rho)=-tr(\rho \log_{2}\rho)$$
Donde $tr$ es la traza de la matriz.

Si escribimos $\rho$ en términos de autovectores y autovalores:
$$\rho=\sum_{j}\eta_{j}\ket{j}\bra{j}  $$
La expresión de la entropía queda como:
$$S(\rho) = -\sum\eta_{j}\log_{2}\eta_{j}$$
## Propiedades

* $S(\rho)$ es 0 sólo si $\rho$ representa a un estado puro.
* $S(\rho)$ es máxima e igual a $\log N$ para un estado máximamente mixto, siendo $N$ la dimensión del estado de Hilbert.
* $S(\rho)$ es invariante bajo cambios de base de $\rho$, es decir $$S(\rho)=S(U\rho U^{\dagger})$$


