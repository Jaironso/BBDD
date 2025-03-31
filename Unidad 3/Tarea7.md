<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

## **Unidad 3. Tarea 7: Lenguajes de definición/consulta y manipulación de información en Base de Datos.**

-- Listar los coches vendidos con sus modelos y precios, junto con los nombres de los clientes que los compraron.
-- Cosas que debo de tener en cuenta:
-- ¿Qué me están pidiendo?. ¿Qué es lo que no me han pedido?

<details>
<summary>Respuesta</summary>
  
```
select
(select modelo from coches where coches.id_coche = ventas.id_coche) AS modelo,
(select precio from coches where coches.id_coche = ventas.id_coche) AS precio,
(select nombre from clientes where clientes.id_cliente = ventas.id_cliente) AS nombreCliente
from ventas;
┌────────────────┬─────────┬─────────────────┐
│     modelo     │ precio  │  nombreCliente  │
├────────────────┼─────────┼─────────────────┤
│ Sedán 2022     │ 25000.0 │ Juan Pérez      │
│ Hatchback 2021 │ 22000.0 │ María Gómez     │
│ SUV 2023       │ 30000.0 │ Carlos López    │
│ Coupé 2022     │ 28000.0 │ Ana Martínez    │
│ Camioneta 2023 │ 32000.0 │ Pedro Rodríguez │
│ Compacto 2021  │ 20000.0 │ Laura Sánchez   │
│ Híbrido 2022   │ 27000.0 │ Miguel González │
│ Deportivo 2023 │ 35000.0 │ Isabel Díaz     │
│ Eléctrico 2021 │ 40000.0 │ Elena Torres    │
└────────────────┴─────────┴─────────────────┘
```
</details>

-- Encontrar los clientes que han comprado coches con precios superiores al promedio de todos los coches vendidos.
  -- Cosas que debo de tener en cuenta:
    -- Precios superiores.
    -- Obtener la media. AVG(precio)

<details>
<summary>Respuesta</summary>
  
```
select id_cliente, nombre from clientes where id_cliente IN
(select id_cliente from ventas where id_coche IN
(select id_coche from coches where precio >
(select AVG(precio) from coches where id_coche IN
(select id_coche from ventas))));
┌────────────┬─────────────────┐
│ id_cliente │     nombre      │
├────────────┼─────────────────┤
│ 3          │ Carlos López    │
│ 5          │ Pedro Rodríguez │
│ 8          │ Isabel Díaz     │
│ 10         │ Elena Torres    │
└────────────┴─────────────────┘
```
</details>

-- Mostrar los modelos de coches y sus precios que no han sido vendidos aún:
  -- Cosas que debo de tener en cuenta:
    -- Coches que han sido vendidos.
    -- Quiero los coches que no han sido vendidos. NOT id_coche IN ventas

<details>
<summary>Respuesta</summary>
  
```
select id_coche, modelo, precio from coches where id_coche IN
(select id_coche from coches where id_coche NOT IN
(select id_coche from ventas));
┌──────────┬─────────────┬─────────┐
│ id_coche │   modelo    │ precio  │
├──────────┼─────────────┼─────────┤
│ 9        │ Pickup 2022 │ 31000.0 │
└──────────┴─────────────┴─────────┘
```
</details>

-- Calcular el total gastado por todos los clientes en coches:
  -- Cosas que debo de tener en cuenta:
    -- Me estan pidiendo la suma total de todos los coches vendidos, NO de aquellos que aún no se han vendido.

<details>
<summary>Respuesta</summary>
  
```
select SUM(precio) AS Total_Vendido from coches where id_coche IN
(select id_coche from ventas);
┌───────────────┐
│ Total_Vendido │
├───────────────┤
│ 259000.0      │
└───────────────┘
```
</details>


-- Listar los coches vendidos junto con la fecha de venta y el nombre del cliente, ordenados por fecha de venta de forma descendente:
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. ¿Por qué campo tengo que ordenadar. Es uno o más campos?

