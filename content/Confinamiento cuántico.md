# Confinamiento cuántico

En un material conductor, los portadores de carga son libres de moverse en 3 dimensiones del espacio y sus propiedades se pueden aproximar con modelos de electrones libres.

## Densidad de estados 

Esta densidad de estados representa el número de estados electrónicos disponibles por unidad de volumen. Los podemos calcular de la siguiente manera

Para los metales utilizamos al [[Energía de Fermi]] como la energía cinética del estado ocupado de mayor energía a 0K. También necesitamos calcular la [[Energía cinética electrones libres]]. A partir de estas dos energías, podemos calcular la **==densidad de estados de un gas de electrones libres a una energía==** dada de esta forma:
$$g(E)_{3D} = \frac{m_{e}}{\pi^2\hbar^3}\sqrt{ 2m_{e}E} = \frac{3n}{2E_{F}}\sqrt{ \frac{E}{E_{F}} }$$


Siendo $E_{F}$ la [[Energía de Fermi]] y $E$ la [[Energía cinética electrones libres]]. También podemos expresar esta densidad de estados en función del fondo de la banda de conducción, $E_{c}$, de un semiconductor:
$$g(E)_{3D} = \frac{m_{e}}{\pi^2\hbar^3}\sqrt{ 2m_{e}(E-E_{c}) }$$


En los materiales de 3 dimensiones, con tamaños mucho mayores a la longitud de onda de los electrones, la relación entre densidad de estados y energía presenta relación cuadrática.

### Pozo cuántico

Si reducimos las dimensiones espaciales del material a tamaños comparables a longitudes de onda del electrón, los portadores de carga pierden un grado de libertad al no poder escapar del material en esa dirección. Esto implica que los niveles de energía están cuantizados en la dirección de la dimensión reducida, pero conservan su libertad de movimiento en el plano perpendicular. 

Esta estructura es el pozo cuántico, y su densidad de estados no depende la energía:

$$g(E)_{2D}= \frac{m}{\pi \hbar^2}$$
### Hilo cuántico

Si en vez de reducir una dimensión, reducimos dos de ellas, los portadores estarán forzados a moverse en una estructura unidimensional, lo que llamamos hilo cuántico, y su densidad de estados viene dada por:
$$g(E)_{1D}= \frac{1}{\pi \hbar }\sqrt{ \frac{m}{2(E-E_{c})} }$$
### Punto cuántico 

Si reducimos otra dimensión más, los electrones no tiene ningun grado de libertad de movimiento, y su energía queda totalmente cuantizada a los niveles discreto dados por su geometría. Esta estructura es el punto cuántico, y su densidad de estados viene dada por:
$$g(E)_{0D} = 2\delta (E-E_{c})$$

De esta manera como los electrones se encuentran confinados en un lugar del espacio presentan un espectro de energía discreto, muy similares a los espectros de un átomo, por lo que a veces se les llama "átomos artificiales". Como podemos localizar los electrones en una región muy pequeña y sus energías están limitadas a a una cantidad de estados discretos. de esta manera, las transiciones entre estados seguirán dinámicas similares a los átomos: absorber energía electromagnética para promocionarse a [[Estado excitado]], emitir energía y decaer al [[Estado fundamental]], lo que nos permite manipular sus estados electrónicos.

![[Pasted image 20240602120520.png]]