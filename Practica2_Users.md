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