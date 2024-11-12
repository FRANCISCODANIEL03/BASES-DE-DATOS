# Privilegios de Usuarios en MySQL
- - - 
En MySQL, los privilegios determinan qué operaciones puede realizar un usuario sobre las bases de datos y los objetos de la base de datos. Los privilegios se asignan a los usuarios cuando se crean o mediante el uso de los comandos GRANT y REVOKE . Estos privilegios pueden ser generales, para toda la base de datos, o específicos para una tabla, columna o incluso una consulta.

## ~ Ejercicios
- - -
1. ### Ejercicio 1: Crear un Usuario con Privilegios Específicos
 
*Enunciado:*
*	Crea un usuario llamado empleado con la     contraseña empleado123 .
*	Asigna al usuario empleado permisos de solo lectura ( `SELECT` ) sobre la base de datos empresa_db .
*	El usuario empleado no debe poder modificar ni eliminar datos en empresa_db .
```sql
CREATE USER "empleado"@"localhost" IDENTIFIED BY "empleado123";

GRANT SELECT ON empresa_db.* TO  "empleado"@"localhost";

REVOKE UPDATE, DELETE ON empresa_db.* FROM "empleado"@"localhost";

FLUSH PRIVILEGES;
```

2. ### Ejercicio 2: Revocar Privilegios y Modificar Permisos
 
*Enunciado:*
* El usuario empleado anteriormente tenía permisos de solo lectura sobre la base de datos empresa_db .
* Ahora, revoca el privilegio `SELECT` al usuario empleado y asigna el privilegio `INSERT` para que pueda agregar datos a las tablas de empresa_db .
```sql
REVOKE SELECT ON empresa_db.* FROM "empleado"@"localhost";

GRANT INSERT ON empresa_db.* TO  "empleado"@"localhost";

FLUSH PRIVILEGES;
```
