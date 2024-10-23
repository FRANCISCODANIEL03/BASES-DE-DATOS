# SUB-SELECT

### Se utiliza al realizar un consulta dentro de una consulta, se utiliza la misma estructura de `SELECT`

### ~ Ejercicios 
[DATOS UTILIZADOS](sakila.sql)
- - -
1. *Seleccionar todos los nombres que sean mas largos que el promedio.*
- -
```sql
SELECT * FROM actor WHERE LENGTH(first_name) > (SELECT AVG(LENGTH(first_name)) FROM actor);
```
