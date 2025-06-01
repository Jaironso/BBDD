<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

## **Unidad 4. Tarea 5: Simulacro, optimización de BBDD y programación.**

## Parte 1: Consultas para Explorar la Estructura de las Tablas.

### Consultas simples.

1. Mostrar las columnas de la tabla estudiantes.

<details>
<summary>Respuesta</summary>

```sql
SELECT * FROM estudiantes;
```
| id |     nombre       |        email        |  ciudad   |
|----|------------------|---------------------|-----------|
| 1  | Maria Lopez      | maria@uni.edu       | Madrid    |
| 2  | Juan Perez       | juan@uni.edu        | Barcelona |
| 3  | Lucia Fernandez  | lucia@uni.edu       | Valencia  |
| 4  | Carlos Ruiz      | carlos@uni.edu      | Sevilla   |



</details>

2. Mostrar las columnas de la tabla cursos.

<details>
<summary>Respuesta</summary>

```sql
SELECT * FROM cursos;
```
| id |        nombre         | profesor_id | creditos |
|----|------------------------|-------------|----------|
| 1  | Algebra Lineal        | 1           | 6        |
| 2  | Programacion I        | 2           | 5        |
| 3  | Mecanica Clasica      | 3           | 6        |
| 4  | Estructuras de Datos  | 2           | 5        |
| 5  | Calculo I             | 1           | 6        |

</details>

3. Mostrar las columnas de la tabla matriculas.

<details>
<summary>Respuesta</summary>

```sql
SELECT * FROM matriculas;
```

| id | estudiante_id | curso_id |   fecha     |
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


## Parte 2: Consultas Avanzadas sobre Datos.

1. Mostrar cada estudiante con la cantidad de cursos en los que está matriculado.

<details>
<summary>Respuesta</summary>

```sql
SELECT e.*, COUNT(m.estudiante_id) AS Q_cursos
FROM estudiantes e
JOIN matriculas m
ON m.estudiante_id = e.id
GROUP BY e.id;
```
| id |     nombre       |       email        |  ciudad   | Q_cursos |
|----|------------------|--------------------|-----------|----------|
| 1  | Maria Lopez      | maria@uni.edu      | Madrid    |    2     |
| 2  | Juan Perez       | juan@uni.edu       | Barcelona |    2     |
| 3  | Lucia Fernandez  | lucia@uni.edu      | Valencia  |    2     |
| 4  | Carlos Ruiz      | carlos@uni.edu     | Sevilla   |    2     |


</details>


2. Mostrar cada estudiante con el total de créditos acumulados.

<details>
<summary>Respuesta</summary>

```sql
SELECT e.*, SUM(c.creditos) AS Q_creditos
FROM estudiantes e
JOIN matriculas m ON m.estudiante_id = e.id
JOIN cursos c ON c.id = m.curso_id
GROUP BY e.id;
```

| id |     nombre       |       email        |  ciudad   | Q_creditos |
|----|------------------|--------------------|-----------|------------|
| 1  | Maria Lopez      | maria@uni.edu      | Madrid    |     12     |
| 2  | Juan Perez       | juan@uni.edu       | Barcelona |     10     |
| 3  | Lucia Fernandez  | lucia@uni.edu      | Valencia  |     12     |
| 4  | Carlos Ruiz      | carlos@uni.edu     | Sevilla   |     10     |

</details>

3. Mostrar cursos con la cantidad de estudiantes matriculados, ordenados de mayor a menor.

<details>
<summary>Respuesta</summary>

```sql
SELECT c.*, COUNT(e.id) AS Q_Alumnos 
FROM matriculas m, cursos c, estudiantes e
WHERE m.curso_id = c.id 
AND m.estudiante_id = e.id
GROUP BY c.id
ORDER BY Q_Alumnos;
```

| id |        nombre         | profesor_id | creditos | Q_Alumnos |
|----|------------------------|-------------|----------|-----------|
| 1  | Algebra Lineal        | 1           | 6        |     2     |
| 2  | Programacion I        | 2           | 5        |     2     |
| 4  | Estructuras de Datos  | 2           | 5        |     2     |
| 5  | Calculo I             | 1           | 6        |     1     |
| 3  | Mecanica Clasica      | 3           | 6        |     1     |


</details>

4. Mostrar la media de créditos por curso.

<details>
<summary>Respuesta</summary>

```sql
SELECT c.*, AVG(c.creditos) AS Media_Creditos 
FROM cursos c
GROUP BY c.id;
```

