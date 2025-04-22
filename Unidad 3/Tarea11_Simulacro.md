<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

## **Unidad 3. Tarea 11: Simulacro de Examen**

-- 1. Consultas Básicas (8 consultas - 1.6 puntos)
-- Listar todos los libros disponibles.

<details>
<summary>Respuesta</summary>

```
select * from libro;
┌────┬───────────────────────────────────┬────────────────────────┬─────────────────┬─────────────────┬────────────┐
│ id │              titulo               │         autor          │     genero      │ año_publicacion │ disponible │
├────┼───────────────────────────────────┼────────────────────────┼─────────────────┼─────────────────┼────────────┤
│ 1  │ El Quijote                        │ Miguel de Cervantes    │ Clásico         │ 1605            │ 1          │
│ 2  │ Cien años de soledad              │ Gabriel García Márquez │ Realismo mágico │ 1967            │ 0          │
│ 3  │ 1984                              │ George Orwell          │ Ciencia ficción │ 1949            │ 1          │
│ 4  │ Orgullo y prejuicio               │ Jane Austen            │ Romance         │ 1813            │ 0          │
│ 5  │ La sombra del viento              │ Carlos Ruiz Zafón      │ Misterio        │ 2001            │ 1          │
│ 6  │ Rayuela                           │ Julio Cortázar         │ Experimental    │ 1963            │ 0          │
│ 7  │ Ficciones                         │ Jorge Luis Borges      │ Cuentos         │ 1944            │ 1          │
│ 8  │ Los pilares de la Tierra          │ Ken Follett            │ Histórica       │ 1989            │ 0          │
│ 9  │ El amor en los tiempos del cólera │ Gabriel García Márquez │ Romance         │ 1985            │ 1          │
│ 10 │ La casa de los espíritus          │ Isabel Allende         │ Realismo mágico │ 1982            │ 0          │
└────┴───────────────────────────────────┴────────────────────────┴─────────────────┴─────────────────┴────────────┘
```
</details>


-- Mostrar socios de Madrid ordenados por apellido

<details>
<summary>Respuesta</summary>

```
select * from socio where ciudad = 'Madrid' ORDER BY apellido1;
┌────┬────────┬───────────┬───────────┬────────┬────────────┬───────────┐
│ id │ nombre │ apellido1 │ apellido2 │ ciudad │ fecha_alta │ categoria │
├────┼────────┼───────────┼───────────┼────────┼────────────┼───────────┤
│ 1  │ Laura  │ García    │ Martínez  │ Madrid │ 2020-03-15 │ A         │
│ 5  │ Elena  │ Martín    │ Díaz      │ Madrid │ 2023-02-18 │ B         │
└────┴────────┴───────────┴───────────┴────────┴────────────┴───────────┘
```
</details>

-- Libros publicados después de 1950

<details>
<summary>Respuesta</summary>

```
select * from libro WHERE año_publicacion > 1950 ORDER BY año_publicacion;
┌────┬───────────────────────────────────┬────────────────────────┬─────────────────┬─────────────────┬────────────┐
│ id │              titulo               │         autor          │     genero      │ año_publicacion │ disponible │
├────┼───────────────────────────────────┼────────────────────────┼─────────────────┼─────────────────┼────────────┤
│ 6  │ Rayuela                           │ Julio Cortázar         │ Experimental    │ 1963            │ 0          │
│ 2  │ Cien años de soledad              │ Gabriel García Márquez │ Realismo mágico │ 1967            │ 0          │
│ 10 │ La casa de los espíritus          │ Isabel Allende         │ Realismo mágico │ 1982            │ 0          │
│ 9  │ El amor en los tiempos del cólera │ Gabriel García Márquez │ Romance         │ 1985            │ 1          │
│ 8  │ Los pilares de la Tierra          │ Ken Follett            │ Histórica       │ 1989            │ 0          │
│ 5  │ La sombra del viento              │ Carlos Ruiz Zafón      │ Misterio        │ 2001            │ 1          │
└────┴───────────────────────────────────┴────────────────────────┴─────────────────┴─────────────────┴────────────┘
```
</details>

