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
```