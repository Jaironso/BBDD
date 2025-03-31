<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

## **Unidad 3. Tarea 6: Lenguajes de definición/consulta y manipulación de información en Base de Datos.**


-- Obtener todos los clientes.

<details>
<summary>Respuesta</summary>
  
```
select * from clientes;
┌────┬─────────────────┬───────────────────────────┐
│ id │     nombre      │           email           │
├────┼─────────────────┼───────────────────────────┤
│ 1  │ Juan Pérez      │ juan@example.com          │
│ 2  │ María Gómez     │ maria@example.com         │
│ 3  │ Carlos López    │ carlos@example.com        │
│ 4  │ Ana Rodríguez   │ ana@example.com           │
│ 5  │ Luisa Martínez  │ luisa@example.com         │
│ 6  │ Pedro Sánchez   │ pedro@example.com         │
│ 7  │ Laura García    │ laura@example.com         │
│ 8  │ Miguel Martín   │ miguel@example.com        │
│ 9  │ Elena González  │ elena@example.com         │
│ 10 │ David Torres    │ david@example.com         │
│ 11 │ Sofía Ruiz      │ sofia@example.com         │
│ 12 │ Javier López    │ javier@example.com        │
│ 13 │ Carmen Vargas   │ carmen@example.com        │
│ 14 │ Daniel Muñoz    │ daniel@example.com        │
│ 15 │ Isabel Serrano  │ isabel@example.com        │
│ 16 │ Alejandro Muñoz │ alejandro@example.com     │
│ 17 │ Raquel Herrera  │ raquel@example.com        │
│ 18 │ Francisco Mora  │ francisco@example.com     │
│ 19 │ Marina Díaz     │ marina@example.com        │
│ 20 │ Antonio Jiménez │ antonio@example.com       │
│ 21 │ Beatriz Romero  │ beatriz@example.com       │
│ 22 │ Carlos Gómez    │ carlos.gomez@example.com  │
│ 23 │ Clara Sánchez   │ clara.sanchez@example.com │
│ 24 │ Andrés Martínez │ andres@example.com        │
│ 25 │ Lucía Díaz      │ lucia@example.com         │
│ 26 │ Mario Serrano   │ mario@example.com         │
│ 27 │ Eva Torres      │ eva.torres@example.com    │
│ 28 │ Roberto Ruiz    │ roberto@example.com       │
│ 29 │ Celia García    │ celia@example.com         │
└────┴─────────────────┴───────────────────────────┘
```
</details>

-- Obtener la cantidad total de productos en todos los pedidos.

<details>
<summary>Respuesta</summary>
  
```
select SUM(cantidad) AS Q_total_Prod_Pedidos from Pedidos;
┌──────────────────────┐
│ Q_total_Prod_Pedidos │
├──────────────────────┤
│ 54                   │
└──────────────────────┘
```
</details>

-- Obtener el precio promedio de los productos:

<details>
<summary>Respuesta</summary>
  
```
select AVG(precio) Precio_Medio from productos;
┌──────────────────┐
│   Precio_Medio   │
├──────────────────┤
│ 188.294285714286 │
└──────────────────┘
```
</details>

-- Obtener los clientes que tienen un email válido (contiene '@'):

<details>
<summary>Respuesta</summary>
  
```
select email from clientes where email REGEXP '@';
┌───────────────────────────┐
│           email           │
├───────────────────────────┤
│ alejandro@example.com     │
│ ana@example.com           │
│ andres@example.com        │
│ antonio@example.com       │
│ beatriz@example.com       │
│ carlos.gomez@example.com  │
│ carlos@example.com        │
│ carmen@example.com        │
│ celia@example.com         │
│ clara.sanchez@example.com │
│ daniel@example.com        │
│ david@example.com         │
│ elena@example.com         │
│ eva.torres@example.com    │
│ francisco@example.com     │
│ isabel@example.com        │
│ javier@example.com        │
│ juan@example.com          │
│ laura@example.com         │
│ lucia@example.com         │
│ luisa@example.com         │
│ maria@example.com         │
│ marina@example.com        │
│ mario@example.com         │
│ miguel@example.com        │
│ pedro@example.com         │
│ raquel@example.com        │
│ roberto@example.com       │
│ sofia@example.com         │
└───────────────────────────┘
```
</details>

-- Obtener el producto más caro.

<details>
<summary>Respuesta</summary>
  
```
select nombre, MAX(precio) from productos;
┌────────┬─────────────┐
│ nombre │ MAX(precio) │
├────────┼─────────────┤
│ Laptop │ 1200.0      │
└────────┴─────────────┘
```

-- Obtener los pedidos realizados en febrero de 2024.


<details>
<summary>Respuesta</summary>
  
