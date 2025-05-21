<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

## **Unidad 4. Tarea 3: Simulacro, optimización de BBDD y programación.**

## Parte 1: Creación de tablas.

<details>
<summary>Respuesta</summary>

SELECT * FROM `clientes`;

| id | nombre       | ciudad         |
|----|--------------|----------------|
| 1  | Ana Pérez    | Barcelona      |
| 2  | Luis Gómez   | Las Palmas GC  |
| 3  | Carlos Ruiz  | Madrid         |

SELECT * FROM `productos`;

| id | nombre   | precio  |
|----|----------|---------|
| 1  | Laptop   | 1200.00 |
| 2  | Teclado  | 50.00   |
| 3  | Monitor  | 300.00  |

SELECT * FROM `ventas`;

| id | cliente_id | producto_id |    fecha    | cantidad |
|----|------------|-------------|-------------|----------|
| 1  |     1      |      1      | 2024-05-01  |    1     |
| 2  |     1      |      2      | 2024-05-12  |    2     |
| 3  |     2      |      3      | 2024-05-13  |    1     |
| 4  |     3      |      2      | 2024-05-14  |    1     |

</details>

## Parte 2: Creación de los índices.


<details>
<summary>Respuesta</summary>

CREATE idx_ciudad ON clientes(ciudad);

SHOW INDEX from `clientes`;

| Tabla    | Índice | Nombre del índice | Secuencia | Columna | Orden | Cardinalidad | Nulo | Tipo  | Único | Comentario |
|----------|--------|-------------------|-----------|---------|-------|--------------|------|--------|--------|-------------|
| clientes | 0      | PRIMARY           | 1         | id      | A     | 3            | NULL | BTREE | Sí     | NULL        |
| clientes | 1      | idx_ciudad        | 1         | ciudad  | A     | 3            | YES  | BTREE | No     | NULL        |

CREATE idx_fecha ON ventas(fecha);

SHOW INDEX from `ventas`;

| Tabla   | Índice | Nombre del índice | Secuencia | Columna     | Orden | Cardinalidad | Nulo | Tipo  | Único | Comentario |
|---------|--------|-------------------|-----------|-------------|-------|--------------|------|--------|--------|-------------|
| ventas  | 0      | PRIMARY           | 1         | id          | A     | 0            | NULL | BTREE | Sí     | NULL        |
| ventas  | 1      | cliente_id        | 1         | cliente_id  | A     | 0            | NULL | BTREE | No     | NULL        |
| ventas  | 1      | producto_id       | 1         | producto_id | A     | 0            | NULL | BTREE | No     | NULL        |
| ventas  | 1      | idx_fecha         | 1         | fecha       | A     | 4            | NULL | BTREE | No     | NULL        |



Preguntas:
- Crea los indices, muestra su rendimiento, y explica si son óptimos y por qué?

Ambos mejoran el rendimiento. En el caso de la ciudad, serían optimos si sueles filtrar por ese valor o si hay bastantes valores diferentes en ese campo. En el caso de las fechas resulta especialmente útil para realizar busquedas entre diferentes intervalos de fechas o si realizas busquedas con un orden especifico.

</details>

## Parte 3: Creación de vistas.

<details>
<summary>Respuesta</summary>

```
CREATE VIEW ventas_detalladas AS
	SELECT 
    	v.id AS venta_id,
        c.nombre AS nombre_cliente,
        p.nombre AS nombre_producto,
        v.fecha AS fecha_venta,
        v.cantidad AS Q_comprada,
        (p.precio * v.cantidad) AS total_venta
    	FROM ventas v
    	JOIN clientes c ON v.cliente_id = c.id
    	JOIN productos p ON v.producto_id = p.id;
```
SELECT * FROM ventas_detalladas;

| venta_id | nombre_cliente | nombre_producto | fecha_venta | Q_comprada | total_venta |
|----------|----------------|------------------|-------------|------------|-------------|
| 1        | Ana Pérez      | Laptop           | 2024-05-01  | 1          | 1200.00     |
| 2        | Ana Pérez      | Teclado          | 2024-05-12  | 2          | 100.00      |
| 3        | Luis Gómez     | Monitor          | 2024-05-13  | 1          | 300.00      |
| 4        | Carlos Ruiz    | Teclado          | 2024-05-14  | 1          | 50.00       |

</details>

