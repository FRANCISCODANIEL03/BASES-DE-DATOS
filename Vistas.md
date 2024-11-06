# VISTAS

### Se utiliza para crear "tablas" a partir de consultas de otras tablas, para poder mostrarlas se debe hacer otra consulta

### ~ Ejercicios 
[DATOS UTILIZADOS](tienda.sql)
- - - 
1. *Crear una vista que muestre los detalles de los `administradores` y las tiendas que administran, incluyendo el nombre de los `usuarios`, nombre de la `tienda` y `estado` en el que se encuentran*
- -
```sql
CREATE VIEW detalles_admin AS
SELECT admin.username AS admin, 
user.username AS user, store.name AS store, admin.status AS status_admin, store.status AS status_tienda, user.status AS status_user
FROM admin 
INNER JOIN store ON store.id_admin = admin.id_admin
INNER JOIN user ON store.id_store = user.id_store;

SELECT * FROM detalles_admin;
```

2. *Crea una vista que muestre las `transacciones` realizadas para las `tarjetas`, incluye el id del `cliente`, el nombre de la `tienda`, la fecha de la `transaccion`, la cantidad de `puntos` obtenidos y el nombre de la `transaccion`*
- -
```sql
CREATE VIEW transacciones_tarjetas AS
SELECT 
    client.id_client,
    store.name AS store_name,
    transaction.date AS fecha_transaccion,
    transaction.points AS puntos_obtenidos,
    transaction.amount AS monto_transaccion
FROM transaction
JOIN card_points ON transaction.id_card = card_points.id_card
JOIN client ON card_points.id_client = client.id_client
JOIN store ON card_points.id_store = store.id_store;

SELECT * FROM transacciones_tarjetas; 
```

3. *Crea una vista que muestre el id del `cliente`, el `telefono`, la `tienda` a la que pertenece, la `tarjeta` de puntos y la cantidad de `puntos` acumulados en esa tienda*
- -
```sql
CREATE VIEW clientes_puntos_por_tienda AS
SELECT 
    client.id_client,
    client.phone AS telefono,
    store.name AS store_name,
    card_points.id_card AS id_tarjeta,
    card_points.point AS puntos_acumulados
FROM client
JOIN card_points ON client.id_client = card_points.id_client
JOIN store ON card_points.id_store = store.id_store;

SELECT * FROM clientes_puntos_por_tienda;
```