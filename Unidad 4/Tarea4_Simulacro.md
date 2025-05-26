<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

## **Unidad 4. Tarea 4: Simulacro, optimización de BBDD y programación.**

## Parte 1: Consultas SQL. 

### Consultas simples.

1. Mostrar todos los cursos disponibles.

<details>
<summary>Respuesta</summary>

SELECT * FROM `cursos`;

| id | nombre               | profesor_id | creditos |
|----|----------------------|-------------|----------|
| 1  | Álgebra Lineal       | 1           | 6        |
| 2  | Programación I       | 2           | 5        |
| 3  | Mecánica Clásica     | 3           | 6        |
| 4  | Estructuras de Datos | 2           | 5        |
| 5  | Cálculo I            | 1           | 6        |

</details>

2. Mostrar el nombre de todos los profesores.

<details>
<summary>Respuesta</summary>

SELECT nombre FROM `profesores`;

| nombre           |
|------------------|
| Dra. Ana Torres  |
| Dr. Luis Gmez    |
| Dra. Marta Daz   |


</details>


3. Listar todas las matrículas.

<details>
<summary>Respuesta</summary>

SELECT * FROM `matriculas`;

| id | estudiante_id | curso_id | fecha       |
|----|---------------|----------|-------------|
| 1  | 1             | 1        | 2021-09-01  |
| 2  | 2             | 2        | 2022-09-01  |
| 3  | 3             | 3        | 2023-09-02  |
| 4  | 4             | 4        | 2024-09-03  |
| 5  | 1             | 5        | 2020-09-04  |
| 6  | 2             | 4        | 2022-09-05  |
| 7  | 3             | 1        | 2023-09-06  |
| 8  | 4             | 2        | 2024-09-06  |

</details>


4. Ver los nombres y correos de los estudiantes.

<details>
<summary>Respuesta</summary>

SELECT nombre, email FROM estudiantes;

| nombre         | email          |
|----------------|----------------|
| Maria Lpez      | maria@uni.edu  |
| Juan Prez      | juan@uni.edu   |
| Lucia Fernndez  | lucia@uni.edu  |
| Carlos Ruiz    | carlos@uni.edu |

</details>


5. Ver los cursos y su número de créditos

<details>
<summary>Respuesta</summary>

SELECT nombre, creditos FROM cursos;

| nombre               | creditos |
|----------------------|----------|
| Algebra Lineal        | 6        |
| Programacion I        | 5        |
| Mecanica Clasica      | 6        |
| Estructuras de Datos  | 5        |
| Calculo I             | 6        |

</details>

### Consultas WHERE.

1. Obtener los cursos impartidos por profesores del departamento de Informática.

<details>
<summary>Respuesta</summary>

```
SELECT
  p.nombre AS Nombre_Profesor,
  c.nombre AS Nombre_Curso, 
  p.departamento AS Nombre_Dpto
FROM profesores p, cursos c
WHERE c.profesor_id = p.id
AND p.departamento = 'Informatica';
```

| Nombre_Profesor  | Nombre_Curso           | Nombre_Dpto |
|------------------|------------------------|--------------|
| Dr. Luis Gomez   | Programacion I         | Informatica  |
| Dr. Luis Gomez   | Estructuras de Datos   | Informatica  |

</details>

2. Obtener los estudiantes que viven en Madrid.

<details>
<summary>Respuesta</summary>

```
SELECT
  e.nombre AS Nombre_Estudiante,
  e.ciudad AS Nombre_Ciudad 
FROM estudiantes e
WHERE ciudad = 'Madrid';
```

| Nombre_Estudiante | Nombre_Ciudad |
|--------------------|----------------|
| Maria Lopez        | Madrid         |


</details>

3. Mostrar los cursos con más de 5 créditos.

<details>
<summary>Respuesta</summary>

```
SELECT * FROM cursos
WHERE cursos.creditos > 5;
```

| id | nombre            | profesor_id | creditos |
|----|-------------------|-------------|----------|
| 1  | Algebra Lineal    | 1           | 6        |
| 3  | Mecanica Clasica  | 3           | 6        |
| 5  | Calculo I         | 1           | 6        |

</details>

4. Ver las matrículas realizadas después del año 2022.

<details>
<summary>Respuesta</summary>

```
SELECT * FROM matriculas
WHERE fecha > '2022-12-31';
```
  
| id | estudiante_id | curso_id | fecha       |
|----|---------------|----------|-------------|
| 3  | 3             | 3        | 2023-09-02  |
| 4  | 4             | 4        | 2024-09-03  |
| 7  | 3             | 1        | 2023-09-06  |
| 8  | 4             | 2        | 2024-09-06  |
</details>

5. Ver los cursos impartidos por la profesora “Dra. Ana Torres”

<details>
<summary>Respuesta</summary>

```
SELECT
  p.nombre AS Nombre_Profesor,
  c.nombre AS Nombre_Curso
FROM cursos c, profesores p
WHERE c.profesor_id = p.id
AND p.nombre = 'Dra. Ana Torres';
```

