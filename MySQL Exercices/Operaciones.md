
CREATE TABLE Facturas (
    Letra CHAR,
    Numero INT,
    ClienteID INT,
    ArticuloID INT,
    Fecha DATE,
    Monto DOUBLE,
    PRIMARY KEY (Letra, Numero)
);
CREATE TABLE ARTICULOS (
         ArticuloID INT PRIMARY KEY,
        Nombre VARCHAR(50),
         Precio DOUBLE,
         Stock INT

CREATE TABLE CLIENTES (
ClienteID INT PRIMARY KEY,
Nombre varchar(25),
Apellido varchar(25),
CUIT char(16),
Dirección varchar(50),
Comentarios varchar(50)
);

ALTER TABLE Facturas
CHANGE ClienteID IDCliente INT;

ALTER TABLE Facturas
MODIFY Monto DOUBLE UNSIGNED;

ALTER TABLE Articulos
CHANGE ArticuloID IDArticulo INT;

ALTER TABLE Articulos
Modify Nombre VARCHAR(75);

ALTER TABLE Articulos
MODIFY Precio DOUBLE UNSIGNED NOT NULL;

ALTER TABLE Articulos
MODIFY Stock int UNSIGNED NOT NULL;

ALTER TABLE Clientes
CHANGE ClienteID IDCliente INT;

ALTER TABLE Clientes
Modify Nombre VARCHAR(30) NOT NULL;

ALTER TABLE Clientes
Modify Apellido VARCHAR(35) NOT NULL;

ALTER TABLE Clientes
CHANGE Comentarios Observaciones VARCHAR(255);

Primera factura
Letra: A
Número: 28
IDCliente: 14
IDArticulo: 335
Fecha: 2021-03-18
Monto: 1589.50

INSERT INTO Facturas(Letra, Numero, IDCliente, ID_articulo, Fecha, Monto)
VALUES ('A', 28, 14, 335, '2021-03-18', 1589.50);

Segunda factura
Letra: A
Número: 39
IDCliente: 26
IDArticulo: 157
Fecha: 2021-04-12
Monto: 979.75

Tercera factura
Letra: B
Número: 8
IDCliente: 17
IDArticulo: 95
Fecha: 2021-04-25
Monto: 513.35

Cuarta factura
Letra: B
Número: 12
IDCliente: 5
IDArticulo: 411
Fecha: 2021-05-03
Monto: 2385.70

Quinta factura
Letra: B
Número: 19
IDCliente: 50
IDArticulo: 157
Fecha: 2021-05-26
Monto: 979.7


INSERT INTO Facturas(Letra, Numero, IDCliente, ID_articulo, Fecha, Monto)
VALUES ('A', 39, 26, 157, '2021-04-12', 979.75),
("B", 8, 17, 95, '2021-04-25', 513.35),
("B",12, 5, 411, '2021-05-03', 2385.70),
("B", 19, 50, 157,'2021-05-26', 979.70);

ARTICULOS

Primer artículo
IDArticulo: 95
Nombre: Webcam con Micrófono Plug & Play
Precio: 513.35
Stock: 39

Segundo artículo
IDArticulo: 157
Nombre: Apple AirPods Pro
Precio: 979.75
Stock: 152

Tercer artículo
IDArticulo: 335
Nombre: Lavasecarropas Automático Samsung
Precio: 1589.50
Stock: 12

Cuarto artículo
IDArticulo: 411
Nombre: Gloria Trevi / Gloria / CD+DVD
Precio: 2385.70
Stock: 2

INSERT INTO articulos (IDArticulo, Nombre, Precio, Stock) VALUES
(95,"Webcam con Micrófono Plug & Play", 513.35, 39),
(157,"Apple AirPods Pro", 979.75, 152),
(335,"Lavasecarropas Automático Samsung", 1589.5, 12),
(411,"Gloria Trevi / Gloria / CD+DVD", 2385.7, 2);


// En el caso que quiera borrar una columna
ALTER TABLE Articulos
DROP COLUMN Extra;

CLIENTES

Primer cliente
IDCliente: 5
Nombre: Santiago
Apellido: González
CUIT: 23-24582359-9
Dirección: Uriburu 558 - 7ºA
Comentarios: VIP

Segundo cliente
IDCliente: 14
Nombre: Gloria
Apellido: Fernández
CUIT: 23-35965852-5
Dirección: Constitución 323
Comentarios: GBA

Tercer cliente
IDCliente: 17
Nombre: Gonzalo
Apellido: López
CUIT: 23-33587416-0
Dirección: Arias 2624
Comentarios: GBA

Cuarto cliente
IDCliente: 26
Nombre: Carlos
Apellido: García
CUIT: 23-42321230-9
Dirección: Pasteur 322 - 2ºC
Comentarios: VIP

Quinto cliente
IDCliente: 50
Nombre: Micaela
Apellido: Altieri
CUIT: 23-22885566-5
Dirección: Santamarina 1255
Comentarios: GB

INSERT INTO Clientes(IDCliente, Nombre, Apellido, CUIT, Dirección, Observaciones) VALUES
(5, "Santiago", "González", "23-24582359-9", "Uriburu 558 - 7ºA", "VIP"),
(14, "Gloria", "Fernández", "23-35965852-5", "Constitución 323", "GBA"),
(17, "Gonzalo", "López", "23-33587416-0", "Arias 2624", "GBA"),
(26, "Carlos", "García", "23-42321230-9", "Pasteur 322 - 2ºC", "VIP"),
(50, "Micaela", "Altieri", "23-22885566-5", "Santamarina 1255", "GBA"); 


SELECT* FROM articulos AS A
JOIN facturas AS f
ON a.IDArticulo = f.IDArticulo;

-- Creando las vistas

CREATE VIEW `los_precios` AS
SELECT precio FROM laboratorio_eduit.articulos;

SELECT * FROM los_precios;

-- Filtrar las vistas

SELECT * FROM los_precios WHERE precio > 100;

-- Si se crease una tabla de pedidos 

SELECT id_cliente, MAX(precio) AS max_precio
FROM pedidos
JOIN los_precios ON pedidos.id_articulo = los_precios.id_articulo
GROUP BY id_cliente;

-- Obtener los precios

 select max(precio)
     from los_precios;

 select min(precio)
     from los_precios;

SELECT precio FROM los_precios WHERE precio BETWEEN 500 AND 1500;

SELECT precio AS "precios entre 500 y 1500"
FROM los_precios
WHERE precio BETWEEN 500 AND 1500;

SELECT precio AS "precios entre 500 y 1500", nombre as "producto"
FROM articulos
WHERE precio BETWEEN 500 AND 1500;

SELECT* precio AS "precios entre 500 y 1500", nombre as "producto"
FROM articulos;

-- Crear una llave foranea

CREATE TABLE Orders (
    or	der_id INT PRIMARY KEY,
    IDCliente INT,
    order_date DATE,
    FOREIGN KEY (IDCliente) REFERENCES Clientes (IDCliente)
);


-- Buscar valores nulos o no nulos
 
SELECT* FROM clientes WHERE Dirección IS NULL;
SELECT* FROM clientes WHERE Dirección IS NULL LIMIT 2;
SELECT* FROM clientes WHERE Dirección IS NOT NULL;

-- Formas de ordenar los datos

SELECT* FROM articulos
ORDER BY precio ASC;

SELECT* FROM articulos
ORDER BY precio DESC;

SELECT* FROM articulos
ORDER BY precio DESC;












