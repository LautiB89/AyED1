# Algoritmos e Implementaciones

## Algoritmos de Búsqueda

### Búsqueda lineal
Recorre todo el vector hasta encontrar una ocurrencia de $x$, su complejidad de peor caso es de $O(n)$ con $n$ igual al tamaño del vector
```cpp
int busquedaLineal(vector<int> &v, int x){
	int res = -1;
	    for(int i = 0; i < v.size() and res == -1; i++){
    		if(v[i] == x){
				res = i;
    		}
    	}
    	return res;
    }
```
    
### Búsqueda binaria
Necesita como precondición extra que el vector esté **ordenado.**
```cpp
int busquedaBinaria(vector<int> &v, int x){
	int low = 0, high = v.size() - 1, mid;
	int res = -1;	
	while(low < high - 1){
		mid = (low + high) / 2;
		if (v[mid] <= x) {
			low = mid;
		} else {
			high = mid;
		}
	}
	return low;
}
```
    
### Jump search
Necesita como precondición que la secuencia esté ordenada.
```cpp
int jumpSearch(vector<int> &v, int x){
	int jump = sqrt(v.size());
	int ind = 0;
	while(v[ind] <= x and ind < v.size()){
		i += jump;
	}
	ind = min(ind, v.size());
	int res = -1;
	for(int i = ind-jump; i < ind; i++){
		if(v[i] == x){
			res = i;
		}
	}
	return res;
}
```
    
## Algoritmos de Ordenamiento
### Counting sort
#### Ordenar ascendente
```cpp
vector<int> countingSort(vector<int> &v){
	//En este counting mis elementos estan acotados por n = v.size()

	//Primero cuento cada elemento: en v[i] guardo la cantidad de i
	vector<int> count(v.size() + 1);
	for(int i = 0; i < v.size(); i++)
		count[v[i]]++;

	//Calculo la acumulada: ahora v[i] = v[i]+v[i-1]+...+v[0]
	for(int i = 1; i < count.size(); i++)
		count[i] += count[i-1];

	//Ahora recorro desde atras y voy completando la lista ordenada
	vector<int> res(v.size());
	for(int i = v.size()-1; i >= 0; i--)
		res[--count[v[i]]] = v[i];

	return res;
}
```    
#### Ordenar descendente
```cpp
vector<int> countingSort_desc(vector<int> &v){
	//En este counting mis elementos estan acotados por n = v.size()

	//Primero cuento cada elemento: en v[i] guardo la cantidad de i
	vector<int> count(v.size() + 1);
	for(int i = 0; i < v.size(); i++)
		count[v[i]]++;

	//Calculo la acumulada: ahora v[i] = v[i]+v[i+1]+...+v[v.size()-1]
	for(int i = count.size()-2; i >= 0; i--)
		count[i] += count[i+1];

	//Ahora recorro desde el principio y voy completando la lista ordenada
	vector<int> res(v.size());
	for(int i = 0; i < v.size(); i++)
		res[--count[v[i]]] = v[i];

	return res;
}
```
    
### Cocktail sort
```cpp
void cocktailSort(vector<int> &v){
	if(v.size() == 0){ return; }
	int d = 0, n = v.size()-1;
	int indiceMin, indiceMax;
	while(d <= n/2){
		indiceMin = d;
		indiceMax = d;
		//Busco minimo y maximo
		for(int i = d; i <= n-d; i++){
			if(v[i] <= v[indiceMin]){
				indiceMin = i;
			}
			if(v[i] >= v[indiceMax]){
				indiceMax = i;
			}
		}
		swap(v[d], v[indiceMin]);
		if(v.size() > 2) {
			swap(v[n - d], v[indiceMax]);
		}
		d++;
	}
}
```
    
### Cocktail shaker sort
```cpp
void cocktailShakerSort(vector<int> &v){
	bool ida = true;
	int d = 0, h = v.size();
	for(int i = d; i < h - 1; i += ida?1:-1){
		if(v[i] > v[i+1]){
			swap(v[i], v[i+1]);
		}
		if(ida and i == h-2){
			ida = false;
			h--;
		} else if(!ida and i == d){
			ida = true;
			d++;
		}
	}
}
```

## Algoritmos para matrices
### Rotaciones
```cpp
vector<vector<int>> rotacion1(vector<vector<int>> m, int f, int c){ //N= |m| M=|m[0]|
	vector<vector<int>> res = m;                                //O(N * M)
  for(int i = 0; i < m.size(); i++){                          //N
		for(int j = 0; j < m[0].size(); j++){                     //M
			res[i][j] = m[(i+f) % m.size()][(j+c) % m[0].size()];   //O(1)
		}
	}
return res;                                                   //O(N*M)
}

vector<vector<int>> rotacion2(vector<vector<int>> &m, int f, int c){ //N= |m| M=|m[0]|
	vector<vector<int>> res = m;                                //O(N * M)
	for(int i = 0; i < m.size(); i++){                          //N
		for(int j = 0; j < m[0].size(); j++){                     //M
			res[(i+f) % m.size()][(j+c) % m[0].size()] = m[i][j];   //O(1)
		}
	}
	return res;                                                   //O(N*M)
}
```
### Vecinos
Devolver una lista de las coordenadas de los vecinos del casillero $(i_0,j_0)$ dado.
```cpp
// F son las filas, C son las columnas
vector<pair<int,int>> vecinos(int F, int C, int i0, int j0){
	vector<pair<int,int>> res;
	for(int i = max(i0-1, 0); i < min(i0+2, F); i++){
		for(int j = max(j0-1, 0); j < min(j0+2, C); j++){
			if(i != i0 || j != j0)
				res.push_back(make_pair(i,j));
		}
	}
	return res;
}

//Puedo reemplazar los F y C por sus respectivos size
vector<pair<int,int>> vecinos(vector<vector<int>> m, int i0, int j0){
	vector<pair<int,int>> res;
	for(int i = max(i0-1, 0); i < min(i0+2, m.size()); i++){
		for(int j = max(j0-1, 0); j < min(j0+2, m[0].size()); j++){
			if(i != i0 || j != j0)
				res.push_back(make_pair(i,j));
		}
	}
	return res;
}
```
    

## Otros (de la guía)
### dosMitades
```cpp
void dosMitades(vector<int> &a) {
	// ni me gasto en hacer nada que tenga mejor complejidad que O(n)
	// ya que para crear la lista final voy a tener que escribir n eltos

	//Busco el "escaloncito"
	int esc = 1;
	while (esc < a.size() && a[esc-1] <= a[esc]) {
		esc++;
	}

	//Ahora voy comparando cada elemento y apareo las dos sublistas
	int i = 0, j = esc;
	vector<int> res;
	while(i < esc || j < a.size()){
		res.push_back(a[i] < a[j] ? a[i++] : a[j++]);
	}
	a = res;
}
```