## Parte 4: Creación de una función.

<details>
<summary>Respuesta</summary>

```
DELIMITER //
DROP FUNCTION IF EXISTS calcular_total //
CREATE FUNCTION calcular_total(venta_id INT) 
RETURNS DECIMAL (15,2)
DETERMINISTIC
BEGIN
    	DECLARE total DECIMAL (15,2);
	SELECT p.precio * v.cantidad 
        INTO total
        FROM ventas v
        JOIN productos p ON p.id = v.producto_id
        WHERE v.id = venta_id;
	RETURN total;
END //
DELIMITER ;
```
SELECT calcular_total(1);

| calcular_total(1) |
|-------------------|
| 1200.00           |


</details>

## Parte 5: Creación de un procedimiento.

<details>
<summary>Respuesta</summary>

```
DELIMITER //
DROP PROCEDURE IF EXISTS resumen_cliente //
CREATE PROCEDURE resumen_cliente (IN id_de_cliente INT)
BEGIN
	SELECT
	c.nombre AS Nombre_Cliente,
	v.fecha AS Fecha_Venta,
	p.nombre AS Nombre_Producto,
	v.cantidad AS Q_comprada,
	calcular_total(v.id) AS Total_Venta
    	FROM ventas v
    	JOIN clientes c ON v.cliente_id =  c.id
    	JOIN productos p ON v.producto_id = p.id
    	WHERE v.cliente_id = id_de_cliente;
END //
DELIMITER ; 
```
CALL resumen_cliente(1);

| Nombre_Cliente | Fecha_Venta | Nombre_Producto | Q_Comprada | Total_Venta |
|----------------|-------------|------------------|------------|--------------|
| Ana Pérez      | 2024-05-01  | Laptop           | 1          | 1200.00      |
| Ana Pérez      | 2024-05-12  | Teclado          | 2          | 100.00       |

</details>

## Preguntas teoricas.

#### ¿Qué ventajas ofrece el uso de una vista en lugar de una consulta con múltiples JOIN?

<details>
<summary>Respuesta</summary>

- Encapsula una búsqueda compleja y reutilizable.
- Permiten limitar el acceso a la información de ciertas columnas.
- Las vistas hacen que todos los usuarios conectados a la BBDD accedan a la misma información.

</details>

#### ¿Por qué es importante declarar una función como DETERMINISTIC?

<details>
<summary>Respuesta</summary>

- Por optiminzación, ayuda que la función sepa si va a devolver los mismos valores de resultado.
- Ayuda a conocer si la función depende de factores externos (tiempo u otras tablas).

</details>

#### ¿Cuál es la diferencia entre una función y un procedimiento?

<details>
<summary>Respuesta</summary>

- Las funciones retornan un valor, mientras que los procedimientos no necesariamente.
- Las funciones pueden usarse dentro de consultas, los procedimientos no.
- Las llamadas son diferentes, SELECT y CALL.
- Generalmente se usan con propósitos diferentes, funciones para calcular y devolver cierto valor, mientras que los procedimientos se encargan de ejecutar un conjunto de acciones.

</details>

#### ¿Qué impacto tienen los índices sobre el rendimiento de una base de datos?

<details>
<summary>Respuesta</summary>

Ventajas: 
 
 - Aceleran las búsquedas evitando escaneos completos de tablas.
 - Mejoran el rendimiento en consultas frecuentes.

Desventajas:

- Las modificaciones pueden ser más lentas.
- Un uso excesivo en busquedas poco frecuentes sería negativo para el almacenamiento.

</details>

#### ¿Cuándo se recomienda usar un trigger en lugar de un procedimiento?

<details>
<summary>Respuesta</summary>

- Para ejecutar logicas de manera automatica cuando ocurre un evento.
- Auditorias.

</details>

## Preguntas prácticas.

#### Modifica el procedimiento para filtrar también por un rango de fechas.

<details>
<summary>Respuesta</summary>

