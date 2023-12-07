### ACTIVIDAD 3 - TABLERO DE ALFILES
### VILLASEÑOR CORNEJO RODRIGO SEBASTIAN

# PROBLEMA DE LOS ALFILES

## Introducción

En este problema se busca analizar y buscar el número mínimo de movimientos en el cual se pueda pasar todos los alfiles de un lado al otro invirtiendo las posiciones, es decir, los 4 alfiles de un color que se encuentra en la fila superior deben terminar en la inferior y viceversa.
Entonces lo que se busca es que los alfiles negros queden en la parte inferior y que los alfiles blancos queden en la parte superior, esto junto con buscar el camino más corto o el número mínimo de movimientos.

En este problema se tiene hay que tener varias consideraciones y reglas para poder llevar a cabo el análisis y la solución posible solución:

1. Los alfiles solo se pueden mover en diagonal, no hacia enfrente ni atrás, tampoco a los lados, solo diagonal como lo hacen piezas de ajedrez comunes.
2. El tablero es un rectángulo de 4 casillas de ancho por 5 casillas de alto, con 4 alfiles en la fila superior de un mismo color y 4 alfiles en la fila inferior del color contrario.
3. Los turnos son alternados, no importa quien empiece, ya que es uno y uno en los turnos.
4. Ningún alfil debe atacar en ningún momento otro del color opuesto.

El tablero con el que se trabaja se vería entonces de la siguiente manera:

<div style="text-align:center;"> <img src="https://i0.wp.com/divulgadores.com/wp-content/uploads/2015/01/intercambiar_alfiles_dudeney_2.png?resize=189%2C236"> </div>

Teniendo esto en cuenta ahora podemos comenzar a plantear una posible solución. Si tenemos en cuenta que es un tablero de 5 casillas de alto pues podemos deducir que el número mínimo de movimientos por alfil es de 4, ya que al moverse en diagonal ocuparían solo cuatro movimientos para quedar en el final.

## Desarrollo

Considerando las reglas que ya se tienen sobre el funcionamiento del problema se pueden ir creando distintas deducciones que se explicaran a continuación.

**Deducción 1:**
> Cada pieza le tomaría 4 movimientos en diagonal, lleno solo hacia adelante, para tomar el lugar del alfil contrario. Esto ya que se busca el mínimo número de movimientos para realizar esta tarea.

> En la siguiente tabla se muestra enumeradas las casillas con los movimientos casilla por casilla del alfil, esto también dependerá de la posición inicial del alfil.

Esta es la tabla de movimientos enumerados partiendo desde la posición [0,0] para un único alfil en la fila superior.

> |♝ | * | * | * |
> |---|---|---|---|
> | * | 1 | * | * |
> | 2 | * | 2 | * |
> | * | 3 | * | 3 |
> | 4 | * | 4 | * |

Esta es la tabla de movimientos enumerados partiendo desde la posición [0,1].

> | * |♝ | * | * |
> |---|---|---|---|
> | 1 | * | 1 | * |
> | * | 2 | * | 2 |
> | 3 | * | 3 | * |
> | * | 4 | * | 4 |

Esta es la tabla de movimientos enumerados partiendo desde la posición [0,2].

> | * | * |♝ | * |
> |---|---|---|---|
> | * | 1 | * | 1 |
> | 2 | * | 2 | * |
> | * | 3 | * | 3 |
> | 4 | * | 4 | * |

Esta es la tabla de movimientos enumerados partiendo desde la posición [0,3].

> | * | * | * | ♝|
> |---|---|---|---|
> | * | * | 1 | * |
> | * | 2 | * | 2 |
> | 3 | * | 3 | * |
> | * | 4 | * | 4 |

**Deducción 2:**
> La deducción 2 parte de la primera, pues como se dijo la posición de partida es importante para predecir en que posición posible puede terminar, ya que un alfil que está en las posiciones [0, 0] o [0, 2] solo puede terminar en 2 posibles casillas, ya sea en la [4, 0] o en la [4, 2]. Lo mismo aplicaría con las filas 1 y 3.

