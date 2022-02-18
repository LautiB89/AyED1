# Busqueda lineal
###### Especificación
proc *contiene*(in s : $seq<\mathbb{Z}>$, in x : $\mathbb{Z}$, out result : Bool){
	Pre { True }
	Post { result = true $\iff (\exists i : \mathbb{Z})(0\leq i < |s| \land_L s[i]=x)$}
}
###### Invariante
$I \equiv 0\leq i\leq |s| \land_L (\forall j : \mathbb{Z})(0\leq j<i \to_L s[j] \neq x)$
###### Implementación
```cpp
bool contiene(vector<int> &s, int x){
	int i = 0;
	while(i < s.size() && s[i] != x){
		i = i + 1;
	}
	return i < s.size(); 
}
```
# Busqueda binaria
proc *contieneOrdenada*(in s : $seq<\mathbb{Z}>$, in x : $\mathbb{Z}$, out result : Bool){
	Pre { ordenado(s) }
	Post { result = true $\iff (\exists i : \mathbb{Z})(0\leq i < |s| \land_L s[i]=x)$}
}
```cpp
bool contieneOrdenada(vector<int> &s, int x){
	int low = 0;
	int high = s.size() - 1;
	while(low+1 < high){
		int mid = (low+high) / 2;
		if(s[mid] <= x){
			low = mid;
		} else{
			high = mid;
		}
	}
	return s[low] == x;
}
```