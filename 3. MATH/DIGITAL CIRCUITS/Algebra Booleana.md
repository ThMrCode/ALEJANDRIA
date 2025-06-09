Dado una tabla de verdad que relaciona todas las combinaciones de los bits de entrada con los respectivos bits de salida, se busca hallar la función booleana para cada bit de salida, y reducirla.

El método general consiste en que cada numero tiene una función booleana asociada, por ejemplo.
$$
f(101) = 1 \to f(n) = A\hat{B}C
$$
Entonces la función booleana será la suma de todas estas funciones.
$$
F(X) = \sum{f(n_i)}
$$
El objetivo es reducir esta expresión por artificios.

Sistemas de integracion de mediana escala msi



Sumador completo, y semisumador con bit de acarreo



74LS283