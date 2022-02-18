## Definición: Función de Complejidad
La **función de complejidad** de un algoritmo es una función $f: \mathbb{N} \to \mathbb{R}_{\geq 0}$ tal que $f(n)$ es la cantidad de operaciones elementales que realiza el algoritmo en el peor caso para una entrada de tamaño $n$.
#### Observaciones
1. Medimos la cantidad de operaciones elementales en lugar del tiempo total.
2. Nos interesa el <u>peor caso</u> (el que genera la mayor cantidad de operaciones elementales) del programa.
3. El tiempo de ejecución se mide en función del tamaño de la entrada y no de la entrada particular.
#### Algunos tiempos de ejecución
- El tiempo de ejecución de peor caso de un programa es la suma de los tiempos de sus instrucciones.
- El tiempo de ejecución de peor caso de una operación elemental es 1.
- El tiempo de ejecución de peor caso de la instrucción `if B then S1 else S2 endif` es de $(t(B) + max(t(S1),t(S2)))$
- El tiempo de ejecución de peor caso de la instrucción `while(B) do S endwhile` es de $t(B) + (\text{cantidad de iteraciones}*(t(B) + t(S)))$
--- 
## Definición: Notación "O grande"
Si $f$ y $g$ son dos funciones, decimos que $f \in O(g)$ si existen $c \in \mathbb{R}$ y $n_0 \in \mathbb{N}$ tales que
$$
f(n) \leq c\ g(n) \text{\hspace{15pt} para todo } n \geq n_0
$$
Intuitivamente, $f \in O(g)$ si $g(n)$ "le gana" (la supera) a $f(n)$ para valores grandes de n.

### Cheatshet: Orden de los órdenes de Complejidad
$$
\begin{align*}
&\log(\log(n))<\log(n) &&\forall n \in \mathbb{N}\\
&\log(n) < n &&\forall n \in \mathbb{N}\\
&n < n\ \log(n) && \forall n \geq 3 \in \mathbb{N} \\
&n\ \log() < n^2 && \forall n > 1 \in \mathbb{N} \\
&n^2 < 2^n && \forall n > 4 \in \mathbb{N} \\
&2^n < n! && \forall n > 3 \in \mathbb{N} \\
&n! <(n!)^2 && \forall n > 1 \in \mathbb{N} \\
&(n!)^2 < (2n)! && \forall n > 1 \in \mathbb{N} \\
\end{align*}
$$
