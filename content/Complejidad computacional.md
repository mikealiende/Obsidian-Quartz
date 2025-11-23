# Complejidad computacional

La complejidad computacional se centra en los recursos que se necesitan para resolver una tarea dada. Podemos distinguir dos usos:

* Referido al **Algoritmo** para resolver instancias de un problema. La complejidad computacional de un algoritmo es una medida de cuantos pasos requerirá el algoritmo (en el peor de los casos) para una instancia de un tamaño dado. 
* Referido al **Problema** en sí. Clasificar los problemas de acuerdo a su con su trazabilidad o intratabilidad  inherente (si son fáciles de resolver o no).

## Medir la complejidad computacional

Sea $M$ una [[La máquina de Turing]] determinista que se para en todas sus entradas, el tiempo de ejecución o complejidad de tiempo de $M$ es la función $f:\mathbb{N} \to \mathbb{N}$, 

* Si $f(n)$ es el número máximo de pasos que $M$ usa en cada entrada de longitud $n$.
* Si $f(n)$ es el tiempo de ejecución de $M$, decimos que $M$ ejecuta en tiempo $f(n)$.


### Técnicas para medir complejidad computacional

* [[Complejidad en función del tamaño de las entradas]]
* [[Complejidad asintótica]]