| Nombre_Profesor   | Nombre_Curso   |
|-------------------|----------------|
| Dra. Ana Torres   | Algebra Lineal |
| Dra. Ana Torres   | Calculo I      |

</details>


### Consultas JOIN.

1. Obtener los cursos impartidos por profesores del departamento de Informática.

<details>
<summary>Respuesta</summary>
  
```
SELECT
  p.nombre AS Nombre_Profesor, 
  c.nombre AS Nombre_Curso, 
  p.departamento AS Nombre_Dpto
FROM cursos c
JOIN profesores p ON c.profesor_id = p.id
WHERE p.departamento = 'Informatica';
```

| Nombre_Profesor  | Nombre_Curso           | Nombre_Dpto |
|------------------|------------------------|--------------|
| Dr. Luis Gomez   | Programacion I         | Informatica  |
| Dr. Luis Gomez   | Estructuras de Datos   | Informatica  |

</details>

2. Obtener los estudiantes que viven en Madrid.

<details>
<summary>Respuesta</summary>

```
NO ES POSIBLE HACER UN JOIN EN ESTA CONSULTA, SOLO UNA TABLA.

SELECT
  e.nombre AS Nombre_Estudiante,
  e.ciudad AS Nombre_Ciudad 
FROM estudiantes e
WHERE ciudad = 'Madrid';
```

| Nombre_Estudiante | Nombre_Ciudad |
|--------------------|----------------|
| Maria Lopez        | Madrid         |

</details>

3. Mostrar los cursos con más de 5 créditos.

<details>
<summary>Respuesta</summary>


```
NO ES POSIBLE HACER UN JOIN EN ESTA CONSULTA, SOLO UNA TABLA.

SELECT * FROM cursos
WHERE cursos.creditos > 5;
```

| id | nombre            | profesor_id | creditos |
|----|-------------------|-------------|----------|
| 1  | Algebra Lineal    | 1           | 6        |
| 3  | Mecanica Clasica  | 3           | 6        |
| 5  | Calculo I         | 1           | 6        |

</details>

4. Ver las matrículas realizadas después del año 2022.

<details>
<summary>Respuesta</summary>

```
SELECT * FROM matriculas
WHERE fecha > '2022-12-31';
```

| id | estudiante_id | curso_id | fecha       |
|----|---------------|----------|-------------|
| 3  | 3             | 3        | 2023-09-02  |
| 4  | 4             | 4        | 2024-09-03  |
| 7  | 3             | 1        | 2023-09-06  |
| 8  | 4             | 2        | 2024-09-06  |

</details>

5. Ver los cursos impartidos por la profesora “Dra. Ana Torres”

<details>
<summary>Respuesta</summary>

```
SELECT
  p.nombre AS Nombre_Profesor,
  c.nombre AS Nombre_Curso 
FROM cursos c
JOIN profesores p ON c.profesor_id = p.id
WHERE p.nombre = 'Dra. Ana Torres';
```

| Nombre_Profesor   | Nombre_Curso   |
|-------------------|----------------|
| Dra. Ana Torres   | Algebra Lineal |
| Dra. Ana Torres   | Calculo I      |

</details>

### Subconsultas.

1. Obtener los cursos impartidos por profesores del departamento de Informática.

<details>
<summary>Respuesta</summary>

```
SELECT
  (SELECT	p.nombre FROM profesores p WHERE p.id = c.profesor_id) AS Nombre_Profesor,
  c.nombre AS Nombre_Curso,
  (SELECT	p.departamento FROM profesores p WHERE p.id = c.profesor_id) AS Nombre_Dpto
FROM cursos c WHERE profesor_id IN
	(SELECT id FROM profesores
	WHERE departamento = 'Informatica');
```
| Nombre_Profesor  | Nombre_Curso           | Nombre_Dpto |
|------------------|------------------------|--------------|
| Dr. Luis Gomez   | Programacion I         | Informatica  |
| Dr. Luis Gomez   | Estructuras de Datos   | Informatica  |



</details>

2. Obtener los estudiantes que viven en Madrid.

<details>
<summary>Respuesta</summary>

```
SELECT * FROM estudiantes e
WHERE e.ciudad = 
	(SELECT ciudad FROM estudiantes 
     WHERE ciudad = 'Madrid');
```

| id | nombre       | email          | ciudad |
|----|--------------|----------------|--------|
| 1  | Maria Lopez  | maria@uni.edu  | Madrid |


</details>

3. Mostrar los cursos con más de 5 créditos.

<details>
<summary>Respuesta</summary>

```
SELECT * FROM cursos c WHERE c.id IN
	(SELECT c.id FROM cursos c WHERE c.creditos > 5);
```

| id | nombre           | profesor_id | creditos |
|----|------------------|-------------|----------|
| 1  | Algebra Lineal   | 1           | 6        |
| 3  | Mecanica Clasica | 3           | 6        |
| 5  | Calculo I        | 1           | 6        |



</details>

4. Ver las matrículas realizadas después del año 2022.

<details>
<summary>Respuesta</summary>

```
SELECT * FROM matriculas m WHERE m.id IN 
	(SELECT m.id FROM matriculas m 
    WHERE m.fecha > '2022-12-31');
```