-- Bibliotecarios con más de 3 años de antigüedad

<details>
<summary>Respuesta</summary>

```
select * from bibliotecario where antiguedad > 3 ORDER BY antiguedad;
┌────┬───────────┬───────────┬───────────┬────────────┐
│ id │  nombre   │ apellido1 │ apellido2 │ antiguedad │
├────┼───────────┼───────────┼───────────┼────────────┤
│ 6  │ Isabel    │ Morales   │ Iglesias  │ 4          │
│ 1  │ Daniel    │ Vázquez   │ Gil       │ 5          │
│ 7  │ Francisco │ Santana   │ Méndez    │ 6          │
│ 4  │ Lucía     │ Reyes     │ Martín    │ 7          │
└────┴───────────┴───────────┴───────────┴────────────┘
```
</details>

-- Préstamos realizados en 2023


<details>
<summary>Respuesta</summary>

```
select * from prestamo WHERE fecha_prestamo REGEXP '2023-[0-9]{2}-[0-9]{2}' ORDER BY fecha_prestamo;
┌────┬────────────────┬──────────────────┬──────────┬──────────┐
│ id │ fecha_prestamo │ fecha_devolucion │ id_socio │ id_libro │
├────┼────────────────┼──────────────────┼──────────┼──────────┤
│ 11 │ 2023-01-05     │ 2023-01-19       │ 1        │ 1        │
│ 1  │ 2023-01-10     │ 2023-01-24       │ 1        │ 2        │
│ 6  │ 2023-01-22     │ 2023-02-05       │ 6        │ 2        │
│ 12 │ 2023-02-10     │ 2023-02-24       │ 2        │ 3        │
│ 2  │ 2023-02-15     │ 2023-03-01       │ 3        │ 4        │
│ 7  │ 2023-02-18     │ 2023-03-04       │ 7        │ 4        │
│ 13 │ 2023-03-15     │                  │ 3        │ 5        │
│ 3  │ 2023-03-20     │                  │ 5        │ 6        │
│ 8  │ 2023-03-25     │                  │ 8        │ 6        │
│ 4  │ 2023-04-05     │ 2023-04-19       │ 2        │ 8        │
│ 9  │ 2023-04-10     │ 2023-04-24       │ 9        │ 8        │
│ 14 │ 2023-04-20     │ 2023-05-04       │ 4        │ 7        │
│ 5  │ 2023-05-12     │                  │ 4        │ 10       │
│ 10 │ 2023-05-15     │                  │ 10       │ 10       │
│ 15 │ 2023-05-25     │                  │ 5        │ 9        │
└────┴────────────────┴──────────────────┴──────────┴──────────┘

```
</details>

-- Socios sin segundo apellido


<details>
<summary>Respuesta</summary>

```
select * from socio where apellido2 IS NULL;
┌────┬──────────┬───────────┬───────────┬───────────┬────────────┬───────────┐
│ id │  nombre  │ apellido1 │ apellido2 │  ciudad   │ fecha_alta │ categoria │
├────┼──────────┼───────────┼───────────┼───────────┼────────────┼───────────┤
│ 3  │ Ana      │ Sánchez   │           │ Valencia  │ 2022-01-10 │ C         │
│ 9  │ Patricia │ Romero    │           │ Barcelona │ 2023-01-15 │ A         │
└────┴──────────┴───────────┴───────────┴───────────┴────────────┴───────────┘
```
</details>

-- Libros del género "Realismo mágico"


<details>
<summary>Respuesta</summary>

```
select * from libro where genero = 'Realismo mágico';
┌────┬──────────────────────────┬────────────────────────┬─────────────────┬─────────────────┬────────────┐
│ id │          titulo          │         autor          │     genero      │ año_publicacion │ disponible │
├────┼──────────────────────────┼────────────────────────┼─────────────────┼─────────────────┼────────────┤
│ 2  │ Cien años de soledad     │ Gabriel García Márquez │ Realismo mágico │ 1967            │ 0          │
│ 10 │ La casa de los espíritus │ Isabel Allende         │ Realismo mágico │ 1982            │ 0          │
└────┴──────────────────────────┴────────────────────────┴─────────────────┴─────────────────┴────────────┘
```
</details>

