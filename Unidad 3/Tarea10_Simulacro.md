<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

## **Unidad 3. Tarea 10: Simulacro de Examen**

-- ----------------------------------------
-- Consultas sobre una tabla
-- 0,2 puntos la correcta. Total = 1,4 puntos
-- ----------------------------------------

-- 1.- Devuelve un listado con todos las compras que se han realizado. Las compras deben estar ordenados
-- por la fecha de realización, mostrando en primer lugar las compras más recientes.

<details>
<summary>Respuesta</summary>

```
select * from compra ORDER BY fecha DESC;
┌────┬─────────┬────────────┬───────────────┬──────────────────┐
│ id │  total  │   fecha    │ id_consumidor │ id_suministrador │
├────┼─────────┼────────────┼───────────────┼──────────────────┤
│ 15 │ 370.85  │ 2022-03-11 │ 1             │ 5                │
│ 16 │ 2389.23 │ 2022-03-11 │ 1             │ 5                │
│ 13 │ 545.75  │ 2022-01-25 │ 6             │ 1                │
│ 8  │ 1983.43 │ 2020-10-10 │ 4             │ 6                │
│ 1  │ 150.5   │ 2020-10-05 │ 5             │ 2                │
│ 3  │ 65.26   │ 2020-10-05 │ 2             │ 1                │
│ 5  │ 948.5   │ 2020-09-10 │ 5             │ 2                │
│ 12 │ 3045.6  │ 2020-04-25 │ 2             │ 1                │
│ 14 │ 145.82  │ 2020-02-02 │ 6             │ 1                │
│ 9  │ 2480.4  │ 2019-10-10 │ 8             │ 3                │
│ 2  │ 270.65  │ 2019-09-10 │ 1             │ 5                │
│ 4  │ 110.5   │ 2019-08-17 │ 8             │ 3                │
│ 11 │ 75.29   │ 2019-08-17 │ 3             │ 7                │
│ 6  │ 2400.6  │ 2019-07-27 │ 7             │ 1                │
│ 7  │ 5760.0  │ 2018-09-10 │ 2             │ 1                │
│ 10 │ 250.45  │ 2018-06-27 │ 8             │ 2                │
└────┴─────────┴────────────┴───────────────┴──────────────────┘
```
</details>

-- 2. Devuelve todos los datos de los dos compras de mayor valor.

<details>
<summary>Respuesta</summary>

```
select * from compra ORDER BY total DESC limit 2;
┌────┬────────┬────────────┬───────────────┬──────────────────┐
│ id │ total  │   fecha    │ id_consumidor │ id_suministrador │
├────┼────────┼────────────┼───────────────┼──────────────────┤
│ 7  │ 5760.0 │ 2018-09-10 │ 2             │ 1                │
│ 12 │ 3045.6 │ 2020-04-25 │ 2             │ 1                │
└────┴────────┴────────────┴───────────────┴──────────────────┘
```
</details>

-- 3. Devuelve un listado con los identificadores de los consumidores que han realizado algún compra.
-- Tenga en cuenta que no debe mostrar identificadores que estén repetidos.


<details>
<summary>Respuesta</summary>

```
select DISTINCT(id_consumidor) from compra;
┌───────────────┐
│ id_consumidor │
├───────────────┤
│ 5             │
│ 1             │
│ 2             │
│ 8             │
│ 7             │
│ 4             │
│ 3             │
│ 6             │
└───────────────┘
```
</details>

-- 4. Devuelve un listado de todos las compras que se realizaron durante el año 2020,
-- cuya cantidad total sea superior a 500€.

<details>
<summary>Respuesta</summary>

```
select * from compra where total > 500 AND fecha REGEXP '2020-[0-9]{2}-[0-9]{2}';
┌────┬─────────┬────────────┬───────────────┬──────────────────┐
│ id │  total  │   fecha    │ id_consumidor │ id_suministrador │
├────┼─────────┼────────────┼───────────────┼──────────────────┤
│ 5  │ 948.5   │ 2020-09-10 │ 5             │ 2                │
│ 8  │ 1983.43 │ 2020-10-10 │ 4             │ 6                │
│ 12 │ 3045.6  │ 2020-04-25 │ 2             │ 1                │
└────┴─────────┴────────────┴───────────────┴──────────────────┘
```
</details>

-- 5. Devuelve un listado con el nombre y los apellidos de los suministradores que tienen una comisión entre 0.11 y 0.15.

<details>
<summary>Respuesta</summary>

```
select nombre, apellido1, apellido2, categoria from suministrador 
WHERE categoria between 0.11 AND 0.15 
ORDER BY categoria DESC;
┌─────────┬───────────┬───────────┬───────────┐
│ nombre  │ apellido1 │ apellido2 │ categoria │
├─────────┼───────────┼───────────┼───────────┤
│ Daniel  │ Sáez      │ Vega      │ 0.15      │
│ Marta   │ Herrera   │ Gil       │ 0.14      │
│ Juan    │ Gómez     │ López     │ 0.13      │
│ Manuel  │ Domínguez │ Hernández │ 0.13      │
│ Antonio │ Carretero │ Ortega    │ 0.12      │
│ Diego   │ Flores    │ Salas     │ 0.11      │
│ Antonio │ Vega      │ Hernández │ 0.11      │
└─────────┴───────────┴───────────┴───────────┘
```
</details>

-- 6. Devuelve el valor de la comisión de mayor valor que existe en la tabla suministrador.

<details>
<summary>Respuesta</summary>

```
select MAX(categoria) from suministrador;
┌────────────────┐
│ MAX(categoria) │
├────────────────┤
│ 0.15           │
└────────────────┘
```
</details>

