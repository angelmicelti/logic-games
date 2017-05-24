# Introducción

Este tutorial es una introducción a la electrónica digital y la lógica binaria que utiliza una perspectiva diferente para interiorizar los conceptos básicos.

Esta perspectiva consiste en diseñar cirtuitos digitales a partir de acertijos lógicos mediante la descripción del problema. Éstos circuitos permiten mediante un circuito de prueba encontar la o las soluciones al problema lógico de forma automática.

### Caballeros y escuderos

El tipo de acertijos que se analizarán son de: "La isla de los caballeros y escuderos", y comienzan así:

> Existe una isla en la que
ciertos habitantes llamados «caballeros»
dicen siempre la verdad, y otros
llamados «escuderos» mienten siempre.
Se supone que todo habitante de la isla
es o caballero o escudero.

### Lógica binaria

En electrónica digital sólo se utilizan unos y ceros. Se trata por lo tanto de lógica binaria también conocida como lógica booleana.

### Operadores lógicos

Los operadores lógicos o conectivas son símbolos utilizados para representar funciones en **lenguajes formales**. En este tutorial utilizaremos los cuatro primeros operadores.

| Operador | Símbolo | Lenguaje natural | Puerta |
|:-:|:-:|:-:|:-:|
| Negación | ¬ | no | NOT
| Conjunción | ∧ | y | AND
| Disyunción | ∨ | o | OR
| Disyunción opuesta | ↓ | ni... ni | NOR
| Disyunción exclusiva | ⊕ | o bien... o bien | XOR
| Bicondicional | ↔ | si y sólo si | XNOR
| Condicional | → | si... entonces | NOT + AND

PISTA: para recordar el símbolo **∧** podemos pensar que se parece a la A de And (y).

#### Negación

| A | ¬A |
|:-:|:-:|
| 0 | 1 |
| 1 | 0 |

#### Conjunción

| A | B | A ∧ B |
|:-:|:-:|:-:|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

#### Disyunción

| A | B | A ∨ B |
|:-:|:-:|:-:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

# Caso 0

Ejemplo:

> Se encuentran dos habitantes: A y B. A dice «B es un escudero». ¿Qué podemos determinar?

A ⇔ P
A: P = ¬B


* LECCIÓN: NOT, XNOR
* SOLUCIÓN: A y B son distintos

Los siguientes casos están ordenados por orden de complejidad de la sentencia, pero no de evaluación de la respuesta.


# Caso 1

[29]

> En este caso, supóngase que A dice, «O yo soy un escudero o B es un caballero». ¿Qué son A y B?

A: P = ¬A ∨ B

* LECCIÓN: OR
* SOLUCIÓN: A y B son caballeros


# Caso 2

[30]

> Nuevamente se encuentras dos personas, A y B, y A dice, «O yo soy un escudero o en caso contrario dos más dos es igual a cinco». ¿Qué concluirías?

A: P = ¬A ∨ 0

* LECCIÓN: 0, contradicciones (⊥)
* SOLUCIÓN: el enunciado es imposible ya que contiene una contradicción (P=¬A)


# Caso 3

[33]

> En este caso la sentencia de A es, «Yo soy escudero, pero B no lo es». ¿Qué son A y B?

A: P = ¬A ∧ B

* LECCIÓN: AND
* SOLUCIÓN: A y B son escuderos


# Caso 4

[28]

> En otra ocasión se encuentran otros dos habitantes, A y B, y A dice: «Uno al menos de nosotros es escudero». ¿Qué son A y B?

A: P = ¬A ∨ ¬B = ¬(A ∧ B)

La sentencia se puede expresar de dos maneras:

- ¬A ∨ ¬B: "O A es escudero o B es escudero"
- ¬(A ∧ B): "A y B no son ambos caballeros"

* LECCIÓN: Ley de De Morgan, NAND
* SOLUCIÓN: A es caballero y B es escudero


# Caso 5

[35]

> Hay tres personas, A, B y C. A dice, «B y C son del mismo tipo». Alguien pregunta entonces a C, «¿Son A y B del mismo tipo?». ¿Qué responde C?

A: P = (B ⇔ C)

* LECCIÓN: XNOR
* SOLUCIÓN: se obtienen las soluciones válidas (1,0,0), (0,1,0), (0,0,1), (1,1,1)
En los casos que C es un escudero A y B son de distinto tipo.
En los casos que C es un caballero A y B son del mismo tipo.
En ambos casos C responderá SÍ.


# Caso 6

[34]

> Nuevamente se encuentran A, B y C. Se dice que dos personas son del mismo tipo si son ambos caballeros o ambos escuderos. A y B dicen lo siguiente:

> A: B es un escudero.
<br>
> B: A y C son del mismo tipo.