**Deducción 3:**
> La tercera deducción se trata de evitar bloqueos y ataques hacia las otras pizas, manteniendo lo más optimo sería viable que dependiendo de que pieza se mueve primero en un lado deberíamos mover la pieza contraria de cualquiera de las dos columnas en número par; Es decir, si se mueven las piezas [0, 0] o [0, 2] sería lo más viable comenzar a mover los alfiles de las casillas [4, 0] o [4, 2].

> La finalidad es que los alfiles tomen el lugar de la pieza que se está moviendo inicialmente y no dejar piezas en medio del tablero para evitar que se hagan bloqueos entre las piezas y no se tengan que retroceder entre piezas porque eso generaría más movimientos y lo que se busca el número mínimo de movimientos.

**Deducción 4:**
> Esta se refiere al número total de movimientos. Como vimos en el primer punto, el número mínimo para mover una pieza de un lado al otro es de cuatro movimientos, entonces el número de movimientos por jugador o lado es de 16. Esto se puede ver con la siguiente formula:

> N_movimientos = 4 * 4 = 16

> N_total = 2 * 16 = 32

**Deducción 5:**
> La última deducción que sería clave para mantener el margen del mínimo número de movimientos lo mejor o más optimo es mover una pieza a la vez, no mover una pieza y luego dejarla en medio de del tablero ya que puede provocar que haya bloqueos entre las piezas y no se coman entre sí.

## Solución
Para proceder con una posible solución al problema, ya vimos que tiene varios caminos para resolverse, dependiendo de quien comience el juego, así como si solo se mueve un alfil a la vez o más de uno. Todo esto debido a que todos los alfiles de un lado son iguales y es un poco irrelevante el orden de los mismos ya que al final lo que se busca es que queden del lado contrario.

La solución propuesta está dada del siguiente modo:

**Comienzo**
>| ♝₁ | ♝₁ | ♝₁ | ♝₁ |
>|---|---|---|---|
>| * | * | * | * |
>| * | * | * | * |
>| * | * | * | * |
>| ♝₂ | ♝₂ | ♝₂ | ♝₂ |

**Paso #1**
>| * | ♝₁ | ♝₁ | ♝₁ |
>|---|---|---|---|
>| * | ♝₁ | * | * |
>| * | * | * | * |
>| * | * | * | * |
>| ♝₂ | ♝₂ | ♝₂ | ♝₂ |

**Paso #2**
>| * | ♝₁ | ♝₁ | ♝₁ |
>|---|---|---|---|
>| * | ♝₁ | * | * |
>| * | * | * | * |
>| * | ♝₂ | * | * |
>| ♝₂ | ♝₂ | * | ♝₂ |

**Paso #3**
>| * | ♝₁ | ♝₁ | ♝₁ |
>|---|---|---|---|
>| * | * | * | * |
>| * | * | ♝₁ | * |
>| * | ♝₂ | * | * |
>| ♝₂ | ♝₂ | * | ♝₂ |

**Paso #4**
>| * | ♝₁ | ♝₁ | ♝₁ |
>|---|---|---|---|
>| * | * | * | * |
>| ♝₂ | * | ♝₁ | * |
>| * | * | * | * |
>| ♝₂ | ♝₂ | * | ♝₂ |

**Paso #5**
>| * | ♝₁ | ♝₁ | ♝₁ |
>|---|---|---|---|
>| * | * | * | * |
>| ♝₂ | * | * | * |
>| * | * | * | ♝₁ |
>| ♝₂ | ♝₂ | * | ♝₂ |

**Paso #6**
>| * | ♝₁ | ♝₁ | ♝₁ |
>|---|---|---|---|
>| * | ♝₂ | * | * |
>| * | * | * | * |
>| * | * | * | ♝₁ |
>| ♝₂ | ♝₂ | * | ♝₂ |

