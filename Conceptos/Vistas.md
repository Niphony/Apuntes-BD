# CREATE VIEW
Sirve para desde un SELECT especifico, tener una consulta guardada por nombre como una tabla virtual, sin afectar a la real.
- Refleja datos reales
- Guarda Joins
- Solo ve la vista no la tabla base
## Ejemplo:

```sql
CREATE VIEW v_ventas_por_categoria AS
SELECT cat.nombre   AS categoria,
       COUNT(f.id)  AS total_ventas,
       SUM(j.precio * f.cantidad) AS ingresos
FROM categorias cat
JOIN juegos j   ON j.id_categoria = cat.id
LEFT JOIN facturas f ON f.id_juego = j.id
GROUP BY cat.id, cat.nombre
ORDER BY ingresos DESC;
```

Las vistas no guardan datos, solo el query (la consulta) de estos.

Accede a lo ya hecho por el [[CRUD]]. Por eso mismo se actualiza cuando las reales lo hagan. Aunque se puede editar datos en la vista desde ciertas condiciones no es recomendable. Sin [[Producto cartesiano (JOIN)]] o [[Where - Group By]], se pueden editar. Pero **NO ES RECOMENDABLE HACERLO DESDE LA VISTA**. 

Si se dropea no elimina ningun dato real.

