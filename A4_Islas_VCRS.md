### ACTIVIDAD 4 - MATRIZ CON ISLAS
### VILLASEÑOR CORNEJO RODRIGO SEBASTIAN

# CONTEO DE ISLAS EN UNA MATRIZ

## Introducción

Esta cuarta actividad nos plantea un problema que ya había trabajado con anterioridad durante las clases, siendo el caso del conteo de islas, que nos dice que planteemos la existencia de un mapa representado como una matriz en donde puede haber islas. Se considera como una isla a aquellos espacios de la matriz donde hay símbolos iguales pegados unos a otros, pero solo en posiciones verticales u horizontales, osease que si hay dos símbolos en posición diagonal no se considera isla

El problema dicta entonces que debemos encontrar los fragmentos de islas que se hallan en el mapa, esto se hará por medio de recursividad e iteraciones. De manera sencilla podemos representar una matriz o mapa con la siguiente imagen.

| · | ■ | ■ | · | · | · |
|---|---|---|---|---|---|
| · | · | · | · | ■ | ■ |
| · | · | · | · | · | · |
| · | · | · | · | ■ | · |
| ■ | · | · | · | ■ | ■ |
| ■ | ■ | · | · | · | ■ |
| ■ | ■ | · | · | ■ | ■ |


Podemos ver una pequeña representación de lo que sería el mapa, mostrando en las 4 pequeñas islas representadas por cuadrados, la parte vacía o 'no islas' es representada por puntos. Se puede deducir que hay cuatro islas en el mapa, así que lo que plantea el problema es encontrar la solución de manera recursiva y más fácil de contar las islas en el mapa.

## Desarrollo

Parece fácil si lo planteamos desde ahora, hay que tener bien en cuenta el método recursivo que se utilizara, ya que sabemos que los métodos recursivos pueden llegar a ser bucles infinitos y que pueden llegar a causar problemas de rendimiento para nuestro equipo, así que bien, vamos con las deducciones para así poder llegar a la solución.

**Deducción 1:**
>La primer cosa a tener en cuenta es tener en cuenta el tamaño de la matriz o mapa, esto es super importante ya que las funciones encargadas de buscar las islas se rigen por esto mismo, este tamaño bien puede estar dado por el usuario si lo que queremos es generar un mapa del tamaño que se desee, puede ser que también sea un tamaño fijo puesto por el desarrollador de la solución, o bien puede ser también en el caso de que lo que se busque sea extraer datos de una imagen, hoja de datos, tabla, etc. Entonces ahí el tamaño estaría dado por el archivo en cuestión. Para el uso practico yo lo he definido como *H* y *W*, como sus siglas en ingles se deduce que me refiero a height y width, así podemos modificarlas a elección del desarrollador.

~~~
H = Alto·del·mapa (Numero·de·filas)
W = Ancho·del·mapa (Numero·de·columnas)
~~~

**Deducción 2:**
>El segundo factor es la manera de representar en un formato en que se pueda entender y simbolizar a manera de código entre las casillas o posiciones de la matriz que sean tierra (o parte de una isla) y las cuales sean mar o agua (partes que no pertenezcan a una isla). La manera con la cual yo la voy a simbolizar es por números, aunque puede hacerse de muchas maneras, a mí me parece más fácil trabajar simbolizando esto con números, utilizare el ***0*** para partes del mapa o posiciones en la matriz que se simbolicen como agua, partes del mapa que no pertenecen y delimitan a una isla, el ***1*** para simbolizar las partes del mapa que simbolicen tierra o partes del mapa que sean parte de una isla, este sería el estado inicial que tomaría el mapa, sin ninguna modificación o alteración por parte de nosotros, pero la cosa no acaba ahí ya que debemos tomar en cuenta que al momento de revisar el mapa e ir verificando casilla por casilla debemos marcar las casillas por las que ya pasamos y fueron revisadas, ya que si vamos a utilizar métodos recursivos no bastara con un ciclo para hacer la revisión ordenada de la matriz, para esto voy a utilizar el numero ***2*** para simbolizar las casillas de la matriz las cuales son partes de tierra o de una isla, pero aparte que ya están revisadas o son parte de una isla la cual ya fue revisada y descubierta con anterioridad.

