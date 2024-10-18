# JOIN
***
## Creacion de la tabla rol y usuario 

```sql
CREATE TABLE rol(
    id_rol      INT AUTO_INCREMENT PRIMARY KEY,
    role_name   VARCHAR(30)
);

CREATE TABLE usuarios (
    id_usuario INT AUTO_INCREMENT PRIMARY KEY,
    nickname   VARCHAR(30) UNIQUE NOT NULL,
    password   VARCHAR(15) NOT NULL,
    id_rol     INT,

    FOREIGN KEY(id_rol) REFERENCES rol(id_rol),
		CHECK (LENGTH(password) > 6)
);
```
* Insertar datos a las tablas
```sql
INSERT rol(role_name) VALUES
 ("admin"),
 ("cliente"),
 ("auditor"),
 ("contador");
 
INSERT usuarios(nickname, password, id_rol) VALUES
 ("user2", "oififdse9", 1),
 ("user3", "ijdicsjef", 2),
 ("user4", "39874jds", 2),
 ("user5", "jsufnjw809", 2),
 ("user6", "ijeifj23", 2),
 ("user7", "832498kis", 2),
 ("user8", "ldedqdkm", 2),
 ("user9", "ijewe823w", 2),
 ("user10", "di3kd0wsq", 3),
 ("user11", "oififse93", 3),
 ("user12", "soie3iksl", 1),
 ("user13", "48773598iwj", 1),
 ("user14", "dik9kdwala", 3),
 ("user15", "9385uiirfke", 3),
 ("user16", "478uwkalq", 3);
 

```