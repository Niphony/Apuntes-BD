# Árboles rojinegros y su comparación con los árboles AVL

## 1. ¿Qué es un árbol rojinegro?

Un **árbol rojinegro (Red-Black Tree)** es una estructura de datos no lineal basada en un árbol binario de búsqueda (ABB), en el que cada nodo tiene asignado uno de dos colores: rojo o negro. Estos colores permiten mantener el árbol aproximadamente balanceado durante las operaciones de inserción y eliminación.

Su objetivo principal es garantizar que la altura del árbol permanezca en un orden logarítmico respecto al número de nodos, evitando que las operaciones de búsqueda, inserción y eliminación se degraden hasta comportarse como una lista enlazada.

Para mantener el balance, los árboles rojinegros utilizan reglas de coloración, rotaciones y recoloreos de nodos.

## 2. Propiedades de un árbol rojinegro

Un árbol rojinegro debe cumplir las siguientes propiedades:

1. **Propiedad de color:** cada nodo es rojo o negro.
    
2. **Raíz negra:** la raíz del árbol siempre debe ser negra.
    
3. **Hojas negras:** todas las hojas NIL (nodos externos que representan hijos nulos) son negras.
    
4. **Restricción de nodos rojos:** un nodo rojo no puede tener un padre rojo ni un hijo rojo. Es decir, no pueden existir dos nodos rojos consecutivos en un camino.
    
5. **Altura negra uniforme:** todos los caminos desde un nodo hasta sus hojas NIL descendientes contienen la misma cantidad de nodos negros.
    

Estas propiedades garantizan que la altura del árbol esté acotada por:

[  
h \leq 2\log_2(n+1)  
]

Donde:

- (h) representa la altura del árbol.
    
- (n) representa el número de nodos internos.
    

## 3. Operaciones principales

### Búsqueda

La búsqueda funciona igual que en un árbol binario de búsqueda tradicional: se compara el valor buscado con el nodo actual y se continúa por el subárbol izquierdo o derecho.

Su complejidad en el peor caso es (O(\log n)).

### Inserción

El nuevo nodo se inserta siguiendo las reglas de un árbol binario de búsqueda. Normalmente se asigna el color rojo al nodo recién insertado. Después, se revisan las propiedades del árbol y se aplican rotaciones o recoloreos cuando sea necesario.

La complejidad en el peor caso es (O(\log n)).

### Eliminación

La eliminación comienza como en un árbol binario de búsqueda. Sin embargo, quitar un nodo negro puede alterar la cantidad de nodos negros de algunos caminos, por lo que es necesario realizar ajustes para recuperar las propiedades rojinegras.

La complejidad en el peor caso es (O(\log n)).

### Rotaciones

Las rotaciones son transformaciones locales que cambian la estructura del árbol sin alterar el orden de sus elementos. Existen dos tipos básicos:

- **Rotación izquierda:** reorganiza un nodo con su hijo derecho.
    
- **Rotación derecha:** reorganiza un nodo con su hijo izquierdo.
    

## 4. ¿Qué es un árbol AVL?

Un **árbol AVL** es un árbol binario de búsqueda autoequilibrado que mantiene una diferencia de altura limitada entre los subárboles izquierdo y derecho de cada nodo.

Esta diferencia se conoce como factor de equilibrio y se calcula mediante:

[  
FE(n)=h(\text{izquierdo})-h(\text{derecho})  
]

Para que el árbol AVL esté equilibrado, cada nodo debe cumplir:

[  
FE(n)\in{-1,0,1}  
]

Cuando una inserción o eliminación rompe esta condición, se aplican rotaciones simples o dobles para restaurar el equilibrio.

## 5. Diferencias entre árboles rojinegros y AVL

|Característica|Árbol rojinegro|Árbol AVL|
|---|---|---|
|Tipo|Árbol binario de búsqueda autoequilibrado|Árbol binario de búsqueda autoequilibrado|
|Criterio de balance|Reglas de color y altura negra|Diferencia de altura entre subárboles|
|Información adicional|Color de cada nodo|Factor de equilibrio o altura|
|Equilibrio|Menos estricto|Más estricto|
|Búsqueda|(O(\log n)) en el peor caso|(O(\log n)) en el peor caso|
|Inserción|(O(\log n)) en el peor caso|(O(\log n)) en el peor caso|
|Eliminación|(O(\log n)) en el peor caso|(O(\log n)) en el peor caso|
|Rotaciones|Puede necesitar rotaciones y recoloreos|Puede necesitar rotaciones simples o dobles|
|Búsquedas frecuentes|Buen rendimiento|Suele favorecer las búsquedas gracias a su mayor equilibrio|
|Actualizaciones frecuentes|Suele ser una buena opción|Puede requerir más ajustes de balance, especialmente al eliminar|

## 6. Ventajas y desventajas

### Árboles rojinegros

**Ventajas:**

- Mantienen operaciones de búsqueda, inserción y eliminación en tiempo (O(\log n)).
    
- Su balance es menos estricto, lo que suele favorecer las actualizaciones frecuentes.
    
- Combinan rotaciones y recoloreos para recuperar sus propiedades.
    

**Desventajas:**

- Sus reglas de balance son más complejas de comprender e implementar.
    
- Las búsquedas pueden recorrer más niveles que en un AVL equivalente.
    

### Árboles AVL

**Ventajas:**

- Mantienen una altura más reducida gracias a su balance estricto.
    
- Suelen ser convenientes cuando las búsquedas son muy frecuentes.
    
- Su criterio de equilibrio se basa directamente en las alturas de los subárboles.
    

**Desventajas:**

- Las inserciones y eliminaciones pueden exigir ajustes de equilibrio.
    
- La eliminación puede requerir reajustes en varios niveles del árbol.
    
- Es necesario mantener correctamente las alturas o los factores de equilibrio.
    

## 7. Conclusión

Los árboles rojinegros y los árboles AVL son estructuras de datos diseñadas para mantener ordenados los elementos y garantizar operaciones eficientes.

La principal diferencia radica en su mecanismo de equilibrio: los AVL controlan directamente la diferencia de altura de los subárboles, mientras que los rojinegros utilizan reglas de coloración y altura negra.

En términos generales, un AVL puede ser una buena elección cuando predominan las búsquedas, mientras que un árbol rojinegro suele ser conveniente cuando existe una combinación frecuente de búsquedas, inserciones y eliminaciones.

Ambos ofrecen complejidad logarítmica en sus operaciones principales, por lo que la elección depende de las necesidades de la aplicación y de los costos de implementación.