~~~
0 = Partes·del·mapa·vacias·(Agua)
1 = Partes·del·mapa·pertenecientes·a·una·isla·(Tierra)
2 = Partes·de·tierra·ya·revisadas·(Tierra·ya·descubierta)
~~~

**Deducción 3:**
>Ahora, como el método es recursivo tenemos que ver como se ejecutara y las restricciones que tiene, para empezar aunque el método sea recursivo hay que tener en cuenta que para recorrer la matriz si se va a necesitar de 2 ciclos anidados, los cuales van a iterar las posiciones de la matriz buscando inicialmente una casilla con el valor **1**, al encontrar este valor entraría al método recursivo el cual describe en la siguiente deducción, así que sería la única función del ciclo anidado, ya que puede haber 2 posibles casos, el primero en donde encuentre la casilla con un valor de **0**, esto pues significaría que no ha encontrado una isla, mismo caso cuando encuentre una casilla con el valor 2, ya que esto significaría que esta celda forma parte de una isla ya descubierta o contada, al final del caso lo que se busca es contar el número total de islas, al hacer esto nos aseguramos que no se cometa un error contando más de una vez las islas.

~~~
for (let i = 0; i < W; i++) {
for (let j = 0; j < H; j++) {
if (mapa[i][j]) {
MetodoRecursivo(i, j);
}
}
}
~~~

**Deducción 4:**
>Ahora veamos el método recursivo, este al estar ya en la validación tenemos la certeza de que estamos en una casilla perteneciente a una isla, así que podemos comenzar a buscar casillas alrededor para buscar más casillas que pertenezcan a la misma isla, así que lo primero es marcar la casilla actual como casilla descubierta o revisada, como ya lo vimos arriba es con el número 2. Lo siguiente el hacer uso de la recursividad, La función recibe 2 parámetros, que son las posiciones en *x* y *y*, así que si queremos revisar las posiciones alrededor es hacia arriba, abajo, derecha e izquierda.
Otra cosa importante para revisar es los límites del mapa o matriz, para que no nos genere error al hacer esto. Entonces para hacer lo que acabamos de explicar simplemente hay que verificar si las casillas vecinas tienen un valor de 1, así como verificar que haya más casillas alrededor o estemos en la orilla del mapa, se haría de la siguiente manera.

~~~
function MetodoRecursivo(i, j){
Mapa[i, j] = 2;

//Verifica y lanza hacia casilla superior
if(j>0){
if(Mapa(i,j-1) == 1){
MetodoRecursivo(i,j-1);
}
}

//Verifica y lanza hacia casilla inferior
if(j<H-1){
if(Mapa(i,j+1) == 1){
MetodoRecursivo(i,j+1);
}
}

//Verifica y lanza hacia casilla de la izquierda
if(i>0){
if(Mapa(i-1,j) == 1){
MetodoRecursivo(i-1,j);
}
}

//Verifica y lanza hacia casilla de la derecha
if(i<W-1){
if(Mapa(i+1,j) == 1){
MetodoRecursivo(i+1,j);
}
}
}
~~~

**Deducción 5:**
>Acabamos de ver como disparar o enviar la función recursiva a casillas vecinas, con esto se cubrirá que se descubran las casillas que pertenezcan a cada isla, si lo que queremos es contar las islas que halla en el mapa, lo que se agregaría es una variable contador que sume uno cada vez que encuentra un valor 1, pero no dentro de la función recursiva, si no dentro de los ciclos anidados, y así se asegura que solo se cuente una vez, ya que si analizamos, la iteración, solo encuentra una casilla de la isla y la recursividad se encarga de encontrar el resto.

A todo esto, podemos añadirle varias cosas, como si queremos que se impriman las posiciones de cada elemento de la isla, podemos añadirlo dentro de la forma recursiva, así como si queremos encontrar algún color en alguna imagen o un elemento a destacar, podemos encontrarla cambiando la validación, en este caso tratando a una imagen como matriz y cambiando la validación de 1 por el color (ya sea decimal, hexadecimal o código de color) deseado.

## Solución

La solución al problema se encuentra a manera de código dentro del programa adjunto a la actividad con el nombre de **'A4_Islas_VCRS.ipynb'**.