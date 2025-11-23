# Puertas de cuánticas fotónicas dos qubit

Uno de los mayores impedimentos de la óptica lineal en la computación cuántica es realizar puertas de más de un qubit. Para añadir interacción entre dos haces de luz diferentes, hay que introducir algún tipo de no-linealidad que permita la interacción entre fotones.

## Medios Kerr

Una primera propuesta para realizar circuito ópticos no-lineales hacía uso de los medios Kerr. Este tipo de materiales presentan un índice de refracción $n_{kerr}$, el cual posee una componente no lineal que depende de la intensidad del haz incidente. Un haz que atraviese este medio sufrirá un cambio de fase proporcional a su intensidad.

## Medios Kerr cruzados

En estos sistemas, la fase de un haz de señal depende de la intensidad de otro haz de control que también los atraviesa. Si introducimos un medio de Kerr cruzado en interferómetro de Mach-Zehdner, como en el de la figura:
![[Pasted image 20240625191351.png|300]]
La medida a la salida del haz de control nos indicará la intensidad del haz señal. Si el cambio de fase $\tau$ es lo suficientemente intenso, podría indicarnos la presencia o ausencia de un fotón individual.

Usando esto podríamos construir una puerta CZ mediante elementos ópticos lineales y un medio de Kerr cruzado:

### Puerta CZ
Las transformaciones necesarias para una puerta CZ son:
$$\begin{align}
\hat{a}_{H}\hat{b}_{H} &\rightarrow \hat{a'}_{H}\hat{b'}_{H} \\
\hat{a}_{V}\hat{b}_{H} &\rightarrow \hat{a'}_{V}\hat{b'}_{H} \\
\hat{a}_{H}\hat{b}_{V} &\rightarrow \hat{a'}_{H}\hat{b'}_{V} \\
\hat{a}_{V}\hat{b}_{V} &\rightarrow \hat{a'}_{V}\hat{b'}_{V}\cdot e^{i\tau}
\end{align}$$

Para que esto funcione necesitamos un medio de Kerr que se cumpla que $\tau = \pi$. El problema que tienen es que los materiales cuya transparencia pueda ser modulada electromagnéticamente se han logrado valores de $\tau =10^-5$, muy lejos de nuestro objetivo.

## Átomos de cesio en cavidades ópticas

Para forzar la interacción entre dos modos de polarización de diferente frecuencia en un único fotón. Al introducir estos modos en un a cavidad con átomos de cesio es posible observar un cambio de fase que depende  del estado estado de polarización de los modos de entrada. Un diseño adecuado de estas cavidades, es capaz de amplificar pequeñas no-linealidades hasta conseguir desfase de $\pi$.

## Protocolo KLM

En los 2000,  Knill, Laflamme y Millburn demostraron que es posible hacer ordenadores cuánticos usando óptica lineal, fotones individuales y detectores de fotones. 

La base de este protocolo es el uso de medidas proyectivas con fotodetectores y las puertas de cambio de signo condicionales no deterministas, puertas $NS$. Las puertas $NS$ introducen un cambio de fase en un modo a partir de los estados de otros dos modos o qubits auxiliares. El problema de las puertas $NS$ es que al no ser deterministas, tienen una posibilidad de falla que puede llegar a ser de esta el $75\%$.

Es posible mejorar la fiabilidad de este tipo de circuitos mediante la preparación de estados entrelazados a la entrada de estos y mediante teleportación cuántica.