-- 7. Devuelve el identificador, nombre y primer apellido de aquellos consumidores cuyo segundo apellido no es NULL.
-- El listado deberá estar ordenado alfabéticamente por apellidos y nombre.

<details>
<summary>Respuesta</summary>

```
select id, nombre, apellido1 from consumidor 
WHERE apellido2 NOT NULL 
ORDER BY apellido1, apellido2, nombre;
┌────┬───────────┬───────────┐
│ id │  nombre   │ apellido1 │
├────┼───────────┼───────────┤
│ 5  │ Marcos    │ Loyola    │
│ 9  │ Guillermo │ López     │
│ 1  │ Aarón     │ Rivero    │
│ 3  │ Adolfo    │ Rubio     │
│ 8  │ Pepe      │ Ruiz      │
│ 2  │ Adela     │ Salas     │
│ 10 │ Daniel    │ Santana   │
│ 6  │ María     │ Santana   │
└────┴───────────┴───────────┘
```
</details>


-- -----------------------------------------------
-- (Consultas Multitabla Where)
-- 0,3 puntos la correcta. Total =  2,1 puntos
-- -----------------------------------------------

-- 1. Devuelve un listado con el identificador, nombre y los apellidos de todos los consumidores que han realizado algún compra.
-- El listado debe estar ordenado alfabéticamente y se deben eliminar los elementos repetidos.

<details>
<summary>Respuesta</summary>

```
select DISTINCT(con.id), con.apellido1, con.apellido2
from consumidor con, compra c
WHERE con.id = c.id_consumidor
ORDER BY con.nombre, con.apellido1, con.apellido2;
┌────┬───────────┬───────────┬───────────┐
│ id │  nombre   │ apellido1 │ apellido2 │
├────┼───────────┼───────────┼───────────┤
│ 1  │ Aarón     │ Rivero    │ Gómez     │
│ 2  │ Adela     │ Salas     │ Díaz      │
│ 3  │ Adolfo    │ Rubio     │ Flores    │
│ 4  │ Adrián    │ Suárez    │           │
│ 10 │ Daniel    │ Santana   │ Loyola    │
│ 9  │ Guillermo │ López     │ Gómez     │
│ 5  │ Marcos    │ Loyola    │ Méndez    │
│ 6  │ María     │ Santana   │ Moreno    │
│ 8  │ Pepe      │ Ruiz      │ Santana   │
│ 7  │ Pilar     │ Ruiz      │           │
└────┴───────────┴───────────┴───────────┘

(SUBCONSULTA)
select DISTINCT(id), nombre, apellido1, apellido2 from consumidor
WHERE (select id_consumidor from compra)
ORDER BY nombre, apellido1, apellido2;
┌────┬───────────┬───────────┬───────────┐
│ id │  nombre   │ apellido1 │ apellido2 │
├────┼───────────┼───────────┼───────────┤
│ 1  │ Aarón     │ Rivero    │ Gómez     │
│ 2  │ Adela     │ Salas     │ Díaz      │
│ 3  │ Adolfo    │ Rubio     │ Flores    │
│ 4  │ Adrián    │ Suárez    │           │
│ 10 │ Daniel    │ Santana   │ Loyola    │
│ 9  │ Guillermo │ López     │ Gómez     │
│ 5  │ Marcos    │ Loyola    │ Méndez    │
│ 6  │ María     │ Santana   │ Moreno    │
│ 8  │ Pepe      │ Ruiz      │ Santana   │
│ 7  │ Pilar     │ Ruiz      │           │
└────┴───────────┴───────────┴───────────┘
```
</details>

-- 2. Devuelve un listado que muestre todos las compras que ha realizado cada consumidor. 
-- El resultado debe mostrar todos los datos de las compras y del consumidor. El listado debe mostrar los datos de los consumidores ordenados alfabéticamente.

<details>
<summary>Respuesta</summary>

```
select * from consumidor con, compra c
WHERE con.id = c.id_consumidor
ORDER BY con.nombre;
┌────┬────────┬───────────┬───────────┬─────────┬───────────┬────┬─────────┬────────────┬───────────────┬──────────────────┐
│ id │ nombre │ apellido1 │ apellido2 │ ciudad  │ categoria │ id │  total  │   fecha    │ id_consumidor │ id_suministrador │
├────┼────────┼───────────┼───────────┼─────────┼───────────┼────┼─────────┼────────────┼───────────────┼──────────────────┤
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 2  │ 270.65  │ 2019-09-10 │ 1             │ 5                │
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 15 │ 370.85  │ 2022-03-11 │ 1             │ 5                │
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 16 │ 2389.23 │ 2022-03-11 │ 1             │ 5                │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 3  │ 65.26   │ 2020-10-05 │ 2             │ 1                │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 7  │ 5760.0  │ 2018-09-10 │ 2             │ 1                │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 12 │ 3045.6  │ 2020-04-25 │ 2             │ 1                │
│ 3  │ Adolfo │ Rubio     │ Flores    │ Sevilla │           │ 11 │ 75.29   │ 2019-08-17 │ 3             │ 7                │
│ 4  │ Adrián │ Suárez    │           │ Jaén    │ 300       │ 8  │ 1983.43 │ 2020-10-10 │ 4             │ 6                │
│ 5  │ Marcos │ Loyola    │ Méndez    │ Almería │ 200       │ 1  │ 150.5   │ 2020-10-05 │ 5             │ 2                │
│ 5  │ Marcos │ Loyola    │ Méndez    │ Almería │ 200       │ 5  │ 948.5   │ 2020-09-10 │ 5             │ 2                │
│ 6  │ María  │ Santana   │ Moreno    │ Cádiz   │ 100       │ 13 │ 545.75  │ 2022-01-25 │ 6             │ 1                │
│ 6  │ María  │ Santana   │ Moreno    │ Cádiz   │ 100       │ 14 │ 145.82  │ 2020-02-02 │ 6             │ 1                │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 4  │ 110.5   │ 2019-08-17 │ 8             │ 3                │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 9  │ 2480.4  │ 2019-10-10 │ 8             │ 3                │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 10 │ 250.45  │ 2018-06-27 │ 8             │ 2                │
│ 7  │ Pilar  │ Ruiz      │           │ Sevilla │ 300       │ 6  │ 2400.6  │ 2019-07-27 │ 7             │ 1                │
└────┴────────┴───────────┴───────────┴─────────┴───────────┴────┴─────────┴────────────┴───────────────┴──────────────────┘
```
</details>

