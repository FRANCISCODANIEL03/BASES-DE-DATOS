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
## Ejercicio 4: Modificar permisos existentes
El usuario `lector` necesita permisos adicionales para consultar y exportar datos. Otórgale
también permisos de lectura en `SHOW DATABASES`.
```sql
GRANT SELECT, SHOW DATABASES ON *.* TO 'lector'@'%';
```
![users.png](/imgs/P3_roles.png)
> Nota: Para poder ejecutar esta consulta se necesita iniciar sesion con el ususario indicado
* *
## Ejercicio 5: Eliminar usuarios
Elimina al usuario `usuario_remoto` y asegúrate de que ya no aparezca en la lista de usuarios.
```sql
DROP USER 'usuario_remoto'@'%';
SELECT User, Host FROM mysql.user;
```