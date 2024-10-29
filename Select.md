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
3. *Encuentra a los clientes que no han realizado ningun alquiler en los ultimos 30 dias*
- - 
```sql
-- Seleccionar los id de los clientes que no hayan realizado un alquiler en losultimos 30 dias 
SELECT customer_id FROM rental WHERE DATEDIFF(NOW(),rental_date) > 30;
-- Seleccionar el nombre y apellido de estos
SELECT first_name, last_name FROM customer WHERE customer_id IN (SELECT customer_id FROM rental WHERE DATEDIFF(NOW(),rental_date) > 30);
```
4. *Muestra los nombres de los actores y los titulos 
de las peliculas en las que han participado*
- - 
```sql
SELECT actor.first_name, actor.last_name, film.title FROM actor RIGHT JOIN (film_actor INNER JOIN film) ON actor.actor_id = film_actor.actor_id;
```
5. *Muestra las veces que se ha rentado una pelicula*
- - 
```sql
SELECT film.title, COUNT(rental.rental_id) AS rental_count FROM film LEFT JOIN inventory ON 
film.film_id = inventory.film_id
LEFT JOIN rental ON inventory.inventory_id = rental.inventory_id
GROUP BY film.title;
```
6. *Muestra los nombres de los actores y los titulos de las peliculas en las que han participado* 
```sql
SELECT CONCAT(a.first_name," ", a.last_name) AS full_name, f.title AS participo_en 
FROM actor AS a
JOIN film_actor AS fa ON a.actor_id = fa.actor_id
JOIN film AS f ON fa.film_id = f.film_id;
```
## Otras opciones

* UNION --> Si existen datos repetidos los elimina 
* UNION ALL --> Da los datos completos
* INTERSECT --> Encuentra los datos en comun entre ambas tablas
* EXCEPT --> Elimina los datos que se intersecten

**Ejemplo:**
```sql
SELECT first_name FROM actor
UNION 
SELECT first_name FROM customer;
```