| id | estudiante_id | curso_id | fecha       |
|----|---------------|----------|-------------|
| 3  | 3             | 3        | 2023-09-02  |
| 4  | 4             | 4        | 2024-09-03  |
| 7  | 3             | 1        | 2023-09-06  |
| 8  | 4             | 2        | 2024-09-06  |

</details>

5. Ver los cursos impartidos por la profesora “Dra. Ana Torres”.

<details>
<summary>Respuesta</summary>

```
SELECT c.*, 
	(SELECT p.nombre FROM profesores p WHERE p.id = c.profesor_id) AS Nombre_Profesor
FROM cursos c
WHERE profesor_id IN 
  (SELECT p.id FROM profesores p 
  WHERE p.nombre = 'Dra. Ana Torres');
```

| id | nombre         | profesor_id | creditos | Nombre_Profesor  |
|----|----------------|-------------|----------|------------------|
| 1  | Algebra Lineal | 1           | 6        | Dra. Ana Torres  |
| 5  | Calculo I      | 1           | 6        | Dra. Ana Torres  |


</details>

## Parte 2: Índices.

1. Crear un índice en la columna ciudad de la tabla estudiantes.

<details>
<summary>Respuesta</summary>

```
CREATE INDEX idx_ciudad ON estudiantes(ciudad);
```

</details>

2. Crear un índice en la columna departamento de la tabla profesores.

<details>
<summary>Respuesta</summary>

```
CREATE INDEX idx_dpto ON profesores(departamento);
```
</details>

3. Consultar los índices creados.

<details>
<summary>Respuesta</summary>

```
SHOW INDEX FROM `estudiantes`;
```

| Tabla      | Seq_in_index | Nombre_indice | Columna | Orden | Longitud | Nulo | Tipo_indice | Único | Comentario |
|------------|--------------|----------------|---------|-------|----------|------|--------------|--------|-------------|
| estudiantes | 0            | PRIMARY        | id      | A     | 4        | NULL | BTREE        | YES    | NULL        |
| estudiantes | 1            | idx_ciudad     | ciudad  | A     | 4        | YES  | BTREE        | YES    | NULL        |

```
SHOW INDEX FROM `profesores`;
```

| Tabla      | Seq_in_index | Nombre_indice | Columna      | Orden | Longitud | Nulo | Tipo_indice | Único | Comentario |
|------------|---------------|----------------|--------------|-------|----------|------|--------------|--------|-------------|
| profesores | 0             | PRIMARY        | id           | A     | 3        | NULL | BTREE        | YES    | NULL        |
| profesores | 1             | idx_dpto       | departamento | A     | 3        | NULL | BTREE        | YES    | NULL        |


</details>

4. Eliminar ambos índices.

<details>
<summary>Respuesta</summary>

```
DROP INDEX idx_ciudad ON `estudiantes`;
```

| Tabla      | Seq_in_index | Nombre_indice | Columna | Orden | Longitud | Nulo | Tipo_indice | Único | Comentario |
|------------|--------------|----------------|---------|-------|----------|------|--------------|--------|-------------|
| estudiantes | 0            | PRIMARY        | id      | A     | 4        | NULL | BTREE        | YES    | NULL        |

```
DROP INDEX idx_dpto ON `profesores`;
```

| Tabla      | Seq_in_index | Nombre_indice | Columna      | Orden | Longitud | Nulo | Tipo_indice | Único | Comentario |
|------------|---------------|----------------|--------------|-------|----------|------|--------------|--------|-------------|
| profesores | 0             | PRIMARY        | id           | A     | 3        | NULL | BTREE        | YES    | NULL        |

</details>

## Parte 3: Vistas.

1. Crear una vista llamada vista_matriculas_completas que muestre:

- nombre del estudiante,
- nombre del curso,
- fecha de la matrícula.

<details>
<summary>Respuesta</summary>

</details>

2. Consultar datos desde la vista, mostrando el nombre del estudiante y la fecha de matrícula.

<details>
<summary>Respuesta</summary>

</details>

3. Eliminar la vista.

<details>
<summary>Respuesta</summary>

</details>

## Parte 4: Procedimiento Almacenado.

1. Crear un procedimiento llamado cursos_por_profesor que reciba el nombre del profesor como parámetro y devuelva los cursos que imparte y su número de créditos.

<details>
<summary>Respuesta</summary>

</details>

2. Ejecutar el procedimiento con el nombre “Dr. Luis Gómez”.

<details>
<summary>Respuesta</summary>

</details>

3. Eliminar el procedimiento.

<details>
<summary>Respuesta</summary>

</details>

## Parte 5: Función Definida por el Usuario.

1. Crear una función llamada total_creditos_estudiante que reciba el ID de un estudiante y devuelva el total de créditos que ha matriculado.

<details>
<summary>Respuesta</summary>

</details>

2. Ejecutar la función para un estudiante específico.

<details>
<summary>Respuesta</summary>

</details>

3. Eliminar la función.

<details>
<summary>Respuesta</summary>

</details>


</div>
