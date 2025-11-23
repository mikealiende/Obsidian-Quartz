# Puertas de rotación QAOA

Explicaremos dos puertas unitarias que utilizaremos en el algoritmo QAOA, que son $U(C,\gamma)$ y $U(B,\beta)$.

## $U(C,\gamma)$. Rotación en Z

$$U(C,\gamma) = e^{-iC\gamma} = e^{-i\gamma \sum_{i=1}^{m}C_{{i}}} = \prod_{i=1}^{m}e^{-i\gamma C_{i}}$$
Existe una relación entre C y  el Hamiltoniano tipo Ising, por lo tanto podemos descomponer C utilizado puertas de Pauli Z $\sigma_{z}$. Por lo tanto, ==podemos aprovechar la descomposición de la exponencial Hamiltoniano tipo Ising para construir la puerta  $U(C,\gamma)$, ya que serán iguales.==
![[Modelo Ising#Descomponer exponencial de Hamiltoniano tipo Ising como puertas de Pauli]]



## $U(B,\beta)$. Rotación en X

Siendo:
$$B = \sum_{i=1}^m \sigma_{i}^x$$


Podemos definir: 
$$U(B,\beta) = e^{-i\beta B} = \prod_{i=1}^n e^{-i\beta \sigma_{i}^x}$$

Vamos a hacerlo lo mismo que para la otra puerta pero utilizando la propiedad $H\sigma^z H = \sigma^x$ siendo $H$ la puerta de Hadamard.[[Puertas cuánticas#Puerta Hadamard (H)]]. Tenemos que:

$$e^{it\sigma^x} = \cos(t)I + i\sin(t)\sigma^x = \cos(t)I + i\sin(t)H\sigma^z H = HR_{z}H = R_{X}$$
Por lo tanto la puerta $U(B,\beta)$ es equivalente a una puerta $R_{x}(-2\beta)$
