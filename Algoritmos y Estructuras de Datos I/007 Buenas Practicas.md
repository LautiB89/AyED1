# Buenas Practicas de Programación
## Nombres de variables y funciones
- Usar nombres que revelen la intención de los elementos nombrados. El nombre de una variable/función debería decir todo lo que hay que saber sobre la variable/función!
	1. Los nombres deben referirse a conceptos del dominio del problema.
	2. Una excepción suelen ser las variables con scopes pequeños. Es habitual usar i, j, k para las variables de control de los ciclos
	3. Si es complicado decidirse por un nombre o un nombre no parece natural, quizas es porque esa variable o función no representa un concepto claro del problema a resolver.
- Evitar la desinformación.
	1. Llamar hp a la hipotenusa es una mala idea
	2. Tener variables llamadas
		**cantidadDeElementosEnElEjeXSinMarcar** y
		**cantidadDeElementosEnElEjeYSinMarcar** no es una buena idea.
- Usar nombres pronunciables! No es una buena idea tener una variable llamada cdcptdc para representar la "cantidad de cuentas por tipo de cliente"
- Se debe tener un nombre por concepto. No tener funciones llamadas grabar, guardar y registrar
- Los nombres de las funciones deben representar el concepto calculado, o la acción realizada en el caso de las funciones **void**.
- No hacer chistes!
##### Mantener una buena indentación
## Comentarios
- Ademas de escribir comandos, los lenguajes de programación permiten escribir comentarios.
- Tipos de comentarios en C++:
	- Comentario de línea: // ...
	- Comentario de bloque: / * ... * /
- Es importante hacer un uso adecuado de los comentarios, para que no oscurezcan el código.
- Los comentarios no arreglan codigo de mala calidad! En lugar de comentar el codigo, hay que clarificarlo.
- Es importante expresar las ideas en el codigo, y no en los comentarios
- Los mejores comentarios son  los conceptos que no se pueden escribir en el lenguaje de programación utilizado:
	1. Explicar la intención del programador.
	2. Explicitar precondiciones o suposiciones.
	3. Clarificar codigo que a primera vista puede no ser claro.
## Inicialización de Variables
En C/C++ podemos tener variables declaradas pero no inicializadas, y el valor que contienen en ese caso es impredecible (decimos que contienen "basura").
Para evitar esta situación, es recomendable inicializar siempre las variables.
## Funciones
Las funciones deben ser pequeñas! Una función con demasiado codigo es dificil de entender y mantener.
1. Encapsular comportamiento dentro de funciones auxiliares!
**Regla fundamental.** Cada función debe...
1. ... hacer solo una cosa,
2. ... hacerla bien, y
3. ... ser el unico componente del programa encargado de esa tarea particular.
Las funciones no deben tener efectos colaterales! En particular, el uso de variables globales debe ser particularmente cuidado.
## Formato vertical
- Los archivos del proyecto no deben ser demasiado grandes!
- Conceptos relacionados deben aparecer verticalmente cerca en los archivos
- Las funciones mas importantes deben estar en la parte superior, seguidas de las funciones auxiliares
	1. Siempre la funcion llamada debe estar debajo de la funcion llamadora.
	2. Las funciones menos importantes deben estar en la parte inferior del archivo.
- Se suele equiparar un archivo de codigo con un articulo periodistico. Debemos poder interrumpir la lectura en cualquier momento, teniendo informacion acorde con la lecture realizada.
## Modularización
- Cada archivo del proyecto debe tener codigo homogeneo, y relacionado con un concepto o grupo de conceptos coherentes.
- Los nombres de los archivos tambien deben ser representativos!
- Muchos lenguajes de programación dan facilidades para organizar archivos en paquetes (o conceptos similares), para tener una organizacion en mas de un nivel.
- **Single responsibility principle:** Cada función debe tener un unico motivo de cambio.
	1. Interfaz de usuario.
	2. Tecnología para la interfaz de usuario.
	3. Lógica de negocio.
	4. Consideraciones sobre los algoritmos.
	5. Almacenamiento permanente.
	6. ...
- El codigo responsable de cada uno de estos aspectos debe estar separado del resto!
## Al momento de escribir código
**Desarrollo incremental:** Escribir bloques pequeños y testeables de funcionalidad teniendo en todo momento una aplicación (parcialmente) funcional.
   1. Esto implica conocer en todo momento el objetivo del codigo que estamos escribiendo
   2. Si se usa un repositorio de control de versiones, el proximo commit debe estar bien definido.
- Para el codigo mas critico, recurrir a **pair programming**: dos personas juntas sobre una unica computadora.
- Descansar! Es importante destinar tiempo de descanso entre las sesiones de codigo. 