**Paso #7**
>| * | ♝₁ | ♝₁ | ♝₁ |
>|---|---|---|---|
>| * | ♝₂ | * | * |
>| * | * | * | * |
>| * | * | * | * |
>| ♝₂ | ♝₂ | ♝₁ | ♝₂ |

**Paso #8**
>| ♝₂ | ♝₁ | ♝₁ | ♝₁ |
>|---|---|---|---|
>| * | * | * | * |
>| * | * | * | * |
>| * | * | * | * |
>| ♝₂ | ♝₂ | ♝₁ | ♝₂ |

### **A partir de este punto ya se intercambiaron dos piezas**

**Paso #9**
>| ♝₂ | ♝₁ | ♝₁ | * |
>|---|---|---|---|
>| * | * | ♝₁ | * |
>| * | * | * | * |
>| * | * | * | * |
>| ♝₂ | ♝₂ | ♝₁ | ♝₂ |

**Paso #10**
>| ♝₂ | ♝₁ | ♝₁ | * |
>|---|---|---|---|
>| * | * | ♝₁ | * |
>| * | * | * | * |
>| ♝₂ | * | * | * |
>| ♝₂ | * | ♝₁ | ♝₂ |

**Paso #11**
>| ♝₂ | ♝₁ | ♝₁ | * |
>|---|---|---|---|
>| * | * | * | * |
>| * | * | * | ♝₁ |
>| ♝₂ | * | * | * |
>| ♝₂ | * | ♝₁ | ♝₂ |

**Paso #12**
>| ♝₂ | ♝₁ | ♝₁ | * |
>|---|---|---|---|
>| * | * | * | * |
>| * | ♝₂ | * | ♝₁ |
>| * | * | * | * |
>| ♝₂ | * | ♝₁ | ♝₂ |

**Paso #13**
>| ♝₂ | ♝₁ | ♝₁ | * |
>|---|---|---|---|
>| * | * | * | * |
>| * | ♝₂ | * | * |
>| * | * | ♝₁ | * |
>| ♝₂ | * | ♝₁ | ♝₂ |

**Paso #14**
>| ♝₂ | ♝₁ | ♝₁ | * |
>|---|---|---|---|
>| * | * | ♝₂ | * |
>| * | * | * | * |
>| * | * | ♝₁ | * |
>| ♝₂ | * | ♝₁ | ♝₂ |

**Paso #15**
>| ♝₂ | ♝₁ | ♝₁ | * |
>|---|---|---|---|
>| * | * | ♝₂ | * |
>| * | * | * | * |
>| * | * | * | * |
>| ♝₂ | ♝₁ | ♝₁ | ♝₂ |

**Paso #16**
>| ♝₂ | ♝₁ | ♝₁ | ♝₂ |
>|---|---|---|---|
>| * | * | * | * |
>| * | * | * | * |
>| * | * | * | * |
>| ♝₂ | ♝₁ | ♝₁ | ♝₂ |

### **Aquí se han intercambiado 4 piezas**

**Paso #17**
>| ♝₂ | * | ♝₁ | ♝₂ |
>|---|---|---|---|
>| * | * | ♝₁ | * |
>| * | * | * | * |
>| * | * | * | * |
>| ♝₂ | ♝₁ | ♝₁ | ♝₂ |

**Paso #18**
>| ♝₂ | * | ♝₁ | ♝₂ |
>|---|---|---|---|
>| * | * | ♝₁ | * |
>| * | * | * | * |
>| * | * | ♝₂ | * |
>| ♝₂ | ♝₁ | ♝₁ | * |

**Paso #19**
>| ♝₂ | * | ♝₁ | ♝₂ |
>|---|---|---|---|
>| * | * | * | * |
>| * | ♝₁ | * | * |
>| * | * | ♝₂ | * |
>| ♝₂ | ♝₁ | ♝₁ | * |

