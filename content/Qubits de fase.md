# Qubits de fase

Un qubit de fase (Martinis et al., 2002) consiste básicamente en una una unión Josephson por la que pasa una corriente polarizada. Las componentes inductiva y capacitiva de la uni ́on Josephson hace que este circuito se comporte como resonador LC no armónico, donde el estado en reposo y el primer estado excitado de energía conformarán los dos estados del qubit. Normalmente la corriente polarizada que pasa por la uni ́on es muy cercana a la corriente crítica Ic, por lo tanto el potencial no armónico se puede aproximar con un potencial cúbico y el espectro de energía tiene esta forma:


![[Pasted image 20240512194452.png]]


Para pedir un el estado de un qubit de fase hacemos uso de pulsos de microondas y de un dispositivo que llamado SQUID(superconducting quantum interference device), que es un magnetómetro muy preciso basado en el efecto Josepshon de corriente continua. Como se ilustra en la figura, si aplicamos un pulso de microondas de frecuencia $\omega_{21}$ cuando el qubit está en $\ket{1}$, pasará al siguiente estado excitado $\ket{2}$, lo que provoca que aparezca una tensión $(v)$ en el SQUID acoplado al circuito, y ahí tendremos nuestro ’1’. En cambio, si el estado del qubit es $\ket{0}$, el pulso de microondas no hará que salte al siguiente estado excitado, y no aparecerá ninguna tensión en el SQUID, por lo tanto será nuestro ’0’.