<details>
<summary>Respuesta</summary>
  
```
select fecha_venta AS fecha_venta,
(select modelo from coches where coches.id_coche = ventas.id_coche) AS Modelo_Coche,
(select nombre from clientes where clientes.id_cliente = ventas.id_cliente) AS Nombre_Cliente
from ventas ORDER BY fecha_venta DESC;
┌─────────────┬────────────────┬─────────────────┐
│ fecha_venta │  Modelo_Coche  │ Nombre_Cliente  │
├─────────────┼────────────────┼─────────────────┤
│ 2023-10-05  │ Eléctrico 2021 │ Elena Torres    │
│ 2023-08-25  │ Deportivo 2023 │ Isabel Díaz     │
│ 2023-07-20  │ Híbrido 2022   │ Miguel González │
│ 2023-06-15  │ Compacto 2021  │ Laura Sánchez   │
│ 2023-05-05  │ Camioneta 2023 │ Pedro Rodríguez │
│ 2023-04-10  │ Coupé 2022     │ Ana Martínez    │
│ 2023-03-25  │ SUV 2023       │ Carlos López    │
│ 2023-02-20  │ Hatchback 2021 │ María Gómez     │
│ 2023-01-15  │ Sedán 2022     │ Juan Pérez      │
└─────────────┴────────────────┴─────────────────┘
```
</details>

-- Encontrar el modelo de coche más caro.
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. MAX

<details>
<summary>Respuesta</summary>
  
```
select modelo from coches where precio =
(select MAX(precio) from coches);
┌────────────────┐
│     modelo     │
├────────────────┤
│ Eléctrico 2021 │
└────────────────┘
```
</details>

-- Mostrar los clientes que han comprado al menos un coche (un coche o más) y la cantidad de coches comprados.
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. COUNT

<details>
<summary>Respuesta</summary>
  
```
select nombre, COUNT(*) AS NumeroDeCompras from clientes WHERE id_cliente IN
(select id_cliente from ventas) group by id_cliente;
┌─────────────────┬─────────────────┐
│     nombre      │ NumeroDeCompras │
├─────────────────┼─────────────────┤
│ Juan Pérez      │ 1               │
│ María Gómez     │ 1               │
│ Carlos López    │ 1               │
│ Ana Martínez    │ 1               │
│ Pedro Rodríguez │ 1               │
│ Laura Sánchez   │ 1               │
│ Miguel González │ 1               │
│ Isabel Díaz     │ 1               │
│ Elena Torres    │ 1               │
└─────────────────┴─────────────────┘
```
</details>

-- Encontrar los clientes que han comprado coches de la marca 'Toyota':
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. Like | regexp | =. Tabla normalizada ?.

<details>
<summary>Respuesta</summary>
  
```

```
</details>

-- Calcular el promedio de edad de los clientes que han comprado coches de más de 25,000.
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. 

<details>
<summary>Respuesta</summary>
  
```

```
</details>

-- Mostrar los modelos de coches y sus precios que fueron comprados por clientes mayores de 30 años.
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?.

<details>
<summary>Respuesta</summary>
  
```

```
</details>

-- Encontrar los coches vendidos en el año 2022 junto con la cantidad total de ventas en ese año.
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?.

<details>
<summary>Respuesta</summary>
  
```

```
</details>

-- Listar los coches cuyos precios son mayores que el precio promedio de coches vendidos a clientes menores de 30 años.
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. AVG

<details>
<summary>Respuesta</summary>
  
```

```
</details>

-- Calcular el total de ventas por marca de coche, ordenado de forma descendente por el total de ventas:
  -- Cosas que debo de tener en cuenta:
    -- ¿Qué me están pidiendo?. COUNT| DESC|ASC precio

<details>
<summary>Respuesta</summary>
  
```

```
</details>

</div>
