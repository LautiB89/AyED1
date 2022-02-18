# Teorema de terminacion de un ciclo
Sea $\mathbb{V}$ el producto cartesiano de los dominios de las variables del programa y sea I un invariante del ciclo **while B do S endwhile**. Si existe una función fv: $\mathbb{V} \to \mathbb{Z}$ tal que
1. $\{I \land B \land v_0 = fv\}$  **S**  $\{fv < v_0\}$
2. $I \land fv \leq 0 \implies \neg B$
... entonces la ejecución del ciclo **while B do S endwhile** siempre termina.
La función fv se llama función variante del ciclo.

# Teorema de corrección de un ciclo
Sean un predicado I y una función fv: $\mathbb{V} \to \mathbb{Z}$ y supongamos que I $\implies$ def(B). Si
1. $P_c \implies I$
2. $\{I \land B\}\ S\ \{I\}$
3. $I \land \neg B \implies Q_c$
4. $\{I \land B \land v_0 = fv\}$  **S**  $\{fv < v_0\}$
5. $I \land fv \leq 0 \implies \neg B$
... entonces la siguiente tripla de Hoare es válida:
$$
\{P_C\}\text{while B do S endwhile} \{Q_C\}
$$
Entonces probamos que $P_C \implies wp(\text{while B do S endwhile}, Q_C)$
En la demostración se reemplaza fv por la funcion variante encontrada.