-- 3. Devuelve un listado que muestre todos las compras en los que ha participado un suministrador.
-- El resultado debe mostrar todos los datos de las compras y de los suministradores.
-- El listado debe mostrar los datos de los suministradores ordenados alfabéticamente.

<details>
<summary>Respuesta</summary>

```
select * from suministrador s, compra c
WHERE s.id = c.id_suministrador
ORDER BY nombre, apellido1, apellido2;
┌────┬─────────┬───────────┬───────────┬───────────┬────┬─────────┬────────────┬───────────────┬──────────────────┐
│ id │ nombre  │ apellido1 │ apellido2 │ categoria │ id │  total  │   fecha    │ id_consumidor │ id_suministrador │
├────┼─────────┼───────────┼───────────┼───────────┼────┼─────────┼────────────┼───────────────┼──────────────────┤
│ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │ 2  │ 270.65  │ 2019-09-10 │ 1             │ 5                │
│ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │ 15 │ 370.85  │ 2022-03-11 │ 1             │ 5                │
│ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │ 16 │ 2389.23 │ 2022-03-11 │ 1             │ 5                │
│ 7  │ Antonio │ Vega      │ Hernández │ 0.11      │ 11 │ 75.29   │ 2019-08-17 │ 3             │ 7                │
│ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 3  │ 65.26   │ 2020-10-05 │ 2             │ 1                │
│ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 6  │ 2400.6  │ 2019-07-27 │ 7             │ 1                │
│ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 7  │ 5760.0  │ 2018-09-10 │ 2             │ 1                │
│ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 12 │ 3045.6  │ 2020-04-25 │ 2             │ 1                │
│ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 13 │ 545.75  │ 2022-01-25 │ 6             │ 1                │
│ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 14 │ 145.82  │ 2020-02-02 │ 6             │ 1                │
│ 3  │ Diego   │ Flores    │ Salas     │ 0.11      │ 4  │ 110.5   │ 2019-08-17 │ 8             │ 3                │
│ 3  │ Diego   │ Flores    │ Salas     │ 0.11      │ 9  │ 2480.4  │ 2019-10-10 │ 8             │ 3                │
│ 2  │ Juan    │ Gómez     │ López     │ 0.13      │ 1  │ 150.5   │ 2020-10-05 │ 5             │ 2                │
│ 2  │ Juan    │ Gómez     │ López     │ 0.13      │ 5  │ 948.5   │ 2020-09-10 │ 5             │ 2                │
│ 2  │ Juan    │ Gómez     │ López     │ 0.13      │ 10 │ 250.45  │ 2018-06-27 │ 8             │ 2                │
│ 6  │ Manuel  │ Domínguez │ Hernández │ 0.13      │ 8  │ 1983.43 │ 2020-10-10 │ 4             │ 6                │
└────┴─────────┴───────────┴───────────┴───────────┴────┴─────────┴────────────┴───────────────┴──────────────────┘
```
</details>

-- 4. Devuelve un listado que muestre todos los consumidores, con todos las compras que han realizado 
-- y con los datos de los suministradores asociados a cada compra.

<details>
<summary>Respuesta</summary>

```
select * from consumidor con, suministrador s, compra c
WHERE s.id = c.id_suministrador
AND con.id = c.id_consumidor
ORDER BY nombre, apellido1, apellido2;
┌────┬────────┬───────────┬───────────┬─────────┬───────────┬────┬─────────┬───────────┬───────────┬───────────┬────┬─────────┬────────────┬───────────────┬──────────────────┐
│ id │ nombre │ apellido1 │ apellido2 │ ciudad  │ categoria │ id │ nombre  │ apellido1 │ apellido2 │ categoria │ id │  total  │   fecha    │ id_consumidor │ id_suministrador │
├────┼────────┼───────────┼───────────┼─────────┼───────────┼────┼─────────┼───────────┼───────────┼───────────┼────┼─────────┼────────────┼───────────────┼──────────────────┤
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │ 2  │ 270.65  │ 2019-09-10 │ 1             │ 5                │
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │ 15 │ 370.85  │ 2022-03-11 │ 1             │ 5                │
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │ 16 │ 2389.23 │ 2022-03-11 │ 1             │ 5                │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 3  │ 65.26   │ 2020-10-05 │ 2             │ 1                │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 7  │ 5760.0  │ 2018-09-10 │ 2             │ 1                │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 12 │ 3045.6  │ 2020-04-25 │ 2             │ 1                │
│ 3  │ Adolfo │ Rubio     │ Flores    │ Sevilla │           │ 7  │ Antonio │ Vega      │ Hernández │ 0.11      │ 11 │ 75.29   │ 2019-08-17 │ 3             │ 7                │
│ 4  │ Adrián │ Suárez    │           │ Jaén    │ 300       │ 6  │ Manuel  │ Domínguez │ Hernández │ 0.13      │ 8  │ 1983.43 │ 2020-10-10 │ 4             │ 6                │
│ 5  │ Marcos │ Loyola    │ Méndez    │ Almería │ 200       │ 2  │ Juan    │ Gómez     │ López     │ 0.13      │ 1  │ 150.5   │ 2020-10-05 │ 5             │ 2                │
│ 5  │ Marcos │ Loyola    │ Méndez    │ Almería │ 200       │ 2  │ Juan    │ Gómez     │ López     │ 0.13      │ 5  │ 948.5   │ 2020-09-10 │ 5             │ 2                │
│ 6  │ María  │ Santana   │ Moreno    │ Cádiz   │ 100       │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 13 │ 545.75  │ 2022-01-25 │ 6             │ 1                │
│ 6  │ María  │ Santana   │ Moreno    │ Cádiz   │ 100       │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 14 │ 145.82  │ 2020-02-02 │ 6             │ 1                │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 3  │ Diego   │ Flores    │ Salas     │ 0.11      │ 4  │ 110.5   │ 2019-08-17 │ 8             │ 3                │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 3  │ Diego   │ Flores    │ Salas     │ 0.11      │ 9  │ 2480.4  │ 2019-10-10 │ 8             │ 3                │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 2  │ Juan    │ Gómez     │ López     │ 0.13      │ 10 │ 250.45  │ 2018-06-27 │ 8             │ 2                │
│ 7  │ Pilar  │ Ruiz      │           │ Sevilla │ 300       │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 6  │ 2400.6  │ 2019-07-27 │ 7             │ 1                │
└────┴────────┴───────────┴───────────┴─────────┴───────────┴────┴─────────┴───────────┴───────────┴───────────┴────┴─────────┴────────────┴───────────────┴──────────────────┘
```
</details>

