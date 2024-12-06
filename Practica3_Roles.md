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
## Ejercicio 4: Activar roles
Los usuarios no pueden usar un rol asignado hasta que lo activen explícitamente. Activa el rol
`rol_lector` para el usuario `lector` en su sesión actual.
```sql
SET ROLE 'rol_lector';
```
* *
## Ejercicio 5: Ver roles asignados
Consulta los roles asignados a los usuarios para verificar configuraciones.
```sql
SELECT * FROM information_schema.applicable_roles;
```
![image.png](/imgs/P3_roles.png)
* *
## Ejercicio 6: Crear un rol combinado
Crea un rol llamado `rol_administrador` que combine los permisos de `rol_lector` y
`rol_editor`. Luego, asígnalo al usuario `admin_biblioteca`.
```sql
CREATE ROLE 'rol_administrador';
GRANT 'rol_lector', 'rol_editor' TO 'rol_administrador';
GRANT 'rol_administrador' TO 'admin_biblioteca'@'localhost';
```
