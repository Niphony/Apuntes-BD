# Tablas, Tipos de Datos y Llaves (Keys)

## Creación y Modificación de Tablas
Las tablas representan las entidades (del Modelo Entidad-Relación o diagrama de Chen) traducidas a código.

*   **Crear:** Se utiliza la sentencia `CREATE TABLE nombre_tabla ( columna1 tipo, columna2 tipo );`.
*   **Alterar:** Si se cometió un error o se olvidó un campo al crearla, se usa el comando `ALTER TABLE nombre_tabla` para añadir columnas o restricciones sin necesidad de borrar y recrear la tabla completa.

## Tipos de Datos Principales
*   **Texto:** 
    *   `varchar(n)`: Cadena de texto con un límite máximo de *n* caracteres. Ideal para optimizar memoria en nombres, correos, etc.
    *   `text`: Texto extenso sin límite predefinido.
*   **Numéricos:** 
    *   `integer`: Números enteros.
    *   `numeric`: Números exactos con cantidad de decimales personalizable.
    *   `float`: Números de coma flotante.
    *   `serial`: Entero autoincremental. **Muy útil para IDs**, ya que la base de datos aumenta el número sola cada vez que se inserta un registro.
*   **Fecha y Hora:**
    *   `date`: Almacena solo la fecha.
    *   `time`: Almacena solo la hora.
    *   `timestamp`: Almacena fecha y hora exactas.
    *   `interval`: Define duraciones o rangos (ej. "15 minutos").
*   **Otros:** `boolean` (valores lógicos true/false), `uuid` (identificador único universal), `json` (estructuras de datos complejas), `bytea` (archivos binarios sin comprimir, como imágenes).

## Restricciones (Constraints)
Son reglas opcionales que aseguran la consistencia de los datos en las columnas:
*   `NOT NULL`: El campo es obligatorio y no puede quedar vacío al registrar datos.
*   `UNIQUE`: El valor ingresado no puede repetirse en ninguna otra fila de la misma tabla (ideal para emails).
*   *Valores por defecto*: Asignar un valor predeterminado si no se ingresa nada (ej. activo por defecto en `true`).
*   *Reglas personalizadas*: Validaciones matemáticas o de formato.

## Llaves (Primary y Foreign Keys)
*   **Llave Primaria (Primary Key):** Columna (o conjunto de columnas) que identifica de manera única cada registro dentro de una tabla. No admite valores nulos ni repetidos. Si una entidad no tiene un identificador natural evidente, la mejor práctica es agregar una columna `ID` de tipo `serial`.
*   **Llave Foránea (Foreign Key):** Columna que hace referencia directa a la llave primaria de otra tabla. Es el mecanismo técnico para relacionar dos tablas (ej. decir que el ID de Facultad en la tabla Profesores corresponde a una Facultad específica).
*   **Integridad Referencial:** Es el principio que garantizan las llaves foráneas. Asegura que las relaciones sean coherentes (ej. si el nombre de una facultad cambia, la base de datos se actualiza automáticamente sin romper los registros de los profesores asociados).

Con estos elementos se pueden hacer operaciones [[CRUD]].