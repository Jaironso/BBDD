<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

## **Unidad 4. Tarea 2: Trabajo con índices.**

## **Una empresa guarda los siguientes datos de sus clientes, con los siguientes campos:**

- documento char (8) not null,
- nombre varchar(30) not null,
- domicilio varchar(30),
- ciudad varchar(20),
- provincia varchar (20),
- telefono varchar(11)

Se pide:

## Elimine la tabla "cliente" si existe.
Nota: Muestra el comando y la salida.

<details>
<summary>Respuesta</summary>

```
DROP TABLE IF EXISTS cliente;
0 row(s) affected, 1 warning(s): 1051 Unknown table 'empresa.cliente'
```
</details>

## Cree la tabla sin clave primaria y incluye a posteriori esta.
Nota: Muestra el comando y la salida.

<details>
<summary>Respuesta</summary>

```
CREATE TABLE cliente (
	dni CHAR(8) NOT NULL,
    nombres VARCHAR(30) NOT NULL,
	domicilio VARCHAR (30),
    ciudad VARCHAR (20),
    provincia VARCHAR (20),
    telefono VARCHAR (11)
);

0 row(s) affected

ALTER TABLE cliente
ADD PRIMARY KEY (dni);

0 row(s) affected Records: 0  Duplicates: 0  Warnings: 0

```
</details>

## Define los siguientes indices:
Un índice único por el campo "documento" y un índice común por ciudad y provincia.
Nota: Muestra el comando y la salida. Justifica el tipo de indice en un comentario.
Vea los índices de la tabla.
Nota: Muestra el comando y la salida "show index".

<details>
<summary>Respuesta</summary>

CREATE INDEX idx_ciudad_pronvincia ON cliente(ciudad, provincia);

0 row(s) affected Records: 0  Duplicates: 0  Warnings: 0


SHOW INDEX from cliente;
| Table   | Non_unique | Key_name              | Seq_in_index | Column_name | Collation | Cardinality | Sub_part | Packed | Null | Index_type | Comment | Index_comment | Visible | Expression |
|---------|------------|-----------------------|--------------|-------------|-----------|-------------|----------|--------|------|------------|---------|----------------|---------|-------------|
| cliente | 0          | PRIMARY               | 1            | dni         | A         | 0           |          |        |      | BTREE      |         |                | YES     |             |
| cliente | 1          | idx_ciudad_pronvincia | 1            | ciudad      | A         | 0           |          |        | YES  | BTREE      |         |                | YES     |             |
| cliente | 1          | idx_ciudad_pronvincia | 2            | provincia   | A         | 0           |          |        | YES  | BTREE      |         |                | YES     |             |

</details>

## Agregue un índice único por el campo "telefono".
Nota: Muestra el comando y la salida.

<details>
<summary>Respuesta</summary>

CREATE UNIQUE INDEX idx_telefono ON cliente(telefono);

0 row(s) affected Records: 0  Duplicates: 0  Warnings: 0


SHOW INDEX from cliente;

| Table   | Non_unique | Key_name              | Seq_in_index | Column_name | Collation | Cardinality | Sub_part | Packed | Null | Index_type | Comment | Index_comment | Visible | Expression |
|---------|------------|-----------------------|--------------|-------------|-----------|-------------|----------|--------|------|------------|---------|----------------|---------|-------------|
| cliente | 0          | PRIMARY               | 1            | dni         | A         | 0           |          |        |      | BTREE      |         |                | YES     |             |
| cliente | 0          | idx_telefono          | 1            | telefono    | A         | 0           |          |        | YES  | BTREE      |         |                | YES     |             |
| cliente | 1          | idx_ciudad_pronvincia | 1            | ciudad      | A         | 0           |          |        | YES  | BTREE      |         |                | YES     |             |
| cliente | 1          | idx_ciudad_pronvincia | 2            | provincia   | A         | 0           |          |        | YES  | BTREE      |         |                | YES     |             |


</details>

## Elimina los índices.
Nota: Muestra el comando y la salida.

<details>
<summary>Respuesta</summary>

```
DROP INDEX idx_ciudad_provincia ON cliente;
0 row(s) affected Records: 0  Duplicates: 0  Warnings: 0


DROP INDEX idx_telefono ON cliente;
0 row(s) affected Records: 0  Duplicates: 0  Warnings: 0
```
</details>

</div>