-- Préstamos no devueltos (fecha_devolucion IS NULL)


<details>
<summary>Respuesta</summary>

```
select * from prestamo where fecha_devolucion IS NULL;
┌────┬────────────────┬──────────────────┬──────────┬──────────┐
│ id │ fecha_prestamo │ fecha_devolucion │ id_socio │ id_libro │
├────┼────────────────┼──────────────────┼──────────┼──────────┤
│ 3  │ 2023-03-20     │                  │ 5        │ 6        │
│ 5  │ 2023-05-12     │                  │ 4        │ 10       │
│ 8  │ 2023-03-25     │                  │ 8        │ 6        │
│ 10 │ 2023-05-15     │                  │ 10       │ 10       │
│ 13 │ 2023-03-15     │                  │ 3        │ 5        │
│ 15 │ 2023-05-25     │                  │ 5        │ 9        │
└────┴────────────────┴──────────────────┴──────────┴──────────┘
```
</details>

-- 2. Consultas Multitabla (WHERE) (8 consultas - 2.4 puntos)
-- Préstamos con nombres de socio y libro (sin JOIN)


<details>
<summary>Respuesta</summary>

```
select p.*, s.nombre, l.titulo from prestamo p, libro l, socio s
WHERE p.id_socio = s.id
AND p.id_libro = l.id; 
┌────┬────────────────┬──────────────────┬──────────┬──────────┬──────────┬───────────────────────────────────┐
│ id │ fecha_prestamo │ fecha_devolucion │ id_socio │ id_libro │  nombre  │              titulo               │
├────┼────────────────┼──────────────────┼──────────┼──────────┼──────────┼───────────────────────────────────┤
│ 1  │ 2023-01-10     │ 2023-01-24       │ 1        │ 2        │ Laura    │ Cien años de soledad              │
│ 2  │ 2023-02-15     │ 2023-03-01       │ 3        │ 4        │ Ana      │ Orgullo y prejuicio               │
│ 3  │ 2023-03-20     │                  │ 5        │ 6        │ Elena    │ Rayuela                           │
│ 4  │ 2023-04-05     │ 2023-04-19       │ 2        │ 8        │ Carlos   │ Los pilares de la Tierra          │
│ 5  │ 2023-05-12     │                  │ 4        │ 10       │ David    │ La casa de los espíritus          │
│ 6  │ 2023-01-22     │ 2023-02-05       │ 6        │ 2        │ Javier   │ Cien años de soledad              │
│ 7  │ 2023-02-18     │ 2023-03-04       │ 7        │ 4        │ Sofía    │ Orgullo y prejuicio               │
│ 8  │ 2023-03-25     │                  │ 8        │ 6        │ Miguel   │ Rayuela                           │
│ 9  │ 2023-04-10     │ 2023-04-24       │ 9        │ 8        │ Patricia │ Los pilares de la Tierra          │
│ 10 │ 2023-05-15     │                  │ 10       │ 10       │ Antonio  │ La casa de los espíritus          │
│ 11 │ 2023-01-05     │ 2023-01-19       │ 1        │ 1        │ Laura    │ El Quijote                        │
│ 12 │ 2023-02-10     │ 2023-02-24       │ 2        │ 3        │ Carlos   │ 1984                              │
│ 13 │ 2023-03-15     │                  │ 3        │ 5        │ Ana      │ La sombra del viento              │
│ 14 │ 2023-04-20     │ 2023-05-04       │ 4        │ 7        │ David    │ Ficciones                         │
│ 15 │ 2023-05-25     │                  │ 5        │ 9        │ Elena    │ El amor en los tiempos del cólera │
└────┴────────────────┴──────────────────┴──────────┴──────────┴──────────┴───────────────────────────────────┘

```
</details>
-- Libros prestados a socios de Barcelona (sin JOIN)

