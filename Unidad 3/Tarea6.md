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
</details>

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
</details>

-- Obtener la cantidad total de productos en todos los pedidos por producto.

<details>
<summary>Respuesta</summary>
  
```
select pe.id_pedido, p.nombre, pe.cantidad from Pedidos pe
JOIN Productos p ON pe.id_producto = p.id;
┌───────────┬───────────────────────────────────┬──────────┐
│ id_pedido │              nombre               │ cantidad │
├───────────┼───────────────────────────────────┼──────────┤
│ 1         │ Laptop                            │ 2        │
│ 2         │ Smartphone                        │ 1        │
│ 3         │ TV LED                            │ 3        │
│ 4         │ Tablet                            │ 1        │
│ 5         │ Auriculares Bluetooth             │ 2        │
│ 6         │ Impresora                         │ 1        │
│ 7         │ Cámara Digital                    │ 3        │
│ 8         │ Reproductor de Audio              │ 2        │
│ 9         │ Altavoces Inalámbricos            │ 1        │
│ 10        │ Reloj Inteligente                 │ 2        │
│ 11        │ Teclado Inalámbrico               │ 1        │
│ 12        │ Ratón Óptico                      │ 3        │
│ 13        │ Monitor LED                       │ 1        │
│ 14        │ Mochila para Portátil             │ 2        │
│ 15        │ Disco Duro Externo                │ 1        │
│ 16        │ Router Wi-Fi                      │ 3        │
│ 17        │ Lámpara LED                       │ 2        │
│ 18        │ Batería Externa                   │ 1        │
│ 19        │ Estuche para Auriculares          │ 2        │
│ 20        │ Tarjeta de Memoria                │ 1        │
│ 21        │ Cargador Inalámbrico              │ 3        │
│ 22        │ Kit de Limpieza para Computadoras │ 1        │
│ 23        │ Funda para Tablet                 │ 2        │
│ 24        │ Soporte para Teléfono             │ 1        │
│ 25        │ Hub USB                           │ 3        │
│ 26        │ Webcam HD                         │ 2        │
│ 27        │ Funda para Laptop                 │ 1        │
│ 28        │ Adaptador HDMI                    │ 2        │
└───────────┴───────────────────────────────────┴──────────┘
```
</details>

-- Obtener los clientes que han realizado más de un pedido.
<details>
<summary>Respuesta</summary>
  
```
select c.nombre, COUNT(p.id_cliente) AS Q_Pedidos from Clientes c
JOIN Pedidos p ON c.id  = p.id_cliente
GROUP BY p.id_cliente
HAVING COUNT(p.id_cliente) > 1;
Respuesta: Ningún cliente realizó más de un pedido.
```
</details>

-- Obtener los productos que tienen un precio registrado.
<details>
<summary>Respuesta</summary>
  
```
select nombre, precio from productos;
┌───────────────────────────────────┬────────┐
│              nombre               │ precio │
├───────────────────────────────────┼────────┤
│ Laptop                            │ 1200.0 │
│ Smartphone                        │ 699.99 │
│ TV LED                            │ 799.5  │
│ Tablet                            │ 299.99 │
│ Auriculares Bluetooth             │ 79.99  │
│ Impresora                         │ 199.99 │
│ Cámara Digital                    │ 499.99 │
│ Reproductor de Audio              │ 149.99 │
│ Altavoces Inalámbricos            │ 129.99 │
│ Reloj Inteligente                 │ 249.99 │
│ Teclado Inalámbrico               │ 59.99  │
│ Ratón Óptico                      │ 29.99  │
│ Monitor LED                       │ 349.99 │
│ Mochila para Portátil             │ 49.99  │
│ Disco Duro Externo                │ 89.99  │
│ Router Wi-Fi                      │ 69.99  │
│ Lámpara LED                       │ 39.99  │
│ Batería Externa                   │ 19.99  │
│ Estuche para Auriculares          │ 14.99  │
│ Tarjeta de Memoria                │ 24.99  │
│ Cargador Inalámbrico              │ 34.99  │
│ Kit de Limpieza para Computadoras │ 9.99   │
│ Funda para Tablet                 │ 19.99  │
│ Soporte para Teléfono             │ 14.99  │
│ Hub USB                           │ 29.99  │
│ Webcam HD                         │ 59.99  │
│ Funda para Laptop                 │ 29.99  │
│ Adaptador HDMI                    │ 12.99  │
└───────────────────────────────────┴────────┘
```
</details>

