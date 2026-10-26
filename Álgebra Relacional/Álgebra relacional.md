Lenguaje formal de consulta basado en operaciones algebraicas para conjuntos de tuplas, es la base de [[PostgreSQL]], ya que trabaja internamente con un árbol algebraico, para razonar con precisión el sentido de una consulta.

Esta detrás de los motores de BD

### ¿Cómo funcionan las consultas?

![[Pasted image 20260907104420.png]]

### Operadores primitivos:

- **FIltrar filas (Seleccion) ($\sigma$):** Devuelve solo las tuplas que satisfacen una condición el esquema no cambia, equivale al WHERE. Va entre parentesis como ultima condición en el álgebra relacional.


- **Elegir Columnas (Proyección) ($\pi$):** Devuelve solo los atributos especificados. El número de filas no cambia (solo la eliminación de duplicados), equivale al SELECT. Por ejemplo una relación de A1, A2 devolviendo solo las condiciones que se cumplan.

Resumen:

![[Pasted image 20260907104306.png]]

### Condiciones Compuestas:
- **AND:** Ambos datos deben cumplirse.
- **OR:** Basta con una que se cumple.
- **NOT:** Niega la condición.


### Equivalencia de álgebra relacional a SQL:

![[Pasted image 20260907104345.png]]

![[Pasted image 20260907111137.png|536]]


