# SmallLang
Es un lenguaje imperativo similar a C++ pero más sencillo.
###### Instrucciones en SmallLang:
1. Asignación: Instrucción **x := E**.
2. Nada: Instrucción **skip** que no hace nada.
> Una instrucción es un programa.
###### Estructuras de Control:
1. Secuencia: **S1 ; S2** es un programa, si **S1** y **S2** son dos programas.
2. Condicional: **if B then S1 else S2 endif** es un programa, si **B** es una expresión logica y **S1 y S2** son dos programas.
3. CIclo: **while B do S endwhile** es un programa, si **B** es una expresión logica y **S** es un programa.

# Corrección de un programa
#### Definición:
Decimos que un programa S es **correcto respecto de una especificación** dada por una precondición P y una postcondicion Q, si siempre que el programa comienza en un estado que cumple P, el programa **termina su ejecución**, y en el estado final **se cumple** Q.
#### Notación:
Cuando S es correcto respecto de la especificación (P, Q), lo denotamos con la siguiente **tripla de Hoare**:
$$
\{P\}\ S \ \{Q\}
$$
# Invariante de un Ciclo
#### Definición:
Un predicado I es un invariante de un ciclo si:
1. I vale antes de comenzar el ciclo, y
2. si vale I $\land$ B al comenzar una iteración arbitraria, entonces sigue valiendo I al finalizar la ejecución del cuerpo del ciclo.

# Teorema del Invariante
Si existe un predicado I tal que...
1. $P_c \implies I$
2. $\{I \land B\}\ S\ \{I\}$
3. $I \land \neg B \implies Q_c$
entonces el ciclo **while(B) S** es parcialmente correcto respecto de la especificación.