<details>
<summary>Respuesta</summary>

```
select p.*, s.nombre, s.ciudad, l.titulo from prestamo p, libro l, socio s
WHERE p.id_socio = s.id
AND p.id_libro = l.id
AND s.ciudad = 'Barcelona'; 
┌────┬────────────────┬──────────────────┬──────────┬──────────┬──────────┬───────────┬──────────────────────────┐
│ id │ fecha_prestamo │ fecha_devolucion │ id_socio │ id_libro │  nombre  │  ciudad   │          titulo          │
├────┼────────────────┼──────────────────┼──────────┼──────────┼──────────┼───────────┼──────────────────────────┤
│ 4  │ 2023-04-05     │ 2023-04-19       │ 2        │ 8        │ Carlos   │ Barcelona │ Los pilares de la Tierra │
│ 9  │ 2023-04-10     │ 2023-04-24       │ 9        │ 8        │ Patricia │ Barcelona │ Los pilares de la Tierra │
│ 12 │ 2023-02-10     │ 2023-02-24       │ 2        │ 3        │ Carlos   │ Barcelona │ 1984                     │
└────┴────────────────┴──────────────────┴──────────┴──────────┴──────────┴───────────┴──────────────────────────┘
```
</details>
-- Socios que han tomado prestado "Cien años de soledad" (sin JOIN)

<details>
<summary>Respuesta</summary>

```
select s.* from prestamo p, libro l, socio s
WHERE p.id_socio = s.id
AND p.id_libro = l.id
AND l.titulo = 'Cien años de soledad'; 
┌────┬────────┬───────────┬───────────┬────────┬────────────┬───────────┐
│ id │ nombre │ apellido1 │ apellido2 │ ciudad │ fecha_alta │ categoria │
├────┼────────┼───────────┼───────────┼────────┼────────────┼───────────┤
│ 1  │ Laura  │ García    │ Martínez  │ Madrid │ 2020-03-15 │ A         │
│ 6  │ Javier │ Ruiz      │ Moreno    │ Bilbao │ 2020-07-22 │ A         │
└────┴────────┴───────────┴───────────┴────────┴────────────┴───────────┘
```
</details>
-- Bibliotecarios que han gestionado préstamos (sin JOIN)


<details>
<summary>Respuesta</summary>

```
no se puede hacer
```
</details>
-- Préstamos con retraso (fecha_devolucion > fecha_prestamo + 14 días)


<details>
<summary>Respuesta</summary>

```

```
</details>
-- Socios que nunca han tomado prestado un libro (sin LEFT JOIN)


<details>
<summary>Respuesta</summary>

```
select * from socio s
where s.id NOT IN
  (select p.id_socio from prestamo p);
sqlite> SIN RESULTADOS.

```
</details>

-- Libros más prestados (sin JOIN)

<details>
<summary>Respuesta</summary>

```

```
</details>

-- Autores cuyos libros han sido prestados (sin JOIN)


<details>
<summary>Respuesta</summary>

```
select l.autor from libro l
WHERE l.id IN
  (select id_libro from prestamo);
┌────────────────────────┐
│         autor          │
├────────────────────────┤
│ Miguel de Cervantes    │
│ Gabriel García Márquez │
│ George Orwell          │
│ Jane Austen            │
│ Carlos Ruiz Zafón      │
│ Julio Cortázar         │
│ Jorge Luis Borges      │
│ Ken Follett            │
│ Gabriel García Márquez │
│ Isabel Allende         │
└────────────────────────┘

```
</details>


-- 3. Consultas Multitabla (JOIN) (8 consultas - 2.4 puntos)

-- Préstamos con nombres de socio y libro (JOIN)
<details>
<summary>Respuesta</summary>

