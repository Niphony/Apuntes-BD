Errores de pasar del relacional a documentos.

| Antipatrón | Ejemplo | Por qué falla | Mejor |
|------------|---------|---------------|-------|
| **Arreglos que crecen sin límite** | Todos los comentarios de un post dentro del post | Cada comentario reescribe un documento cada vez más grande hasta chocar con 16 MB | Comentarios en su propia colección con `post_id` |
| **Normalizar como en SQL** | Ocho colecciones para un catálogo, cada pantalla con varios `$lookup` | Se pierde la ventaja del documento y no hay FK que proteja referencias | Embeber lo que se lee junto; si todo es relacional, usar PostgreSQL |
| **Uniones en la aplicación** | Una consulta por cada ítem para mostrar un pedido (problema N+1) | 50 ítems = 50 idas y vueltas a la base | Embeber lo que se muestra, o un solo `$lookup` / `$in` con todos los `_id` |

> El segundo antipatrón es el más común entre estudiantes que vienen de SQL: **un documento no es una fila.**