-- Obtener la fecha del primer pedido realizado:

<details>
<summary>Respuesta</summary>
  
```
sqlite> select id_pedido, MIN(fecha_pedido) from Pedidos;
┌───────────┬───────────────────┐
│ id_pedido │ MIN(fecha_pedido) │
├───────────┼───────────────────┤
│ 1         │ 2024-02-01        │
└───────────┴───────────────────┘
sqlite>
```
</details>

-- Obtener los productos cuyos nombres comienzan con 'A' o 'B':
<details>
<summary>Respuesta</summary>
  
```
select nombre from productos where nombre REGEXP '^[Aa]|^[Bb]';
┌────────────────────────┐
│         nombre         │
├────────────────────────┤
│ Auriculares Bluetooth  │
│ Altavoces Inalámbricos │
│ Batería Externa        │
│ Adaptador HDMI         │
└────────────────────────┘
```
</details>

-- Obtener la cantidad total de productos en todos los pedidos por cliente ordenado por cliente.
<details>
<summary>Respuesta</summary>
  
```
select c.nombre, pe.id_pedido, SUM(pe.cantidad) AS Q_total_productos from Pedidos pe
JOIN Clientes c ON pe.id_cliente = c.id
GROUP BY pe.id_pedido
ORDER BY c.nombre;
┌─────────────────┬───────────┬───────────────────┐
│     nombre      │ id_pedido │ Q_total_productos │
├─────────────────┼───────────┼───────────────────┤
│ Alejandro Muñoz │ 16        │ 3                 │
│ Ana Rodríguez   │ 4         │ 1                 │
│ Andrés Martínez │ 24        │ 1                 │
│ Antonio Jiménez │ 20        │ 1                 │
│ Beatriz Romero  │ 21        │ 3                 │
│ Carlos Gómez    │ 22        │ 1                 │
│ Carlos López    │ 3         │ 3                 │
│ Carmen Vargas   │ 13        │ 1                 │
│ Celia García    │ 29        │ 1                 │
│ Clara Sánchez   │ 23        │ 2                 │
│ Daniel Muñoz    │ 14        │ 2                 │
│ David Torres    │ 10        │ 2                 │
│ Elena González  │ 9         │ 1                 │
│ Eva Torres      │ 27        │ 1                 │
│ Francisco Mora  │ 18        │ 1                 │
│ Isabel Serrano  │ 15        │ 1                 │
│ Javier López    │ 12        │ 3                 │
│ Juan Pérez      │ 1         │ 2                 │
│ Laura García    │ 7         │ 3                 │
│ Lucía Díaz      │ 25        │ 3                 │
│ Luisa Martínez  │ 5         │ 2                 │
│ Marina Díaz     │ 19        │ 2                 │
│ Mario Serrano   │ 26        │ 2                 │
│ María Gómez     │ 2         │ 1                 │
│ Miguel Martín   │ 8         │ 2                 │
│ Pedro Sánchez   │ 6         │ 1                 │
│ Raquel Herrera  │ 17        │ 2                 │
│ Roberto Ruiz    │ 28        │ 2                 │
│ Sofía Ruiz      │ 11        │ 1                 │
└─────────────────┴───────────┴───────────────────┘
```
</details>

-- Obtener los clientes que han realizado más de un pedido en febrero de 2024.
<details>
<summary>Respuesta</summary>
  
```
select c.nombre, COUNT(p.id_cliente) AS Q_Pedidos from Clientes c
JOIN Pedidos p ON c.id  = p.id_cliente GROUP BY p.id_cliente
HAVING COUNT(p.id_cliente) > 1
AND p.fecha_pedido
REGEXP '2024-02-[0-9]';
Respuesta: Ninguno.
```
</details>


-- Obtener los productos con precio entre 100 y 500.

<details>
<summary>Respuesta</summary>
  
```
select nombre, precio from productos where precio between 100 and 500;
┌────────────────────────┬────────┐
│         nombre         │ precio │
├────────────────────────┼────────┤
│ Tablet                 │ 299.99 │
│ Impresora              │ 199.99 │
│ Cámara Digital         │ 499.99 │
│ Reproductor de Audio   │ 149.99 │
│ Altavoces Inalámbricos │ 129.99 │
│ Reloj Inteligente      │ 249.99 │
│ Monitor LED            │ 349.99 │
└────────────────────────┴────────┘
```
</details>