-- 5. Devuelve un listado de todos los consumidores que realizaron un compra durante el año 2020,
-- cuya cantidad esté entre 300 € y 1000 €.

<details>
<summary>Respuesta</summary>

```
select * from consumidor con, compra c
WHERE con.id = c.id_consumidor
AND c.fecha REGEXP '2020-[0-9]{2}-[0-9]{2}'
AND c.total BETWEEN 300 AND 1000;
┌────┬────────┬───────────┬───────────┬─────────┬───────────┬────┬───────┬────────────┬───────────────┬──────────────────┐
│ id │ nombre │ apellido1 │ apellido2 │ ciudad  │ categoria │ id │ total │   fecha    │ id_consumidor │ id_suministrador │
├────┼────────┼───────────┼───────────┼─────────┼───────────┼────┼───────┼────────────┼───────────────┼──────────────────┤
│ 5  │ Marcos │ Loyola    │ Méndez    │ Almería │ 200       │ 5  │ 948.5 │ 2020-09-10 │ 5             │ 2                │
└────┴────────┴───────────┴───────────┴─────────┴───────────┴────┴───────┴────────────┴───────────────┴──────────────────┘
```
</details>

-- 6. Devuelve el nombre y los apellidos de todos los suministradores que ha participado en algún compra realizado por María Santana Moreno.

<details>
<summary>Respuesta</summary>

```
select DISTINCT(s.nombre), s.apellido1, s.apellido2
FROM suministrador s, compra c, consumidor con
WHERE s.id = c.id_suministrador
AND con.id = c.id_consumidor
AND con.nombre REGEXP 'María'
AND con.apellido1 REGEXP 'Santana'
AND con.apellido2 REGEXP 'Moreno';
┌────────┬───────────┬───────────┐
│ nombre │ apellido1 │ apellido2 │
├────────┼───────────┼───────────┤
│ Daniel │ Sáez      │ Vega      │
└────────┴───────────┴───────────┘
```
</details>

-- 7. Devuelve el nombre de todos los consumidores que han realizado algún compra con el suministrador Daniel Sáez Vega.

<details>
<summary>Respuesta</summary>

```
select DISTINCT(con.nombre), con.apellido1, con.apellido2
FROM suministrador s, compra c, consumidor con
WHERE s.id = c.id_suministrador
AND con.id = c.id_consumidor
AND s.nombre REGEXP 'Daniel'
AND s.apellido1 REGEXP 'Sáez'
AND s.apellido2 REGEXP 'Vega';
┌────────┬───────────┬───────────┐
│ nombre │ apellido1 │ apellido2 │
├────────┼───────────┼───────────┤
│ Adela  │ Salas     │ Díaz      │
│ Pilar  │ Ruiz      │           │
│ María  │ Santana   │ Moreno    │
└────────┴───────────┴───────────┘
```
</details>


-- -----------------------------------------------
-- (Consultas Multitabla Join)
-- 0,3 puntos la correcta. Total = 2,1 puntos
-- -----------------------------------------------

-- 1. Devuelve un listado con el identificador, nombre y los apellidos de todos los consumidores que han realizado algún compra.
-- El listado debe estar ordenado alfabéticamente y se deben eliminar los elementos repetidos.

<details>
<summary>Respuesta</summary>

```
select DISTINCT(con.id), con.nombre, con.apellido1, con.apellido2
from consumidor con
JOIN compra c ON con.id = c.id_consumidor
ORDER BY con.nombre;
┌────┬────────┬───────────┬───────────┐
│ id │ nombre │ apellido1 │ apellido2 │
├────┼────────┼───────────┼───────────┤
│ 1  │ Aarón  │ Rivero    │ Gómez     │
│ 2  │ Adela  │ Salas     │ Díaz      │
│ 3  │ Adolfo │ Rubio     │ Flores    │
│ 4  │ Adrián │ Suárez    │           │
│ 5  │ Marcos │ Loyola    │ Méndez    │
│ 6  │ María  │ Santana   │ Moreno    │
│ 8  │ Pepe   │ Ruiz      │ Santana   │
│ 7  │ Pilar  │ Ruiz      │           │
└────┴────────┴───────────┴───────────┘
```
</details>


