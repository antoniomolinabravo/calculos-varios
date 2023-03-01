# calculos-varios
#CALCULO PI

a partir del ejemplo en libro Classic Computers Science Problems de David Kopec
https://github.com/davecom

fuente: https://github.com/davecom/ClassicComputerScienceProblemsInPython/blob/master/Chapter1/calculating_pi.py

donde presenta una solucion del tipo secuencia para calcular el numero Pi

`ej: 4/1 - 4/3 + 4/5 - 4/7 + 4/9 - 4/11 + .... - 4/1000000`

dando como resultado al millon de iteraciones: **3.14159**


se realiza propuesta de mejora al calculo

dando como resultado a las 29 iteraciones y 18 promedios: **3.1415926535897**

*la mejora realiza lo siguiente:*

- debido a que la iteracion suma y resta fracciones del numero 4 cada vez mas pequeñas, que son divisiones de numeros impares, esta ira generando por cada ciclo una diferencia hacia arriba con las sumas y hacia abajo con la resta, asi hasta aproximarse al numero final (el limite de la funcion, que en este caso el Pi)

- tras iterar una candidad pequeña definida por los parametros n_iter - n_prom, ej. 20, comienza a guardar los ultimos n_prom calculos de la iteracion

- los datos guardados seran promediados de a dos solapandose (aqui existe una diferencia entre numeros que sumaron y los que restaron en la secuencia, su promedio tiende a ser el resultado)

- luego los promedios resultantes que son uno menos que al inicio, vuelven a ser promediados y siguen iterando los promedios hasta que solo queda un numero como resultado


El Algoritmo propuesto:
+ Calcula Pi en una secuencia con promedios en cascada
+ Reduce el numero de iteraciones y aumenta la precisión rápidamente
+ Aporte realizado por Antonio Molina

Como:
- Calcula el promedio para los N últimos números de la secuencia
- a continuación calcula los promedios de los resultados
- y luego itera al siguiente nivel realizando calculando el promedio hasta que solo queda un numero

```
results:
iter, prom, error      result
  9,   6   err:5e-5    3.14153820036173
 11,   7   err:6e-6    3.1415986833943497
 29,   18  err:9e-15   3.1415926535897833
```