-- Obtener la cantidad total de productos en todos los pedidos por cliente ordenado por cantidad descendente.

<details>
<summary>Respuesta</summary>
  
```
select c.nombre, pe.id_pedido, SUM(pe.cantidad) AS Q_total_productos from Pedidos pe
JOIN Clientes c ON pe.id_cliente = c.id
GROUP BY pe.id_pedido
ORDER BY pe.cantidad DESC;
┌─────────────────┬───────────┬───────────────────┐
│     nombre      │ id_pedido │ Q_total_productos │
├─────────────────┼───────────┼───────────────────┤
│ Carlos López    │ 3         │ 3                 │
│ Laura García    │ 7         │ 3                 │
│ Javier López    │ 12        │ 3                 │
│ Alejandro Muñoz │ 16        │ 3                 │
│ Beatriz Romero  │ 21        │ 3                 │
│ Lucía Díaz      │ 25        │ 3                 │
│ Juan Pérez      │ 1         │ 2                 │
│ Luisa Martínez  │ 5         │ 2                 │
│ Miguel Martín   │ 8         │ 2                 │
│ David Torres    │ 10        │ 2                 │
│ Daniel Muñoz    │ 14        │ 2                 │
│ Raquel Herrera  │ 17        │ 2                 │
│ Marina Díaz     │ 19        │ 2                 │
│ Clara Sánchez   │ 23        │ 2                 │
│ Mario Serrano   │ 26        │ 2                 │
│ Roberto Ruiz    │ 28        │ 2                 │
│ María Gómez     │ 2         │ 1                 │
│ Ana Rodríguez   │ 4         │ 1                 │
│ Pedro Sánchez   │ 6         │ 1                 │
│ Elena González  │ 9         │ 1                 │
│ Sofía Ruiz      │ 11        │ 1                 │
│ Carmen Vargas   │ 13        │ 1                 │
│ Isabel Serrano  │ 15        │ 1                 │
│ Francisco Mora  │ 18        │ 1                 │
│ Antonio Jiménez │ 20        │ 1                 │
│ Carlos Gómez    │ 22        │ 1                 │
│ Andrés Martínez │ 24        │ 1                 │
│ Eva Torres      │ 27        │ 1                 │
│ Celia García    │ 29        │ 1                 │
└─────────────────┴───────────┴───────────────────┘
```
</details>

-- Obtener los clientes que tienen una 'a' en cualquier posición de su nombre.

<details>
<summary>Respuesta</summary>
  
```
 select nombre from Clientes where nombre REGEXP 'A|a';
┌─────────────────┐
│     nombre      │
├─────────────────┤
│ Juan Pérez      │
│ María Gómez     │
│ Carlos López    │
│ Ana Rodríguez   │
│ Luisa Martínez  │
│ Laura García    │
│ Miguel Martín   │
│ Elena González  │
│ David Torres    │
│ Sofía Ruiz      │
│ Javier López    │
│ Carmen Vargas   │
│ Daniel Muñoz    │
│ Isabel Serrano  │
│ Alejandro Muñoz │
│ Raquel Herrera  │
│ Francisco Mora  │
│ Marina Díaz     │
│ Antonio Jiménez │
│ Beatriz Romero  │
│ Carlos Gómez    │
│ Clara Sánchez   │
│ Andrés Martínez │
│ Lucía Díaz      │
│ Mario Serrano   │
│ Eva Torres      │
│ Celia García    │
└─────────────────┘
```
</details>

-- Obtener el precio máximo de los productos.

<details>
<summary>Respuesta</summary>
  
```
select MAX(precio) AS precio_max_prod from productos;
┌─────────────────┐
│ precio_max_prod │
├─────────────────┤
│ 1200.0          │
└─────────────────┘
```
</details>

-- Obtener los pedidos realizados por el cliente con ID 1 en febrero de 2024.

<details>
<summary>Respuesta</summary>
  
```
select * from pedidos where id_cliente = 1 and fecha_pedido REGEXP '2024-02-01';
┌───────────┬────────────┬─────────────┬──────────┬──────────────┐
│ id_pedido │ id_cliente │ id_producto │ cantidad │ fecha_pedido │
├───────────┼────────────┼─────────────┼──────────┼──────────────┤
│ 1         │ 1          │ 1           │ 2        │ 2024-02-01   │
└───────────┴────────────┴─────────────┴──────────┴──────────────┘
```
</details>

