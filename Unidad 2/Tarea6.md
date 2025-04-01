<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

# Ejercicios de Normalización de Bases de Datos (1FN y 2FN)

> **IMP**: Genera las claves necesarias para corregir las tablas resultantes.

## **Ejercicio 1: Lista de Productos**

### **Tabla Inicial: Productos**

| ID_Producto | Nombre_Producto | Proveedores      | Categoría   | Precio |
|------------|----------------|-----------------|------------|--------|
| 1          | Laptop         | Dell, HP        | Tecnología | 1000   |
| 2          | Mouse          | Logitech        | Accesorios | 25     |

### **Tareas:**

1. Aplicar **1FN**, eliminando los valores multivaluados en "Proveedores".
2. Aplicar **2FN**, asegurando que cada campo dependa completamente de la clave primaria.

> Verifica generando el modelo Entidad/Relación

<details>
<summary>Respuesta</summary>
<br>

**Tabla Proveedor**

| ID_Proveedor | Nombre       | ID_Producto |
|------------|----------------|----------------|
| 1          | Dell           | 1
| 2          | HP             | 1
| 3          | Logitech       | 2 |


**Tabla Producto**

| ID_Producto | Nombre        | Precio | ID_Categoria |
|------------|----------------|--------|--------------|
| 1          | Laptop         | 1000   | 1            |
| 2          | Mouse          | 25     | 2            |


**Tabla Categoria**

| ID_Categoria | Nombre  |
|------------|----------------|
| 1          | Tecnologia |
| 2          | Accesorios  |

### **Entidad Relación:**

  <div align="center">
    <img src=Images/Normalizacion1.drawio.png>
  </div>
</details>

---

## **Ejercicio 2: Pedidos de Clientes**

### **Tabla Inicial: Pedidos**

| ID_Pedido | Cliente   | Dirección       | Producto     | Cantidad | Precio |
|----------|----------|---------------|--------------|-----------|--------|
| 101      | Juan Pérez | Calle 123     | Laptop     | 1       | 1000   |
| 102      | Ana López | Av. Central   | Teclado     | 2        | 50     |

### **Tareas:**

1. Aplicar **1FN**, separando valores repetidos y creando nuevas tablas si es necesario.
2. Aplicar **2FN**, asegurando que las dependencias parciales sean eliminadas.

> Verifica generando el modelo Entidad/Relación

<details>
<summary> Respuesta </summary>
<br>

**Tabla Pedido**

| ID_Pedido | ID_Cliente | ID_Producto
|------|------|--------|
| 101 |1  | 1    |
| 102 |2  | 2    |

**Tabla Producto**

| ID_Producto | Nombre | Precio |
|----|----------|-------|
| 1    | Laptop| 1000   |
| 2    | Teclado  | 25     |

**Tabla Detalle Pedido (Pedido + Producto + Q)**

| ID_Pedido | ID_Producto | Cantidad
|------|---|--------|
| 101  |1  | 1     |
| 102  |2  | 2    |

**Tabla Cliente**

| ID_Cliente | Nombre |
|--------|----------|
| 1      | Juan Pérez   |
| 2      | Ana López  | 

**Tabla Direccion**

| ID_Cliente | Direccion |
|------------|-----------|
| 1          | Calle 123 |
| 2          | Av. Central |

### **Entidad Relación:**

  <div align="center">
    <img src=Images/Normalizacion2.drawio.png
  </div>
</details>

---

## **Ejercicio 3: Registro de Empleados**

### **Tabla Inicial: Empleados**

| ID_Empleado | Nombre     | Teléfonos         | Departamento |
|------------|------------|------------------|--------------|
| 1          | Carlos R.  | 12345, 67890     | Ventas       |
| 2          | Laura M.   | 54321            | Finanzas     |

### **Tareas:**

1. Aplicar **1FN**, eliminando los valores multivaluados en "Teléfonos".
2. Aplicar **2FN**, asegurando que cada atributo dependa completamente de la clave primaria.

