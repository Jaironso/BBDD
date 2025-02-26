<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

# Ejercicio de Normalización

La siguiente tabla muestra la información de una tienda con sus productos.

## Base de Datos No Normalizada: Tienda

| ProductoID | Nombre          | Categorias                  | Precio | ClienteID | NombreCliente | DireccionesEnvio                    |
|------------|-----------------|-----------------------------|--------|-----------|---------------|-------------------------------------|
| 1          | Laptop HP       | Electrónicos, Informática   | 800    | 101       | Juan          | Calle 1, Ciudad A / Calle 2, Ciudad A |
| 2          | Camiseta Nike    | Ropa, Deportes              | 30     | 102       | María         | Calle 3, Ciudad B                    |
| 3          | Libro "Dune"     | Libros, Ciencia Ficción     | 20     | 101       | Juan          | Calle 1, Ciudad A                     |

Se pide:

- Verifica y transforma a __1FN__ justificando la respuesta.

<details>
<summary>Respuesta</summary>
<br>

**Tabla Categoria** 

| ID_Categoria | Categoria  |
|--------------|------------|
|1             |Electrónicos|
|2             |Informática |
|3             |Ropa        |
|4             |Deportes    |
|5             |Libros      |
|6             |Ciencia Ficción|

**Tabla Direcciones** 

| Ciudad       | Calle      | ClienteID |
|--------------|------------|------------
| Ciudad A     | Calle 1    | 101       |
| Ciudad A     | Calle 2    | 101       |
| Ciudad B     | Calle 3    | 102       |


</details>

- Verifica y transforma a __2FN__ justificando la respuesta.

<details>
<summary>Respuesta</summary>
<br>

**Tabla Categoria** 

| ID_Categoria | Categoria  |
|--------------|------------|
|1             |Electrónicos|
|2             |Informática |
|3             |Ropa        |
|4             |Deportes    |
|5             |Libros      |
|6             |Ciencia Ficción|

**Tabla Direcciones** 

| Ciudad       | Calle      | ClienteID |
|--------------|------------|------------
| Ciudad A     | Calle 1    | 101       |
| Ciudad A     | Calle 2    | 101       |
| Ciudad B     | Calle 3    | 102       |

  <div align="center">
    <img src=Images/Normalizacion1.drawio.png>
  </div>
</details>


- Verifica y transforma a __3FN__ justificando la respuesta.

<details>
<summary>Respuesta</summary>
<br>

**Tabla Categoria** 

| ID_Categoria | Categoria  |
|--------------|------------|
|1             |Electrónicos|
|2             |Informática |
|3             |Ropa        |
|4             |Deportes    |
|5             |Libros      |
|6             |Ciencia Ficción|

**Tabla Direcciones** 

| Ciudad       | Calle      | ClienteID |
|--------------|------------|------------
| Ciudad A     | Calle 1    | 101       |
| Ciudad A     | Calle 2    | 101       |
| Ciudad B     | Calle 3    | 102       |

  <div align="center">
    <img src=Images/Normalizacion1.drawio.png>
  </div>
</details>

 </div>
