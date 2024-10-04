# Operaciones CRUD en MySQL
---
Las operaciones *CRUD* son un conjunto de cuatro opraciones fundamentales en el manejo de bases de datos. *CRUD* es un acronimo que representa la siguientes operaciones.

1. **C**REATE (Crear)
2. **R**EAD (Leer)
3. **U**PDATE (Actualizar)
4. **D**ELETE (Eliminar)

**Primero creamos una tabla:**
```sql
CREATE TABLE Usuarios (
    id_usuario INT PRIMARY KEY AUTO_INCREMENT,
    email      VARCHAR(100) UNIQUE NOT NULL 
    CHECK(email LIKE "%_@_%._%"),
    password   VARCHAR(15) NOT NULL
    CHECK(LENGTH(password) >= 8)
); 
```
* ## CREATE 
La operacion crear es responsable de insertar nuevos datos en la base de datos. En MySQL, esto se realiza con la sentencia:

`INSERT INTO` o `INSERT`

El proposito de la operacion es añadir el nuevo registro o fila a una tabla.

```sql
-- Ejemplo de una inserción valida usando todos los caracteres 
INSERT INTO Usuarios VALUES (1,"ejemplo1@gmail.com","12345678");

-- Ejemplo de una inserción valida usando el comando de DEFAULT
INSERT INTO Usuarios VALUES (DEFAULT,"ejemplo2@gmail.com","12345678");

-- ejemplo de una inserción sin incluir el id_usurio
INSERT Usuarios(email,password) VALUES("ejemplo3@gmail.com","ta2b3cda") 
```

### Ejercicio
---
```sql
-- Errores
-- Email no valido
INSERT Usuarios (email,password) VALUES ("nombre1","12345678910");
-- Password menor al tamaño permitido
INSERT Usuarios (email,password) VALUES ("user1@gmail.com","1234567");
-- Correo repetido
INSERT Usuarios (email,password) VALUES ("user1@gmail.com",
"12345678");
-- Password mayor a 15 caracteres
INSERT Usuarios (email,password) VALUES ("user1@gmail.com",
"12345678947809765");
```
Inserta 4 registros nuevos en un solo insert 
```sql
INSERT Usuarios (email,password) 
    VALUES 
        ("nombre1","12345678910"), 
        ("nombre2","usjfdkdfjks"),
        ("nombre3","878fdjiddw"),
        ("nombre4","yeijdnmksfd");
```
<>

* ## READ
La operacion *READ* es utilizada para consuktar o recuperar datos de la base de datos. Esto no modifica los datos simplemente los extrae. En MySQL, esta operación se realiza con la sentencia:

`SELECT`

```sql
-- Ejemplo de consulta para todos los datos de una tabla 
SELECT * FROM Usuarios;

-- Ejemplo de consulta para un registro en especifico a travez del id
SELECT * FROM Usuarios WHERE id_usuario = 1;

-- Ejemplo de consulta para un registro con un email en especifico 
SELECT * FROM Usuarios WHERE email = "ejemplo1@gmail.com";

-- Ejemplo de consulta con solo el campo email
SELECT email FROM Usuarios;

-- Ejemplo de consulta con un condicional logico
SELECT * FROM Usuarios WHERE LENGTH(password) > 9;
```

**TAREA**:
Realiza una consulta que muestre solo el email que coincida con una contraseña de mas de ocho caracteres
```sql
SELECT email FROM Usuarios WHERE LENGTH(password) > 8;
```
Realiza un consulta a los id´s pares 
```sql
SELECT * FROM Usuarios WHERE MOD(id_usuario, 2) = 0;
```
* ## UPDATE
La operacion actualizar se utiliza para modificar registros existentes en la base de datos. estose hace con la sentecia:

`UPDATE`

Especificamos que datos cambiar y aplicamos condiciones para identificar los registros a actualizar 

```sql
-- Ejemplo para actualizar la contraseña de un usuario por su id 
UPDATE Usuarios SET password="12345xyz" WHERE id_usuario=52;
-- Ejemplo para actualizar el email y password de un usuario en especifico
UPDATE Usuarios SET email="user323@gmail.com", password="12324352" WHERE id_usuario=52;
```

### Ejercicio
intenta actualizar registros con valores que violen las restricciones
```sql
UPDATE Usuarios SET password="1ueidkfhryti8493" WHERE id_usuario=52;
UPDATE Usuarios SET password="1ue" WHERE id_usuario=52;
UPDATE Usuarios SET email="user52@gmail.com" WHERE id_usuario=53;
UPDATE Usuarios SET email="user52gmail.com" WHERE id_usuario=52;
```
* ## DELTE
La operacion *ELIMINAR* se usa para borrar registros de la base de dato, esto se realiza con la sentencia: 

`DELETE`

Debemos ser muy cuidadosos con esta operacion, ya que una vez que los datos son eliminados no pueden ser recuperados 
```sql
-- Eliminar el usuario por el id
DELETE FROM Usuarios WHERE id_usuario=52;
-- Eliminar los usurios con el email especifico 
DELETE FROM Usuarios WHERE email="user32@gamil.com";
-- Eliminar todos los registros de la tabla 
DELETE FROM Usuarios;
-- Eliminar usuarios cuya contraseña menos de 10 caracteres 
DELETE FROM Usuarios WHERE LENGTH(password) < 10;
```

### Ejercicios 

* Eliminar usuarios cuyo  email contenga un o mas 5 
* Eliminar usuarios que tengan una contraseña que contenga letras mayusculas 
* Eliminar usuarios con contraseñas que contengan solo numeros 
* Eliminar usuarios que no tengan el dominio gmail
```sql
DELETE FROM Usuarios WHERE email REGEXP '[5]';

DELETE FROM Usuarios WHERE password REGEXP '[A-Z]';

DELETE FROM Usuarios WHERE password REGEXP '^[0-9]';

DELETE FROM Usuarios WHERE email NOT LIKE "%_@gmail._%";
```