> Verifica generando el modelo Entidad/Relación

<details>
<summary>Respuesta</summary>
<br>

**Tabla Empleado**

| ID_Empleado | Nombre    | ID_Dpto|
|------------|------------|--------|
| 1          | Carlos R.  | 1      |
| 2          | Laura M.   | 2      |

**Tabla Teléfono**

| Telefono | ID_Empleado |       
|------------|-------------|
| 12345      |  1          |
| 67890      | 1           | 
| 54321      | 2           |

**Tabla Departamento**

| ID_Dpto | Nombre     |
|------------|---------|
| 1          | Ventas  | 
| 2          | Finanzas |


### **Entidad Relación:**

  <div align="center">
    <img src=Images/Normalizacion3.drawio.png>
  </div>
</details>

---

## **Ejercicio 4: Reservas de Hotel**

### **Tabla Inicial: Reservas**

| ID_Reserva | Cliente    | Habitación | Fechas              | Precio |
|------------|-----------|------------|---------------------|--------|
| 5001      | Pedro G.  | 101        | 01/02, 02/02, 03/02 | 300    |
| 5002      | María T.  | 202        | 10/03, 11/03       | 200    |

### **Tareas:**

1. Aplicar **1FN**, eliminando los valores multivaluados en "Fechas".
2. Aplicar **2FN**, asegurando que las dependencias parciales sean eliminadas.

> Verifica generando el modelo Entidad/Relación

<details>
<summary>Respuesta</summary>
<br>

**Tabla Reserva**

| ID_Reserva | ID_Cliente | ID_Habitacion| Precio|
|------------|----------|----------------|-------|
| 5001       | 1        | 1              | 300   |
| 5002       | 2        | 2              | 200   |

**Tabla Fechas**

| ID_Reserva | Fecha|
|---------|--------|
| 5001    | 01/02 |
| 5001    | 02/02 |
| 5001    | 03/02 |
| 5002    | 10/03 |
| 5002    | 11/03 |

**Tabla Habitacion**

| ID_Habitacion | Precio |       
|------------|-----------|
| 101        |  100      |
| 102        |  100      | 

**Tabla Cliente**

| ID_Cliente | Nombre  |
|------------|---------|
| 1          | Carlos R. | 
| 2          | Laura M. |


### **Entidad Relación:**

  <div align="center">
    <img src=Images/Normalizacion4.drawio.png>
  </div>
</details>

---

## **Ejercicio 5: Inscripciones a Cursos**

### **Tabla Inicial: Inscripciones**

| ID_Inscripción | Estudiante | Curso        | Profesor    | Horarios |
|---------------|------------|--------------|------------|----------|
| 3001         | Luis R.    | Matemáticas  | Prof. Pérez | Lunes 10AM, Miércoles 2PM |
| 3002         | Ana S.     | Física       | Prof. Gómez | Martes 3PM |

### **Tareas:**

1. Aplicar **1FN**, eliminando valores multivaluados en "Horarios".
2. Aplicar **2FN**, asegurando que cada campo dependa completamente de la clave primaria.

> Verifica generando el modelo Entidad/Relación

<details>
<summary>Respuesta</summary>
<br>

**Tabla Inscripción**

| ID_Inscripcion | ID_Estudiante    | ID_Curso
|------------|------------|-------|
| 3001        | 1  | 1
| 3002        | 2   | 2

**Tabla Estudiante**

| ID_Estudiante | Nombre |       
|------------|----------|
| 1          | Luis R.   |
| 2          | Ana S.   | 

**Tabla Profesor**

| ID_Profesor | Nombre | 
|------------|----------|
| 1          | Prof. Pérez  |
| 2          | Prof. Gómez  | 


**Tabla Curso**

| ID_Curso | Nombre     | ID_Profesor |
|------------|----------|------------|
| 1          | Matematicas  | 1 |
| 2          | Fisica       | 2 |
 
