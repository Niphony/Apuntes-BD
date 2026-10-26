# Introducción a PostgreSQL

## ¿Qué es PostgreSQL?
Es un sistema de gestión de bases de datos objeto-relacional de código abierto. Es ampliamente reconocido por su robustez, extensibilidad y estricto cumplimiento de los estándares SQL. 

## Características Principales
*   **Código Abierto:** Es mantenido por una comunidad global siguiendo la filosofía del software libre.
*   **Gestor Objeto-Relacional:** Soporta conceptos de programación orientada a objetos aplicados directamente en la base de datos.
*   **Estándar SQL:** Tiene un alto cumplimiento del estándar, lo que facilita las migraciones desde o hacia otros motores como Oracle.
*   **Tipos de Datos Avanzados:** Soporta rangos, arreglos, formato JSON y datos geoespaciales nativamente.
*   **Concurrencia:** Permite múltiples lecturas y escrituras simultáneas por diferentes usuarios sin bloqueos.
*   **Replicación y Backups:** Posee capacidades nativas para establecer reglas y crear copias de seguridad automatizadas.

## Instalación
*   Durante el proceso de instalación, el sistema solicitará definir una contraseña de superusuario. La recomendación estricta de la clase es utilizar **`postgres`** (en minúsculas) para estandarizar el acceso y evitar olvidos, ya que es la misma que usan los equipos de la universidad.
*   El puerto por defecto suele ser el 5432 o 5433; si hay conflictos, se puede cambiar (ej. 5435).
*   Se instalarán varios componentes. El *Stack Builder* (gestor de paquetes adicionales) se puede omitir o cancelar al finalizar la instalación inicial.

Aca puedes ver el [[Entorno]]. 