```
select p.*, s.nombre, l.titulo from prestamo p 
JOIN libro l ON p.id_libro = l.id 
JOIN socio s ON p.id_socio = s.id;
┌────┬────────────────┬──────────────────┬──────────┬──────────┬──────────┬───────────────────────────────────┐
│ id │ fecha_prestamo │ fecha_devolucion │ id_socio │ id_libro │  nombre  │              titulo               │
├────┼────────────────┼──────────────────┼──────────┼──────────┼──────────┼───────────────────────────────────┤
│ 1  │ 2023-01-10     │ 2023-01-24       │ 1        │ 2        │ Laura    │ Cien años de soledad              │
│ 2  │ 2023-02-15     │ 2023-03-01       │ 3        │ 4        │ Ana      │ Orgullo y prejuicio               │
│ 3  │ 2023-03-20     │                  │ 5        │ 6        │ Elena    │ Rayuela                           │
│ 4  │ 2023-04-05     │ 2023-04-19       │ 2        │ 8        │ Carlos   │ Los pilares de la Tierra          │
│ 5  │ 2023-05-12     │                  │ 4        │ 10       │ David    │ La casa de los espíritus          │
│ 6  │ 2023-01-22     │ 2023-02-05       │ 6        │ 2        │ Javier   │ Cien años de soledad              │
│ 7  │ 2023-02-18     │ 2023-03-04       │ 7        │ 4        │ Sofía    │ Orgullo y prejuicio               │
│ 8  │ 2023-03-25     │                  │ 8        │ 6        │ Miguel   │ Rayuela                           │
│ 9  │ 2023-04-10     │ 2023-04-24       │ 9        │ 8        │ Patricia │ Los pilares de la Tierra          │
│ 10 │ 2023-05-15     │                  │ 10       │ 10       │ Antonio  │ La casa de los espíritus          │
│ 11 │ 2023-01-05     │ 2023-01-19       │ 1        │ 1        │ Laura    │ El Quijote                        │
│ 12 │ 2023-02-10     │ 2023-02-24       │ 2        │ 3        │ Carlos   │ 1984                              │
│ 13 │ 2023-03-15     │                  │ 3        │ 5        │ Ana      │ La sombra del viento              │
│ 14 │ 2023-04-20     │ 2023-05-04       │ 4        │ 7        │ David    │ Ficciones                         │
│ 15 │ 2023-05-25     │                  │ 5        │ 9        │ Elena    │ El amor en los tiempos del cólera │
└────┴────────────────┴──────────────────┴──────────┴──────────┴──────────┴───────────────────────────────────┘

```
</details>


-- Libros prestados a socios de Barcelona (JOIN)


<details>
<summary>Respuesta</summary>

```
select l.*, s.ciudad from prestamo p 
JOIN libro l ON p.id_libro = l.id 
JOIN socio s ON p.id_socio = s.id 
WHERE s.ciudad = 'Barcelona';
┌────┬──────────────────────────┬───────────────┬─────────────────┬─────────────────┬────────────┬───────────┐
│ id │          titulo          │     autor     │     genero      │ año_publicacion │ disponible │  ciudad   │
├────┼──────────────────────────┼───────────────┼─────────────────┼─────────────────┼────────────┼───────────┤
│ 8  │ Los pilares de la Tierra │ Ken Follett   │ Histórica       │ 1989            │ 0          │ Barcelona │
│ 8  │ Los pilares de la Tierra │ Ken Follett   │ Histórica       │ 1989            │ 0          │ Barcelona │
│ 3  │ 1984                     │ George Orwell │ Ciencia ficción │ 1949            │ 1          │ Barcelona │
└────┴──────────────────────────┴───────────────┴─────────────────┴─────────────────┴────────────┴───────────┘

```
</details>

-- Socios que han tomado prestado "Cien años de soledad" (JOIN)

<details>
<summary>Respuesta</summary>