-- 2. Devuelve un listado que muestre todos las compras que ha realizado cada consumidor. 
-- El resultado debe mostrar todos los datos de las compras y del consumidor. El listado debe mostrar los datos de los consumidores ordenados alfabéticamente.

<details>
<summary>Respuesta</summary>

```
select * from consumidor con
JOIN compra c ON con.id = c.id_consumidor
ORDER BY con.nombre;
┌────┬────────┬───────────┬───────────┬─────────┬───────────┬────┬─────────┬────────────┬───────────────┬──────────────────┐
│ id │ nombre │ apellido1 │ apellido2 │ ciudad  │ categoria │ id │  total  │   fecha    │ id_consumidor │ id_suministrador │
├────┼────────┼───────────┼───────────┼─────────┼───────────┼────┼─────────┼────────────┼───────────────┼──────────────────┤
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 2  │ 270.65  │ 2019-09-10 │ 1             │ 5                │
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 15 │ 370.85  │ 2022-03-11 │ 1             │ 5                │
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 16 │ 2389.23 │ 2022-03-11 │ 1             │ 5                │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 3  │ 65.26   │ 2020-10-05 │ 2             │ 1                │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 7  │ 5760.0  │ 2018-09-10 │ 2             │ 1                │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 12 │ 3045.6  │ 2020-04-25 │ 2             │ 1                │
│ 3  │ Adolfo │ Rubio     │ Flores    │ Sevilla │           │ 11 │ 75.29   │ 2019-08-17 │ 3             │ 7                │
│ 4  │ Adrián │ Suárez    │           │ Jaén    │ 300       │ 8  │ 1983.43 │ 2020-10-10 │ 4             │ 6                │
│ 5  │ Marcos │ Loyola    │ Méndez    │ Almería │ 200       │ 1  │ 150.5   │ 2020-10-05 │ 5             │ 2                │
│ 5  │ Marcos │ Loyola    │ Méndez    │ Almería │ 200       │ 5  │ 948.5   │ 2020-09-10 │ 5             │ 2                │
│ 6  │ María  │ Santana   │ Moreno    │ Cádiz   │ 100       │ 13 │ 545.75  │ 2022-01-25 │ 6             │ 1                │
│ 6  │ María  │ Santana   │ Moreno    │ Cádiz   │ 100       │ 14 │ 145.82  │ 2020-02-02 │ 6             │ 1                │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 4  │ 110.5   │ 2019-08-17 │ 8             │ 3                │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 9  │ 2480.4  │ 2019-10-10 │ 8             │ 3                │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 10 │ 250.45  │ 2018-06-27 │ 8             │ 2                │
│ 7  │ Pilar  │ Ruiz      │           │ Sevilla │ 300       │ 6  │ 2400.6  │ 2019-07-27 │ 7             │ 1                │
└────┴────────┴───────────┴───────────┴─────────┴───────────┴────┴─────────┴────────────┴───────────────┴──────────────────┘
```
</details>


-- 3. Devuelve un listado que muestre todos las compras en los que ha participado un suministrador.
-- El resultado debe mostrar todos los datos de las compras y de los suministradores.
-- El listado debe mostrar los datos de los suministradores ordenados alfabéticamente.

<details>
<summary>Respuesta</summary>

```
select * from suministrador s
RIGHT JOIN compra c ON s.id = c.id_suministrador
ORDER BY s.nombre;
┌────┬─────────┬───────────┬───────────┬───────────┬────┬─────────┬────────────┬───────────────┬──────────────────┐
│ id │ nombre  │ apellido1 │ apellido2 │ categoria │ id │  total  │   fecha    │ id_consumidor │ id_suministrador │
├────┼─────────┼───────────┼───────────┼───────────┼────┼─────────┼────────────┼───────────────┼──────────────────┤
│ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │ 2  │ 270.65  │ 2019-09-10 │ 1             │ 5                │
│ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │ 15 │ 370.85  │ 2022-03-11 │ 1             │ 5                │
│ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │ 16 │ 2389.23 │ 2022-03-11 │ 1             │ 5                │
│ 7  │ Antonio │ Vega      │ Hernández │ 0.11      │ 11 │ 75.29   │ 2019-08-17 │ 3             │ 7                │
│ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 3  │ 65.26   │ 2020-10-05 │ 2             │ 1                │
│ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 6  │ 2400.6  │ 2019-07-27 │ 7             │ 1                │
│ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 7  │ 5760.0  │ 2018-09-10 │ 2             │ 1                │
│ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 12 │ 3045.6  │ 2020-04-25 │ 2             │ 1                │
│ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 13 │ 545.75  │ 2022-01-25 │ 6             │ 1                │
│ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 14 │ 145.82  │ 2020-02-02 │ 6             │ 1                │
│ 3  │ Diego   │ Flores    │ Salas     │ 0.11      │ 4  │ 110.5   │ 2019-08-17 │ 8             │ 3                │
│ 3  │ Diego   │ Flores    │ Salas     │ 0.11      │ 9  │ 2480.4  │ 2019-10-10 │ 8             │ 3                │
│ 2  │ Juan    │ Gómez     │ López     │ 0.13      │ 1  │ 150.5   │ 2020-10-05 │ 5             │ 2                │
│ 2  │ Juan    │ Gómez     │ López     │ 0.13      │ 5  │ 948.5   │ 2020-09-10 │ 5             │ 2                │
│ 2  │ Juan    │ Gómez     │ López     │ 0.13      │ 10 │ 250.45  │ 2018-06-27 │ 8             │ 2                │
│ 6  │ Manuel  │ Domínguez │ Hernández │ 0.13      │ 8  │ 1983.43 │ 2020-10-10 │ 4             │ 6                │
└────┴─────────┴───────────┴───────────┴───────────┴────┴─────────┴────────────┴───────────────┴──────────────────┘
```
</details>


