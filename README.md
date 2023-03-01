# CALCULO PI

A partir del ejemplo en libro Classic Computers Science Problems de David Kopec
https://github.com/davecom

fuente: https://github.com/davecom/ClassicComputerScienceProblemsInPython/blob/master/Chapter1/calculating_pi.py

Donde presenta una solución del tipo secuencia para calcular el número Pi

`ej: 4/1 - 4/3 + 4/5 - 4/7 + 4/9 - 4/11 + .... - 4/1000000`

dando como resultado tras el **1 millon** de iteraciones: **3.14159**

Se realiza propuesta de mejora al cálculo

dando como resultado a las 29 iteraciones y 18 promedios: **3.1415926535897**

## Mejoras del Algoritmo propuesto:
+ Calcula Pi en una secuencia con promedios en cascada.
+ Reduce considerablemente el número de iteraciones y aumenta la precisión rápidamente.
+ Aporte realizado por Antonio Molina.

## Como:
- Calcula el promedio para los N últimos números de la secuencia.
- A continuación calcula los promedios de los resultados de a pares solapados, reduciendo la cantidad de resultados en uno.
- Luego itera al siguiente nivel realizando cálculo del promedio de la misma forma hasta que solo queda un número.

## Que ocurre ?

- Debido a que la iteración suma y resta fracciones del número 4 cada vez más pequeñas, que son divisiones de números impares, esta ira generando por cada ciclo una diferencia hacia arriba con las sumas y hacia abajo con las restas, así hasta aproximarse al número final, el límite de la función, que en este caso el Pi

- Lo que se plantea es promediar estas diferencias que se generan al tirar hacia arriba y hacia abajo, llegando más rápido al resultado

- El truco esta en realizar promedios solapados únicamente de a pares, aprovechando la diferencia entre un numero sumado y uno restado, luego el restado con el siguiente sumado y así sucesivamente, cada par dará una aproximación al número limite, si se promedia un set de *N* números, con sus resultados obtendremos *N-1* números, cada vez perderemos un número y seguir así hasta que solo queda un número, este será la aproximación más cercana que podremos tener con muy pocas iteraciones

## Algoritmo:

- Tras iterar una cantidad pequeña definida por los parámetros *n_iter - n_prom*, ej. 20, comienza a guardar los últimos *n_prom* cálculos de la iteración.

- Los datos guardados serán promediados de a dos solapándose (aquí existe una diferencia entre números que sumaron y los que restaron en la secuencia, su promedio tiende a ser el resultado).

- Luego los promedios resultantes que son uno menos que al inicio, vuelven a ser promediados y siguen iterando los promedios hasta que solo queda un número como resultado.

## Resultados:
```
Pi = 3.141592653589793

iter, prom, error,     result
   9,   6   err:5e-5   3.1415 3820036173 
  11,   7   err:-6e-6  3.14159 86833943497       <-  el original requirio 1 millon de iter para alcanzar esto
  13,  10   err:5e-7   3.141592 1043704067 
  16,   9   err:3e-8   3.1415926 186270062 
  17,  11   err:-6e-9  3.14159265 9926378
  20,  11   err:4e-10  3.141592653 10039 
  21,  14   err:6e-11  3.1415926535 244623
  23,  14   err:9e-12  3.14159265358 0177 
  25,  18   err:7e-13  3.141592653589 0586
  27,  18   err:7e-14  3.1415926535897 16
  29,  18   err:9e-15  3.14159265358978 33
```

- El resultado de 9 iteraciones en la serie y los últimos 6 números promediados nos da un resultado de 3,1415 clásico.
- Con 11 iteraciones y 7 promedios alcanzamos un digito más.
- Pero con solo 29 iteraciones y 18 promedios logramos un número con bastante precisión de 14 dígitos 3.1415926535897.

## Conclusión:
Merece al menos un análisis la optimización del esfuerzo computacional, hay una gran reducción y permitirá alcanzar una muy alta precisión con muy poco esfuerzo, aunque sabemos que PI es una constante conocida en todo entorno de desarrollo, es la solución del problema la que se plantea, como si estuviéramos en la era pre computadoras, darse cuenta de estos detalles hubiesen permitido un gran avance.
