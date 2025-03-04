-- Tabla para Comida
CREATE TABLE Comida (
    id INT AUTO_INCREMENT PRIMARY KEY,
    codigo VARCHAR(50) UNIQUE NOT NULL,
    nombre_producto VARCHAR(100) NOT NULL,
    precio DECIMAL(10, 2) NOT NULL,
    fecha_vencimiento DATE,
    stock INT DEFAULT 0,
    proveedor VARCHAR(100)
);

INSERT INTO Comida (codigo, nombre_producto, precio, fecha_vencimiento, stock, proveedor) VALUES
('C001', 'Arroz', 1.50, '2025-12-31', 100, 'Proveedor A'),
('C002', 'Fideos', 2.00, '2025-12-31', 80, 'Proveedor B'),
('C003', 'Azúcar', 1.20, '2026-01-15', 90, 'Proveedor C'),
('C004', 'Harina', 1.00, '2025-11-20', 70, 'Proveedor A'),
('C005', 'Aceite', 3.50, '2026-02-01', 60, 'Proveedor D'),
('C006', 'Sal', 0.80, '2027-03-10', 50, 'Proveedor B'),
('C007', 'Leche', 1.10, '2025-10-05', 110, 'Proveedor C'),
('C008', 'Queso', 4.00, '2025-09-12', 30, 'Proveedor A'),
('C009', 'Manteca', 2.50, '2025-08-22', 40, 'Proveedor D'),
('C010', 'Yogurt', 1.80, '2025-07-15', 45, 'Proveedor B');

-- Tabla para Artículos de Limpieza
CREATE TABLE Articulos_Limpieza (
    id INT AUTO_INCREMENT PRIMARY KEY,
    codigo VARCHAR(50) UNIQUE NOT NULL,
    nombre_producto VARCHAR(100) NOT NULL,
    precio DECIMAL(10, 2) NOT NULL,
    marca VARCHAR(100),
    stock INT DEFAULT 0,
    proveedor VARCHAR(100)
);

INSERT INTO Articulos_Limpieza (codigo, nombre_producto, precio, marca, stock, proveedor) VALUES
('L001', 'Detergente', 2.50, 'Marca A', 100, 'Proveedor X'),
('L002', 'Lavandina', 1.80, 'Marca B', 90, 'Proveedor Y'),
('L003', 'Esponja', 0.50, 'Marca C', 110, 'Proveedor Z'),
('L004', 'Jabón líquido', 3.00, 'Marca A', 70, 'Proveedor X'),
('L005', 'Desinfectante', 4.20, 'Marca B', 60, 'Proveedor Y'),
('L006', 'Limpiavidrios', 2.70, 'Marca C', 80, 'Proveedor Z'),
('L007', 'Trapo de piso', 1.50, 'Marca A', 50, 'Proveedor X'),
('L008', 'Escoba', 5.00, 'Marca B', 30, 'Proveedor Y'),
('L009', 'Balde', 4.50, 'Marca C', 40, 'Proveedor Z'),
('L010', 'Guantes', 2.00, 'Marca A', 95, 'Proveedor X');

-- Tabla para Productos de Higiene
CREATE TABLE Productos_Higiene (
    id INT AUTO_INCREMENT PRIMARY KEY,
    codigo VARCHAR(50) UNIQUE NOT NULL,
    nombre_producto VARCHAR(100) NOT NULL,
    precio DECIMAL(10, 2) NOT NULL,
    tipo VARCHAR(100),
    stock INT DEFAULT 0,
    proveedor VARCHAR(100)
);

INSERT INTO Productos_Higiene (codigo, nombre_producto, precio, tipo, stock, proveedor) VALUES
('H001', 'Shampoo', 5.00, 'Cabello', 100, 'Proveedor M'),
('H002', 'Acondicionador', 5.50, 'Cabello', 90, 'Proveedor N'),
('H003', 'Jabón', 1.50, 'Corporal', 110, 'Proveedor O'),
('H004', 'Pasta dental', 2.80, 'Bucal', 70, 'Proveedor M'),
('H005', 'Enjuague bucal', 3.50, 'Bucal', 60, 'Proveedor N'),
('H006', 'Desodorante', 4.00, 'Corporal', 80, 'Proveedor O'),
('H007', 'Cepillo de dientes', 2.00, 'Bucal', 50, 'Proveedor M'),
('H008', 'Crema hidratante', 6.00, 'Piel', 30, 'Proveedor N'),
('H009', 'Perfume', 7.50, 'Corporal', 40, 'Proveedor O'),
('H010', 'Toallas húmedas', 3.00, 'Piel', 95, 'Proveedor M');