-- 4. Devuelve un listado que muestre todos los consumidores, con todos las compras que han realizado 
-- y con los datos de los suministradores asociados a cada compra.

<details>
<summary>Respuesta</summary>

```
select * from consumidor con
JOIN compra c ON con.id = c.id_consumidor
JOIN suministrador s ON s.id = c.id_suministrador
ORDER BY con.nombre;
┌────┬────────┬───────────┬───────────┬─────────┬───────────┬────┬─────────┬────────────┬───────────────┬──────────────────┬────┬─────────┬───────────┬───────────┬───────────┐
│ id │ nombre │ apellido1 │ apellido2 │ ciudad  │ categoria │ id │  total  │   fecha    │ id_consumidor │ id_suministrador │ id │ nombre  │ apellido1 │ apellido2 │ categoria │
├────┼────────┼───────────┼───────────┼─────────┼───────────┼────┼─────────┼────────────┼───────────────┼──────────────────┼────┼─────────┼───────────┼───────────┼───────────┤
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 2  │ 270.65  │ 2019-09-10 │ 1             │ 5                │ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 15 │ 370.85  │ 2022-03-11 │ 1             │ 5                │ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 16 │ 2389.23 │ 2022-03-11 │ 1             │ 5                │ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 3  │ 65.26   │ 2020-10-05 │ 2             │ 1                │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 7  │ 5760.0  │ 2018-09-10 │ 2             │ 1                │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 12 │ 3045.6  │ 2020-04-25 │ 2             │ 1                │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │
│ 3  │ Adolfo │ Rubio     │ Flores    │ Sevilla │           │ 11 │ 75.29   │ 2019-08-17 │ 3             │ 7                │ 7  │ Antonio │ Vega      │ Hernández │ 0.11      │
│ 4  │ Adrián │ Suárez    │           │ Jaén    │ 300       │ 8  │ 1983.43 │ 2020-10-10 │ 4             │ 6                │ 6  │ Manuel  │ Domínguez │ Hernández │ 0.13      │
│ 5  │ Marcos │ Loyola    │ Méndez    │ Almería │ 200       │ 1  │ 150.5   │ 2020-10-05 │ 5             │ 2                │ 2  │ Juan    │ Gómez     │ López     │ 0.13      │
│ 5  │ Marcos │ Loyola    │ Méndez    │ Almería │ 200       │ 5  │ 948.5   │ 2020-09-10 │ 5             │ 2                │ 2  │ Juan    │ Gómez     │ López     │ 0.13      │
│ 6  │ María  │ Santana   │ Moreno    │ Cádiz   │ 100       │ 13 │ 545.75  │ 2022-01-25 │ 6             │ 1                │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │
│ 6  │ María  │ Santana   │ Moreno    │ Cádiz   │ 100       │ 14 │ 145.82  │ 2020-02-02 │ 6             │ 1                │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 4  │ 110.5   │ 2019-08-17 │ 8             │ 3                │ 3  │ Diego   │ Flores    │ Salas     │ 0.11      │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 9  │ 2480.4  │ 2019-10-10 │ 8             │ 3                │ 3  │ Diego   │ Flores    │ Salas     │ 0.11      │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 10 │ 250.45  │ 2018-06-27 │ 8             │ 2                │ 2  │ Juan    │ Gómez     │ López     │ 0.13      │
│ 7  │ Pilar  │ Ruiz      │           │ Sevilla │ 300       │ 6  │ 2400.6  │ 2019-07-27 │ 7             │ 1                │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │
└────┴────────┴───────────┴───────────┴─────────┴───────────┴────┴─────────┴────────────┴───────────────┴──────────────────┴────┴─────────┴───────────┴───────────┴───────────┘
```
</details>


-- 5. Devuelve un listado de todos los consumidores que realizaron un compra durante el año 2020,
-- cuya cantidad esté entre 300 € y 1000 €.

<details>
<summary>Respuesta</summary>

```
select * from consumidor con
JOIN compra c ON con.id = c.id_consumidor
WHERE c.fecha REGEXP '2020-[0-9]{2}-[0-9]{2}'
AND c.total BETWEEN 300 AND 1000;
┌────┬────────┬───────────┬───────────┬─────────┬───────────┬────┬───────┬────────────┬───────────────┬──────────────────┐
│ id │ nombre │ apellido1 │ apellido2 │ ciudad  │ categoria │ id │ total │   fecha    │ id_consumidor │ id_suministrador │
├────┼────────┼───────────┼───────────┼─────────┼───────────┼────┼───────┼────────────┼───────────────┼──────────────────┤
│ 5  │ Marcos │ Loyola    │ Méndez    │ Almería │ 200       │ 5  │ 948.5 │ 2020-09-10 │ 5             │ 2                │
└────┴────────┴───────────┴───────────┴─────────┴───────────┴────┴───────┴────────────┴───────────────┴──────────────────┘
```
</details>


-- 6. Devuelve el nombre y los apellidos de todos los suministradores que ha participado en algún compra realizado por María Santana Moreno.

<details>
<summary>Respuesta</summary>

```
select DISTINCT(s.nombre), s.apellido1, s.apellido2 from suministrador s
JOIN compra c ON s.id = c.id_suministrador
JOIN consumidor con ON con.id = c.id_consumidor
WHERE con.nombre REGEXP 'María'
AND con.apellido1 REGEXP 'Santana'
AND con.apellido2 REGEXP 'Moreno';
┌────────┬───────────┬───────────┐
│ nombre │ apellido1 │ apellido2 │
├────────┼───────────┼───────────┤
│ Daniel │ Sáez      │ Vega      │
└────────┴───────────┴───────────┘
```
</details>


-- 7. Devuelve el nombre de todos los consumidores que han realizado algún compra con el suministrador Daniel Sáez Vega.

