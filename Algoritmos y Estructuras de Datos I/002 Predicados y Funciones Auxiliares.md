[[000Indice Resumen]]
- ----
$$
\newcommand{\Z}{\mathbb{Z}}
\newcommand{\Q}{\mathbb{Q}}
\newcommand{\R}{\mathbb{R}}
$$
----
> Se ignoran muchas cosas que ya se dan por sabidas:
	Contrato 
	 Logica, Logica trivaluada
	 Expresiones bien Definidas
# Predicados y Funciones Auxiliares
- Asignan un nombre a una expresión
- Facilitan la lectura y la escritura de especificaciones (reemplazo sintáctico)
- **Modularizan** la especificación
###### aux f(argumentos) : tipo = e;
- f es el nombre de la función, sirve para escribir f en vez de la expresión e
- Los argumentos son opcionales y se reemplazan en e cada vez que se usa f
- tipo es el tipo del resultado de la función (el tipo de e)
###### pred p(argumentos){f}
- p es el nombre que puede usarse en el resto de la especificación en lugar de la formula de f

## Expresiones Condicionales
Funcion que elige entre dos elementos del mismo tipo, segun una formula logica (guarda)
	ejemplo: 
		aux max( a, b : $\Z$) : $\Z$ = IfThenElseFi<$\Z$>(a > b, a, b);
Si el tipo se deduce del contexto no es necesario escribir el tipo del resultado "<$\Z$>"

## Relaciones de Fuerza
Decimos que **A es mas fuerte que B** cuando $A \to B$  es una tautología. 
Se puede pensar como que **cuando A es verdadero, si o si B tambien debe ser verdadero**.

## Cuantificadores
El lenguaje de especificación provee formas de predicar sobre los elementos de un tipo de datos
- $(\forall x : T)P(x)$ Afirma que **todos** los elementos de tipo T cumplen la propiedad P.
- $(\exists x : T)P(x)$ Afirma que **al menos un** elemento de tipo T cumple la propiedad P.
Cuando una variable viene con un $\forall$ o un $\exists$ entonces está **ligada**,  si no es **libre**.

En general cuando queremos decir que todos los elementos de tipo T que cumplen P(x) tambien cumplen Q(x), decimos:
$$
(\forall x : T)(P(x)\to Q(x))
$$
Para decir que existe un elemento de tipo T que cumple P(x) y tambien cumple Q(x), decimos:
$$
(\exists x : T)(P(x) \wedge Q(x))
$$
### Operaciones con Cuantificadores
###### Observación importante:
Se puede pensar al cuantificador universal como un **generalizador de la conjunción**:
$$
(\forall n : \Z)(a\leq n\leq b\to P(n))\; \wedge \ P(b+1) \\
\iff \ (\forall n : \Z)(a\leq n\leq b+1\to P(n))
$$
Y al cuantificador existencial como un **generalizador de la disyunción**:
$$
(\exists n : \Z)(a\leq n\leq b\wedge P(n))\; \lor \ P(b+1) \\
\iff \ (\forall n : \Z)(a\leq n\leq b+1\land P(n))
$$
###### Negación
$$
\neg(\forall n : \Z)P(n) \iff (\exists n : \Z)\neg P(n)
$$
$$
\neg(\exists n : \Z)P(n) \iff (\forall n : \Z)\neg P(n)
$$
