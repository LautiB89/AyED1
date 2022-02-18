[[000Indice Resumen]]
- ----
$$
\newcommand{\Z}{\mathbb{Z}}
\newcommand{\Q}{\mathbb{Q}}
\newcommand{\R}{\mathbb{R}}
$$
----

# Especificación
## Definición (especificación) de un problema
proc nombre(parámetros){
	Pre{$P$}
	Post{$Q$}
}
- *nombre*: nombre que le damos al problema
	- será resuelto por una función con ese mismo nombre
- *parámetros*: lista de parámetros separada por comas, donde cada parámetro contiene:
	- Tipo de pasaje(entrada, salida, entrada y salida)
	- Nombre del parámetro
	- Tipo de datos del parámetro
- P y Q son predicados, denominados la **precondición** y la **postcondición** del **procedimiento**

# Tipos de datos
## Definición:
Un **tipo de datos** es un **conjunto de valores** ( el conjunto base del tipo ) con una serie de operaciones que se pueden hacer a estos.

Cuando un elemento es de tipo $T$ en nuestro lenguaje, se escribe como un termino o expresión que puede ser:

- Una variable de tipo $T$ (e.g. $x, \; y , \; z$, etc)
- Una constante de tipo $T$ ( e.g. $1$, $-1$, "a", etc)
- Una función ( operación ) aplicada a otros términos ( del tipo $T$ o de otro tipo ).

Todos los tipos tienen un elemento distinguido: $\bot$  o Indef (bottom)

### Tipos de datos:
- Basicos 
    - Enteros $(\Z)$
    - Reales $(\R)$
    - Booleanos ($Bool$)
    - Caracteres ($Char$)
- Enumerados
- Uplas
- Secuencias

## Tipo Entero: $\Z$
Su **conjunto base** son los números enteros.

Operaciones aritmeticas: 
- Suma, resta y producto ( a + b, a - b, a * b )
- Division entera, resto y potencia ( a div b, a mod b, $a^b$ o pot(a,b) )
- Division ( a / b , devuelve un $\R$ )

Formulas que comparan terminos de tipo $\Z$ (devuelven booleanos) :
- Menor y menor o igual: $< y \leq$
- Mayor y mayor o igual: $> y \geq$
- Iguales o distintos: $= o \neq$

## Tipo Real: $\R$
Su **conjunto base** son los números reales.

Operaciones aritméticas:
- Suma, resta y producto ( pero no div y mod )
- a / b ( división )
- $\log_{b}(a)$ ( logaritmo )
- Funciones trigonométricas

Formulas que comparan terminos de tipo $\R$ (devuelven booleanos) :
- Menor y menor o igual: $< y \leq$
- Mayor y mayor o igual: $> y \geq$
- Iguales o distintos: $= o \neq$

## Tipo Bool
Su **conjunto base** es $\mathbb{B}$ = { **true**, **false** }

Conectivos lógicos:
- ! ( $\neg$ ), && ( $\land$ ), || ( $\lor$ ), con la semántica bi-valuada estándar.

Formulas que comparan términos de tipo Bool:
- Igual o distinto: $= o \neq$

## Tipo Char
Sus elementos son las letras, digitos y simbolos.

Funcion $\text{ord}$, que enumera los caracteres, con las siguientes propiedades:
- ord('a') + 1 = ord('b')
- ord('B') + 1 = ord('B')
- ord('1') + 1 = ord('2')

Pero ord('a') no se relaciona con ord('A')
Funcion char, de modo tal que si c es cualquier char entonces char(ord(c))=c (sería como la inversa de ord).
Las comparaciones entre caracteres son comparaciones entre sus órdenes, de modo tal que a < b es equivalente a ord(a)<ord(b).

## Tipos enumerados
Tiene una cantidad finita de elementos, cada uno denotado por una constante
$$
\text{enum Nombre\{ constantes \}}
$$
- Nombre (del tipo): tiene que ser nuevo
- constantes: nombres nuevos separados por comas
- Convención: todos en mayúsculas
- $ord$(a) da la posición del elemento en la definición (empezando por 0)
- $nombre$(a): se usa el *Nombre* del tipo y funciona como la inversa de ord
## Tipo upla (o tupla)
Uplas, de dos o más elementos, cada uno de cualquier tipo
- $T_0 \times T_1 \times T_2 \times \dots \times T_k$ tipo de las *k*-uplas de elementos de tipos $T_0,T_1,T_2,\dots,T_k$, respectivamente, donde *k* es fijo.
- nésimo: $(a_0,\dots,a_k)_m$ es el valor $a_m$ en caso de que $0\leq m \leq k$. Si no, está indefinido.
