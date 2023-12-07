### ACTIVIDAD 6 - FLAVIUS JOSEPHUS
### VILLASEÑOR CORNEJO RODRIGO SEBASTIAN

# PROBLEMA MATEMÁTICO DE FLAVIUS JOSEPHUS

## Introducción

En esta sexta actividad se trabajará el pensamiento matemático mediante un conocido problema que existe desde hace muchos años y hoy por hoy se puede resolver desde el ámbito de la programación, Se lo conoce con el nombre del “Problema de Josephus”, ya que se supone que fue Flavius Josephus, un historiador judío nacido en Jerusalén, quien describió la situación que vivieron él y 40 soldados que lo acompañaban allá por el siglo I de nuestra era.

Supongamos que hay n personas numeradas de 1 a n alrededor de un círculo. Comenzando desde una posición inicial, cada k-ésima persona es eliminada del círculo hasta que queda solo una persona. El objetivo es determinar la posición de la última persona que permanece en el círculo.

Para ilustrar con un ejemplo específico, en esta actividad consideremos el caso donde hay 41 personas en un círculo y se elimina cada 2ª persona. El proceso sería el siguiente:

Comenzamos en la posición 1 y eliminamos la 2ª persona (1, 2, 3).

Luego, comenzamos en la posición 3 y eliminamos la 2ª persona (4, 5, 6).

Continuamos este proceso hasta que queda solo una persona.

La solución al problema de Flavio Josefo con 41 personas y eliminando cada 2ª persona sería que la última persona que queda es la que inicialmente estaba en la posición 19.

El problema de Flavio Josefo tiene aplicaciones en teoría de números y es un ejemplo clásico de cómo se pueden abordar problemas de eliminación cíclica. La fórmula general para determinar la posición de la última persona en función de n y k se conoce como la función de Josephus y puede expresarse matemáticamente.

<div style="text-align:center;"> <img src="https://www.elcohetealaluna.com/wp-content/uploads/2018/03/Screenshot-2018-03-05-11.07.18-e1520378491341.png
"> </div>

## Desarrollo

Conociendo el funcionamiento general del juego se puede comenzar a obtener deducciones sobre la resolución del problema, comenzando desde un punto de partida de pocos jugadores para visualizar cómo funciona la formula.

- Tendremos que un jugador vivo es = 🟢
- Mientras que un jugador muerto será = ❌

**Deducción 1:**
>Comenzaremos por empezar a ver cómo se comporta el sistema propuesto a partir de 3 jugadores, ya que sería lo mínimo necesario si estamos teniendo en cuenta que se va a eliminar a la 2ª posición, lo cual, gráficamente explicado se vería de la siguiente manera.

> Con 3 participantes:

- Inicio: 1🟢 2🟢 3🟢
- Paso 1: 1🟢 2❌ 3🟢 (1 mata 2)
- Paso 2: 1❌ 2❌ 3🟢 (3 mata 1)

> Con 5 participantes:

- Inicio: 1🟢 2🟢 3🟢 4🟢 5🟢
- Paso 1: 1🟢 2❌ 3🟢 4🟢 5🟢 (1 mata 2)
- Paso 2: 1🟢 2❌ 3🟢 4❌ 5🟢 (3 mata 4)
- Paso 3: 1❌ 2❌ 3🟢 4❌ 5🟢 (5 mata 1)
- Paso 4: 1❌ 2❌ 3🟢 4❌ 5❌ (3 mata 5)

>Con 7 participantes:

- Inicio: 1🟢 2🟢 3🟢 4🟢 5🟢 6🟢 7🟢
- Paso 1: 1🟢 2❌ 3🟢 4🟢 5🟢 6🟢 7🟢 (1 mata 2)
- Paso 2: 1🟢 2❌ 3🟢 4❌ 5🟢 6🟢 7🟢 (3 mata 4)
- Paso 3: 1🟢 2❌ 3🟢 4❌ 5🟢 6❌ 7🟢 (5 mata 6)
- Paso 4: 1❌ 2❌ 3🟢 4❌ 5🟢 6❌ 7🟢 (7 mata 1)
- Paso 5: 1❌ 2❌ 3🟢 4❌ 5❌ 6❌ 7🟢 (3 mata 5)
- Paso 6: 1❌ 2❌ 3❌ 4❌ 5❌ 6❌ 7🟢 (7 mata 3)

>Con 11 participantes:

- 1🟢 2🟢 3🟢 4🟢 5🟢 6🟢 7🟢 8🟢 9🟢 10🟢 11🟢
- 1🟢 2❌ 3🟢 4🟢 5🟢 6🟢 7🟢 8🟢 9🟢 10🟢 11🟢 (1 mata 2)
- 1🟢 2❌ 3🟢 4❌ 5🟢 6🟢 7🟢 8🟢 9🟢 10🟢 11🟢 (3 mata 4)
- 1🟢 2❌ 3🟢 4❌ 5🟢 6❌ 7🟢 8🟢 9🟢 10🟢 11🟢 (5 mata 6)
- 1🟢 2❌ 3🟢 4❌ 5🟢 6❌ 7🟢 8❌ 9🟢 10🟢 11🟢 (7 mata 8)
- 1🟢 2❌ 3🟢 4❌ 5🟢 6❌ 7🟢 8❌ 9🟢 10❌ 11🟢 (9 mata 10)
- 1❌ 2❌ 3🟢 4❌ 5🟢 6❌ 7🟢 8❌ 9🟢 10❌ 11🟢 (11 mata 1)
- 1❌ 2❌ 3🟢 4❌ 5❌ 6❌ 7🟢 8❌ 9🟢 10❌ 11🟢 (3 mata 5)
- 1❌ 2❌ 3🟢 4❌ 5❌ 6❌ 7🟢 8❌ 9❌ 10❌ 11🟢 (7 mata 9)
- 1❌ 2❌ 3❌ 4❌ 5❌ 6❌ 7🟢 8❌ 9❌ 10❌ 11🟢 (11 mata 3)
- 1❌ 2❌ 3❌ 4❌ 5❌ 6❌ 7🟢 8❌ 9❌ 10❌ 11❌ (7 mata 11)

Si continuamos con esta sucesión de resultados obtenidos a través de realizar pruebas de supervivencia unas tras otras aumentando el número de jugadores, podremos notar que pronto se llegaría a un patrón escalable, pues con 17 jugadores ya podemos ver como vuelve a comenzar dicha sucesión de resultados.

| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 |
|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|----|----|
| 1 | 1 | 3 | 1 | 3 | 5 | 7 | 1 | 3 | 5 | 7 | 9 | 11 | 13 | 15 | 1 | 3 |

**Deducción 2:**
>Para este punto, al analizar la tabla de resultados y revisar los supervivientes que se obtienen, ya hay cierto patrón que es de 2 en 2, esto siempre y cuando no caiga en un exponente de 2, ya que al caer en un exponente de 2 se reinicia la cuenta a 1, dando vuelta al ciclo.

**Deducción final:**
>Considerando que el problema tiene una sucesión creciente de manera exponencial, podemos comenzar a programar una solución con una función dada según el problema matemático. Esto en realidad es bastante sencillo, pues para el cálculo de la persona que será eliminada tendremos una formula como la siguiente:

<div style="text-align:center;"> <img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/fd4a1f796181ff160f2a353cb6d4aaa3edaa767f"> </div>

Que en cuestiones de código en Python se vería del modo siguiente:

~~~
idx = (idx + k - 1) % len(personas)
~~~

> A su vez esto entraría dentro de un ciclo que podría estar eliminando los elementos de una lista que serían las personas participantes en el juego, y trabajándolo de manera correcta, nos devolvería el superviviente con incluso un número aleatorio de personas y también de exponente, es decir, podría aplicar en lugar de eliminar a la 2ª persona, que fuera la 3ª.

## Solución

En vista de código la solución se vería de la siguiente manera:

~~~
def Josephus(n, k):
# SE CREA UNA LISTA NÚMERADA PARA LAS PERSONAS PARTICIPANTES
personas = list(range(1, n + 1))

# SE UTILIZA ESTA VARIABLE COMO INDEX DE ELIMINACIÓN INICIALIZADO EN 0
idx = 0

# ESTE CICLO ELIMINARA A LAS PERSONAS DE LA LISTA SEGÚN LA FORMULA
while len(personas) > 1:
# ESTA ES LA FORMULA QUE CALCULA LA POSICIÓN
idx = (idx + k - 1) % len(personas)

# SE ELIMINA DE LA LISTA CON EL INDEX
eliminado = personas.pop(idx)

print(f"Eliminado: {eliminado}")
print("Personas restantes:", personas)

# LA ÚLTIMA PERSONA QUE SOBRE EN LA LISTA ES EL SUPERVIVIENTE
return personas[0]
~~~

Cómo se puede destacar no es un código muy complejo de comprender, además que se puede visualizar su funcionamiento correctamente en el archivo adjunto de nombre **'A6_Josephus_VCRS.ipynb'**. Por último, la respuesta a que posición tomo el filósofo fue la posición número 19.