# Variational Quantum Eigensolver #Tema 

Se trata de un algoritmo mixto que utiliza computadores cuánticos y clásicos para encontrar el [[Estado fundamental]] de un sistema físico dado. El algoritmo funciona así: dado un [[ansatz]], el procesador cuántico calcula el valor esperado de un [[Observables]], generalmente el Hamiltoniano, y posteriormente un optimizador clásico mejora el ansatz para repetir el proceso hasta encontrar el valor mínimo.

## Relación con problemas QUBO

Los [[Problemas QUBO]] cuyas variables son binarias $\vec{x}$, tratan de minimizar una función objetivo $f(\vec{x})$. Podemos decir que esta función objetivo es la energía del problema y que nuestra tarea es encontrar el vector $\vec{x}$ que minimice la energía. El hamiltoniano es el [[Operadores]] que representa la energía de un sistema. Los posibles valores de energía de un sistema vienen dados por los valores propios del Hamiltoniano:

$$H \ket{\phi} = E_{{\phi}}\ket{\phi}$$
Siendo $\ket{\phi}$ un estado propio del sistema y $E_{\phi}$ el autovalor que representa la energía asociada a dicho estado.

Definimos el valor esperado de un estado $\ket{\phi}$ como $\bra{ \phi}H\ket{\phi}$. Lo que estamos haciendo es una ponderación de las energías de los estados propios que forman $\ket{\phi}$ con la probabilidad que tenemos de observar cada uno de ellos: 
$$\bra{ \phi}H\ket{\phi} = \left( \sum_{i}^{n}\bra{u_{i}}\alpha_{i}^{*}  \right) H \left( \sum_{i}^{n}\alpha_{i}\ket{u_{i}} \right)= \sum_{i}^{n}  |\alpha_{i}|^{2}E_{ui}$$


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
En nuestro ejemplo, si queremos obtener $f(-1,1)$ lo que haremos será $\bra{10}H \ket{10} = f(-1,1)$.

De esta manera, parametrizando los estados, debemos calcular para que estado arbitrario el resultado es mínimo. $\bra{\psi(\theta)}H\ket{\psi (\theta)}$. Entonces lo que hacemos es probar con los distintos valores de $\theta$ para encontrar que estado minimiza el Hamiltoniano del sistema. Por lo tanto, el siguiente paso es poder introducir este Hamiltoniano como una función objetivo en el computador cuántico.

## Descomponer Hamiltoniano en puertas unitarias

Vamos a a tomar un Hamiltoniano puede ser descrito como:
$$H = \sum_{i=1}^{n} \alpha_{i} z_{i} + \sum_{i=1}^{n} \sum_{j=1}^{n}\beta_{i,j}z_{i}z_{j}+ \cdots$$
Nos vamos a quedar con la parte solo la parte lineal y cuadrática, por lo tanto necesitamos poder descomponer $z_{i}$ y $z_{i}z_{j}$ en puertas cuánticas:

#### Descomponer $z_{i}$

Lo que vamos a hacer ahora es definir representar el Hamiltoniano como puertas cuánticas, para ilustrar esto vamos a usar el ejemplo más sencillo $f(z_{1}) =z_{1}$ . Buscamos entonces H tal que: $\bra{0}H\ket{0} = 1$ y $\bra{1}H\ket{1} = -1$. En este caso particular vemos que la puerta Z cumple con esta condición, con lo que es suficiente para definir H. De esta manera, en este caso podemos escribir H como: $$H =I \otimes I\otimes \cdots\otimes Z\otimes \cdots\otimes I\otimes I$$
Todo puertas $I$ excepto una puerta $Z$ en la posición i-esima. Se puede demostrar calculando el valor esperado:
$$\begin{align}
\bra{z_{1},\dots,z_{i},\dots z_{n}}&H \ket{z_{1},\dots,z_{i},\dots z_{n}} = \\
\bra{z_{1},\dots,z_{i},\dots z_{n}} I \otimes I\otimes \cdots\otimes &Z\otimes \cdots\otimes I\otimes I\ket{z_{1},\dots,z_{i},\dots z_{n}} = \\
\bra{z_{1}}I\ket{z_{1}}\dots \bra{z_{i}}&Z\ket{z_{i}}\dots \bra{z_{n}}I\ket{z_{n}}= \\
\bra{z_{i}}&Z\ket{z_{i}}        
\end{align}$$
#### Descomponer $z_{i}z_{j}$

