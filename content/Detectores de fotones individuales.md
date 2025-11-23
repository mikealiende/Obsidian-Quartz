# Detectores de fotones individuales

Para caracterizas las [[Fuentes de fotones individuales]] y realizar medidas necesitamos ser capaces de detectar un solo fotón. Deben tener la suficiente sensibilidad para convertir el evento de llegada de un fotón en un pulso de corriente.

## Fotodetectores clásicos amplificados

En algunos casos se pueden utilizar fotodetectores normales que son amplificados hasta su punto de saturación. Los detectores de fotones individuales más modernos están diseñados específicamente para cumplir esta función. Podemos encontrar los tubos fotomultiplicadores y los fotodiodos de avalancha

### Tubos fotomultiplicadores

Son dispositivos basados en el efecto fotoeléctrico, consisten en una serie de electrodos en cascada en una ampolla de vacío con un fotocátodo expuesto al exterior. Cuando los fotones llegan al fotocátodo, arrancarán  electrones de este por efecto fotoeléctrico. Los electrones expulsados del electrodo son acelerados y conducidos al siguiente electrodo mediante diferencia de potencial.

Cada uno de estos electrones arranca por emisión secundaria un número variable de electrones que son conducidos al siguiente electrodo, serán conducidos al siguiente electrodo arrancando más electrones. Si se ponen varios electrodos en cascada, se consiguen ganancias de $16dB$.

![[Pasted image 20240626194729.png|500]]

### Fotodiodos de avalancha

En un diodo semiconductor, si se la aplica tensión en dirección inversa no se observará corriente porque este la bloquea, sin embargo, si la tensión inversa es muy elevada, cualquier electrón excitado térmicamente en el semiconductor será fuertemente acelerado por el campo eléctrico. Esto provoca que se liberan más electrones en el camino que también son acelerados lo que provoca un efecto cascada. 

Este fenómeno se llama ruptura por avalancha y suele suponer la destrucción del diodo por picos de corriente muy altos.

![[Pasted image 20240626195354.png|200]]

En la figura podemos ver como el impacto de un fotón en la región genera un par electrón-hueco que comienza la ruptura por avalancha. 

* **Diodos de avalancha**: Son diodos diseñados para soportar mayores corrientes, lo que les permite trabajar en régimen de avalancha durante un tiempo.
* **Fotodiodos de avalancha**: En estos diodos de avalancha los electrones que inician la avalancha son generados mediante la excitación por fotones.

==El problema de estos sistemas== es que después de cada evento tienen un tiempo muerto en el que no detectan nada.

## Detectores de nanohilos superconductores

Esta tecnología emergente consiste en un hilo muy largo y fino que se hace funcionar a bajas temperaturas, cerca de su corriente crítica. La absorción de un fotón es suficiente para hacerle transitar localmente del estado superconductor al no superconductor, pasando de una resistencia nula a una finita. Este cambio brusco en la resistencia provoca un pulso eléctrico.

![[Pasted image 20240628115115.png]]

La llegada del fotón produce un calentamiento local del hilo lo que provoca el aumento de resistencia al perder las propiedades de superconductividad.