-- Obtener la cantidad total de productos en todos los pedidos por producto ordenado por total de productos descendente.

<details>
<summary>Respuesta</summary>
  
```
select pr.nombre, (select SUM(pe.cantidad) from pedidos pe where pr.id = pe.id_producto) AS Q_total_Productos
from productos pr
GROUP BY pr.nombre
ORDER BY Q_total_productos DESC;
┌───────────────────────────────────┬───────────────────┐
│              nombre               │ Q_total_Productos │
├───────────────────────────────────┼───────────────────┤
│ TV LED                            │ 3                 │
│ Router Wi-Fi                      │ 3                 │
│ Ratón Óptico                      │ 3                 │
│ Hub USB                           │ 3                 │
│ Cámara Digital                    │ 3                 │
│ Cargador Inalámbrico              │ 3                 │
│ Webcam HD                         │ 2                 │
│ Reproductor de Audio              │ 2                 │
│ Reloj Inteligente                 │ 2                 │
│ Mochila para Portátil             │ 2                 │
│ Lámpara LED                       │ 2                 │
│ Laptop                            │ 2                 │
│ Funda para Tablet                 │ 2                 │
│ Estuche para Auriculares          │ 2                 │
│ Auriculares Bluetooth             │ 2                 │
│ Adaptador HDMI                    │ 2                 │
│ Teclado Inalámbrico               │ 1                 │
│ Tarjeta de Memoria                │ 1                 │
│ Tablet                            │ 1                 │
│ Soporte para Teléfono             │ 1                 │
│ Smartphone                        │ 1                 │
│ Monitor LED                       │ 1                 │
│ Kit de Limpieza para Computadoras │ 1                 │
│ Impresora                         │ 1                 │
│ Funda para Laptop                 │ 1                 │
│ Disco Duro Externo                │ 1                 │
│ Batería Externa                   │ 1                 │
│ Altavoces Inalámbricos            │ 1                 │
└───────────────────────────────────┴───────────────────┘
```
</details>

-- Obtener los productos que no tienen un precio registrado.

<details>
<summary>Respuesta</summary>
  
```
No entiendo el enunciado.
```
</details>

-- Obtener la fecha del último pedido realizado.

<details>
<summary>Respuesta</summary>
  
```
select id_pedido, MAX(fecha_pedido) from pedidos;
┌───────────┬───────────────────┐
│ id_pedido │ MAX(fecha_pedido) │
├───────────┼───────────────────┤
│ 30        │ 2024-03-01        │
└───────────┴───────────────────┘
```
</details>

-- Obtener los clientes cuyo nombre tiene al menos 5 caracteres.

<details>
<summary>Respuesta</summary>
  
```
select nombre from clientes WHERE nombre REGEXP '^.{5,}$';
┌─────────────────┐
│     nombre      │
├─────────────────┤
│ Juan Pérez      │
│ María Gómez     │
│ Carlos López    │
│ Ana Rodríguez   │
│ Luisa Martínez  │
│ Pedro Sánchez   │
│ Laura García    │
│ Miguel Martín   │
│ Elena González  │
│ David Torres    │
│ Sofía Ruiz      │
│ Javier López    │
│ Carmen Vargas   │
│ Daniel Muñoz    │
│ Isabel Serrano  │
│ Alejandro Muñoz │
│ Raquel Herrera  │
│ Francisco Mora  │
│ Marina Díaz     │
│ Antonio Jiménez │
│ Beatriz Romero  │
│ Carlos Gómez    │
│ Clara Sánchez   │
│ Andrés Martínez │
│ Lucía Díaz      │
│ Mario Serrano   │
│ Eva Torres      │
│ Roberto Ruiz    │
│ Celia García    │
└─────────────────┘
```
</details>

-- Obtener los productos que tienen la letra 'o' en cualquier posición del nombre.

<details>
<summary>Respuesta</summary>
  
