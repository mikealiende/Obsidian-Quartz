# Canales de comunicación y capacidad de compresión

![[Pasted image 20240218182356.png]]


### Medida de sorpresa

Sea X una variable aleatoria con la distribución que hemos utilizado antes, una medida de sorpresa del símbolo X es:
![[Pasted image 20240218182528.png]]

La medida de sorpresa tiene la propiedad deseable de que es mayor para los sucesos de menor probabilidad y menor para los eventos de mayor probabilidad.

Es aditiva, si una fuente de información emite los símbolos x1 y x2 --> i(x1,x2) = i(x1) + i(x2)

### Entropia de fuente de información

![[Pasted image 20240218182913.png]]


### Ratio de compresión

![[Pasted image 20240218183100.png]]


Es igual a la entropía 𝐻(𝑋) dado que el número de bits transmitidos por el canal es igual a 𝑛𝐻(𝑋). El ratio de compresión que indicamos es el considerado como óptimo, si bien se pueden conseguir ratios de compresión superior. Calificarlo de óptimo significa, en el fondo, minimizar la probabilidad de pérdida de información.