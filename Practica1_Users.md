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