```
select nombre from productos where nombre REGEXP 'O|o';
┌───────────────────────────────────┐
│              nombre               │
├───────────────────────────────────┤
│ Laptop                            │
│ Smartphone                        │
│ Auriculares Bluetooth             │
│ Impresora                         │
│ Reproductor de Audio              │
│ Altavoces Inalámbricos            │
│ Reloj Inteligente                 │
│ Teclado Inalámbrico               │
│ Ratón Óptico                      │
│ Monitor LED                       │
│ Mochila para Portátil             │
│ Disco Duro Externo                │
│ Router Wi-Fi                      │
│ Tarjeta de Memoria                │
│ Cargador Inalámbrico              │
│ Kit de Limpieza para Computadoras │
│ Soporte para Teléfono             │
│ Funda para Laptop                 │
│ Adaptador HDMI                    │
└───────────────────────────────────┘
```
</details>


-- Obtener la cantidad total de productos en todos los pedidos por cliente ordenado por cliente.

<details>
<summary>Respuesta</summary>
  
```
select cl.nombre,
(select SUM(pe.cantidad) from pedidos pe where cl.id = pe.id_cliente) AS Q_total_productos from clientes cl
GROUP BY cl.nombre ORDER BY cl.nombre;
┌─────────────────┬───────────────────┐
│     nombre      │ Q_total_productos │
├─────────────────┼───────────────────┤
│ Alejandro Muñoz │ 3                 │
│ Ana Rodríguez   │ 1                 │
│ Andrés Martínez │ 1                 │
│ Antonio Jiménez │ 1                 │
│ Beatriz Romero  │ 3                 │
│ Carlos Gómez    │ 1                 │
│ Carlos López    │ 3                 │
│ Carmen Vargas   │ 1                 │
│ Celia García    │ 1                 │
│ Clara Sánchez   │ 2                 │
│ Daniel Muñoz    │ 2                 │
│ David Torres    │ 2                 │
│ Elena González  │ 1                 │
│ Eva Torres      │ 1                 │
│ Francisco Mora  │ 1                 │
│ Isabel Serrano  │ 1                 │
│ Javier López    │ 3                 │
│ Juan Pérez      │ 2                 │
│ Laura García    │ 3                 │
│ Lucía Díaz      │ 3                 │
│ Luisa Martínez  │ 2                 │
│ Marina Díaz     │ 2                 │
│ Mario Serrano   │ 2                 │
│ María Gómez     │ 1                 │
│ Miguel Martín   │ 2                 │
│ Pedro Sánchez   │ 1                 │
│ Raquel Herrera  │ 2                 │
│ Roberto Ruiz    │ 2                 │
│ Sofía Ruiz      │ 1                 │
└─────────────────┴───────────────────┘
```
</details>

-- Obtener los clientes cuyos nombres no contienen la letra 'i':

<details>
<summary>Respuesta</summary>
  
```
select nombre from clientes where nombre REGEXP 'I|i';
┌─────────────────┐
│     nombre      │
├─────────────────┤
│ Luisa Martínez  │
│ Miguel Martín   │
│ David Torres    │
│ Sofía Ruiz      │
│ Javier López    │
│ Daniel Muñoz    │
│ Isabel Serrano  │
│ Francisco Mora  │
│ Marina Díaz     │
│ Antonio Jiménez │
│ Beatriz Romero  │
│ Mario Serrano   │
│ Roberto Ruiz    │
│ Celia García    │
└─────────────────┘
```
</details>

-- Obtener los pedidos realizados por el cliente con ID 2 en febrero de 2024.

<details>
<summary>Respuesta</summary>
  
```
select * from pedidos where id_cliente = 2 and fecha_pedido REGEXP '2024-02-[0-9]';
┌───────────┬────────────┬─────────────┬──────────┬──────────────┐
│ id_pedido │ id_cliente │ id_producto │ cantidad │ fecha_pedido │
├───────────┼────────────┼─────────────┼──────────┼──────────────┤
│ 2         │ 2          │ 2           │ 1        │ 2024-02-02   │
└───────────┴────────────┴─────────────┴──────────┴──────────────┘
```
</details>

-- Obtener el precio mínimo de los productos.

<details>
<summary>Respuesta</summary>
  
```
select MIN(precio) AS precio_min_prod from productos;
┌─────────────────┐
│ precio_min_prod │
├─────────────────┤
│ 9.99            │
└─────────────────┘
```
</details>

-- Obtener los clientes que han realizado al menos un pedido en febrero de 2024.

<details>
<summary>Respuesta</summary>
  
