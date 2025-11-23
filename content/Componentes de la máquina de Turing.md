# Componentes de la máquina de Turing

Los componentes de una máquina de Turing son:

* **Controlador de estados finitos.**
* **Una cinta** infinita dividida en celdas, cada celda contiene un símbolo.
* Un **cabezal de lectura/escritura** que:
	* Esta posicionado en una celda específica
	* Puede leer un símbolo de esa celda y suministrarlo al controlador como entrada.
	* Puede aceptar un símbolo del controlador y lo inserta en esa celda.
	* Puede aceptar una instrucción del controlador para mover la celda a la derecha o izquierda de la posición actual.

El movimiento de una maquina de Turing depende de el estado actual del controlador y el símbolo debajo del cabezal de lectura/escritura

En respuesta a las entradas, la maquina de Turing puede:

* Cambiar el estado del controlador.
* Escribir un símbolo en la celda actual de la cinta (reemplazando lo que había).
* Mover el cabeza a izquierda o derecha.
* Dejar el estado sin cambios 