```
DELIMITER //

DROP PROCEDURE IF EXISTS resumen_cliente //

CREATE PROCEDURE resumen_cliente (
    IN id_de_cliente INT,
    IN fecha_inicio DATE,
    IN fecha_fin DATE
)
	BEGIN
	    	SELECT
		c.nombre AS Nombre_Cliente,
		v.fecha AS Fecha_Venta,
		p.nombre AS Nombre_Producto,
		v.cantidad AS Q_comprada,
		calcular_total(v.id) AS Total_Venta
		FROM ventas v
		JOIN clientes c ON v.cliente_id = c.id
		JOIN productos p ON v.producto_id = p.id
		WHERE v.cliente_id = id_de_cliente
		AND v.fecha BETWEEN fecha_inicio AND fecha_fin;
	END //

DELIMITER ;
```
CALL resumen_cliente(1, '2024-05-01', '2024-05-02');

| Nombre_Cliente | Fecha_Venta | Nombre_Producto | Q_comprada | Total_Venta |
|----------------|-------------|------------------|------------|--------------|
| Ana Pérez      | 2024-05-01  | Laptop           | 1          | 1200.00      |

CALL resumen_cliente(1, '2024-05-01', '2024-05-31');

| Nombre_Cliente | Fecha_Venta | Nombre_Producto | Q_comprada | Total_Venta |
|----------------|-------------|------------------|------------|--------------|
| Ana Pérez      | 2024-05-01  | Laptop           | 1          | 1200.00      |
| Ana Pérez      | 2024-05-12  | Teclado          | 2          | 100.00       |


</details>

#### Crea un índice sobre la columna producto_id en la tabla ventas.

<details>
<summary>Respuesta</summary>

CREATE INDEX idx_producto_id ON ventas(producto_id);

SHOW INDEX FROM ventas;

| Table  | Non_unique | Key_name       | Seq_in_index | Column_name | Collation | Cardinality | Sub_part | Packed | Null | Index_type | Comment | Index_comment | Visible | Expression |
|--------|------------|----------------|--------------|--------------|-----------|--------------|-----------|--------|------|-------------|---------|----------------|---------|-------------|
| ventas | 0          | PRIMARY        | 1            | id           | A         | 4            | NULL      | NULL   |      | BTREE       | YES     | NULL           |         | NULL        |
| ventas | 1          | cliente_id     | 1            | cliente_id   | A         | 3            | NULL      | NULL   | YES  | BTREE       | YES     | NULL           |         | NULL        |
| ventas | 1          | idx_fecha      | 1            | fecha        | A         | 4            | NULL      | NULL   | YES  | BTREE       | YES     | NULL           |         | NULL        |
| ventas | 1          | idx_producto_id| 1            | producto_id  | A         | 3            | NULL      | NULL   | YES  | BTREE       | YES     | NULL           |         | NULL        |

</details>

#### ¿Qué ocurre si insertas una venta con un cliente_id inexistente?

<details>
<summary>Respuesta</summary>

Falla la inserción debido a que el cliente no existe y la tabla ventas está asociada a través de la foreing key con de la id de cliente de la tabla clientes.

</details>

#### Modifica la vista para incluir también el nombre de la ciudad del cliente.

<details>
<summary>Respuesta</summary>

```
DROP VIEW IF EXISTS ventas_detalladas; 

CREATE VIEW ventas_detalladas AS
	SELECT 
    	v.id AS venta_id,
        c.nombre AS nombre_cliente,
        c.ciudad AS ciudad_cliente,
        p.nombre AS nombre_producto,
        v.fecha AS fecha_venta,
        v.cantidad AS Q_comprada,
        (p.precio * v.cantidad) AS total_venta
    	FROM ventas v
    	JOIN clientes c ON v.cliente_id = c.id
    	JOIN productos p ON v.producto_id = p.id;
```

SELECT * FROM ventas_detalladas;

| venta_id | nombre_cliente | ciudad_cliente     | nombre_producto | fecha_venta  | Q_comprada | total_venta |
|----------|----------------|--------------------|-----------------|--------------|------------|-------------|
| 1        | Ana Pérez      | Barcelona          | Laptop          | 2024-05-01   | 1          | 1200.00     |
| 2        | Ana Pérez      | Barcelona          | Teclado         | 2024-05-12   | 2          | 100.00      |
| 3        | Luis Gómez     | Las Palmas GC      | Monitor         | 2024-05-13   | 1          | 300.00      |
| 4        | Carlos Ruiz    | Madrid             | Teclado         | 2024-05-14   | 1          | 50.00       |

</details>

#### Agrega una validación en el procedimiento para evitar resultados si el cliente no existe.

<details>
<summary>Respuesta</summary>



</details>


</div>
