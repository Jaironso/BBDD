<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

## **Unidad 3. Tarea 3: Lenguajes de definición/consulta y manipulación de información en Base de Datos.**

### Paso 1: Creación de la BBDD.
### Paso 2 Lectura del fichero sql.
### Paso 3: Realización de consultas.

- Funciones UPPER y LOWER:
  - Muestra el nombre de todos los empleados en mayúsculas.

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_1.PNG>
  </div>
</details>

- Funciones Numéricas:
  - Calcula el valor absoluto del salario de todos los empleados.
 
<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_2.PNG>
  </div>
</details>

- Funciones de Fecha y Hora:
  - Muestra la fecha actual.
 
<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_3.PNG>
  </div>
</details>

- Funciones de Agregación:
  - Calcula el promedio de salarios de todos los empleados

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_4.PNG>
  </div>
</details>

  - Convierte la cadena '123' a un valor entero.

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_4_2.PNG>
  </div>
</details>
  
- Funciones de Manipulación de Cadenas:
  - Concatena el nombre y el departamento de cada empleado.
 
<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_5y6.PNG>
  </div>
</details>

- Funciones de Manipulación de Cadenas (CONCAT_WS):
  - Concatena el nombre y el departamento de cada empleado con un guion como separador.
 
<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_5y6.PNG>
  </div>
</details>

- Funciones de Control de Flujo (CASE):
  - Categoriza a los empleados según sus salarios.
 
<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_7.PNG>
  </div>
</details>

- Funciones de Agregación (SUM):
  - Calcula la suma total de salarios de todos los empleados.
 
<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_8.PNG>
  </div>
</details>

- Funciones Numéricas (ROUND):
  - Redondea el salario de todos los empleados a dos decimales.
 
<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_9.PNG>
  </div>
</details>

- Funciones de Manipulación de Cadenas (LENGTH):
  - Muestra la longitud de cada nombre de empleado.
 
<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_10.PNG>
  </div>
</details>

- Funciones de Agregación (COUNT):
  - Cuenta el número total de empleados en cada departamento.
 
<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_11.PNG>
  </div>
</details>

- Funciones de Fecha y Hora (CURRENT_TIME):
  - Muestra la hora actual.
 
<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_12.PNG>
  </div>
</details>

- Funciones de Conversión (CAST):
  - Convierte el salario a un valor de punto flotante.
 
<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_13.PNG>
  </div>
</details>

- Funciones de Manipulación de Cadenas (SUBSTR):
  - Muestra los primeros tres caracteres de cada nombre de empleado.

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_14.PNG>
  </div>
</details>

- __Order By__ and __Like__.

  - Empleados en el departamento de 'Ventas' con salarios superiores a 52000.

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_ORDERLIKE1.PNG>
  </div>
</details>

  - Empleados cuyos nombres contienen la letra 'a' y tienen salarios ordenados de manera ascendente.

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_ORDERLIKE2.PNG>
  </div>
</details>

  - Empleados en el departamento 'Recursos Humanos' con salarios entre 45000 y 55000.

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_ORDERLIKE3.PNG>
  </div>
</details>

  - Empleados con salarios en orden descendente, limitando a los primeros 5 resultados.

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_ORDERLIKE4.PNG>
  </div>
</details>

  - Empleados cuyos nombres comienzan con 'M' o 'N' y tienen salarios superiores a 50000.

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_ORDERLIKE5.PNG>
  </div>
</details>

  - Empleados en el departamento 'TI' o 'Ventas' ordenados alfabéticamente por nombre.

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_ORDERLIKE6.PNG>
  </div>
</details>

  - Empleados con salarios únicos (eliminando duplicados) en orden ascendente.

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_ORDERLIKE7.PNG>
  </div>
</details>

  - Empleados cuyos nombres terminan con 'o' o 'a' y están en el departamento 'Ventas'.

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_ORDERLIKE8.PNG>
  </div>
</details>

  - Empleados con salarios fuera del rango de 55000 a 70000, ordenados por departamento.

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_ORDERLIKE9.PNG>
  </div>
</details>

  - Empleados en el departamento 'Recursos Humanos' con nombres que no contienen la letra 'e'.

<details>
<summary>Respuesta</summary>
<br>
  <div align="center">
    <img src=images/Tarea3/Tarea3_Ejercicio3_ORDERLIKE10.PNG>
  </div>
</details>


</div>