<details>
<summary>Respuesta</summary>

```
select DISTINCT(con.nombre), con.apellido1, con.apellido2 from consumidor con
JOIN compra c ON con.id = c.id_consumidor
JOIN suministrador s ON s.id = c.id_suministrador
WHERE s.nombre REGEXP 'Daniel'
AND s.apellido1 REGEXP 'Sáez'
AND s.apellido2 REGEXP 'Vega';
┌────────┬───────────┬───────────┐
│ nombre │ apellido1 │ apellido2 │
├────────┼───────────┼───────────┤
│ Adela  │ Salas     │ Díaz      │
│ Pilar  │ Ruiz      │           │
│ María  │ Santana   │ Moreno    │
└────────┴───────────┴───────────┘
```
</details>

-- ---------------------------
-- Consultas resumen (funciones)
-- 0,2 puntos la correcta. (1-6) 1,2 puntos
-- 0,25 puntos la correcta. (7-10) 1 punto.
-- Total = 2,2 puntos
-- -----------------------------------------------

-- 1. Calcula la cantidad media de todos las compras que aparecen en la tabla compra.

<details>
<summary>Respuesta</summary>

```
select AVG(total) from compra;
┌─────────────┐
│ AVG(total)  │
├─────────────┤
│ 1312.051875 │
└─────────────┘
```
</details>


-- 2. Calcula el número total de suministradores distintos que aparecen en la tabla compra.

<details>
<summary>Respuesta</summary>

```
select COUNT(DISTINCT(id_suministrador)) AS SuministradoresConCompras from compra;
┌───────────────────────────┐
│ SuministradoresConCompras │
├───────────────────────────┤
│ 6                         │
└───────────────────────────┘
```
</details>


-- 3. Calcula el número total de consumidores que aparecen en la tabla consumidor.

<details>
<summary>Respuesta</summary>

```
select COUNT(id) AS Q_Consumidores from consumidor;
┌────────────────┐
│ Q_Consumidores │
├────────────────┤
│ 10             │
└────────────────┘
```
</details>


-- 4. Calcula cuál es la mayor cantidad que aparece en la tabla compra.

<details>
<summary>Respuesta</summary>

```
select MAX(total) AS Max_Compra from compra;
┌────────────┐
│ Max_Compra │
├────────────┤
│ 5760.0     │
└────────────┘
```
</details>


-- 5. Calcula cuál es el valor máximo de categoría para cada una de las ciudades que aparece en la tabla consumidor.

<details>
<summary>Respuesta</summary>

```
select Ciudad, MAX(Categoria) from consumidor
GROUP BY Ciudad;
┌─────────┬────────────────┐
│ Ciudad  │ MAX(Categoria) │
├─────────┼────────────────┤
│ Almería │ 200            │
│ Cádiz   │ 100            │
│ Granada │ 225            │
│ Huelva  │ 200            │
│ Jaén    │ 300            │
│ Sevilla │ 300            │
└─────────┴────────────────┘
```
</details>


-- 6. Calcula cuál es el máximo valor de las compras realizadas durante el mismo día para cada uno de los consumidores.
-- Es decir, el mismo consumidor puede haber realizado varios compras de diferentes cantidades el mismo día.
-- Se pide que se calcule cuál es el compra de máximo valor para cada uno de los días en los que un consumidor ha realizado un compra.
-- Muestra el identificador del consumidor, nombre, apellidos, la fecha y el valor de la cantidad.

<details>
<summary>Respuesta</summary>

```

```
</details>


-- 7. Calcula cuál es el máximo valor de las compras realizadas durante el mismo día para cada uno de los consumidores,
-- teniendo en cuenta que sólo queremos mostrar aquellas compras que superen la cantidad de 2000 €.

<details>
<summary>Respuesta</summary>

```

```
</details>


-- 8. Calcula el máximo valor de las compras realizadas para cada uno de los suministradores durante la fecha 2020-08-17.
-- Muestra el identificador del suministrador, nombre, apellidos y total.

<details>
<summary>Respuesta</summary>

```

```
</details>


-- 9. Devuelve un listado con el identificador de consumidor, nombre y apellidos y el número total de compras que ha realizado cada uno de consumidores.
-- Tenga en cuenta que pueden existir consumidores que no han realizado ninguna compra.
-- Estos consumidores también deben aparecer en el listado indicando que el número de compras realizadas es 0.

<details>
<summary>Respuesta</summary>

```

```
</details>


-- 10. Devuelve un listado con el identificador de consumidor, nombre y apellidos y el número total de compras que ha realizado cada uno de consumidores durante el año 2020.

<details>
<summary>Respuesta</summary>

```

```
</details>

-- ---------------------
-- Subconsultas
-- 0,2 puntos la correcta (1-5).
-- 0,3 puntos la correcta (6-9).
-- Total = 2,2 puntos
--- Con operadores básicos de comparación
-- --------------------

-- 1. Devuelve un listado con todos las compras que ha realizado Adela Salas Díaz. (Sin utilizar INNER JOIN).

<details>
<summary>Respuesta</summary>

```
select * from compra c
where c.id_consumidor IN
  (select con.id from consumidor con
  WHERE con.nombre REGEXP 'Adela'
  AND con.apellido1 REGEXP 'Salas'
  AND con.apellido2 REGEXP 'Díaz');
┌────┬────────┬────────────┬───────────────┬──────────────────┐
│ id │ total  │   fecha    │ id_consumidor │ id_suministrador │
├────┼────────┼────────────┼───────────────┼──────────────────┤
│ 3  │ 65.26  │ 2020-10-05 │ 2             │ 1                │
│ 7  │ 5760.0 │ 2018-09-10 │ 2             │ 1                │
│ 12 │ 3045.6 │ 2020-04-25 │ 2             │ 1                │
└────┴────────┴────────────┴───────────────┴──────────────────┘
```
</details>


