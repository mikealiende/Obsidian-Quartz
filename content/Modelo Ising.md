# Modelo Ising

Modelo que utiliza variables binaras del conjunto $z \in \{-1,1\}$ en vez de variables booleanas. El 0 booleano es el 1 en Ising y el 1 booleano es el -1 Ising, la conversión es:

$$x_{i} = \frac{1-z_{i}}{2}$$



## Definir función objetivo con Hamiltoniano

Para trabajar con este tipo de problemas vamos a trabajar con el [[Modelo Ising]] por ejemplo vamos a suponer un sistema de dos variables $f(x_{i},x_{j})$ entonces vamos a definir el siguiente Hamiltoniano.

$$H = 
\begin{pmatrix}
  f(1,1) & 0 & 0 & 0 \\
  0 & f(1,-1) & 0 & 0 \\
  0 & 0 & f(-1,1) & 0 \\ 
  0 & 0 & 0 & f(-1,-1)
\end{pmatrix}
$$
Nos gustaría encontrar lo siguiente:
 $$\bra{z_{1},z_{2}}H \ket{z_{1},z_{2}} = f(z_{1},z_{2})  $$
En nuestro ejemplo, si queremos obtener $f(-1,1)$ lo que haremos será $\bra{10}H \ket{10} = f(-1,1)$



## Descomponer  exponencial de Hamiltoniano tipo Ising como puertas de Pauli

Veremos como podemos construir $e^{iH}$ como puertas de Pauli $\sigma_{z}$, para utilizarlo en algoritmos cómo [[QAOA]].

Siendo H:
$$H = \sum_{i=1}^{n} \alpha_{i} \sigma_{i}^{z} + \sum_{i=1}^{n} \sum_{j=1}^{n}\beta_{i,j}\sigma_{i}^{z}\sigma_{j}^{z}$$
De esta manera definimos $e^{iH}$ como: 

$$e^{H} = \exp\left( \sum_{i=1}^{n} \alpha_{i} \sigma_{i}^{z} + \sum_{i=1}^{n} \sum_{j=1}^{n}\beta_{i,j}\sigma_{i}^{z}\sigma_{j}^{z} \right) = \prod_{i=1}^{n}e^{i \alpha_{i}\sigma_{i}^z}+  \prod_{i,j=1}^{n}e^{i \alpha_{i}\sigma_{i}^z \sigma_{j}^z}$$
De esta manera para construir el Hamiltoniano, solo nos hará falta construir $\exp(it \sigma_{i}^z)$ y $\exp(it \sigma_{i}^z \sigma_{j}^z)$. Sabiendo que la exponencial de una matriz diagonal es igual a la exponencial de cada uno de sus elementos tenemos:

### Construir $\exp(it \sigma_{i}^z)$

$$\exp(it \sigma_{i}^z) = \begin{pmatrix}
e^{it} & 0 \\
0 & e^{-it}
\end{pmatrix} = e^{-it}\begin{pmatrix}
1 & 0 \\
0 & e^{-2it}
\end{pmatrix}$$
En particular esta expresión corresponde con la puerta $R_{z}$ aplicando una rotación de $-2t$ radianes.

![[Pasted image 20240512111736.png]]

### Construir $\exp(it \sigma_{i}^z \sigma_{j}^z)$

Para este caso necesitamos conocer estas propiedades:

* Si una matriz es $P$ cumple que $P^2 =I$ (lo cumplen todas las puertas de Pauli), se cumple que :
	* $$e^{iPt} = \cos(t)I + \sin (t)P$$
* La puerta CNOT se puede expresar como:
	* $$CNOT = \ket{0}\bra{0} \otimes I + \ket{1}\bra{1}\sigma^x     $$

Jugando con estas propiedades obtenemos:
$$e^{it\sigma^z \sigma^z} = \cos(t)I + \sin (t)\sigma^z \otimes \sigma^z$$


Que si lo relacionamos con la definición de CNOT obtenemos el siguiente circuito:

![[Pasted image 20240512112556.png]]


De esta manera hemos construido la exponencial del Hamiltoniano con puertas cuánticas unitarias. 