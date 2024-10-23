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
2. *Encuentra los actores que han participado en peliculas de la categoria `Comedy`*
- -
```sql
-- Se extrae el id de la categoria `Comedy`
SELECT category_id FROM category WHERE name = "Comedy";
-- Se extrae el id de la pelicula con el id de la categoria `Comedy`
SELECT film_id FROM film_category WHERE category_id = (SELECT category_id FROM category WHERE name = "Comedy");
-- Se extrae el id del actor que participó en la alguna pelicula de categoria `Comedy` 
SELECT actor_id FROM film_actor WHERE film_id IN (SELECT film_id FROM film_category WHERE category_id = (SELECT category_id FROM category WHERE name = "Comedy"));
-- Finalmente se extrae el nombre y apellido de los actores
SELECT first_name, last_name FROM actor WHERE actor_id IN (SELECT actor_id FROM film_actor WHERE film_id IN (SELECT film_id FROM film_category WHERE category_id = (SELECT category_id FROM category WHERE name = "Comedy")));
```