**Tabla Horarios**

| Horario | ID_Curso  |
|------------|---------|
| Lunes 10AM    | 1 | 
| Miercoles 2PM |1 |
| Martes 3PM | 2  |

### **Entidad Relación:**

  <div align="center">
    <img src=Images/Normalizacion5.drawio.png>
  </div>
</details>

---

## **Ejercicio 6: Ventas de Tienda**

### **Tabla Inicial: Ventas**

| ID_Venta | Cliente    | Productos Comprados | Total |
|----------|------------|---------------------|-------|
| 8001     | Juan P.   | Celular, Funda      | 500   |
| 8002     | Andrea M. | Laptop              | 1000  |

### **Tareas:**

1. Aplicar **1FN**, separando valores multivaluados en "Productos Comprados".
2. Aplicar **2FN**, asegurando que cada atributo dependa completamente de la clave primaria.

> Verifica generando el modelo Entidad/Relación

<details>
<summary>Respuesta</summary>
<br>

**Tabla Venta**

| ID_Venta   | ID_Producto | Total  |
|------------|------------|---------|
| 8001       | 1          |   500   |
| 8002       | 2          |   1000  |

**Tabla Producto**

| ID_Producto | Nombre    | Precio
|------------|------------|-------|
| 1         | Celular     |  480  |
| 2         | Funda       |   20  |
| 3         | Laptop      | 1000  |

**Tabla Producto/Venta**

| ID_Producto |ID_Venta   |
|------------|------------|
| 1         | 8001     |
| 2         | 8001     | 
| 3         | 8002     |

**Tabla Cliente**

| ID_Cliente | Nombre     |
|------------|------------|
| 1          | Juan P.    |
| 2          | Andrea M.  |

### **Entidad Relación:**

  <div align="center">
    <img src=Images/Normalizacion6.drawio.png>
  </div>
</details>

---

## **Ejercicio 7: Biblioteca de Libros**

### **Tabla Inicial: Libros**

| ID_Libro | Título | Autores          | Género  |
|----------|--------|-----------------|---------|
| 101      | El Quijote | Cervantes   | Novela  |
| 102      | 1984       | Orwell       | Ciencia Ficción |

### **Tareas:**

1. Aplicar **1FN**, eliminando valores multivaluados en "Autores".
2. Aplicar **2FN**, asegurando que cada atributo dependa completamente de la clave primaria.

> Verifica generando el modelo Entidad/Relación

<details>
<summary>Respuesta</summary>
<br>

**Tabla Libro**

| ID_Libro   | Título     |
|------------|------------|
| 101        | El Quijote |
| 102        | 1984       |

**Tabla Autor**

| ID_Autor  | Nombre     | 
|-----------|------------|
| 1         | Cervantes  |
| 2         | Orwell     |

**Tabla Libro/Autor**

| ID_Libro  | ID_Autor   | 
|-----------|------------|
| 101       | 1          |
| 102       | 2          |

**Tabla Género**

| ID_Genero |Nombre           |
|-----------|-----------------|
| 1         | Novela          |
| 2         | Ciencia Ficcion | 

**Tabla Libro/Género**

| ID_Libro  | ID_Genero   | 
|-----------|------------|
| 101       | 1          |
| 102       | 2          |


### **Entidad Relación:**

  <div align="center">
    <img src=Images/Normalizacion7.drawio.png>
  </div>
</details>

---

## **Ejercicio 8: Facturación de Servicios**

### **Tabla Inicial: Facturas**

| ID_Factura | Cliente   | Servicios Contratados | Costo Total |
|------------|-----------|----------------------|-------------|
| 9001       | Juan P.   | Internet, TV        | 50          |
| 9002       | Ana M.    | Teléfono            | 20          |

### **Tareas:**

