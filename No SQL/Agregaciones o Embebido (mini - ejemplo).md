## Agregación pipeline

Una cadena de etapas; cada una recibe los documentos de la anterior.

| Etapa      | Equivalente SQL                  |
| ---------- | -------------------------------- |
| `$match`   | `WHERE`                          |
| `$group`   | `GROUP BY` + `SUM`/`AVG`/`COUNT` |
| `$sort`    | `ORDER BY`                       |
| `$limit`   | `LIMIT`                          |
| `$project` | `SELECT` (elegir/renombrar)      |
| `$lookup`  | JOIN con otra colección          |

**Ejemplo — Top 3 ciudades por ventas:**

```js
db.pedidos.aggregate([
  { $match: { estado: "completado" } },
  { $group: {
    _id: "$cliente.ciudad",
    ventas_total: { $sum: "$total" },
    num_pedidos:  { $sum: 1 }
  }},
  { $sort: { ventas_total: -1 } },
  { $limit: 3 }
])
```

- `"$total"` con `$` significa "el valor del campo total".
- El `_id` de `$group` es el campo por el que se agrupa.

---

## $unwind

Despliega un arreglo en un documento por cada elemento. Necesario para agrupar por algo dentro de un arreglo (p. ej., por producto).

**Antes:** 1 documento
```json
{ "numero": "ORD-001",
  "items": [
    { "producto": "Laptop", "qty": 1 },
    { "producto": "Mouse",  "qty": 2 }
  ] }
```
`$unwind: "$items"` → **Después:** 2 documentos
```json
{ "numero": "ORD-001", "items": { "producto": "Laptop", "qty": 1 } }
{ "numero": "ORD-001", "items": { "producto": "Mouse",  "qty": 2 } }
```

Es equivalente a un JOIN de pedidos con ítems_pedido (una fila por ítem). Luego:
```js
{ $group: { _id: "$items.producto", unidades: { $sum: "$items.qty" } } }
```
da las unidades vendidas por producto.

---

## Embeber o referenciar

Es la decisión que más pesa en un modelo de documentos. Pregunta guía: *¿qué pantalla o endpoint lee esto, y con qué frecuencia?*

### Embeber (dentro del documento)
**Cuándo:**
- Se lee siempre junto con el padre.
- Son pocos y su número está acotado.
- No tiene vida propia fuera del padre.

**Ganas:** una sola lectura sin `$lookup`; escritura atómica con el padre.

**Ejemplo:** ítems de un pedido; direcciones de un cliente.

### Referenciar (guardar el `_id`)
**Cuándo:**
- Se comparte entre muchos documentos.
- Crece sin límite (riesgo de superar 16 MB).
- Se consulta o actualiza por separado.

**Ganas:** sin duplicación (se actualiza en un lugar); documentos pequeños.

**Ejemplo:** producto del catálogo; comentarios de un post.

### Visualización: mismo pedido, dos diseños

**Embebido** (1 lectura):
```js
{ numero: "ORD-001",
  cliente: { _id: 7, nombre: "Ana García", ciudad: "Bogotá" },
  items: [
    { producto_id: 101, nombre: "Laptop ThinkPad", qty: 1, precio: 3500000 },
    { producto_id: 205, nombre: "Mouse Logitech",  qty: 2, precio: 85000 }
  ],
  total: 3670000 }
```
`db.pedidos.findOne({ numero: "ORD-001" })`

**Referenciado** (3 lecturas o `$lookup`):
```js
// pedidos   { numero: "ORD-001", cliente_id: 7, items: [...] }
// clientes  { _id: 7, nombre: "Ana García", ciudad: "Bogotá" }
// productos { _id: 101, nombre: "Laptop ThinkPad", precio: 3600000 }
```
El precio que se ve es el de *hoy*, no el que pagó. El diseño más común en la práctica es el de la izquierda: embebe lo que se muestra y guarda el `_id` por si hace falta ir al catálogo.


Para No SQL tenemos [[Antipatrones]] que son errores comunes al realizar un ejercicio de documento.