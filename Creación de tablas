-- Armado de base de datos y tablas

CREATE SCHEMA IF NOT EXISTS LibreriaFinanciera;
USE LibreriaFinanciera;

CREATE TABLE IF NOT EXISTS producto (
Id INT AUTO_INCREMENT,
Editorial VARCHAR(100) NOT NULL,
Autor VARCHAR(100) NOT NULL,
Título VARCHAR (100) NOT NULL,
Categoría VARCHAR (50),
Precio DECIMAL (8,2),
PRIMARY KEY (Id)
);

-- Comandos para ir probando:
-- SELECT * FROM producto;
-- DROP TABLE producto; 

CREATE TABLE IF NOT EXISTS cliente (
Id INT AUTO_INCREMENT,
Email VARCHAR (50) NOT NULL UNIQUE,
Nombre_cliente VARCHAR (25) NOT NULL,
Apellido_cliente VARCHAR (25) NOT NULL,
Domicilio_cliente VARCHAR (25) NOT NULL,
Telefono_cliente VARCHAR (25) NOT NULL UNIQUE,
PRIMARY KEY (Id)
);

-- Comandos para ir probando:
-- SELECT * FROM cliente;
-- DROP TABLE cliente;

CREATE TABLE IF NOT EXISTS order_picking (
Id INT AUTO_INCREMENT,
Id_Prod INT NOT NULL,
Fecha_solicitud DATE NOT NULL,
Cantidad INT NOT NULL,
Id_Usuario INT NOT NULL,
PRIMARY KEY (Id),
FOREIGN KEY (Id_Prod) REFERENCES producto (Id),
FOREIGN KEY (Id_usuario) REFERENCES cliente (Id)
);

-- Comandos para ir probando:
-- Select * from Order_picking;
-- DROP TABLE order_picking;

CREATE TABLE IF NOT EXISTS repartidores (
Repartidor INT AUTO_INCREMENT,
Nombre VARCHAR (30) NOT NULL,
Apellido VARCHAR (30) NOT NULL,
Tel_repartidor VARCHAR (25) NULL UNIQUE,
Email_repartidor Varchar (50) NOT NULL UNIQUE,
PRIMARY KEY (Repartidor)
);

-- Comandos para ir probando:
-- SELECT * FROM repartidores;
-- DROP TABLE repartidores;

CREATE TABLE IF NOT EXISTS codigos_postales (
Id INT NOT NULL UNIQUE,
Codigo INT,
Provincia VARCHAR (30) NOT NULL,
Partido VARCHAR (30) NOT NULL,
Localidad VARCHAR (30) NOT NULL,
PRIMARY KEY (Id)
);

-- Comandos para ir probando:
-- SELECT * FROM codigos_postales;
-- DROP TABLE codigos_postales;

CREATE TABLE IF NOT EXISTS envio (
Id INT AUTO_INCREMENT,
Fecha_entrega DATE NOT NULL,
Id_usuario INT NOT NULL,
Costo_envio DECIMAL (6,2) NOT NULL,
Codigo_postal INT NOT NULL, 
Id_repartidor INT NOT NULL, 
PRIMARY KEY (Id),
FOREIGN KEY (Id_usuario) REFERENCES cliente (Id),
FOREIGN KEY (Id_repartidor) REFERENCES repartidores (Repartidor),
FOREIGN KEY (Codigo_postal) REFERENCES codigos_postales (Id)
);

-- Comandos para ir probando:
-- SELECT * FROM envio;
-- DROP TABLE envio;

CREATE TABLE IF NOT EXISTS proveedor (
Id INT AUTO_INCREMENT,
Razon_social VARCHAR (50) NOT NULL UNIQUE,
email VARCHAR (50) NOT NULL UNIQUE,
Tel_prov VARCHAR (25) NOT NULL UNIQUE,
Domicilio_prov Varchar (50) NOT NULL, -- No es unique, porque hay empresas ubicadas dentre de un mismo predio con mismo domicilio
PRIMARY KEY (Id)
);

-- Comandos para ir probando:
-- SELECT * FROM proveedor;
-- DROP TABLE proveedor;

CREATE TABLE IF NOT EXISTS stock (
Item VARCHAR (50) NOT NULL UNIQUE,
Id_Prod INT NOT NULL,
Cantidad INT NOT NULL,
Stock_min INT NOT NULL,
Lead_time INT NOT NULL, -- Este campo indica la cantidad de días que demora el proveedor en entregarnos los productos para nuestro abastecimiento
Id_Proveedor INT NOT NULL,
PRIMARY KEY (Item),
FOREIGN KEY (Id_Prod) REFERENCES producto  (Id),
FOREIGN KEY (Id_Proveedor) REFERENCES proveedor (Id)
);

-- Comandos para ir probando:
-- SELECT * FROM stock;
-- DROP TABLE stock;

CREATE TABLE IF NOT EXISTS compras (
Orden_de_compra VARCHAR (50) NOT NULL UNIQUE,
Fecha DATE NOT NULL,
Id_Proveedor INT NOT NULL,
Costo_compra DECIMAL (9,2) NOT NULL,
PRIMARY KEY (Orden_de_compra),
FOREIGN KEY (Id_Proveedor) REFERENCES proveedor (Id)
);

-- Comandos para ir probando:
-- SELECT * FROM compras;
-- DROP TABLE compras;

CREATE TABLE IF NOT EXISTS entidad_financiera (
Id INT AUTO_INCREMENT,
Entidad_financiera VARCHAR (50) NOT NULL,
Número_Tarjeta VARCHAR (20) NULL UNIQUE,
Pin_seguridad INT NOT NULL,
Nombre VARCHAR (30) NOT NULL,
Apellido VARCHAR (30) NOT NULL,
Vencimiento DATE NOT NULL,
PRIMARY KEY (Id)
);

-- Comandos para ir probando:
-- SELECT * FROM entidad_financiera;
-- DROP TABLE entidad_financiera;

CREATE TABLE IF NOT EXISTS ventas (
Id INT AUTO_INCREMENT,
Fecha_venta DATE NOT NULL,
Id_Prod INT NOT NULL,
Cliente INT NOT NULL,
PRIMARY KEY (Id),
FOREIGN KEY (Id_Prod) REFERENCES producto (Id),
FOREIGN KEY (Cliente) REFERENCES cliente (Id)
);

-- Comandos para ir probando:
-- SELECT * FROM ventas;
-- DROP TABLE ventas;

CREATE TABLE IF NOT EXISTS satisfaccion_cliente (
Id INT AUTO_INCREMENT,
Calificación INT,
Comentarios VARCHAR (250),
Cliente INT NOT NULL,
Fecha_comentario DATE NOT NULL,
PRIMARY KEY (Id),
FOREIGN KEY (Cliente) REFERENCES cliente (Id)
);

-- Comandos para ir probando:
-- SELECT * FROM safitsfaccion_cliente;
-- DROP TABLE satisfaccion_cliente;

