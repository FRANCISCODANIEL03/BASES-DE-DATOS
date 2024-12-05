# Practica 2
# Manipulación de usuarios
***
## Ejercicio 1: Otorgar permisos básicos
Otorga permisos de lectura ( `SELECT` ) sobre la base de datos `biblioteca` al usuario `lector`
desde cualquier dirección IP.
```sql
GRANT SELECT ON biblioteca.* TO 'lector'@'%';
```
* *
## Ejercicio 2: Otorgar permisos de escritura
Otorga permisos para insertar y actualizar ( `INSERT` , `UPDATE` ) datos en la tabla `libros`al
usuario `editor`.
```sql
GRANT INSERT, UPDATE ON biblioteca.libros TO 'editor'@'%';
```
* *
## Ejercicio 3: Revocar permisos específicos
Revoca el permiso de actualización ( `UPDATE` ) al usuario `editor`.
```sql
REVOKE UPDATE ON biblioteca.libros FROM 'editor'@'%';
```
* *