| id | nombre                | profesor_id | creditos | Media_Creditos |
|----|------------------------|--------------|-----------|----------------|
| 1  | Algebra Lineal         | 1            | 6         | 6.0000         |
| 2  | Programacion I         | 2            | 5         | 5.0000         |
| 3  | Mecanica Clasica       | 3            | 6         | 6.0000         |
| 4  | Estructuras de Datos   | 2            | 5         | 5.0000         |
| 5  | Calculo I              | 1            | 6         | 6.0000         |

</details>

5. Listar los cursos que no tienen estudiantes matriculados.

<details>
<summary>Respuesta</summary>

```sql
SELECT c.* 
FROM cursos c
WHERE c.id NOT IN 
	(SELECT m.id FROM matriculas m);
```
Sin Resultados para esta búsqueda.

</details>

6. Mostrar el nombre del profesor y cuántos cursos imparte.

<details>
<summary>Respuesta</summary>

```sql
SELECT p.*, COUNT(p.id) AS Q_Cursos
FROM profesores p
JOIN cursos c ON c.profesor_id = p.id
GROUP BY p.id;
```

| id | nombre           | departamento | Q_Cursos |
|----|------------------|--------------|----------|
| 1  | Dra. Ana Torres  | Matematicas  | 2        |
| 2  | Dr. Luis Gomez   | Informatica  | 2        |
| 3  | Dra. Marta Diaz  | Fisica       | 1        |

</details>

7. Mostrar los profesores que no imparten ningún curso.

<details>
<summary>Respuesta</summary>

```sql
SELECT p.* 
FROM profesores p
WHERE p.id NOT IN
	(SELECT c.profesor_id FROM cursos c);
```

Sin Resultados para está búsqueda.

</details>

8. Mostrar la ciudad con mayor número de estudiantes registrados.

<details>
<summary>Respuesta</summary>

```sql
SELECT e.ciudad, COUNT(e.id) AS Q_estudiantes
FROM estudiantes e
GROUP BY e.ciudad;
```

| ciudad     | Q_estudiantes |
|------------|---------------|
| Madrid     | 1             |
| Barcelona  | 1             |
| Valencia   | 1             |
| Sevilla    | 1             |

</details>

9. Mostrar estudiantes que están matriculados en más de 1 curso.

<details>
<summary>Respuesta</summary>

```sql
SELECT e.*, COUNT(m.estudiante_id) Q_Matriculas
FROM estudiantes e 
JOIN matriculas m ON e.id = m.estudiante_id
GROUP BY e.id;
```

| id | nombre           | email            | ciudad     | Q_Matriculas |
|----|------------------|------------------|------------|--------------|
| 1  | Maria Lopez      | maria@uni.edu    | Madrid     | 2            |
| 2  | Juan Perez       | juan@uni.edu     | Barcelona  | 2            |
| 3  | Lucia Fernandez  | lucia@uni.edu    | Valencia   | 2            |
| 4  | Carlos Ruiz      | carlos@uni.edu   | Sevilla    | 2            |

</details>

10. Listar cursos junto a su clasificación según créditos: 6 o más: "Alta carga". Menos de 6: "Carga estándar"

<details>
<summary>Respuesta</summary>

```sql
SELECT c.*,
CASE
  WHEN c.creditos >= 6 THEN 'Alta Carga'
  ELSE 'Carga Estándar'
  END AS Clasificacion
FROM cursos c;
```

| id | nombre                | profesor_id | creditos | Clasificacion   |
|----|------------------------|--------------|-----------|------------------|
| 1  | Algebra Lineal         | 1            | 6         | Alta Carga       |
| 2  | Programacion I         | 2            | 5         | Carga Estándar   |
| 3  | Mecanica Clasica       | 3            | 6         | Alta Carga       |
| 4  | Estructuras de Datos   | 2            | 5         | Carga Estándar   |
| 5  | Calculo I              | 1            | 6         | Alta Carga       |

</details>

11. Listar estudiantes y clasificar su carga académica: Más de 12 créditos: "Carga Alta" 6 a 12 créditos: "Carga Media" Menos de 6 créditos: "Carga Baja"

<details>
<summary>Respuesta</summary>

```sql
SELECT e.*, SUM(c.creditos) AS Total_Creditos,
CASE
	WHEN SUM(c.creditos) > 12 THEN 'Carga Alta'
	WHEN SUM(c.creditos) BETWEEN 6 AND 12 THEN 'Carga Media'
    	ELSE 'Carga Baja'
    	END AS Clasificacion
FROM estudiantes e
JOIN matriculas m ON m.estudiante_id = e.id
JOIN cursos c ON m.curso_id = c.id
GROUP BY e.id;
```

