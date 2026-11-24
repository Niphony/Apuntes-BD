## ¿Para qué sirve?

Para la escala, disponibilidad y la forma de los datos, no todo iba bien con las columnas fijas.sorprende

- NoSQL = "Not only SQL"

Que se tiene en cuenta para NoSQL:
- Diseñar esquemas mas cuidadosamente debido al diseño flexible que presenta.
- Se usa SQL para reglas y relaciones, NoSQL para problemas de cache o catálogos, etc..
- Antes agregar una columna bloqueaba la tabla actualmente al reemplazar solo metadatos no ocurre.
- NoSQL puede ser mas rápido pero depende del patrón, para un documento completo es rápido, para entidades es mejor SQL.

## Tipos:
- **Documento:** JSON con campos anidados y arreglos, donde pueden haber campos distintos. Se consulta por cualquier campo.
- **Clave-Valor:** Un diccionario donde se consulta por la clave.
- **Columna ancha:** Filas agrupadas por una clave de partición, cada fila puede tener columnas distintas, se consulta por la clave de partición.
- **Grafo:** Nodos con relaciones y propiedades, se recorren por medio de las relaciones.

## Ejemplos:
Mismo dato en los 4 tipos.
- **// CLAVE-VALOR (Redis)**
    
- SET carrito:ana '{"items":["Laptop","Mouse"]}'
    
- GET carrito:ana
    
- // la base no sabe qué hay adentro

- **// DOCUMENTO (MongoDB)**
    
- { cliente: { nombre: "Ana", ciudad: "Bogotá" },
    
-   items: [ { producto: "Laptop", qty: 1 },
    
-            { producto: "Mouse",  qty: 2 } ] }
    
- // se puede buscar por items.producto

- **-- COLUMNAR (Cassandra): una tabla POR CONSULTA**
    
- -- "pedidos de un cliente, recientes primero"
    
- PRIMARY KEY ((cliente), fecha)
    
- ana | 2026-03-15 | Laptop, Mouse
    
- ana | 2026-01-02 | Teclado

- **// GRAFO (Neo4j)**
    
- (Ana)-[:COMPRÓ]->(Laptop)
    
- (Ana)-[:COMPRÓ]->(Mouse)
    
- (Luis)-[:COMPRÓ]->(Laptop)
    
- // "quienes compraron Laptop también compraron…"


Para ver como se maneja el [[CRUD NoSQL]].

De aca se puede ver un [[Agregaciones o Embebido (mini - ejemplo)]].

