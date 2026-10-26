Operación matemática que multiplica los conjuntos (tablas). Si se tiene una tabla M (filas) y N (columnas), al multiplicarse su conjunto daria como resultado otra tabla M x N filas.

#### Ejemplo:

![[Pasted image 20260908184218.png]]

### Operador JOIN:
Es el operador que permite el producto cartesiano se aplica hacia una selección ($\sigma$), solo sobreviven las combinaciones validas.

```sql
SELECT Students.name, Students.grade, Courses.course, Courses.level
FROM Students
CROSS JOIN Courses;
```

Es bueno dejar las tablas con nombres mas cortos como M y N .  Un ejemplo de esto es el INNER JOIN, ON para establecer la condición sobre:

```sql
SELECT c.customer_id, c.email, o.order_date
FROM customers AS c
INNER JOIN orders AS o 
  ON c.customer_id = o.customer_id;
```

Se tiene que especificar el origen para tener solo datos específicos si se necesitan.

### Tipos de JOIN:

- **INNER JOIN (Interno):** Es el más común (se usa en el 70-80% de los casos). Solo devuelve las filas que tienen una coincidencia exacta en ambas tablas.
**Ejemplo:**
```sql
SELECT autores.id_autor, libros.titulo
FROM libros 
RIGHT JOIN autores
    ON autores.id_autor = libros.id_autor; 
```

- **LEFT JOIN (Externo Izquierdo):** Conserva **absolutamente todas** las filas de la tabla de la izquierda (la primera que se escribe en el código), sin importar si tienen o no coincidencias en la tabla de la derecha.
    
    - Si no hay coincidencia, la base de datos rellena los campos de la derecha con valores `NULL`.
        
    - _Caso de uso estrella:_ Sirve para encontrar ausencias. Si se busca `WHERE columna_derecha IS NULL`, se pueden encontrar casos críticos como "Estudiantes que no matricularon nada este semestre" o "Clientes que jamás han comprado".

- **RIGHT JOIN (Externo Derecho):** Funciona exactamente igual que el Left Join, pero conservando todas las filas de la tabla de la derecha (la segunda en escribirse).
    
    - _Caso de uso:_  Útil para hallar "Cursos que no tienen ningún estudiante matriculado". El profesor aclaró que habitualmente se prefiere usar LEFT JOIN e invertir el orden de las tablas en el código porque es más natural leer de izquierda a derecha.
**Ejemplo:**
```sql
SELECT autores.id_autor, libros.titulo
FROM libros 
RIGHT JOIN autores
    ON autores.id_autor = libros.id_autor; 
```

- **FULL OUTER JOIN:**  Existe para traer todo de ambas tablas (hayan coincidencias o no), pero advirtió que rara vez se utiliza.