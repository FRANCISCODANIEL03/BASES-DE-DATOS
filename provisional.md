SELECT film.title, COUNT(rental.rental_id) AS rental_count FROM film LEFT JOIN inventory ON 
film.film_id = inventory.film_id
LEFT JOIN rental ON inventory.inventory_id = r.inventory_id
GROUP BY film.title;
muestra los nombres de los actores y los titulos de las peliculas en las que han participado 

SELECT CONCAT(a.first_name," ", a.last_name) AS full_name, f.title AS participo_en 
FROM actor AS a
JOIN film_actor AS fa ON a.actor_id = fa.actor_id
JOIN film AS f ON fa.film_id = f.film_id;

SELECT first_name FROM actor
UNION 
SELECT first_name FROM customer;

UNION --> Si existen datos repetidos los elimina 
UNION ALL --> Da los datos completos
INTERSECT --> Encuentra los datos en comun entre ambas tablas
EXCEPT --> Elimina los datos que se intersecten

Encuentra las peliculas que no han sido alquiladas
SELECT title FROM film
EXCEPT
SELECT film.title FROM film 
JOIN inventory ON film.film_id = inventory.film_id
JOIN rental ON inventory.inventory_id = rental.inventory_id;

Devuelvce las ciudades donde viven los cilentes o empleados sin duplicados 