1. Aplicar **1FN**, separando valores multivaluados en "Servicios Contratados".
2. Aplicar **2FN**, asegurando que cada atributo dependa completamente de la clave primaria.

> Verifica generando el modelo Entidad/Relación

<details>
<summary>Respuesta</summary>
<br>

**Tabla Facturas**

| ID_Factura | ID_Cliente | Costo_Total |
|------------|------------|-------------|
| 9001       | 1          | 50          |
| 9002       | 2          | 20          |

**Tabla Servicio**

| ID_Servicio| Nombre      | Coste
|-----------|-------------|------|
| 1         | Internet     |  25  |
| 2         | TV           |  25  |
| 3         | Telefono     |  20  |

**Tabla Factura/Servicio**

|ID_Factura | ID_Servicio|
|-----------|-------------|
|9001        | 1         |
|9001        | 2         |
|9002        | 3         | 

**Tabla Cliente**

| ID_Cliente| Nombre     | 
|-----------|------------|
| 1         | Juan P.    |
| 2         | Ana M.     |

### **Entidad Relación:**

  <div align="center">
    <img src=Images/Normalizacion8.drawio.png>
  </div>
</details>

---

## **Ejercicio 9: Gestión de Vehículos**

### **Tabla Inicial: Vehículos**

| ID_Vehículo | Marca   | Modelos      | Año |
|------------|--------|----------------|-----|
| 5001       | Toyota  | Corolla, Yaris  | 2022 |
| 5002       | Honda   | Civic          | 2023 |

### **Tareas:**

1. Aplicar **1FN**, eliminando valores multivaluados en "Modelos".
2. Aplicar **2FN**, asegurando que cada atributo dependa completamente de la clave primaria.

> Verifica generando el modelo Entidad/Relación

<details>
<summary>Respuesta</summary>
<br>

**Tabla Vehículo**

| ID_Vehiculo | Marca |  
|------------|--------|
| 5001       | Toyota | 
| 5002       | Honda  |

**Tabla Modelo**

| ID_Modelo | Nombre      | ID_Vehiculo|
|-----------|-------------|------------|
| 1         | Corolla     | 5001       |
| 2         | Yaris       | 5001       |
| 3         | Civic       | 5002       |

**Tabla Año**

| Anio      | ID_Vehiculo | 
|-----------|-------------|
| 2022      | 5001        | 
| 2023      | 5002        |

### **Entidad Relación:**

  <div align="center">
    <img src=Images/Normalizacion9.drawio.png>
  </div>
</details>

---

## **Ejercicio 10: Gestión de Proyectos**

### **Tabla Inicial: Proyectos**

| ID_Proyecto | Nombre       | Miembros     | Presupuesto |
|------------|-------------|----------------|------------|
| 7001       | Web App     | Juan, Ana      | 5000       |
| 7002       | E-commerce  | Pedro, María   | 10000      |

### **Tareas:**

1. Aplicar **1FN**, eliminando valores multivaluados en "Miembros".
2. Aplicar **2FN**, asegurando que cada atributo dependa completamente de la clave primaria.

> Verifica generando el modelo Entidad/Relación

<details>
<summary>Respuesta</summary>
<br>

**Tabla Proyectos**

| ID_Proyecto| Nombre    | Presupuesto |
|------------|-----------|-------------|
| 7001       | Web App   | 5000        |
| 7002       | E-Commerce| 10000       |

**Tabla Miembros**

| ID_Miembro| Nombre      |
|-----------|-------------|
| 1         | Juan        |
| 2         | Ana         |
| 3         | Pedro       | 
| 4         | Maria       |

**Tabla Proyecto/Miembro**

| ID_Miembro| ID_Proyecto |
|-----------|-------------|
| 1         | 7001        |
| 2         | 7001        |
| 3         | 7002        | 
| 4         | 7002        |

### **Entidad Relación:**

  <div align="center">
    <img src=Images/Normalizacion10.drawio.png>
  </div>
</details>


 </div>
