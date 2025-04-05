<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

## **Unidad 3. Tarea 9: Lenguajes de definición/consulta y manipulación de información en Base de Datos.**

- Obtener el nombre del alumno y el nombre de la clase en la que está inscrito.

<details>
<summary>Respuesta</summary>
  
```
select a.nombre AS Nombre_Alumno, c.nombre AS Nombre_Clase from Inscripciones i
JOIN Alumnos a ON i.id_alumno = a.id
JOIN Clases c ON i.id_clase = c.id;
┌───────────────┬────────────────────────┐
│ Nombre_Alumno │      Nombre_Clase      │
├───────────────┼────────────────────────┤
│ Juan          │ Matemáticas 101        │
│ Juan          │ Historia Antigua       │
│ María         │ Literatura Moderna     │
│ María         │ Biología Avanzada      │
│ Pedro         │ Química Orgánica       │
│ Pedro         │ Física Cuántica        │
│ Laura         │ Arte Contemporáneo     │
│ Laura         │ Inglés Avanzado        │
│ Carlos        │ Economía Internacional │
│ Ana           │ Derecho Penal          │
└───────────────┴────────────────────────┘
```
</details>

- Obtener el nombre del alumno y la materia de las clases en las que está inscrito.

<details>
<summary>Respuesta</summary>
  
```
select a.nombre AS Nombre_Alumno, c.materia AS Nombre_Materia from Inscripciones i
JOIN Alumnos a ON i.id_alumno = a.id
JOIN Clases c ON i.id_clase = c.id;
┌───────────────┬────────────────┐
│ Nombre_Alumno │ Nombre_Materia │
├───────────────┼────────────────┤
│ Juan          │ Matemáticas    │
│ Juan          │ Historia       │
│ María         │ Literatura     │
│ María         │ Biología       │
│ Pedro         │ Química        │
│ Pedro         │ Física         │
│ Laura         │ Arte           │
│ Laura         │ Idiomas        │
│ Carlos        │ Economía       │
│ Ana           │ Derecho        │
└───────────────┴────────────────┘
```
</details>


- Obtener el nombre del alumno, la edad y el nombre del profesor de las clases en las que está inscrito.

<details>
<summary>Respuesta</summary>
  
```
select a.nombre AS Nombre_Alumno, a.edad AS Edad_Alumno, c.profesor AS Nombre_Profesor from Inscripciones i
JOIN Alumnos a ON i.id_alumno = a.id
JOIN Clases c ON i.id_clase = c.id;
┌───────────────┬─────────────┬─────────────────┐
│ Nombre_Alumno │ Edad_Alumno │ Nombre_Profesor │
├───────────────┼─────────────┼─────────────────┤
│ Juan          │ 20          │ Profesor X      │
│ Juan          │ 20          │ Profesor Y      │
│ María         │ 21          │ Profesor Z      │
│ María         │ 21          │ Profesor W      │
│ Pedro         │ 19          │ Profesor V      │
│ Pedro         │ 19          │ Profesor U      │
│ Laura         │ 22          │ Profesor T      │
│ Laura         │ 22          │ Profesor S      │
│ Carlos        │ 20          │ Profesor R      │
│ Ana           │ 19          │ Profesor Q      │
└───────────────┴─────────────┴─────────────────┘
```
</details>


- Obtener el nombre del alumno y la dirección de las clases en las que está inscrito.

<details>
<summary>Respuesta</summary>
  
```
select a.nombre AS Nombre_Alumno, a.direccion AS Direcc_Alumno, c.id AS id_clase from Inscripciones i
JOIN Alumnos a ON i.id_alumno = a.id
JOIN Clases c ON i.id_clase = c.id;
┌───────────────┬───────────────┬──────────┐
│ Nombre_Alumno │ Direcc_Alumno │ id_clase │
├───────────────┼───────────────┼──────────┤
│ Juan          │ Calle A       │ 1        │
│ Juan          │ Calle A       │ 2        │
│ María         │ Calle B       │ 3        │
│ María         │ Calle B       │ 4        │
│ Pedro         │ Calle C       │ 5        │
│ Pedro         │ Calle C       │ 6        │
│ Laura         │ Calle D       │ 7        │
│ Laura         │ Calle D       │ 8        │
│ Carlos        │ Calle E       │ 9        │
│ Ana           │ Calle F       │ 10       │
└───────────────┴───────────────┴──────────┘
```
</details>


- Obtener el nombre del alumno y el nombre de la clase junto con el profesor.

<details>
<summary>Respuesta</summary>
  
```
select a.nombre AS Nombre_Alumno, c.nombre AS Nombre_Clase, c.profesor AS Nombre_Profesor from Inscripciones i
JOIN Alumnos a ON i.id_alumno = a.id
JOIN Clases c ON i.id_clase = c.id;
┌───────────────┬────────────────────────┬─────────────────┐
│ Nombre_Alumno │      Nombre_Clase      │ Nombre_Profesor │
├───────────────┼────────────────────────┼─────────────────┤
│ Juan          │ Matemáticas 101        │ Profesor X      │
│ Juan          │ Historia Antigua       │ Profesor Y      │
│ María         │ Literatura Moderna     │ Profesor Z      │
│ María         │ Biología Avanzada      │ Profesor W      │
│ Pedro         │ Química Orgánica       │ Profesor V      │
│ Pedro         │ Física Cuántica        │ Profesor U      │
│ Laura         │ Arte Contemporáneo     │ Profesor T      │
│ Laura         │ Inglés Avanzado        │ Profesor S      │
│ Carlos        │ Economía Internacional │ Profesor R      │
│ Ana           │ Derecho Penal          │ Profesor Q      │
└───────────────┴────────────────────────┴─────────────────┘
```
</details>