```
select c.nombre, COUNT(p.id_cliente) AS Q_Pedidos from Clientes c
JOIN Pedidos p ON c.id  = p.id_cliente GROUP BY p.id_cliente
HAVING COUNT(p.id_cliente) >= 1 AND fecha_pedido
REGEXP '2024-02-[0-9]{2}';
┌─────────────────┬───────────┐
│     nombre      │ Q_Pedidos │
├─────────────────┼───────────┤
│ Juan Pérez      │ 1         │
│ María Gómez     │ 1         │
│ Carlos López    │ 1         │
│ Ana Rodríguez   │ 1         │
│ Luisa Martínez  │ 1         │
│ Pedro Sánchez   │ 1         │
│ Laura García    │ 1         │
│ Miguel Martín   │ 1         │
│ Elena González  │ 1         │
│ David Torres    │ 1         │
│ Sofía Ruiz      │ 1         │
│ Javier López    │ 1         │
│ Carmen Vargas   │ 1         │
│ Daniel Muñoz    │ 1         │
│ Isabel Serrano  │ 1         │
│ Alejandro Muñoz │ 1         │
│ Raquel Herrera  │ 1         │
│ Francisco Mora  │ 1         │
│ Marina Díaz     │ 1         │
│ Antonio Jiménez │ 1         │
│ Beatriz Romero  │ 1         │
│ Carlos Gómez    │ 1         │
│ Clara Sánchez   │ 1         │
│ Andrés Martínez │ 1         │
│ Lucía Díaz      │ 1         │
│ Mario Serrano   │ 1         │
│ Eva Torres      │ 1         │
│ Roberto Ruiz    │ 1         │
│ Celia García    │ 1         │
└─────────────────┴───────────┘
```
</details>

-- Obtener la fecha del último pedido realizado por el cliente con ID 3.

<details>
<summary>Respuesta</summary>
  
```
select id_cliente, MAX(fecha_pedido) from pedidos where id_cliente= 3;
┌────────────┬───────────────────┐
│ id_cliente │ MAX(fecha_pedido) │
├────────────┼───────────────────┤
│ 3          │ 2024-02-03        │
└────────────┴───────────────────┘
```
</details>

-- Obtener los productos que tienen una 'a' al final del nombre.

<details>
<summary>Respuesta</summary>
  
```
select nombre from productos where nombre REGEXP '[a|A]$';
┌────────────────────┐
│       nombre       │
├────────────────────┤
│ Impresora          │
│ Batería Externa    │
│ Tarjeta de Memoria │
└────────────────────┘
```
</details>

-- Obtener los clientes cuyos nombres tienen al menos 4 vocales (mayúsculas|minúsculas).

<details>
<summary>Respuesta</summary>
  
```

```
</details>

-- Obtener los productos cuyo precio tenga al menos 4 números sin contrar los decimales.

<details>
<summary>Respuesta</summary>
  
```

```
</details>

-- Obtener los clientes cuyos nombres tienen al menos una 'a' seguida de una 'e'.

<details>
<summary>Respuesta</summary>
  
```

```
</details>

-- Obtener los productos cuyos nombres terminan con una consonante.

<details>
<summary>Respuesta</summary>
  
```
select nombre from productos where nombre REGEXP '[^aeiou|AEIOU]$';
┌───────────────────────────────────┐
│              nombre               │
├───────────────────────────────────┤
│ Laptop                            │
│ TV LED                            │
│ Tablet                            │
│ Auriculares Bluetooth             │
│ Cámara Digital                    │
│ Altavoces Inalámbricos            │
│ Monitor LED                       │
│ Mochila para Portátil             │
│ Lámpara LED                       │
│ Estuche para Auriculares          │
│ Kit de Limpieza para Computadoras │
│ Funda para Tablet                 │
│ Hub USB                           │
│ Webcam HD                         │
│ Funda para Laptop                 │
└───────────────────────────────────┘
```
</details>

-- Obtener los productos cuyos nombres empiezan con una vocal.

<details>
<summary>Respuesta</summary>
  
```
select nombre from productos where nombre REGEXP '^[aeiou|AEIOU]';
┌──────────────────────────┐
│          nombre          │
├──────────────────────────┤
│ Auriculares Bluetooth    │
│ Impresora                │
│ Altavoces Inalámbricos   │
│ Estuche para Auriculares │
│ Adaptador HDMI           │
└──────────────────────────┘
```
</details>

</div>