| id | nombre           | email             | ciudad     | Total_Creditos | Clasificacion |
|----|------------------|-------------------|------------|----------------|----------------|
| 1  | Maria Lopez      | maria@uni.edu     | Madrid     | 12             | Carga Media    |
| 2  | Juan Perez       | juan@uni.edu      | Barcelona  | 10             | Carga Media    |
| 3  | Lucia Fernandez  | lucia@uni.edu     | Valencia   | 12             | Carga Media    |
| 4  | Carlos Ruiz      | carlos@uni.edu    | Sevilla    | 10             | Carga Media    |


</details>


12. Mostrar cursos en los que se haya matriculado al menos un estudiante de Sevilla.

<details>
<summary>Respuesta</summary>

```sql
SELECT c.* FROM cursos c
WHERE c.id IN 
	(SELECT m.curso_id 
     	FROM matriculas m 
     	WHERE m.estudiante_id IN
        	(SELECT e.id
        	FROM estudiantes e
        	WHERE e.ciudad = 'Sevilla'));
```

| id | nombre                | profesor_id | creditos |
|----|------------------------|--------------|-----------|
| 4  | Estructuras de Datos   | 2            | 5         |
| 2  | Programacion I         | 2            | 5         |


</details>


13. Listar los cursos impartidos por profesores del departamento de Matemáticas.

<details>
<summary>Respuesta</summary>

```
```


</details>


14. Mostrar los cursos en los que se haya inscrito algún estudiante antes del año 2022.

<details>
<summary>Respuesta</summary>

```
```


</details>


15. Mostrar estudiantes que han cursado materias impartidas por el profesor “Dr. Luis Gómez”.

<details>
<summary>Respuesta</summary>

```
```


</details>


16. Mostrar los cursos más recientes (última matrícula por curso).

<details>
<summary>Respuesta</summary>

```
```


</details>


17. Mostrar el número total de estudiantes por departamento del profesor que imparte el curso.

<details>
<summary>Respuesta</summary>

```
```


</details>



## Parte 3: Procedimiento Almacenado.

1. Crear un procedimiento llamado inscribir_estudiante que reciba:

- ID del estudiante
- ID del curso
- Fecha de inscripción
- El procedimiento debe: Verificar que el estudiante no esté ya matriculado en ese curso. Si no lo está, insertarlo en matriculas; si ya lo está, lanzar un error.


<details>
<summary>Respuesta</summary>

```
```


</details>

2. Ejecutar el procedimiento para inscribir al estudiante con ID 1 en el curso con ID 2.

<details>
<summary>Respuesta</summary>

```
```


</details>


3. Eliminar el procedimiento.

<details>
<summary>Respuesta</summary>

```
```


</details>




## Parte 4: Vistas.

1. Crear una vista llamada resumen_matriculas que muestre:

- Nombre del estudiante
- Nombre del curso
- Nombre del profesor
- Fecha de matrícula

<details>
<summary>Respuesta</summary>

```
```


</details>

2. Consultar los datos desde la vista, mostrando nombre del estudiante y curso.

<details>
<summary>Respuesta</summary>

```
```


</details>


3. Eliminar la vista.

<details>
<summary>Respuesta</summary>

```
```


</details>

## Parte 5: Función Definida por el Usuario.

1. Crear una función llamada promedio_creditos_por_anio que reciba un año como parámetro y devuelva el promedio de créditos matriculados por estudiante ese año.

<details>
<summary>Respuesta</summary>

```
```


</details>


2. Ejecutar la función para el año 2023.

<details>
<summary>Respuesta</summary>

```
```


</details>


3. Eliminar la función.

<details>
<summary>Respuesta</summary>

```
```


</details>



## Parte 6: Índices.

1. Crear un índice en la columna fecha de la tabla matriculas.

<details>
<summary>Respuesta</summary>

```
```


</details>


2. Crear un índice compuesto en la tabla matriculas sobre estudiante_id y curso_id.

<details>
<summary>Respuesta</summary>

```
```


</details>


3. Consultar los índices de la tabla matriculas.

<details>
<summary>Respuesta</summary>

```
```


</details>


4. Eliminar ambos índices.

<details>
<summary>Respuesta</summary>

```
```


</details>

## Parte 7: Trigger de Auditoría.

1. Crear una tabla llamada auditoria_matriculas que registre:

- Tipo de operación (INSERT)
- ID del estudiante
- ID del curso
- Fecha y hora de la operación
- Usuario que realizó la acción

<details>
<summary>Respuesta</summary>

```
```


</details>

2. Crear un trigger AFTER INSERT sobre matriculas que inserte un registro en auditoria_matriculas al realizar una matrícula.

<details>
<summary>Respuesta</summary>

```
```


</details>

3. Consultar los registros de la auditoría.

<details>
<summary>Respuesta</summary>

```
```


</details>

4. Eliminar el trigger y la tabla de auditoría.

<details>
<summary>Respuesta</summary>

```
```


</details>

</div>