```
select s.*, l.titulo from prestamo p
JOIN libro l ON p.id_libro = l.id
JOIN socio s ON p.id_socio = s.id
WHERE l.titulo = 'Cien años de soledad';
┌────┬────────┬───────────┬───────────┬────────┬────────────┬───────────┬──────────────────────┐
│ id │ nombre │ apellido1 │ apellido2 │ ciudad │ fecha_alta │ categoria │        titulo        │
├────┼────────┼───────────┼───────────┼────────┼────────────┼───────────┼──────────────────────┤
│ 1  │ Laura  │ García    │ Martínez  │ Madrid │ 2020-03-15 │ A         │ Cien años de soledad │
│ 6  │ Javier │ Ruiz      │ Moreno    │ Bilbao │ 2020-07-22 │ A         │ Cien años de soledad │
└────┴────────┴───────────┴───────────┴────────┴────────────┴───────────┴──────────────────────┘

```
</details>
-- Bibliotecarios que han gestionado préstamos (JOIN)
<details>
<summary>Respuesta</summary>

```
NO SE PUEDE HACER
```
</details>

-- Préstamos con datos completos (socio, libro, bibliotecario)
<details>
<summary>Respuesta</summary>

```
select p.*, s.*, l.* from prestamo p
JOIN libro l ON p.id_libro = l.id
JOIN socio s ON p.id_socio = s.id;
┌────┬────────────────┬──────────────────┬──────────┬──────────┬────┬──────────┬───────────┬───────────┬───────────┬────────────┬───────────┬────┬───────────────────────────────────┬────────────────────────┬─────────────────┬─────────────────┬────────────┐
│ id │ fecha_prestamo │ fecha_devolucion │ id_socio │ id_libro │ id │  nombre  │ apellido1 │ apellido2 │  ciudad   │ fecha_alta │ categoria │ id │              titulo               │         autor          │     genero      │ año_publicacion │ disponible │
├────┼────────────────┼──────────────────┼──────────┼──────────┼────┼──────────┼───────────┼───────────┼───────────┼────────────┼───────────┼────┼───────────────────────────────────┼────────────────────────┼─────────────────┼─────────────────┼────────────┤
│ 1  │ 2023-01-10     │ 2023-01-24       │ 1        │ 2        │ 1  │ Laura    │ García    │ Martínez  │ Madrid    │ 2020-03-15 │ A         │ 2  │ Cien años de soledad              │ Gabriel García Márquez │ Realismo mágico │ 1967            │ 0          │
│ 2  │ 2023-02-15     │ 2023-03-01       │ 3        │ 4        │ 3  │ Ana      │ Sánchez   │           │ Valencia  │ 2022-01-10 │ C         │ 4  │ Orgullo y prejuicio               │ Jane Austen            │ Romance         │ 1813            │ 0          │
│ 3  │ 2023-03-20     │                  │ 5        │ 6        │ 5  │ Elena    │ Martín    │ Díaz      │ Madrid    │ 2023-02-18 │ B         │ 6  │ Rayuela                           │ Julio Cortázar         │ Experimental    │ 1963            │ 0          │
│ 4  │ 2023-04-05     │ 2023-04-19       │ 2        │ 8        │ 2  │ Carlos   │ López     │ Fernández │ Barcelona │ 2021-05-20 │ B         │ 8  │ Los pilares de la Tierra          │ Ken Follett            │ Histórica       │ 1989            │ 0          │
│ 5  │ 2023-05-12     │                  │ 4        │ 10       │ 4  │ David    │ Pérez     │ Gómez     │ Sevilla   │ 2021-11-30 │ A         │ 10 │ La casa de los espíritus          │ Isabel Allende         │ Realismo mágico │ 1982            │ 0          │
│ 6  │ 2023-01-22     │ 2023-02-05       │ 6        │ 2        │ 6  │ Javier   │ Ruiz      │ Moreno    │ Bilbao    │ 2020-07-22 │ A         │ 2  │ Cien años de soledad              │ Gabriel García Márquez │ Realismo mágico │ 1967            │ 0          │
│ 7  │ 2023-02-18     │ 2023-03-04       │ 7        │ 4        │ 7  │ Sofía    │ Hernández │ Jiménez   │ Zaragoza  │ 2022-09-05 │ C         │ 4  │ Orgullo y prejuicio               │ Jane Austen            │ Romance         │ 1813            │ 0          │
│ 8  │ 2023-03-25     │                  │ 8        │ 6        │ 8  │ Miguel   │ Navarro   │ Torres    │ Málaga    │ 2021-04-12 │ B         │ 6  │ Rayuela                           │ Julio Cortázar         │ Experimental    │ 1963            │ 0          │
│ 9  │ 2023-04-10     │ 2023-04-24       │ 9        │ 8        │ 9  │ Patricia │ Romero    │           │ Barcelona │ 2023-01-15 │ A         │ 8  │ Los pilares de la Tierra          │ Ken Follett            │ Histórica       │ 1989            │ 0          │
│ 10 │ 2023-05-15     │                  │ 10       │ 10       │ 10 │ Antonio  │ Domingo   │ Santos    │ Valencia  │ 2020-12-08 │ C         │ 10 │ La casa de los espíritus          │ Isabel Allende         │ Realismo mágico │ 1982            │ 0          │
│ 11 │ 2023-01-05     │ 2023-01-19       │ 1        │ 1        │ 1  │ Laura    │ García    │ Martínez  │ Madrid    │ 2020-03-15 │ A         │ 1  │ El Quijote                        │ Miguel de Cervantes    │ Clásico         │ 1605            │ 1          │
│ 12 │ 2023-02-10     │ 2023-02-24       │ 2        │ 3        │ 2  │ Carlos   │ López     │ Fernández │ Barcelona │ 2021-05-20 │ B         │ 3  │ 1984                              │ George Orwell          │ Ciencia ficción │ 1949            │ 1          │
│ 13 │ 2023-03-15     │                  │ 3        │ 5        │ 3  │ Ana      │ Sánchez   │           │ Valencia  │ 2022-01-10 │ C         │ 5  │ La sombra del viento              │ Carlos Ruiz Zafón      │ Misterio        │ 2001            │ 1          │
│ 14 │ 2023-04-20     │ 2023-05-04       │ 4        │ 7        │ 4  │ David    │ Pérez     │ Gómez     │ Sevilla   │ 2021-11-30 │ A         │ 7  │ Ficciones                         │ Jorge Luis Borges      │ Cuentos         │ 1944            │ 1          │
│ 15 │ 2023-05-25     │                  │ 5        │ 9        │ 5  │ Elena    │ Martín    │ Díaz      │ Madrid    │ 2023-02-18 │ B         │ 9  │ El amor en los tiempos del cólera │ Gabriel García Márquez │ Romance         │ 1985            │ 1          │
└────┴────────────────┴──────────────────┴──────────┴──────────┴────┴──────────┴───────────┴───────────┴───────────┴────────────┴───────────┴────┴───────────────────────────────────┴────────────────────────┴─────────────────┴─────────────────┴────────────┘
sqlite> 

```
</details>

