La normalización es el estándar al momento de creación de tablas para mantener un orden de la información y poder generar orden entre atributos para no tener la duplicación de datos, genrando las tablas necesarias.

### Dependencia Funcional - La base de todo
[[Primera Forma Normal - (1FN)]]
- Se intenta buscar **dependencias funcionales** como por ejemplo si conozco el ID de un empleado, que este este ligado al nombre y que siempre obtenga el mismo.
- X → Y: conociendo el valor de X, siempre podemos determinar el valor de Y de forma única.

   ![[Pasted image 20260914174013.png|478]]

### Dependencia Parcial - (2FN)
[[Segunda Forma Normal - (2FN)]]
Un atributo no-clave depende de solo UNA PARTE de la clave primaria compuesta, no de toda:

![[Pasted image 20260914175150.png]]

![[Pasted image 20260914175239.png]]


### Dependencia Transitiva - (3FN)
[[Tercera Forma Normal - (3FN)]]
Un atributo no-clave determina a OTRO no-clave. La dependencia llega a la PK solo de forma indirecta.

![[Pasted image 20260914175557.png]]