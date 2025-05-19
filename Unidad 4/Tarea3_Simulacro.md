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

## Parte 4: Crear una función.

<details>
<summary>Respuesta</summary>



</details>

## Parte 5: Crear un procedimiento.

<details>
<summary>Respuesta</summary>



</details>

## Preguntas teoricas.

<details>
<summary>Respuesta</summary>



</details>

## Preguntas prácticas.

<details>
<summary>Respuesta</summary>



</details>


</div>