-- Socios con sus préstamos activos (JOIN)

<details>
<summary>Respuesta</summary>

```


```
</details>
-- Libros nunca prestados (LEFT JOIN)
<details>
<summary>Respuesta</summary>

```


```
</details>
-- Autores con número de libros prestados (JOIN + GROUP BY)
<details>
<summary>Respuesta</summary>

```


```
</details>

-- 4. Consultas Resumen (8 consultas - 2.4 puntos)
-- Número de socios por ciudad

-- Promedio de antigüedad de bibliotecarios

-- Cantidad de préstamos por mes en 2023

-- Libros más populares (por veces prestados)

-- Socios más activos (por préstamos realizados)

-- Porcentaje de libros disponibles

-- Días promedio de préstamo

-- Número de préstamos por categoría de socio

-- 5. Subconsultas (8 consultas - 1.2 puntos)

-- Socios que han prestado libros de Gabriel García Márquez

-- Libros con préstamos superiores al promedio

-- Socios con todos los préstamos devueltos a tiempo

-- Bibliotecarios que no han gestionado préstamos

-- Socios que han prestado más libros que el promedio

-- Libros disponibles que nunca han sido prestados

-- Socios con préstamos en todas las categorías de libros

-- Bibliotecarios que han gestionado préstamos de todos los socios de Madrid

<details>
<summary>Respuesta</summary>

```

```
</details>


</div>
