# Limitaciones EVA

Como hemos visto en [[Cota al error en la estimación EVA]], al elegir un valor $k$ tan grande como queramos, pero veremos porque esto no es así.

El motivo es porque estamos estimando $\frac{\bra{\phi}H\ket{\phi}}{k}0$, en lugar de $\bra{\phi}H\ket{\phi}$, y si queremos conseguir la misma precisión, el numero de shot que tenemos que realizar aumenta en un factor $k^2$. Por lo tanto tenemos un compromiso a la hora de elegir el factor $k$ entre precisión y número de shots necesarios.

El gran inconveniente de este algoritmo es que la puerta exponencial esta formada por un gran número de puertas CNOT,. Por lo tanto al hacer el control sobre la exponencial, esas puertas se convertirán en puertas Toffoli, que tiene un error asociado muy alto. Para solucionar este problema está el algoritmo **EVA reducido**.

