<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

## **Unidad 4. Tarea 1: Trabajo con índices.**

## **Un instituto de enseñanza guarda los siguientes datos de sus alumnos:**

- número de inscripción, comienza desde 1 cada año,
- año de inscripción,
- nombre del alumno,
- documento del alumno,
- domicilio,
- ciudad,
- provincia,
- clave primaria: número de inscripto y año de inscripción.

Se pide:

## Elimine la tabla "alumno" si existe.
Nota: Muestra el comando y la salida.

<details>
<summary>Respuesta</summary>

```
DROP TABLE IF EXISTS alumno;
0 row(s) affected, 1 warning(s): 1051 Unknown table 'instituto.alumno'
```
</details>

## Cree la tabla definiendo una clave primaria compuesta (año de inscripción y número de inscripción).
Nota: Muestra el comando y la salida.


<details>
<summary>Respuesta</summary>

```
CREATE TABLE alumno (
	num_inscripcion INT NOT NULL,
    anio_inscripcion YEAR NOT NULL,
    nombre VARCHAR (100),
    dni VARCHAR (20),
    domicilio VARCHAR (150),
    ciudad VARCHAR (100),
    provincia VARCHAR (100),
    PRIMARY KEY (num_inscripcion, anio_inscripcion)
    );
0 row(s) affected
```
</details>


## Define los siguientes indices:
Un índice único por el campo "documento" y un índice común por ciudad y provincia.
Nota: Muestra el comando y la salida. Justifica el tipo de indice en un comentario.


<details>
<summary>Respuesta</summary>

```
CREATE UNIQUE INDEX idx_dni ON alumno(dni);
0 row(s) affected Records: 0  Duplicates: 0  Warnings: 0
CREATE INDEX idx_ciudad_pronvincia ON alumno(ciudad, provincia);
0 row(s) affected Records: 0  Duplicates: 0  Warnings: 0
```
</details>


## Vea los índices de la tabla.
Nota: Muestra el comando y la salida "show index".

<details>
<summary>Respuesta</summary>

SHOW INDEX from alumno;

| Table  | Non_unique | Key_name               | Seq_in_index | Column_name      | Collation | Cardinality | Sub_part | Packed | Null | Index_type | Comment | Index_comment | Visible | Expression |
|--------|------------|------------------------|---------------|------------------|-----------|-------------|----------|--------|------|-------------|---------|----------------|---------|------------|
| alumno | 0          | PRIMARY                | 1             | num_inscripcion  | A         | 0           |          |        |      | BTREE       |         |                | YES     |            |
| alumno | 0          | PRIMARY                | 2             | anio_inscripcion | A         | 0           |          |        |      | BTREE       |         |                | YES     |            |
| alumno | 0          | idx_dni                | 1             | dni              | A         | 0           |          |        | YES  | BTREE       |         |                | YES     |            |
| alumno | 1          | idx_ciudad_pronvincia  | 1             | ciudad           | A         | 0           |          |        | YES  | BTREE       |         |                | YES     |            |
| alumno | 1          | idx_ciudad_pronvincia  | 2             | provincia        | A         | 0           |          |        | YES  | BTREE       |         |                | YES     |            |

</details>

## Intente ingresar un alumno con clave primaria repetida.
Nota: Muestra el comando y la salida.

<details>
<summary>Respuesta</summary>

```
INSERT INTO alumno VALUES (1,2024, 'Jairo Afonso', '12345678', 'Calle Los Cercados, 2', 'La Victoria', 'Tenerife');
INSERT INTO alumno VALUES (1,2024, 'Begoña Armas', '98765432', 'Calle Los Cercados, 2', 'La Victoria', 'Tenerife');

Error Code: 1062. Duplicate entry '1-2024' for key 'alumno.PRIMARY'
```
</details>

## Intente ingresar un alumno con documento repetido.
Nota: Muestra el comando y la salida.

<details>
<summary>Respuesta</summary>

```
INSERT INTO alumno VALUES (1,2024, 'Jairo Afonso', '12345678', 'Calle Los Cercados, 2', 'La Victoria', 'Tenerife');
INSERT INTO alumno VALUES (2,2024, 'Begoña Armas', '12345678', 'Calle Los Cercados, 2', 'La Victoria', 'Tenerife');

Error Code: 1062. Duplicate entry '12345678' for key 'alumno.idx_dni'
```
</details>

## Ingrese varios alumnos de la misma ciudad y provincia.
Nota: Muestra el comando y la salida.

<details>
<summary>Respuesta</summary>

```
INSERT INTO alumno VALUES (2,2024, 'Begoña Armas', '45678912', 'Calle El Relampago, 8', 'La Victoria', 'Tenerife');
INSERT INTO alumno VALUES (3,2024, 'Evelin Alvarez', '32165487', 'Calle Guaira, 58', 'La Victoria', 'Tenerife');
INSERT INTO alumno VALUES (4,2024, 'Fernando Suarez', '78954123', 'Calle Los Cerditos, 66', 'La Victoria', 'Tenerife');

1 row(s) affected

1 row(s) affected

1 row(s) affected
```
</details>

## Elimina los indices creados, y muestra que ya no se encuentran.
Nota: Muestra el comando y la salida.

<details>
<summary>Respuesta</summary>

```
DROP INDEX idx_dni ON alumno;
DROP INDEX idx_ciudad_pronvincia ON alumno;

0 row(s) affected Records: 0  Duplicates: 0  Warnings: 0

0 row(s) affected Records: 0  Duplicates: 0  Warnings: 0

```
</details>

</div>
