Controla que se hace sobre que objeto, tenemos:
- **Grant:**
```sql
GRANT privilegio ON objeto TO rol_o_usuario
```
Para otrorgsr permisos de SELECT, INSERT, UPDATE, TRUNCATE, ect...

- **Revoke:**
```sql
REVOKE privilegio ON objeto FROM rol_o_usuario;
```
Quita el permiso asignado con grant. (Se puede usar cascade para este)

- **Create role/user:**
```sql 
-- 1. Crear rol agrupador
CREATE ROLE readonly;

-- 2. Dar permisos al rol
GRANT SELECT ON ALL TABLES IN SCHEMA public TO readonly;

-- 3. Asignar el rol a un usuario concreto
GRANT readonly TO maria;
```

Cada usuario solo debe tener lo recomendable para su tarea. Principio del minimo privilegio.