-- 2. Devuelve la fecha y la cantidad del compra de menor valor realizado por el cliente Pepe Ruiz Santana.

<details>
<summary>Respuesta</summary>

```
select MIN(total), fecha from compra c
WHERE c.id_consumidor IN
  (select id from consumidor
  where nombre REGEXP 'Pepe'
  AND apellido1 REGEXP 'Ruiz'
  AND apellido2 REGEXP 'Santana');
┌────────────┬────────────┐
│ MIN(total) │   fecha    │
├────────────┼────────────┤
│ 110.5      │ 2019-08-17 │
└────────────┴────────────┘
```
</details>


-- 3. Devuelve el número de compras en los que ha participado el suministrador Daniel Sáez Vega. (Sin utilizar INNER JOIN)

<details>
<summary>Respuesta</summary>

```
select COUNT(*) AS ComprasByDaniel FROM compra
WHERE id_suministrador IN
  (select id FROM suministrador
  WHERE nombre REGEXP 'Daniel'
  AND apellido1 REGEXP 'Sáez'
  AND apellido2 REGEXP 'Vega');
┌─────────────────┐
│ ComprasByDaniel │
├─────────────────┤
│ 6               │
└─────────────────┘
```
</details>


-- 4. Devuelve los datos del consumidor que realizó el compra más caro en el año 2021. (Sin utilizar INNER JOIN)

<details>
<summary>Respuesta</summary>

```
select * from consumidor
where id IN
  (select MAX(total) from compra
  where fecha REGEXP '2021-[0-9]{2}-[0-9]{2}');

NO DA RESULTADO, NINGUNA COMPRA EN ESA FECHA.
```
</details>


-- 5. Devuelve un listado con los datos de los consumidores y las compras, de todos los consumidores que han realizado un compra durante el año 2020 con un valor mayor o igual al valor medio de las compras realizadas durante ese mismo año.

<details>
<summary>Respuesta</summary>

```
select * from consumidor con
WHERE id IN
  (select id_consumidor from compra c
  where fecha REGEXP '2020-[0-9]{2}-[0-9]{2}'
  AND c.id_consumidor = con.id
  AND c.total >
    (select AVG(total) from compra));
┌────┬────────┬───────────┬───────────┬─────────┬───────────┐
│ id │ nombre │ apellido1 │ apellido2 │ ciudad  │ categoria │
├────┼────────┼───────────┼───────────┼─────────┼───────────┤
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │
│ 4  │ Adrián │ Suárez    │           │ Jaén    │ 300       │
└────┴────────┴───────────┴───────────┴─────────┴───────────┘
```
</details>


-- 6. Devuelve un listado de los consumidores que no han realizado ningún compra. (Utilizando IN o NOT IN).

<details>
<summary>Respuesta</summary>

```
select * from consumidor
WHERE id NOT IN
  (select id_consumidor from compra);
┌────┬───────────┬───────────┬───────────┬─────────┬───────────┐
│ id │  nombre   │ apellido1 │ apellido2 │ ciudad  │ categoria │
├────┼───────────┼───────────┼───────────┼─────────┼───────────┤
│ 9  │ Guillermo │ López     │ Gómez     │ Granada │ 225       │
│ 10 │ Daniel    │ Santana   │ Loyola    │ Sevilla │ 125       │
└────┴───────────┴───────────┴───────────┴─────────┴───────────┘
```
</details>


-- 7. Devuelve un listado de los suministradores que no han realizado ningún compra. (Utilizando IN o NOT IN).

<details>
<summary>Respuesta</summary>

```
select * from suministrador
WHERE id NOT IN
  (select id_suministrador from compra);
┌────┬─────────┬───────────┬───────────┬───────────┐
│ id │ nombre  │ apellido1 │ apellido2 │ categoria │
├────┼─────────┼───────────┼───────────┼───────────┤
│ 4  │ Marta   │ Herrera   │ Gil       │ 0.14      │
│ 8  │ Alfredo │ Ruiz      │ Flores    │ 0.05      │
└────┴─────────┴───────────┴───────────┴───────────┘
```
</details>


-- 8. Devuelve un listado de los consumidores que no han realizado ningún compra. (Utilizando EXISTS o NOT EXISTS).

<details>
<summary>Respuesta</summary>

```
select * from consumidor con
WHERE NOT EXISTS
  (select * from compra c
  where c.id_consumidor = con.id);
┌────┬───────────┬───────────┬───────────┬─────────┬───────────┐
│ id │  nombre   │ apellido1 │ apellido2 │ ciudad  │ categoria │
├────┼───────────┼───────────┼───────────┼─────────┼───────────┤
│ 9  │ Guillermo │ López     │ Gómez     │ Granada │ 225       │
│ 10 │ Daniel    │ Santana   │ Loyola    │ Sevilla │ 125       │
└────┴───────────┴───────────┴───────────┴─────────┴───────────┘
```
</details>


-- 9. Devuelve un listado de los suministradores que no han realizado ningún compra. (Utilizando EXISTS o NOT EXISTS).

<details>
<summary>Respuesta</summary>

```
select * from suministrador s
WHERE NOT EXISTS
  (select id_suministrador from compra c
  WHERE s.id=c.id_suministrador);
┌────┬─────────┬───────────┬───────────┬───────────┐
│ id │ nombre  │ apellido1 │ apellido2 │ categoria │
├────┼─────────┼───────────┼───────────┼───────────┤
│ 4  │ Marta   │ Herrera   │ Gil       │ 0.14      │
│ 8  │ Alfredo │ Ruiz      │ Flores    │ 0.05      │
└────┴─────────┴───────────┴───────────┴───────────┘
```
</details>

</div>
