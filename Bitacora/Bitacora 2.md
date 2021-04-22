# Bitácora 2
## Diseño del proyecto
El proyecto tomará un acercamiento muy similar al juego de la vida hecho originalmente por John Conway.

En nuestra simulación tendremos una población homogénea con un genoma simplificado al extremo que también dictará su comportamiento.

Nuestro genoma se caracteriza por 4 rasgos: (de 0 a 10 enteros)
fertilidad
fuerza
defensa 

Cada individuo interactúa con sus vecinos de la siguiente forma:
si el vecino es de género contrario, entonces dependiendo de su factor de fertilidad se reproducirá.
si el vecino es del mismo género luchará contra el otro y sobrevivirá dependiendo de sus rasgos
todos mueren tras 3 generaciones

Con cada nacimiento de un individuo sus rasgos serán determinados por su gen que será creado por la herencia de sus padres.
* fórmula fertilidad = (1/2)(madre)(random) + (1/2)(padre)(random)
* fórmula fuerza = (1/2)(madre)(random) + (1/2)(padre)(random)
* fórmula defensa = (1/2)(madre)(random) + (1/2)(padre)(random)
* fórmula género = random(0,1)


Las interacciones para la lucha son las siguientes:

* si fuerza1 = fuerza2 y defensa1 = defensa2 entonces sobrevive random
* si fuerza1 > fuerza2 y defensa1 = defensa2 entonces sobrevive (1)random
* si fuerza1 < fuerza2 y defensa1 = defensa2 entonces sobrevive (2)random
* si fuerza1 = fuerza2 y defensa1 > defensa2 entonces sobrevive (1)random
* si fuerza1 = fuerza2 y defensa1 < defensa2 entonces sobrevive (2)random
* si fuerza1 > fuerza2 y defensa1 > defensa2 entonces sobrevive 1
* si fuerza1 < fuerza2 y defensa1 < defensa2 entonces sobrevive 2
* si fuerza1 < fuerza2 y defensa1 > defensa2 entonces sobrevive random
* si fuerza1 > fuerza2 y defensa1 < defensa2 entonces sobrevive random

en los sobrevive random significa que uno de los dos aleatoriamente sobrevive o ninguno de los dos

La dinamica de fertilidad será la siguiente
* si fert1 + fert2 =>10, se tiene un hijo
* si fert1 + fer2 < 10, no se tiene un hijo
el hijo resultante aparecerá en algún espacio en blanco aleatorio

Esta interacción entre vecinos se dará con todos aquellos que estén ya sea a su derecha, izquierda, abajo o arriba
