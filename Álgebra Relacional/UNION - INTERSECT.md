## **Unión:** 
Este operador combina los resultados de dos consultas distintas en una sola. 
Su principal característica, además de unificar los datos, es que elimina los registros duplicados automáticamente.  
### Ejemplo de uso: 
Si se desea saber de qué ciudades proviene toda la comunidad académica, se puede unir la consulta de "ciudades de estudiantes" con la de "ciudades de profesores". 
Si hay 1000 estudiantes de Bogotá y 50 profesores de Bogotá, el resultado mostrará "Bogotá" una sola vez.  
Equivale a usar la palabra reservada UNION entre dos sentencias SELECT (ej. SELECT ciudad FROM estudiantes UNION SELECT ciudad FROM profesores). Se pueden encadenar múltiples uniones para reciclar sentencias ya hechas, como unir las ventas de enero con las de diciembre.

```sql
-- Seleccionamos la ciudad de la tabla estudiantes
SELECT ciudad FROM estudiantes
UNION
-- La unimos con la ciudad de la tabla profesores
SELECT ciudad FROM profesores;
``` 

## Intersect:
Este operador devuelve únicamente las filas que están presentes **simultáneamente** en ambos conjuntos.

- Se utiliza la palabra reservada `INTERSECT`.
### **Ejemplo de uso:**
Si se interceptan las ciudades de los estudiantes activos con las ciudades de los estudiantes graduados, el resultado mostrará solo aquellas ciudades que ambos grupos tienen en común.

- **Utilidad:** Sirve para detectar cruces rápidos de información, como averiguar qué clientes hicieron pedidos tanto en enero como en marzo. En parte cumple una función de filtrado de datos en común muy similar a la de un `INNER JOIN`.

```sql
-- Seleccionamos las ciudades solo de los estudiantes activos
SELECT ciudad FROM estudiantes WHERE estado = 'activo'
INTERSECT
-- Seleccionamos las ciudades solo de los estudiantes graduados
SELECT ciudad FROM estudiantes WHERE estado = 'graduado'; 
```