-- Tabla para Jardinería
CREATE TABLE Jardineria (
    id INT AUTO_INCREMENT PRIMARY KEY,
    codigo VARCHAR(50) UNIQUE NOT NULL,
    nombre_producto VARCHAR(100) NOT NULL,
    precio DECIMAL(10, 2) NOT NULL,
    categoria VARCHAR(100),
    stock INT DEFAULT 0,
    proveedor VARCHAR(100)
);

INSERT INTO Jardineria (codigo, nombre_producto, precio, categoria, stock, proveedor) VALUES
('J001', 'Tierra abonada', 4.00, 'Sustratos', 100, 'Proveedor R'),
('J002', 'Fertilizante', 5.00, 'Químicos', 90, 'Proveedor S'),
('J003', 'Rastrillo', 6.50, 'Herramientas', 110, 'Proveedor T'),
('J004', 'Pala', 7.00, 'Herramientas', 70, 'Proveedor R'),
('J005', 'Regadera', 8.20, 'Accesorios', 60, 'Proveedor S'),
('J006', 'Maceta', 2.50, 'Accesorios', 80, 'Proveedor T'),
('J007', 'Semillas', 3.00, 'Semillas', 50, 'Proveedor R'),
('J008', 'Guantes', 4.50, 'Accesorios', 30, 'Proveedor S'),
('J009', 'Manguera', 10.00, 'Herramientas', 40, 'Proveedor T'),
('J010', 'Aspersor', 12.00, 'Accesorios', 95, 'Proveedor R');

-- Comandos básicos de MySQL

-- Ver las tablas
SHOW TABLES;

-- Ver estructura de una tabla
DESCRIBE Comida;

-- Seleccionar todos los datos de una tabla
SELECT * FROM Productos_Higiene;

-- Contar registros en una tabla
SELECT COUNT(*) FROM Articulos_Limpieza;

-- Borrar un registro por su id
DELETE FROM Jardineria WHERE id = 1;

-- Comandos avanzados de MySQL

-- Seleccionar productos con precios entre un rango específico
SELECT * FROM Comida WHERE precio BETWEEN 1.50 AND 3.00;

-- Obtener el producto más barato
SELECT * FROM Productos_Higiene ORDER BY precio ASC LIMIT 1;

-- Obtener el producto más caro
SELECT * FROM Articulos_Limpieza ORDER BY precio DESC LIMIT 1;

-- Calcular el total a pagar sumando todos los precios de una tabla
SELECT SUM(precio) AS total_pagar FROM Jardineria;

-- Obtener el promedio de precios de una tabla
SELECT AVG(precio) AS precio_promedio FROM Comida;

-- Contar cuántos productos tienen un precio mayor a un valor dado
SELECT COUNT(*) FROM Productos_Higiene WHERE precio > 4.00;

-- Unir dos tablas para ver productos y proveedores
SELECT C.nombre_producto, C.precio, C.proveedor, A.nombre_producto AS producto_limpieza, A.proveedor AS proveedor_limpieza
FROM Comida C
JOIN Articulos_Limpieza A ON C.proveedor = A.proveedor;

-- Buscar productos que contengan una palabra específica en el nombre
SELECT * FROM Jardineria WHERE nombre_producto LIKE '%Guantes%';

-- Ordenar productos por precio de forma descendente y luego por nombre
SELECT * FROM Productos_Higiene ORDER BY precio DESC, nombre_producto ASC;

-- Crear una vista para productos cuyo precio sea superior a un cierto umbral
CREATE VIEW Productos_Caros AS
SELECT nombre_producto, precio FROM Comida WHERE precio > 3.00;
