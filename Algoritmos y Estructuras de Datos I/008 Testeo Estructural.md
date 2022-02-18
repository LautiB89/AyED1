# Testeo Estructural
### Intro
- ¿Que es hacer testing?
    Es ejecutar un producto con el objetivo de encontrar defectos en el software. Sirve para verificar que cumple con sus requerimientos (para nosotros es la **especificación**) y para identificar las diferencias entre el comportamiento **real** y el **esperado.**
- ¿Cómo se hace testing?
    1. Vamos a tener un input, y vamos a correr el programa con este input.
    2. Al correr el programa, recibimos un resultado de parte del programa. Ahora tenemos que verificar si el resultado obtenido es el resultado esperado
    3. El resultado esperado lo vamos a obtener de un oráculo, algo que nos dice las soluciones.
    4. Si el resultado es Distinto → Falló, si es Igual → Está OK.
    ![Untitled](testeo1.png)

# Definiciones
**Programa bajo test:** es el programa que queremos saber si funciona bien o no
**Test input** (o dato de prueba): Es una asignación concreta de valores a los parámetros de entrada para ejecutar el programa bajo test.
**Test case:** Caso de Test (o caso de prueba). Es un programa que ejecuta el programa bajo test usando un dato de test, y chequea (automáticamente) si se cumple la condición de aceptación sobre la salida del programa bajo test.
**Test suite:** Es un conjunto de casos de Test (o de casos de prueba).

## Testing con Especificación
El programa que vamos a testear es la implementación de una especificación. Al ejecutarlo, los datos de prueba que puedo elegir son los que cumplen la precondición de esa especificación. Al terminar la ejecución tengo que chequear que se cumpla la postcondición. 

Notar que solo importa cuando la precondición se cumple, cuando no es asi a nosotros no nos importa que es lo que hace el programa.

# Testeando programas
Algo que uno naturalmente querría hacer es testear todos los valores posibles en su programa. Sabiendo que los enteros se representan con 32 bits, necesitariamos probar $2^{32}$ casos de test, y escribir un test suite de $4,294,967,296$ test cases.
Esta forma de testear se llama testing exhaustivo y no es práctica.
Vamos a ver que existen mejores. 

### Limitaciones del testing
Como vimos antes, no podemos hacer testing exhaustivo asi que el testing no va a servir para probar (demostrar) que el software funciona correctamente.

> *"El testing puede demostrar la presencia de errores, nunca su ausencia."* Edsger Dijkstra

Una de las mayores dificultades es encontrar un conjunto de tests adecuado:

- **Suficientemente grande** para abarcar el dominio y maximizar la probabilidad de encontrar errores.
- **Suficientemente pequeño** para poder ejecutar el proceso con cada elemento del conjunto y minimizar el costo del testing.

### ¿Con qué datos probar?
Cuando uno prueba un programa, podemos ver que hay muchos casos que se pueden agrupar por lo parecidos que son. Si quisiera probar una función que dado un $x$ devuelve $|x|$ podría probar con casos representativos de cada grupo (el 0, uno positivo y uno negativo).

En esta idea se basan las diferentes técnicas. 

Tenemos que tener en cuenta que no hay algoritmos que propongan casos que puedan encontrar todos los errores de un programa, entonces vamos a tener formas bastante diferentes de testear.

Vamos a ver dos tipos de criterios para seleccionar datos de test:

- **Test de Caja Negra:** los casos de test se generan analizando la especificación sin considerar la implementación.
- **Test de Caja Blanca:** los casos de test se generan analizando la implementación para determinar los casos de test.

## Control-Flow Graph (CFG)
 Es una representación grafica del programa. Se usa para definir criterios de adecuación para test suites. Cuanto mas *partes* son ejercitadas, mayores las chances de un test de descubrir una falla.

Las *partes* pueden ser: nodos, arcos, caminos, decisiones...

- **Nodos:** son las sentencias (los globos con codigo adentro)
- **Arcos:** son las flechas que unen cada nodo (incluidas las de True o False).
- **Decisiones o branches:** son las flechas que están con True o con False
- Representaciones graficas
    
    ![Cada globo es un NODO y cada flecha es un ARCO.](testeo2.png)
    Cada globo es un NODO y cada flecha es un ARCO.
    
Usando los control-flow graph podemos ayudarnos para escribir un test suite que sea bueno. Puede ser que nos concentremos en recorrer un arco o decision que vemos que falta ejecutar o ejemplos de este estilo.

Vamos a formular un **criterio de adecuación de test,** que es un predicado que toma un valor de verdad para una tupla <programa, test suite>.

Una regla sería *todas las sentencias deben ser ejecutadas.*

### Cubrimiento de Nodos (Sentencias)
Criterio de Adecuación: cada nodo en el CFG debe ser ejecutado al menos una vez por algún test case
Cobertura del criterio:
$$
 \frac{\text{cantidad de nodos ejercitados}}{\text{cantidad de nodos}}
$$
Un defecto en una sentencia solo puede ser revelado si en algún momento llegamos a ejecutar tal sentencia.

### Cubrimiento de Arcos (Flechas)
Criterio de Adecuación: todo arco en el CFG debe ser ejecutado al menos una vez por algún test case.
Cobertura del criterio:
$$
\frac{\text{cantidad de arcos ejercitados}}{\text{cantidad de arcos}}
$$
Si recorremos todos los arcos, entonces recorremos todos los nodos. Por lo tanto **el cubrimiento de arcos incluye al cubrimiento de sentencias, pero no se cumple la reciproca.**

### Cubrimiento de Decisiones (o Branches)
Criterio de Adecuación: cada decisión en el CFG debe ser ejecutado.
Cobertura del criterio:
$$
 \frac{\text{cantidad de decisiones ejercitadas}}{\text{cantidad de decisiones}}
$$
Por cada arco True o arco False, debe haber al menos un test case que lo ejercite.

### Cubrimiento de Condiciones Básicas
Criterio de adecuación: cada condición básica de cada decisión en el CFG debe ser evaluada a verdadero y a falso al menos una vez.

Condicion basica: es una formula atomica (no divisible) que componen una decision.

- Ejemplo: `(digitHigh==1 || digitLow==-1) && len>0`
    Condiciones básicas del ejemplo:
    - `digitHigh==1`
    - `digitLow==-1`
    - `len>0`
Cobertura del criterio:
$$
 \frac{\text{cantidad de valores evaluados en cada condición}}{2  \cdot \text{cantidad de condiciones básicas}}
$$

El criterio de cubrimiento de Branches y condiciones básicas necesita 100% de cobertura de branches y 100% de cobertura de condiciones básicas.

Branch coverage no implica cubrimiento de Condiciones Básicas.

### Cubrimiento de Caminos
Criterio de Adecuación: cada camino en el CFG debe ser transitado por al menos un test case.

Cobertura del criterio:

$$
 \frac{\text{cantidad de caminos transitados}}{\text{cantidad total de caminos}}
$$

- No es algo muy practico ya que la cantidad de caminos puede no estar acotada.
- Se usa poco en la practica