> ¿Qué es C?

A: P = ¬B
<br>
B: Q = (A ⇔ C)

* LECCIÓN: múltiples frases, AND
* SOLUCIÓN: se obtienen las soluciones válidas (1,0,0), (0,1,0)
Por lo que podemos asegurar que C es escudero.


# Caso 7

[26]

> En este caso los tres habitantes A, B y C se
encontraban en un jardín. Un extranjero
pasó por allí y le preguntó a A, «¿Eres
caballero o escudero?». A respondió,
pero tan confusamente, que el extranjero
no pudo enterarse de lo que decía.
Entonces el extranjero preguntó a B,
«¿Qué ha dicho A?». Y B le respondió:
«A ha dicho que es escudero.» Pero en
ese instante el tercer hombre, C, dijo,
«¡No creas a B, que está mintiendo!».
La pregunta es, ¿qué son B y C?

A: P = ?
B: Q = (A ⇔ ¬A)
C: R = ¬B

LECCIÓN: contradicción y redundancia
A nunca será igual a ¬A por lo que ningún habitante podría decir nunca la frase "Yo soy escudero"
La información aportada por C es redundante y por tanto prescindible para la resolución del problema
<br>
SOLUCIÓN: se obtienen las soluciones válidas (0,0,1), (1,0,1)
Por lo tanto B es escudero y C es caballero.


# Caso 8

Al contrario que en el acertijo anterior, la respuesta de C sí es relevante para la resolución del problema.

[27]

> Supóngase que el extranjero, en
lugar de preguntarle a A por lo que éste
era, le dijese: «¿Cuántos caballeros hay
entre vosotros?» De nuevo, la respuesta
de A es ininteligible. Entonces el
extranjero pregunta a B, «¿Qué ha dicho
A?». Y B replica, «A ha dicho que hay
un caballero entre nosotros». Y C por su
parte dice, «¡No creas a B, que está
mintiendo!».
Ahora, ¿qué son B y C?

A: P = ?
B: Q = (A ⇔ (A ∧ ¬B ∧ ¬C) ∨ (¬A ∧ B ∧ ¬C) ∨ (¬A ∧ ¬B ∧ C))
C: R = ¬B

Definir bloque: (A ∧ ¬B ∧ ¬C) ∨ (¬A ∧ B ∧ ¬C) ∨ (¬A ∧ ¬B ∧ C)
Puerta ONE 1 -> Detector sólo un caballero

LECCIÓN: ONE-1 (3-bit AND, 3-bit OR)
<br>
SOLUCIÓN: se obtienen las soluciones válidas (0,0,1), (1,0,1)
Por lo tanto B es escudero y C es caballero


# Caso 9

[31]

> Nuevamente tenemos tres personas,
A, B, C, cada una de las cuales es o
caballero o escudero. A y B dicen lo
siguiente:

> A: Todos nosotros somos escuderos.
<br>
> B: Uno de nosotros, y sólo uno es un
caballero.

> ¿Qué son A, B, C?

A: P = ¬A ∧ ¬B ∧ ¬C = ¬(A ∨ B ∨ C)
<br>
B: Q = (A ∧ ¬B ∧ ¬C) ∨ (¬A ∧ B ∧ ¬C) ∨ (¬A ∧ ¬B ∧ C)

LECCIÓN: DeMorgan, 3-bit NOR, ONE-1
<br>
SOLUCIÓN: la única solución válida es (0,1,0)
Por lo tanto A es escudero, B es caballero y C es escudero


# Caso 10

[32]

>Supóngase ahora que A y B dicen lo
siguiente:

> A: Todos nosotros somos escuderos.
<br>
> B: Uno de nosotros, y sólo uno, es un
escudero.
<br>

>¿Puede determinarse lo que es B?
<br>
¿Puede determinarse lo que es C?

A: P = ¬A ∧ ¬B ∧ ¬C = ¬(A ∨ B ∨ C)
B: Q = (¬A ∧ B ∧ C) ∨ (A ∧ ¬B ∧ C) ∨ (A ∧ B ∧ ¬C)

Definir bloque: (¬A ∧ B ∧ C) ∨ (A ∧ ¬B ∧ C) ∨ (A ∧ B ∧ ¬C)
Puerta ONE 0 -> Detector sólo 1 escudero

LECCIÓN: DeMorgan, 3-bit NOR, ONE-0
<br>
SOLUCIÓN: se obtienen las soluciones válidas (0,0,1), (0,1,1)
Por lo tanto se puede afirmar que A es un escudero y C un caballero.
No se puede saber qué es B



# Referencias

* ¿Cómo se llama este libro? Capítulo 3: Caballeros y Escuderos, por Raymond Smuyllan