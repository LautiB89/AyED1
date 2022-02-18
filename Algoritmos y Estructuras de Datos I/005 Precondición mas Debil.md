# Precondición más débil
#### Definición:
La **precondición más débil** de un programa **S** respecto de una postcondición Q es el predicado P más débil posible tal que {P}**S**{Q}.
#### Notación:
wp(S, Q)
#### Teorema:
Una tripla de Hoare {P}S{Q} es válida si y solo si $P \implies_{L} \ wp(S,Q)$ 

# Axiomas de la precondición más débil
1.  $wp(\textbf{x := E},Q)\equiv def(E) \land_L Q_{E}^{\text{x}}$    
2.  $wp(\textbf{skip},Q)\equiv Q$
3.  $wp(\textbf{S1; S2},Q)\equiv wp(\textbf{S1, }wp(\textbf{S2},Q)$
4.  Si $\textbf{S = if B then S1 else S2 endif}$, entonces:
    $wp(\textbf{S},Q)\equiv def(B) \land_L \bigg(\big(B \land wp(\textbf{S1},Q)\big) \lor \big(\neg B \land wp(\textbf{S2},Q)\big)\bigg)$
5.  $wp(\textbf{while B do S endwhile}, Q) \equiv (\exists_{i\geq0})(H_i(Q))$

## Definición
Definimos $H_k(Q)$ como el predicado que define el conjunto de estados a partir de los cuales la ejecución del ciclo termina en exactamente *k* iteraciones:
$$
H_0(Q) \equiv \text{def}(B)\land \neg B\land Q
$$
$$
H_{k+1}(Q) \equiv \text{def}(B) \land B \land wp(S, H_k(Q))\text{ para k}\geq0
$$
#### Propiedad
Si el ciclo realiza a lo sumo k iteraciones, entonces
$$
wp(\text{while B do S endwhile, Q}) \equiv \lor_{i=0}^{k}H_i
$$
# Propiedades
##### Monotonía
Si $Q \implies R$ entonces wp(S, Q) $\implies$ wp(S, R)
##### Distributividad
wp(S, Q) $\land$ wp(S, R) $\implies$ wp(S, Q $\land$ R)
wp(S, Q) $\lor$ wp(S, R) $\implies$ wp(S, Q $\lor$ R)
##### Excluded Miracle
wp(S, false) $\equiv$ false
##### Corolario de la monotonía
Si :
	P $\implies$ wp(S1, Q)
	Q $\implies$ wp(S2, R)
entonces
	P $\implies$ wp(S1;S2 , R)

Demo:

Por monotonía sabemos que 
	Q $\implies$ wp(S2, R) implica wp(S1, Q) $\implies$ wp(S1, wp(S2, R))
(es como agregar un wp(S1,...) de cada lado)

Y ahora se cumple esta cadena de implicaciones
P $\implies$ wp(S1, Q) $\implies$ wp(S1, wp(S2, R)) $\equiv$ wp(S1 ; S2, R)

Asi queda demostrado que 
	P $\implies$ wp(S1, Q)
	Q $\implies$ wp(S2, R)
Implica
	P $\implies$ wp(S1;S2 , R)