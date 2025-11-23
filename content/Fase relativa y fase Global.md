# Fase relativa y fase global


## Fase Global

Un mismo  estado cuántico puede estar representado por más de un vector en el espacio de estados, por lo tanto existe una diferencia fundamental entre entre el [[Espacio de Hilbert]] que describe el qubit y el espacio de estados. Queda cierta ambigüedad, dos vectores unitarios equivalentes representan el mismo estado. ==El múltiplo por el cual dos vectores que representan en mismo estado cuántico se diferencian se conoce como fase global==

![[Pasted image 20250108195020.png|500]]

Usamos la relación de equivalencia $\ket{v}\sim \ket{v'}$ para indicar que $\ket{v} = c\ket{v'}$ para cualquier fase global compleja $c=e^{i\psi}$.  

Los estados de un qubit se representan en un espacio de Hilbert de dimensión 2($\mathbb{C}^2$). sin embargo, dos vectores que son múltiplos escalares representan el mismo estado cuántico. Esto implica que ==los estados físicos del qubit están en un espacio proyectivo complejo de dimensión 1 $\mathbb{CP}^1$.== De esta manera todos los vectores equivalentes(múltiplos escalares) en $\mathbb{C}^2$ representan al mismo estado a nivel físico en $\mathbb{CP}^1$. De esta manera demostramos que ==la fase global no tiene un significado físico== (no se detecta experimentalmente, ni influye en las probabilidades ) y puede ser obviada y que lo importante de la representación del estado un qubit como un vector de $\mathbb{C}^2$ es su dirección y no su magnitud.

## Fase relativa

La fase relativa si que tiene si que tiene un significado físico. En un sistema descrito por la superposición $a\ket{0}+b\ket{1}$ es una medida del ángulo en el plano complejo entre los números complejos $a$ y $b$. 

De forma más precisa, la fase relativa es el número complejo $e^{i\psi}$ de módulo 1, que satisface:$$\frac{a}{b}=e^{i\psi}\frac{|a|}{|b|}$$

Dos superposiciones cuyas amplitudes tienen la misma magnitud, pero distinta fase relativa, corresponden a estados diferentes. Es decir $$\frac{1}{\sqrt{ 2 }}(e^{i\psi}\ket{v_{1}}+\ket{v_{2}}) \text{ y }\frac{1}{\sqrt{ 2 }}(\ket{v_{1}}+\ket{v_{2}}) $$
No representan el mismo estado.