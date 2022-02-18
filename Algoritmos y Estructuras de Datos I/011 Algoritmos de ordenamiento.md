## Proc, aux y pred previos
proc *ordenar*(inout s : seq<$\mathbb{Z}$>){
	Pre{s = s0}
	Post{mismos(s, s0) $\land$ ordenado(s)}
}

pred *mismos*(s,t : seq<$\mathbb{Z}$>){
	$(\forall e:\mathbb{Z})(\#apariciones(s,e) = \#apariciones(t,e))$
}

aux # apariciones(s : seq< T >, e : T): $\mathbb{Z}$ = 
$$
\sum_{i=0}^{|s|-1}(\text{if }
S[i] \text{then 1 else 0 fi})
$$
pred ordenado(s : seq< $\mathbb{Z}$ >){
	$(\forall i:\mathbb{Z})(0\leq i < |s|-1 \to_L s[i]\leq s[i+1])$
}

Modificamos la secuencia **solamente** a través de intercambios de elementos

proc swap(inout s : seq< $\mathbb{Z}$ >, in i,j : $\mathbb{Z}$){
	Pre{$0\leq i,j < |s| \land s = s_0$}
	Post{$s[i]=s_0[j] \land s[j]=s_0[i] \land (\forall k:\mathbb{Z})(0\leq k < |s| \land i\neq k \land j\neq k \to_L s[k]=s_0[k])$}
}

###### Propiedad 1
$$
s= s_0 \to mismos(s,s_0)
$$
###### Propiedad 2
$$
\{mismos(s,s_0)\}
$$
$$
swap(s,i,j)
$$
$$
\{mismos(s,s_0)\}
$$
# Algoritmos de Ordenamiento
[[Selection Sort]]
[[Insertion Sort]]
[[Counting Sort]]
[[Merge Sort]]