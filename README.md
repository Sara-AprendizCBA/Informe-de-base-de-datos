# Informe Base de Datos – Tienda de Tecnología

##  Descripción del problema

Una tienda de tecnología vende productos como computadores, celulares y accesorios.
Se requiere almacenar información de:

- Clientes
- Producto
- Ventas
- Detalle de ventas

## 1. Normalización

# Primera Forma Normal (1FN)

- ✔ Todos los atributos son atómicos
- ✔ No existen grupos repetitivos
- ✔ Cada tabla tiene clave primaria

# Segunda Forma Normal (2FN)

- ✔ Está en 1FN
- ✔ No existen dependencias parciales
- ✔ En Detalle_Venta, los atributos dependen completamente de la clave primaria


# Tercera Forma Normal (3FN)

- ✔ Está en 2FN
- ✔ No existen dependencias transitivas
- ✔ Los atributos dependen únicamente de su clave primaria


## 2. Modelo Conceptual 

![Modelo conceptual](/img/modelo%20con%20conceptual.jpeg)

## 3. Modelo Lógico

![Modelo logico](/img/modelo%20logico.jpeg)


## 4. Crear base de datos, crear tablas y sus relaciones

![Base de datos](/img/base%20de%20datos.png)

### sintaxis

```
CREATE TABLE clientes(
id_cliente INT AUTO_INCREMENT PRIMARY KEY,
nombre VARCHAR(100) NOT NULL,
documento VARCHAR(20),
telfono INT(15),
correo VARCHAR(100)
);


CREATE TABLE producto(
id_producto INT AUTO_INCREMENT PRIMARY KEY,
nombre VARCHAR(100),
marca VARCHAR(100),
precio DECIMAL(10,2),
stock INT
);


CREATE TABLE venta(
id_venta INT AUTO_INCREMENT PRIMARY KEY,
fecha DATE NOT NULL,
total DECIMAL(10,2),
id_cliente INT NOT NULL,
FOREIGN KEY (id_cliente) REFERENCES clientes (id_cliente)
);

```

## 5. Inserción de Datos (Mínimo 10 registros)

### Clientes

![Tabla clientes](/img/Clientes.png)

### Productos

![Tabla productos](/img/Productoo.png)

### ventas

![Tabla ventas](/img/venta.png)

### Detalles ventas

![Tabla detalles ventas](/img/detalle_venta.png)


# 6. resultado de las consultas

### 6.1. Consulta 1

![consulta 1](/img/consulta%201.png)

### 6.2. Consulta 2

![consulta 2](/img/consulta%202.png)

### 6.3. Consulta 3

![consulta 3](/img/consulta%203.png)