Hacemos lo mismo para una función $f(\vec{z})=z_{i}z_{j}$, y llegamos a la conclusión de que el Hamiltoniano que describe esta función objetivo es el producto tensorial de todo puertas $I$ excepto una puerta $Z$ en la i-ésima posición y otra en la j-ésima posición.

#### Ejemplo

Queremos calcular la energía de la función objetivo $f(z_{1},z_{2}) = 2z_{1}-3z_{1}z_{2}$ para el estado $z_{1}=1$ y $z_{2}=-1$. Si expresamos la función objetivo como un Hamiltoniano descompuesto en puertas. $Z$, tenemos:
$$f(1,-1)=2\bra{01}Z\otimes I\ket{01} - 3\bra{01}Z\otimes Z\ket{01}    $$

Por último, lo único que nos queda definir es como calcular $\bra{\psi}Z_{i}\ket{\psi}$ y $\bra{\psi}Z_{i}Z_{j}\ket{\psi}$ en un ordenador cuántico para cualquier estado $\psi$, para así saber que estado minimiza la energía y por lo tanto será nuestra solución.
El hecho de poder encontrar un equivalente del Hamiltoniano radica en que podemos calcular de manera eficiente el valor esperado de un estado con un computador cuántico. Por lo tanto la manera de resolver estos problema será **==calculando nuestro Hamiltoniano y descomponerlo en puertas cuánticas unitarias==**.


## Calcular $\bra{\psi}Z_{i}\ket{\psi}$ y $\bra{\psi}Z_{i}Z_{j}\ket{\psi}$

Calcular estas expresión consiste en calcular el valor esperado. En el caso $\bra{\psi}Z_{i}\ket{\psi}$ lo que hacemos es medir en el i-ésimo qubit y restar la probabilidad de observar el qubit en 0 menos la probabilidad de observarlo en 1. Esto es así porque los autovectores de $Z$ coinciden con la base computacional $\{\ket{0},\ket{1}\}$.:
$$\bra{\psi}Z_{i}\ket{\psi} = P(\ket{0}_{i}) - P(\ket{1}_{i} )$$
Para el caso $\bra{\psi}Z_{i}Z_{j}\ket{\psi}$ tenemos:
$$\bra{\psi}Z_{i}Z_{j}\ket{\psi}= P(\ket{00}_{i,j})+P(\ket{11}_{i,j})-P(\ket{01}_{i,j})-P(\ket{10}_{i,j})$$

Siendo por ejemplo, $P(\ket{01}_{i,j})$ la probabilidad de encontrar el qubit i-ésimo en el estado 0 y el j-ésimo en el estado 0.

De esta manera tenemos todos las herramientas necesarias para el VQE
## Desarrollo del Algoritmo VQE
Esta algoritmo se es variacional, es decir, definiremos un estado inicial que irá cambiando a lo largo del tiempo con la idea de ir reduciendo su energía. Para ello utilizaremos una serie de puertas ($R_{z}, R_{x}, R_{y}$) que dependen de ciertos parámetros que iremos modificando para generar el estado óptimo.

![[Pasted image 20240506185705.png|300]]

1. Definimos los valores $\vec{\alpha}$ del [[ansatz]] para crear nuestro estado inicial $\ket{\psi}$.
2. Calculamos la energía que tiene dicho estado definido por el Hamiltoniano utilizado el proceso utilizado en [[#Definir función objetivo con Hamiltoniano]].
3. Calculamos el resultado obtenido midiendo y  utilizamos un optimizador clásico para optimizar los valores $\vec{\alpha}$ y aplicar de nuevo el procedimiento para ir reduciendo la energía.

Se trata de un proceso totalmente a ciegas, donde solo tendremos la información correspondiente a los estados que hemos evaluado.
[[Ejemplo VQE con PennyLane]]