- Obtener el nombre del alumno, la materia y el nombre del profesor de las clases en las que está inscrito.

<details>
<summary>Respuesta</summary>
  
```
select a.nombre AS Nombre_Alumno, c.materia AS Nombre_Materia, c.profesor AS Nombre_Profesor from Inscripciones i
JOIN Alumnos a ON i.id_alumno = a.id
JOIN Clases c ON i.id_clase = c.id;
┌───────────────┬────────────────┬─────────────────┐
│ Nombre_Alumno │ Nombre_Materia │ Nombre_Profesor │
├───────────────┼────────────────┼─────────────────┤
│ Juan          │ Matemáticas    │ Profesor X      │
│ Juan          │ Historia       │ Profesor Y      │
│ María         │ Literatura     │ Profesor Z      │
│ María         │ Biología       │ Profesor W      │
│ Pedro         │ Química        │ Profesor V      │
│ Pedro         │ Física         │ Profesor U      │
│ Laura         │ Arte           │ Profesor T      │
│ Laura         │ Idiomas        │ Profesor S      │
│ Carlos        │ Economía       │ Profesor R      │
│ Ana           │ Derecho        │ Profesor Q      │
└───────────────┴────────────────┴─────────────────┘
```
</details>


- Obtener el nombre del alumno, la edad y la materia de las clases en las que está inscrito.

<details>
<summary>Respuesta</summary>
  
```
select a.nombre AS Nombre_Alumno, a.edad AS Edad_Alumno, c.materia AS Nombre_Materia from Inscripciones i
JOIN Alumnos a ON i.id_alumno = a.id
JOIN Clases c ON i.id_clase = c.id;
┌───────────────┬─────────────┬────────────────┐
│ Nombre_Alumno │ Edad_Alumno │ Nombre_Materia │
├───────────────┼─────────────┼────────────────┤
│ Juan          │ 20          │ Matemáticas    │
│ Juan          │ 20          │ Historia       │
│ María         │ 21          │ Literatura     │
│ María         │ 21          │ Biología       │
│ Pedro         │ 19          │ Química        │
│ Pedro         │ 19          │ Física         │
│ Laura         │ 22          │ Arte           │
│ Laura         │ 22          │ Idiomas        │
│ Carlos        │ 20          │ Economía       │
│ Ana           │ 19          │ Derecho        │
└───────────────┴─────────────┴────────────────┘
```
</details>


- Obtener el nombre del alumno, la dirección y el profesor de las clases en las que está inscrito.

<details>
<summary>Respuesta</summary>
  
```
select a.nombre AS Nombre_Alumno, a.direccion AS Direcc_Alumno, c.profesor AS Nombre_Profesor from Inscripciones i
JOIN Alumnos a ON i.id_alumno = a.id
JOIN Clases c ON i.id_clase = c.id;
┌───────────────┬───────────────┬─────────────────┐
│ Nombre_Alumno │ Direcc_Alumno │ Nombre_Profesor │
├───────────────┼───────────────┼─────────────────┤
│ Juan          │ Calle A       │ Profesor X      │
│ Juan          │ Calle A       │ Profesor Y      │
│ María         │ Calle B       │ Profesor Z      │
│ María         │ Calle B       │ Profesor W      │
│ Pedro         │ Calle C       │ Profesor V      │
│ Pedro         │ Calle C       │ Profesor U      │
│ Laura         │ Calle D       │ Profesor T      │
│ Laura         │ Calle D       │ Profesor S      │
│ Carlos        │ Calle E       │ Profesor R      │
│ Ana           │ Calle F       │ Profesor Q      │
└───────────────┴───────────────┴─────────────────┘
```
</details>


- Obtener el nombre del alumno y la materia de las clases en las que está inscrito, ordenado por el nombre del alumno.

<details>
<summary>Respuesta</summary>
  
```
select a.nombre AS Nombre_Alumno, c.materia AS Nombre_Materia from Inscripciones i
JOIN Alumnos a ON i.id_alumno = a.id
JOIN Clases c ON i.id_clase = c.id
ORDER BY a.nombre;
┌───────────────┬────────────────┐
│ Nombre_Alumno │ Nombre_Materia │
├───────────────┼────────────────┤
│ Ana           │ Derecho        │
│ Carlos        │ Economía       │
│ Juan          │ Matemáticas    │
│ Juan          │ Historia       │
│ Laura         │ Arte           │
│ Laura         │ Idiomas        │
│ María         │ Literatura     │
│ María         │ Biología       │
│ Pedro         │ Química        │
│ Pedro         │ Física         │
└───────────────┴────────────────┘
```
</details>


- Contar cuántos alumnos están inscritos en cada clase.

<details>
<summary>Respuesta</summary>
  
```
select COUNT(*) AS Alumnos_por_Clase, c.nombre AS Nombre_Clase from inscripciones i
JOIN Clases c ON i.id_clase = c.id
GROUP BY c.nombre;
┌───────────────────┬────────────────────────┐
│ Alumnos_por_Clase │      Nombre_Clase      │
├───────────────────┼────────────────────────┤
│ 1                 │ Arte Contemporáneo     │
│ 1                 │ Biología Avanzada      │
│ 1                 │ Derecho Penal          │
│ 1                 │ Economía Internacional │
│ 1                 │ Física Cuántica        │
│ 1                 │ Historia Antigua       │
│ 1                 │ Inglés Avanzado        │
│ 1                 │ Literatura Moderna     │
│ 1                 │ Matemáticas 101        │
│ 1                 │ Química Orgánica       │
└───────────────────┴────────────────────────┘
```
</details>


</div>
