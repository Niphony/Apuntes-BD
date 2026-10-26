# Operaciones Básicas (CRUD) y Advertencias

El estándar SQL se basa en 4 funciones elementales: Insertar (Create), Consultar (Read), Actualizar (Update) y Borrar (Delete).

## 1. Insertar Datos (INSERT)
Sintaxis utilizada para agregar nuevas filas a una tabla.
```sql
INSERT INTO Facultades (nombre) VALUES ('Ingeniería');
```
*   **Atención:** El orden de las columnas declaradas debe coincidir exactamente con el orden de los datos en `VALUES`.
*   Si la tabla tiene un campo autoincremental (`serial`), **no se debe incluir en el INSERT**, ya que PostgreSQL generará y asignará el siguiente número de forma automática.

## 2. Consultar Datos (SELECT)
Es el *query* más frecuente, usado para recuperar información, aplicar filtros y generar informes.
```sql
-- Traer todas las columnas de la tabla
SELECT * FROM profesores;

-- Traer únicamente columnas específicas
SELECT nombre, email FROM profesores;

-- Filtrar resultados y ordenarlos alfabéticamente
SELECT nombre, email FROM profesores WHERE facultad_id = 1 ORDER BY nombre;
```

## 3. Actualizar Datos (UPDATE)
Modifica la información de registros ya existentes.
```sql
UPDATE profesores SET telefono = '3001234567' WHERE matricula = 1;
```

**NO** ejecutar un comando `UPDATE` sin la cláusula condicional `WHERE`. Las bases de datos no avisan ni piden confirmación. Si omites el `WHERE`, aplicarás el mismo cambio a **todos los registros de la tabla**, corrompiendo la base de datos. Tampoco existe un botón de "Ctrl+Z".

## 4. Borrar Datos (DELETE)
Elimina registros completos de la base de datos.
```sql
DELETE FROM estudiantes WHERE matricula = 3;
```
1.  **Omisión del WHERE:** Igual que con el `UPDATE`, ejecutar un `DELETE` sin la instrucción `WHERE` vaciará por completo toda la tabla instantáneamente.
2.  **Cuidado con el punto y coma (`;`):** Un error de tipeo común es poner el `;` antes del `WHERE` (ej. `DELETE FROM tabla; WHERE...`). El motor ejecutará el borrado total de la primera instrucción e ignorará la condición.
3.  **Restricciones de Integridad:** Por defecto, PostgreSQL no te permitirá borrar un registro "padre" (ej. una Facultad) si ya existen registros "hijo" (ej. Profesores) referenciándola a través de una Llave Foránea. El sistema arrojará un error de restricción para proteger la integridad referencial de los datos.
