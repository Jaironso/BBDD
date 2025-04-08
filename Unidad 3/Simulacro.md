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

-- (Consultas Multitabla Where)
-- -----------------------------------------------
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
GROUP BY con.id
ORDER BY con.nombre, con.apellido1, con.apellido2; 
┌────┬────────┬───────────┬───────────┬─────────┬───────────┬────┬─────────┬────────────┬───────────────┬──────────────────┐
│ id │ nombre │ apellido1 │ apellido2 │ ciudad  │ categoria │ id │  total  │   fecha    │ id_consumidor │ id_suministrador │
├────┼────────┼───────────┼───────────┼─────────┼───────────┼────┼─────────┼────────────┼───────────────┼──────────────────┤
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 2  │ 270.65  │ 2019-09-10 │ 1             │ 5                │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 3  │ 65.26   │ 2020-10-05 │ 2             │ 1                │
│ 3  │ Adolfo │ Rubio     │ Flores    │ Sevilla │           │ 11 │ 75.29   │ 2019-08-17 │ 3             │ 7                │
│ 4  │ Adrián │ Suárez    │           │ Jaén    │ 300       │ 8  │ 1983.43 │ 2020-10-10 │ 4             │ 6                │
│ 5  │ Marcos │ Loyola    │ Méndez    │ Almería │ 200       │ 1  │ 150.5   │ 2020-10-05 │ 5             │ 2                │
│ 6  │ María  │ Santana   │ Moreno    │ Cádiz   │ 100       │ 13 │ 545.75  │ 2022-01-25 │ 6             │ 1                │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 4  │ 110.5   │ 2019-08-17 │ 8             │ 3                │
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
GROUP BY s.id
ORDER BY nombre, apellido1, apellido2;
┌────┬─────────┬───────────┬───────────┬───────────┬────┬─────────┬────────────┬───────────────┬──────────────────┐
│ id │ nombre  │ apellido1 │ apellido2 │ categoria │ id │  total  │   fecha    │ id_consumidor │ id_suministrador │
├────┼─────────┼───────────┼───────────┼───────────┼────┼─────────┼────────────┼───────────────┼──────────────────┤
│ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │ 2  │ 270.65  │ 2019-09-10 │ 1             │ 5                │
│ 7  │ Antonio │ Vega      │ Hernández │ 0.11      │ 11 │ 75.29   │ 2019-08-17 │ 3             │ 7                │
│ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 3  │ 65.26   │ 2020-10-05 │ 2             │ 1                │
│ 3  │ Diego   │ Flores    │ Salas     │ 0.11      │ 4  │ 110.5   │ 2019-08-17 │ 8             │ 3                │
│ 2  │ Juan    │ Gómez     │ López     │ 0.13      │ 1  │ 150.5   │ 2020-10-05 │ 5             │ 2                │
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
GROUP BY con.id
ORDER BY nombre, apellido1, apellido2;
┌────┬────────┬───────────┬───────────┬─────────┬───────────┬────┬─────────┬───────────┬───────────┬───────────┬────┬─────────┬────────────┬───────────────┬──────────────────┐
│ id │ nombre │ apellido1 │ apellido2 │ ciudad  │ categoria │ id │ nombre  │ apellido1 │ apellido2 │ categoria │ id │  total  │   fecha    │ id_consumidor │ id_suministrador │
├────┼────────┼───────────┼───────────┼─────────┼───────────┼────┼─────────┼───────────┼───────────┼───────────┼────┼─────────┼────────────┼───────────────┼──────────────────┤
│ 1  │ Aarón  │ Rivero    │ Gómez     │ Almería │ 100       │ 5  │ Antonio │ Carretero │ Ortega    │ 0.12      │ 2  │ 270.65  │ 2019-09-10 │ 1             │ 5                │
│ 2  │ Adela  │ Salas     │ Díaz      │ Granada │ 200       │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 3  │ 65.26   │ 2020-10-05 │ 2             │ 1                │
│ 3  │ Adolfo │ Rubio     │ Flores    │ Sevilla │           │ 7  │ Antonio │ Vega      │ Hernández │ 0.11      │ 11 │ 75.29   │ 2019-08-17 │ 3             │ 7                │
│ 4  │ Adrián │ Suárez    │           │ Jaén    │ 300       │ 6  │ Manuel  │ Domínguez │ Hernández │ 0.13      │ 8  │ 1983.43 │ 2020-10-10 │ 4             │ 6                │
│ 5  │ Marcos │ Loyola    │ Méndez    │ Almería │ 200       │ 2  │ Juan    │ Gómez     │ López     │ 0.13      │ 1  │ 150.5   │ 2020-10-05 │ 5             │ 2                │
│ 6  │ María  │ Santana   │ Moreno    │ Cádiz   │ 100       │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 13 │ 545.75  │ 2022-01-25 │ 6             │ 1                │
│ 8  │ Pepe   │ Ruiz      │ Santana   │ Huelva  │ 200       │ 3  │ Diego   │ Flores    │ Salas     │ 0.11      │ 4  │ 110.5   │ 2019-08-17 │ 8             │ 3                │
│ 7  │ Pilar  │ Ruiz      │           │ Sevilla │ 300       │ 1  │ Daniel  │ Sáez      │ Vega      │ 0.15      │ 6  │ 2400.6  │ 2019-07-27 │ 7             │ 1                │
└────┴────────┴───────────┴───────────┴─────────┴───────────┴────┴─────────┴───────────┴───────────┴───────────┴────┴─────────┴────────────┴───────────────┴──────────────────┘
```
</details>

-- 5. Devuelve un listado de todos los consumidores que realizaron un compra durante el año 2020,
-- cuya cantidad esté entre 300 € y 1000 €.

<details>
<summary>Respuesta</summary>

```