```
select * from pedidos where fecha_pedido REGEXP '2024-02-[0-9]{2}';
┌───────────┬────────────┬─────────────┬──────────┬──────────────┐
│ id_pedido │ id_cliente │ id_producto │ cantidad │ fecha_pedido │
├───────────┼────────────┼─────────────┼──────────┼──────────────┤
│ 1         │ 1          │ 1           │ 2        │ 2024-02-01   │
│ 2         │ 2          │ 2           │ 1        │ 2024-02-02   │
│ 3         │ 3          │ 3           │ 3        │ 2024-02-03   │
│ 4         │ 4          │ 4           │ 1        │ 2024-02-04   │
│ 5         │ 5          │ 5           │ 2        │ 2024-02-05   │
│ 6         │ 6          │ 6           │ 1        │ 2024-02-06   │
│ 7         │ 7          │ 7           │ 3        │ 2024-02-07   │
│ 8         │ 8          │ 8           │ 2        │ 2024-02-08   │
│ 9         │ 9          │ 9           │ 1        │ 2024-02-09   │
│ 10        │ 10         │ 10          │ 2        │ 2024-02-10   │
│ 11        │ 11         │ 11          │ 1        │ 2024-02-11   │
│ 12        │ 12         │ 12          │ 3        │ 2024-02-12   │
│ 13        │ 13         │ 13          │ 1        │ 2024-02-13   │
│ 14        │ 14         │ 14          │ 2        │ 2024-02-14   │
│ 15        │ 15         │ 15          │ 1        │ 2024-02-15   │
│ 16        │ 16         │ 16          │ 3        │ 2024-02-16   │
│ 17        │ 17         │ 17          │ 2        │ 2024-02-17   │
│ 18        │ 18         │ 18          │ 1        │ 2024-02-18   │
│ 19        │ 19         │ 19          │ 2        │ 2024-02-19   │
│ 20        │ 20         │ 20          │ 1        │ 2024-02-20   │
│ 21        │ 21         │ 21          │ 3        │ 2024-02-21   │
│ 22        │ 22         │ 22          │ 1        │ 2024-02-22   │
│ 23        │ 23         │ 23          │ 2        │ 2024-02-23   │
│ 24        │ 24         │ 24          │ 1        │ 2024-02-24   │
│ 25        │ 25         │ 25          │ 3        │ 2024-02-25   │
│ 26        │ 26         │ 26          │ 2        │ 2024-02-26   │
│ 27        │ 27         │ 27          │ 1        │ 2024-02-27   │
│ 28        │ 28         │ 28          │ 2        │ 2024-02-28   │
│ 29        │ 29         │ 29          │ 1        │ 2024-02-29   │
└───────────┴────────────┴─────────────┴──────────┴──────────────┘
```

-- Obtener la cantidad total de productos en todos los pedidos por producto.

<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener los clientes que han realizado más de un pedido.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener los productos que tienen un precio registrado.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener la fecha del primer pedido realizado:
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener los productos cuyos nombres comienzan con 'A' o 'B':
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener la cantidad total de productos en todos los pedidos por cliente ordenado por cliente.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener los clientes que han realizado más de un pedido en febrero de 2024.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener los productos con precio entre 100 y 500.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener la cantidad total de productos en todos los pedidos por cliente ordenado por cantidad descendente.

<details>
<summary>Respuesta</summary>
  
```

```
-- Obtener los clientes que tienen una 'a' en cualquier posición de su nombre.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener el precio máximo de los productos.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener los pedidos realizados por el cliente con ID 1 en febrero de 2024.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener la cantidad total de productos en todos los pedidos por producto ordenado por total de productos descendente.

<details>
<summary>Respuesta</summary>
  
```

```
-- Obtener los productos que no tienen un precio registrado.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener la fecha del último pedido realizado.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener los clientes cuyo nombre tiene al menos 5 caracteres.

<details>
<summary>Respuesta</summary>
  
```

```
-- Obtener los productos que tienen la letra 'o' en cualquier posición del nombre.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener la cantidad total de productos en todos los pedidos por cliente ordenado por cliente.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener los clientes cuyos nombres no contienen la letra 'i':
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener los pedidos realizados por el cliente con ID 2 en febrero de 2024.

<details>
<summary>Respuesta</summary>
  
```

```
-- Obtener el precio mínimo de los productos.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener los clientes que han realizado al menos un pedido en febrero de 2024.

<details>
<summary>Respuesta</summary>
  
```

```
-- Obtener la fecha del último pedido realizado por el cliente con ID 3.

<details>
<summary>Respuesta</summary>
  
```

```
-- Obtener los productos que tienen una 'a' al final del nombre.
<details>
<summary>Respuesta</summary>
  
```

```

-- Obtener los clientes cuyos nombres tienen al menos 4 vocales (mayúsculas|minúsculas).

<details>
<summary>Respuesta</summary>
  
```

```
-- Obtener los productos cuyo precio tenga al menos 4 números sin contrar los decimales.

<details>
<summary>Respuesta</summary>
  
```

```
-- Obtener los clientes cuyos nombres tienen al menos una 'a' seguida de una 'e'.

<details>
<summary>Respuesta</summary>
  
```

```
-- Obtener los productos cuyos nombres terminan con una consonante.

<details>
<summary>Respuesta</summary>
  
```

```
-- Obtener los productos cuyos nombres empiezan con una vocal.
<details>
<summary>Respuesta</summary>
  
```

```

</div>
