El WHERE se usa para seleccionar la columna y sirve para contener las condicionales multiples de AND, OR, NOT.

![[Pasted image 20260930092349.png]]


### Operadores Especiales:
También el WHERE tienes operaciones como BETWEEN, LIKE, IN, IS NULL/IS NOT NULL

![[Pasted image 20260930092433.png]]


## Group By:
Divide las filas en grupos segun una columna, y luego aplica [[Agregación]] a cada grupo:

```sql
SELECT   cod_curso,  COUNT(*)  AS inscritos,  AVG(nota)  AS promedio
FROM     INSCRIPCIONES
GROUP BY cod_curso;
```


![[Pasted image 20260930094220.png]]

Dentro del group by esta el **Having** para filtrar los grupos despues de agrupar por medio de su contenido

![[Pasted image 20260930094542.png]]