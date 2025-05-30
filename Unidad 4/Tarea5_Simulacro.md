<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

## **Unidad 4. Tarea 5: Simulacro, optimización de BBDD y programación.**

## Parte 1: Consultas para Explorar la Estructura de las Tablas.

### Consultas simples.

1. Mostrar las columnas de la tabla estudiantes.

<details>
<summary>Respuesta</summary>

```
```


</details>

2. Mostrar las columnas de la tabla cursos.

<details>
<summary>Respuesta</summary>

```
```


</details>

3. Mostrar las columnas de la tabla matriculas.

<details>
<summary>Respuesta</summary>

```
```


</details>


## Parte 2: Consultas Avanzadas sobre Datos.

1. Mostrar cada estudiante con la cantidad de cursos en los que está matriculado.

<details>
<summary>Respuesta</summary>

```
```


</details>


2. Mostrar cada estudiante con el total de créditos acumulados.

<details>
<summary>Respuesta</summary>

```
```


</details>

3. Mostrar cursos con la cantidad de estudiantes matriculados, ordenados de mayor a menor.

<details>
<summary>Respuesta</summary>

```
```


</details>

4. Mostrar la media de créditos por curso.

<details>
<summary>Respuesta</summary>

```
```


</details>

5. Listar los cursos que no tienen estudiantes matriculados.

<details>
<summary>Respuesta</summary>

```
```


</details>

6. Mostrar el nombre del profesor y cuántos cursos imparte.

<details>
<summary>Respuesta</summary>

```
```


</details>

7. Mostrar los profesores que no imparten ningún curso.

<details>
<summary>Respuesta</summary>

```
```


</details>

8. Mostrar la ciudad con mayor número de estudiantes registrados.

<details>
<summary>Respuesta</summary>

```
```


</details>

9. Mostrar estudiantes que están matriculados en más de 1 curso.

<details>
<summary>Respuesta</summary>

```
```


</details>

10. Listar cursos junto a su clasificación según créditos: 6 o más: "Alta carga". Menos de 6: "Carga estándar"

<details>
<summary>Respuesta</summary>

```
```


</details>

11. Listar estudiantes y clasificar su carga académica: Más de 12 créditos: "Carga Alta" 6 a 12 créditos: "Carga Media" Menos de 6 créditos: "Carga Baja"

<details>
<summary>Respuesta</summary>

```
```


</details>


12. Mostrar cursos en los que se haya matriculado al menos un estudiante de Sevilla.

<details>
<summary>Respuesta</summary>

```
```


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
