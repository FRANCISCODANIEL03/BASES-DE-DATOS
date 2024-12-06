# Práctica 3
# Roles de usuario
***
## Ejercicio 1: Crear roles básicos
Crea dos roles:
* 1.- `rol_lector` : Permite solo lectura ( `SELECT` ) en la base de datos `biblioteca`.
* 2.- `rol_editor` : Permite modificar datos ( `INSERT` , `UPDATE` , `DELETE` ) en la tabla `libros`.
```sql
CREATE ROLE 'rol_lector';
CREATE ROLE 'rol_editor';
GRANT SELECT ON biblioteca.* TO 'rol_lector';
GRANT INSERT, UPDATE, DELETE ON biblioteca.libros TO 'rol_editor';
```
* *
## Ejercicio 2: Asignar roles a usuarios
Asigna el rol `rol_lector` al usuario `lector` y el rol `rol_editor` al usuario `editor`.
```sql
GRANT 'rol_lector' TO 'lector'@'%';
GRANT 'rol_editor' TO 'editor'@'%';
```
* *
## Ejercicio 3: Revocar un rol
El usuario `editor` ya no debe tener permisos de edición. Revoca el rol asignado.
```sql
REVOKE 'rol_editor' FROM 'editor'@'%';
```
* *