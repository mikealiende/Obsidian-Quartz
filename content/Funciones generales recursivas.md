 Funciones generales recursivas

Son funciones parciales que toman tuplas finitas de números naturales y devuelven un solo número natural. Toman su nombre del proceso de recursividad, que hace que que el valor de una función se defina mediante la aplicación de la misma función a argumentos más pequenos.

## Ejemplo

Una función factorial sería: 

```
fact(0)=1
fact(x+1) = fact(x+1)*fact(x)

```


## Recursión en la computación

La recursión es muy usuda en la computación. Permite resolver problemas en los que la solución depende de soluciones a instancias más pequeñas del mismo problema. Estos problemas se suelen resolver mediante iteración, para ellos se usan funciones que se llaman a si mismas.