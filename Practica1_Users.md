# Practica 1 
# Creacion de usuarios
*** 
## Ejercicio 1: Crear un usuario básico
Crea un usuario llamado `biblioteca_usuario` con la contraseña `password123` . Este usuario debe
tener acceso limitado para conectarse solo desde `localhost`.
```sql
CREATE USER 'biblioteca_usuario'@'localhost' IDENTIFIED BY 'password123';
```
* *
## Ejercicio 2: Crear un usuario para acceso remoto
Crea un usuario llamado `usuario_remoto` con la contraseña `remote123` que pueda conectarse
desde cualquier dirección IP ( `%` ).
```sql
CREATE USER 'usuario_remoto'@'%' IDENTIFIED BY 'remote123';
```
* *
## Ejercicio 3: Usuario con restricciones de contraseña
Crea un usuario llamado `usuario_seguro` con la contraseña `seguro123` que expire en 90 días y
permita máximo 5 intentos fallidos de inicio de sesión.
```sql
CREATE USER 'usuario_seguro'@'%' IDENTIFIED BY 'seguro123'
PASSWORD EXPIRE INTERVAL 90 DAY FAILED_LOGIN_ATTEMPTS 5;
```
* *
## Ejercicio 4: Crear varios usuarios a la vez
Crea tres usuarios:
* 1.- `admin_biblioteca` con acceso total desde localhost.
* 2.- `lector` con acceso limitado desde `192.168.0.100`.
* 3.- `editor` con acceso desde cualquier IP.
```sql
CREATE USER 'admin_biblioteca'@'localhost' IDENTIFIED BY 'admin123';
CREATE USER 'lector'@'192.168.0.100' IDENTIFIED BY 'lector123';
CREATE USER 'editor'@'%' IDENTIFIED BY 'editor123';
```
* *
