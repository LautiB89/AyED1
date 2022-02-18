[[000Indice Resumen]]
- ----
$$
\newcommand{\Z}{\mathbb{Z}}
\newcommand{\Q}{\mathbb{Q}}
\newcommand{\R}{\mathbb{R}}
$$
----
# Secuencias
Varios elementos del mismo tipo T, posiblemente repetidos, ubicados en un cierto orden.
- $seq<T>$ es el tipo de las secuencias cuyos elementos son de tipo T
T es un tipo arbitrario (el que querramos)
###### Una secuencia está bien formada si todos sus elementos son del mismo tipo.
## Operaciones sobre secuencias
```
length(a : seq<T>) : Z (notación |a|)

indexación: seq<T>[i : Z] = T
	requiere 0 <= i < |a|
	
igualdad: seq<T> = seq<T>

head(a : seq<T>) : T
	requiere |a|>0
	
tail(a : seq<T>) : T
	requiere |a|>0
	
addFirst(t : T, a : seq<T>) : seq<T>

concat(a : seq<T>, b : seq<T>) : seq<T> (notación a ++ b)

subseq(a : seq<T>, d,h : Z) : seq<T>
	requiere 0 <= d <= h <= |a|
	
setAt(a : seq<T>, i : Z, val : T) : seq<T>
	requiere 0 <= i < |a|
```
##### El lenguaje de especificación provee formas de acumular resultados para los tipos numericos $\Z$ y $\R$.
# Sumatoria
El termino $\sum\limits_{i=from}^{to}\text{Expr(i)}$ retorna la suma de todas las expresiones Expr(i) entre from y to
- Expr(i) tiene que ser de tipo numérico $\Z$ o $\R$.
- from $\leq$ to (retorna 0 si no)
- from y to es un rango (finito) de valores enteros, caso contrario se **indefine**
- Si existe i tq from $\leq$ i $\leq$ to y Expr(i) = $\bot$, entonces toda la sumatoria se **indefine**

# Productoria
El termino $\prod\limits_{i=from}^{to}\text{Expr(i)}$ retorna el producto de todas las expresiones Expr(i) entre from y to
- Expr(i) tiene que ser de tipo numérico $\Z$ o $\R$.
- from $\leq$ to (retorna 1 si no)
- from y to es un rango (finito) de valores enteros, caso contrario se **indefine**
- Si existe i tq from $\leq$ i $\leq$ to y Expr(i) = $\bot$, entonces toda la sumatoria se **indefine**
 # Matrices
 Una matriz es una secuencia de secuencias, todas con la misma longitud (y no ser vacias)
 Mat<Z> es un reemplazo sintactico para seq<seq<Z>>

