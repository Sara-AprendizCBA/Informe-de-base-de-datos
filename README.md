# Informe Base de Datos – Sistema de Gestión Agrícola

Por medio de la presente, se hace entrega de la actividad elaborada por la aprendiz Sara Rodríguez

##  Descripción del problema

Se requiere diseñar una base de datos para gestionar la información de varias granjas agrícolas.

El sistema debe almacenar información sobre:

- Granjas
- Cultivos
- Producción
- Ventas

Posteriormente se realizaron consultas SQL utilizando:

- SELECT
- WHERE
- ORDER BY
- JOIN (INNER, LEFT, RIGHT)
- CRUD (Insert, Update, Delete)
- ALTER TABLE

## Capturar el modelo relacional creado mysql

![Modelo relacional ](/img/Granja.png)





###  Consulta 1: Listar todas las granjas y sus ubicaciones

```
SELECT nombre, ubicacion FROM farms;

```

![consulta 1 ](/img/consulta%201.png)






###  Consulta 2: Obtener todos los cultivos que se cultivan en granja 'Granja El Roble';


```
SELECT crops.nombre_cultivo FROM crops INNER JOIN production on crops.id_cultivo = production.id_cultivo JOIN farms ON production.id_granja = farms.id_granja WHERE farms.nombre = 'Granja El Roble';

```

![consulta 2 ](/img/consulta_2.png)






###  Consulta 3: Listar todas las ventas realizadas en un período específico '2024-01-01' - '2024-12-31';

```
SELECT * FROM sales WHERE fecha_venta BETWEEN '2024-01-01' AND '2024-12-31';

```

![consulta 3 ](/img/Consulta_3.png)






###  Consulta 4: Listar las granjas que han producido más de 50 toneladas de cualquier cultivo


```
SELECT farms.nombre, farms.ubicacion FROM farms JOIN production ON farms.id_granja = production.id_granja  WHERE production.cantidad_toneladas > 50;
```

![consulta 4 ](/img/Consulta_4.png)







###  Consulta 5: Listar las granjas ordenadas Ascendente

```
SELECT * FROM farms ORDER BY nombre ASC;

```

![consulta 5 ](/img/Consulta_5.png)







###  Consulta 6: Listar los nombres de cultivo ordenadas Descendente

```
SELECT nombre_cultivo FROM crops ORDER BY nombre_cultivo DESC; 

```

![consulta 6 ](/img/consulta_6.png)




# Sentencia JOIN

## INNER JOIN

El **INNER JOIN** se utiliza para combinar filas de dos o más tablas basándose en una condición que compara columnas de esas tablas. Este tipo de JOIN solo devuelve las filas que tienen coincidencias en ambas tablas.

Sintaxis básica:

```
SELECT columnas
FROM tabla1
INNER JOIN tabla2
ON tabla1.columna_comun = tabla2.columna_comun;

```

## EJERCICIOS


## Ejercicio 1:

Dada una tabla Empleados con las columnas **id_empleado**, **nombre**, y **departamento_id**, y una tabla Departamentos con las columnas **id_departamento** y **nombre_departamento**.

Escribe una consulta que devuelva el nombre del empleado y elnombre del departamento en el que trabaja.


### Tabla:

![Tabla ](/img/INNER%20JOIN/Ejercicio%201.png)

### Consulta:

![consulta ](/img/INNER%20JOIN/Consulta_Ejercicio%201.png)


### Sintaxis:

```
SELECT Empleados.nombre, Departamentos.nombre_departamento
FROM Empleados
INNER JOIN Departamentos
ON Empleados.departamento_id = Departamentos.id_departamento;

```




## Ejercicio 2:

Supongamos que tienes una tabla Productos con las columnas **id_producto**, **nombre_producto**, y **categoria_id**, y otra tabla Categorias con las columnas **id_categoria** y
**nombre_categoria**. 

Escribe una consulta que muestre el nombre del producto y su
categoría.

### Tabla:

![Tabla ](/img/INNER%20JOIN/Ejercicio%202.png)

### Consulta:

![consulta ](/img/INNER%20JOIN/Consulta_Ejercicio%202.png)


### Sintaxis:

```
SELECT producto.nombre_Producto, categorias.nombre_categoria FROM producto INNER JOIN categorias ON producto.categoria_id = categorias.id_categoria;

```


## Ejercicio 3:

Considera una tabla Estudiantes con las columnas **id_estudiante**, **nombre**, y **curso_id**, y una tabla Cursos con las columnas **id_curso** y **nombre_curso**. 

Escribe una consulta que muestre los nombres de los estudiantes junto con los nombres de los cursos en los que están inscritos.

### Tabla:

![Tabla ](/img/INNER%20JOIN/Ejercicio%203.png)

### Consulta:

![consulta ](/img/INNER%20JOIN/Consulta_%20ejercicio%203.png)


### Sintaxis:

```
SELECT estudiantes.nombre, curso.nombre_curso FROM estudiantes INNER JOIN curso ON estudiantes.curso_id = curso.id_curso;

```


## LEFT JOIN

El **LEFT JOIN** es otro tipo de operación de combinación en SQL que se utiliza para unir dos tablas. A diferencia del INNER JOIN, el LEFT JOIN devuelve todas las filas de la tabla de la izquierda (tabla A) y las filas coincidentes de la tabla de la derecha (tabla B). Si no hay coincidencia, el resultado incluirá NULL para las columnas de la tabla B.

Sintaxis básica:

```
SELECT columnas
FROM tabla1
LEFT JOIN tabla2
ON tabla1.columna_comun = tabla2.columna_comun;

```


## Ejercicio 1:

Tienes una tabla Autores con las columnas **id_autor** y **nombre_autor**, y una tabla Libros con las columnas **id_libro**, **titulo_libro**, y **id_autor**. 


Escribe una consulta que muestre el nombre de todos los autores y los títulos de sus libros. Asegúrate de que los autores sin libros aparezcan en el resultado.


### Tabla:

![Tabla ](/img/LEFT%20JOIN/left%20join%201.png)

### Consulta:

![consulta ](/img/LEFT%20JOIN/left%20join%201.1.png)


### Sintaxis:

```
SELECT Autores.nombre_autor, Libros.titulo_libro
FROM Autores
LEFT JOIN Libros
ON Autores.id_autor = Libros.id_autor;


```


## RIGHT JOIN

El **RIGHT JOIN** en SQL es similar al LEFT JOIN, pero con una diferencia clave: devuelve todas las filas de la tabla de la derecha (tabla B) y las filas coincidentes de la tabla de la izquierda (tabla A). Si no hay coincidencias, el resultado incluirá NULL para las columnas de la tabla A.

Sintaxis básica:

```
SELECT columnas
FROM tabla1
RIGHT JOIN tabla2
ON tabla1.columna_comun = tabla2.columna_comun;

```


## Ejercicio 1:

Tienes una tabla Departamentos con las columnas **id_departamento** y
**nombre_departamento**, y una tabla Empleados con las columnas **id_empleado**, **nombre_empleado**, y **id_departamento**. 

Escribe una consulta que devuelva todos los departamentos y los empleados asignados a cada uno, incluyendo los departamentos que no tienen empleados.

### Tabla:

![Tabla ](/img/RIGTH%20JOIN/Ejercicio%201.png)

### Consulta:

![consulta ](/img/RIGTH%20JOIN/rigth%20join%201.png)


### Sintaxis:

```
SELECT Empleados.nombre_empleado, Departamentos.nombre_departamento
FROM Empleados
RIGHT JOIN Departamentos
ON Empleados.id_departamento = Departamentos.id_departamento;


```

# Consultas de uso y sintaxis CRUD




## - Delete

El comando INSERT se utiliza para agregar nuevos registros a una tabla.

Cuando se inserta un registro, se deben especificar las columnas donde se almacenarán los datos y luego los valores correspondientes.


### Sintaxis básica

```
INSERT INTO nombre_tabla (columna1, columna2, columna3)
VALUES (valor1, valor2, valor3);

```
### Ejemplo