**Paso #20**
>| ♝₂ | * | ♝₁ | ♝₂ |
>|---|---|---|---|
>| * | * | * | * |
>| * | ♝₁ | * | ♝₂ |
>| * | * | * | * |
>| ♝₂ | ♝₁ | ♝₁ | * |

**Paso #21**
>| ♝₂ | * | ♝₁ | ♝₂ |
>|---|---|---|---|
>| * | * | * | * |
>| * | * | * | ♝₂ |
>| * | * | ♝₁ | * |
>| ♝₂ | ♝₁ | ♝₁ | * |

**Paso #22**
>| ♝₂ | * | ♝₁ | ♝₂ |
>|---|---|---|---|
>| * | * | ♝₂ | * |
>| * | * | * | * |
>| * | * | ♝₁ | * |
>| ♝₂ | ♝₁ | ♝₁ | * |

**Paso #23**
>| ♝₂ | * | ♝₁ | ♝₂ |
>|---|---|---|---|
>| * | * | ♝₂ | * |
>| * | * | * | * |
>| * | * | * | * |
>| ♝₂ | ♝₁ | ♝₁ | ♝₁ |

**Paso #24**
>| ♝₂ | ♝₂ | ♝₁ | ♝₂ |
>|---|---|---|---|
>| * | * | * | * |
>| * | * | * | * |
>| * | * | * | * |
>| ♝₂ | ♝₁ | ♝₁ | ♝₁ |

### **Ahora son 6 piezas intercambiadas**

**Paso #25**
>| ♝₂ | ♝₂ | * | ♝₂ |
>|---|---|---|---|
>| * | * | * | ♝₁ |
>| * | * | * | * |
>| * | * | * | * |
>| ♝₂ | ♝₁ | ♝₁ | ♝₁ |

**Paso #26**
>| ♝₂ | ♝₂ | * | ♝₂ |
>|---|---|---|---|
>| * | * | * | ♝₁ |
>| * | * | * | * |
>| * | ♝₂ | * | * |
>| * | ♝₁ | ♝₁ | ♝₁ |

**Paso #27**
>| ♝₂ | ♝₂ | * | ♝₂ |
>|---|---|---|---|
>| * | * | * | * |
>| * | * | ♝₁ | * |
>| * | ♝₂ | * | * |
>| * | ♝₁ | ♝₁ | ♝₁ |

**Paso #28**
>| ♝₂ | ♝₂ | * | ♝₂ |
>|---|---|---|---|
>| * | * | * | * |
>| ♝₂ | * | ♝₁ | * |
>| * | * | * | * |
>| * | ♝₁ | ♝₁ | ♝₁ |

**Paso #29**
>| ♝₂ | ♝₂ | * | ♝₂ |
>|---|---|---|---|
>| * | * | * | * |
>| ♝₂ | * | * | * |
>| * | ♝₁ | * | * |
>| * | ♝₁ | ♝₁ | ♝₁ |

**Paso #30**
>| ♝₂ | ♝₂ | * | ♝₂ |
>|---|---|---|---|
>| * | ♝₂ | * | * |
>| * | * | * | * |
>| * | ♝₁ | * | * |
>| * | ♝₁ | ♝₁ | ♝₁ |

**Paso #31**
>| ♝₂ | ♝₂ | * | ♝₂ |
>|---|---|---|---|
>| * | ♝₂ | * | * |
>| * | * | * | * |
>| * | * | * | * |
>| ♝₁ | ♝₁ | ♝₁ | ♝₁ |

**Paso #32**
**FIN**
>| ♝₂ | ♝₂ | ♝₂ | ♝₂ |
>|---|---|---|---|
>| * | * | * | * |
>| * | * | * | * |
>| * | * | * | * |
>| ♝₁ | ♝₁ | ♝₁ | ♝₁ |

### **Finalmente, se cumple con el objetivo de intercambiar las 8 piezas de posición cumpliendo con las reglas establecidas en un periodo de 32 movimientos como se declaró en la formula del desarrollo.**
