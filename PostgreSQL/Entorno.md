# Entorno PG Admin y Estructura de Bases de Datos

## ¿Qué es PG Admin?
Es el software con interfaz gráfica utilizado para gestionar, administrar e interactuar visualmente con el servidor PostgreSQL.

## Estructura Jerárquica del Entorno
1.  **Servidor:** Al abrir PG Admin, te conectarás al servidor local de tu equipo introduciendo la contraseña configurada (`postgres`).
2.  **Bases de Datos (Databases):** Dentro del servidor puedes tener múltiples bases de datos. Por defecto existe una llamada `postgres`. Durante la clase se crea una de prueba (ej. `demo_universidad`).
3.  **Esquemas (Schemas):** Son contenedores lógicos que funcionan como "carpetas" dentro de la base de datos para organizar los distintos objetos. El esquema por defecto donde se trabaja es el `public`.
4.  **Tablas (Tables):** Las tablas se almacenan siempre dentro de un esquema. La ruta visual en PG Admin es: `Bases de datos > [Tu BD] > Schemas > public > Tables`.

## Query Tool (Herramienta de Consultas)
Es la consola integrada donde se escribe y ejecuta el código SQL.
*   Se accede haciendo clic derecho directamente sobre el nombre de tu base de datos y seleccionando **Query Tool**.
*   **Concepto de Query:** En bases de datos, cada instrucción, acción o bloque de código que se ejecuta se denomina *query* (consulta).
*   **Ejecución Correcta:** La barra superior tiene un botón de "Play" que ejecuta todo el script. Sin embargo, se recomienda utilizar el botón que tiene un **"1"**, ya que este ejecuta **únicamente la consulta que tengas seleccionada** con el cursor, evitando que se corra todo el código escrito accidentalmente.

Luego siguen los [[Tablas y Tipos]]. 