```
INSERT INTO farms (nombre, ubicacion, tamano_hectareas)
VALUES ('Granja Nueva', 'Madrid', 120.50);

```
### ¿Qué hace?

- Elimina la granja con ID 3.
- No afecta los demás registros







## - Update

El comando UPDATE se usa para modificar registros existentes.

Es muy importante usar WHERE, porque si no lo haces, se modificarán todos los registros de la tabla.


### Sintaxis básica

```
UPDATE nombre_tabla
SET columna = nuevo_valor
WHERE condicion;


```
### Ejemplo

```
UPDATE farms
SET ubicacion = 'Valencia'
WHERE id_granja = 1;


```
### ¿Qué hace?

- Cambia la ubicación de la granja con ID 1.
- Solo afecta ese registro específico.











## - Insert

### Sintaxis básica

El comando INSERT se utiliza para agregar nuevos registros a una tabla.

Cuando se inserta un registro, se deben especificar las columnas donde se almacenarán los datos y luego los valores correspondientes.


```
INSERT INTO nombre_tabla (columna1, columna2, columna3)
VALUES (valor1, valor2, valor3);

```
### Ejemplo

```
INSERT INTO farms (nombre, ubicacion, tamano_hectareas)
VALUES ('Granja Nueva', 'Madrid', 120.50);

```
### ¿Qué hace?

- Agrega una nueva fila a la tabla farms.
- Guarda el nombre, ubicación y tamaño.
- Si la clave primaria es AUTO_INCREMENT, no es necesario colocarla.








## - select

El comando SELECT permite consultar y visualizar datos almacenados en la base de datos.

Es el comando más utilizado en SQL.

### Sintaxis básica

```
SELECT columnas
FROM nombre_tabla;


```
### Ejemplo

```

SELECT nombre
FROM farms
WHERE ubicacion = 'Sevilla';

```

### ¿Qué hace?

- Muestra únicamente las granjas ubicadas en Sevilla.
- Se usa WHERE para filtrar datos.





## - Alter table y sus variaciones

A diferencia del CRUD, que modifica datos, ALTER TABLE modifica la estructura de la tabla.

Se usa cuando necesitamos:

- Agregar columnas
- Eliminar colmnas
- Cambiar tipo de dato
- Renombrar columnas


### Sintaxis básica

- Agregar una columna

```
ALTER TABLE farms
ADD telefono VARCHAR(20);


```

- Eliminar una columna

```
ALTER TABLE farms
DROP COLUMN telefono;

```

- Modificar tipo de dato

```
ALTER TABLE farms
MODIFY tamano_hectareas DECIMAL(12,2);
```


- Cambiar nombre de columna

```
ALTER TABLE farms
RENAME COLUMN nombre TO nombre_granja;

```

## ejercicio de aplicación

![FOTO](/img/Ejercicio%20Biblioteca/blibioteca.png)


- 1. El nombre de la autora &quot;Isabel Allende&quot; fue mal escrito y hay que corregirlo 

![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%201.png)

Por: Isabel M. Allende

![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%201.1.png)

Ahora:


![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%201.3.png

)


- 2. Se decide eliminar el libro de J.K. Rowling por derechos de publicación.


![FOTO](/img/Ejercicio%20Biblioteca/ejercicio%202.png)


- 3. Ahora se quiere almacenar el año de publicación de los libros.

![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%203.png)

Ya agregada:

![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%203.1.png)

- 4. Después se quiere almacenar el precio de cada libro.

![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%204.png)

Ya agregada:


![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%204.1.png)


- 5. Actualizar el año del libro cien años de soledad por 1967

![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%20%205.png)

Ya insertada:

![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%205.1.png)


- 6. Colocar GABO - después del nombre de Gabriel García Márquez.

![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%206.png)

Insertada:

![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%206.1.png)


- 7. Agregar columna de género en libros

![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%207.png)

Agregada:

![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%207.1.png)


- 8. Colocar el género de los libros ya almacenados

![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%208.png)

Modificada:

![FOTO](/img/Ejercicio%20Biblioteca/Ejercicio%208.1.png)
