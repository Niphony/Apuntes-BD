Depende del problema, y lo que se quiera realizar.

**Tablas (lo normal):** muchas entidades relacionadas; reglas que la base debe garantizar (FK, CHECK); operaciones que cambian varias tablas a la vez; reportes que cruzan todo. Ej.: matrículas, inventario, facturación.

**Tablas + JSONB:** modelo relacional con una parte de atributos variables; guardar datos externos tal como llegan (respuesta de API, eventos). Ej.: catálogo con características distintas por categoría; auditoría con "antes y después" en JSON.

**MongoDB:** datos que se leen como agregados completos; esquema que cambia seguido; muchísimos datos repartidos en varios servidores. Ej.: contenido y perfiles, eventos de aplicaciones, catálogos muy grandes.

> Para la mayoría de proyectos (curso y empresa), la respuesta honesta es: **PostgreSQL, y JSONB donde haga falta**. MongoDB brilla cuando el agregado es la unidad de trabajo.