```
</details>

-- 6. Devuelve el nombre y los apellidos de todos los suministradores que ha participado en algún compra realizado por María Santana Moreno.
<details>
<summary>Respuesta</summary>

```

```
</details>
-- 7. Devuelve el nombre de todos los consumidores que han realizado algún compra con el suministrador Daniel Sáez Vega.
<details>
<summary>Respuesta</summary>

```

```
</details>

-- (Consultas Multitabla Join)
-- -----------------------------------------------
-- 0,3 puntos la correcta. Total = 2,1 puntos
-- -----------------------------------------------

-- 1. Devuelve un listado con el identificador, nombre y los apellidos de todos los consumidores que han realizado algún compra.
-- El listado debe estar ordenado alfabéticamente y se deben eliminar los elementos repetidos.
-- 2. Devuelve un listado que muestre todos las compras que ha realizado cada consumidor. 
-- El resultado debe mostrar todos los datos de las compras y del consumidor. El listado debe mostrar los datos de los consumidores ordenados alfabéticamente.
-- 3. Devuelve un listado que muestre todos las compras en los que ha participado un suministrador.
-- El resultado debe mostrar todos los datos de las compras y de los suministradores.
-- El listado debe mostrar los datos de los suministradores ordenados alfabéticamente.
-- 4. Devuelve un listado que muestre todos los consumidores, con todos las compras que han realizado 
-- y con los datos de los suministradores asociados a cada compra.
-- 5. Devuelve un listado de todos los consumidores que realizaron un compra durante el año 2020,
-- cuya cantidad esté entre 300 € y 1000 €.
-- 6. Devuelve el nombre y los apellidos de todos los suministradores que ha participado en algún compra realizado por María Santana Moreno.
-- 7. Devuelve el nombre de todos los consumidores que han realizado algún compra con el suministrador Daniel Sáez Vega.


-- ---------------------------
-- Consultas resumen (funciones)
-- -----------------------------------------------
-- 0,2 puntos la correcta. (1-6) 1,2 puntos
-- 0,25 puntos la correcta. (7-10) 1 punto.
-- Total = 2,2 puntos
-- -----------------------------------------------

-- 1. Calcula la cantidad media de todos las compras que aparecen en la tabla compra.
-- 2. Calcula el número total de suministradores distintos que aparecen en la tabla compra.
-- 3. Calcula el número total de consumidores que aparecen en la tabla consumidor.
-- 4. Calcula cuál es la mayor cantidad que aparece en la tabla compra.
-- 5. Calcula cuál es el valor máximo de categoría para cada una de las ciudades que aparece en la tabla consumidor.
-- 6. Calcula cuál es el máximo valor de las compras realizadas durante el mismo día para cada uno de los consumidores.
-- Es decir, el mismo consumidor puede haber realizado varios compras de diferentes cantidades el mismo día.
-- Se pide que se calcule cuál es el compra de máximo valor para cada uno de los días en los que un consumidor ha realizado un compra.
-- Muestra el identificador del consumidor, nombre, apellidos, la fecha y el valor de la cantidad.
-- 7. Calcula cuál es el máximo valor de las compras realizadas durante el mismo día para cada uno de los consumidores,
-- teniendo en cuenta que sólo queremos mostrar aquellas compras que superen la cantidad de 2000 €.
-- 8. Calcula el máximo valor de las compras realizadas para cada uno de los suministradores durante la fecha 2020-08-17.
-- Muestra el identificador del suministrador, nombre, apellidos y total.
-- 9. Devuelve un listado con el identificador de consumidor, nombre y apellidos y el número total de compras que ha realizado cada uno de consumidores.
-- Tenga en cuenta que pueden existir consumidores que no han realizado ninguna compra.
-- Estos consumidores también deben aparecer en el listado indicando que el número de compras realizadas es 0.
-- 10. Devuelve un listado con el identificador de consumidor, nombre y apellidos y el número total de compras que ha realizado cada uno de consumidores durante el año 2020.

-- ---------------------
-- Subconsultas
-- -----------------------------------------------
-- 0,2 puntos la correcta (1-5).
-- 0,3 puntos la correcta (6-9).
-- Total = 2,2 puntos
-- -----------------------------------------------

--- Con operadores básicos de comparación

-- 1. Devuelve un listado con todos las compras que ha realizado Adela Salas Díaz. (Sin utilizar INNER JOIN).
-- 2. Devuelve la fecha y la cantidad del compra de menor valor realizado por el cliente Pepe Ruiz Santana.
-- 3. Devuelve el número de compras en los que ha participado el suministrador Daniel Sáez Vega. (Sin utilizar INNER JOIN)
-- 4. Devuelve los datos del consumidor que realizó el compra más caro en el año 2021. (Sin utilizar INNER JOIN)
-- 5. Devuelve un listado con los datos de los consumidores y las compras, de todos los consumidores que han realizado un compra durante el año 2020 con un valor mayor o igual al valor medio de las compras realizadas durante ese mismo año.
-- 6. Devuelve un listado de los consumidores que no han realizado ningún compra. (Utilizando IN o NOT IN).
-- 7. Devuelve un listado de los suministradores que no han realizado ningún compra. (Utilizando IN o NOT IN).
-- 8. Devuelve un listado de los consumidores que no han realizado ningún compra. (Utilizando EXISTS o NOT EXISTS).
-- 9. Devuelve un listado de los suministradores que no han realizado ningún compra. (Utilizando EXISTS o NOT EXISTS).

</div>
