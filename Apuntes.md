<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 
#### **Apuntes**

###### Cualquier atributo compuesto(multievaluados) -> tabla (como las direcciones o email), esto ocurre al normalizar. Mejor representarlo en el diagrama como tabla desde el inicio.
###### N:M -> Nueva tabla.
###### 1:N -> La N arrastra la PK de la otra tabla. No se crea nueva tabla, se añade el nuevo atributo para la relación.
###### Valor de dominio -> diferentes valores posibles pero solo 1 (ejemplo: sexo).
###### Reflexiva JEFE/EMPLEADO => 1:N (1:1 y 1:n) Una tabla con FK id_jefe (corregir todas las reflexivas)
###### Corregir el de vehiculo jerarquica todos los atributos en vehiculos ya que son los mismos para todos, hacer tabla para cada tipo y añadir una especifica a cada uno.
###### Jerarquias: Arco exclusivo, sin arco no.
###### Ejercicio equipos de futbol correciones: Gol tiene que tener id, las PK que se llamen igual en todas las tablas, las flechas mas claras, que no coincidan, las PK en negrito y que se vean las primeras en el ER
##### Modelo examen: atributo con discontinua = atributo que se calcula de otra cosa. PINTAR tablas N:M de otro color.

UNIDAD 3

LIKE VS REGEX

LIKE '%A' o 'Per%' o '%and%'
REGEXP 'a$' o '^Per' o 'and'

Mas ejemplos:
regexp '^[P/p]erez'
regexp '[0..9]{2}-[0..9]{2}-[0..9]{4}' -> FECHAS
regexp '[0..9]{8}[a..z/A..Z]{1}' -> DNI
regexp '[a..z/A..Z]{1}[0..9]{7}' -> NIE
regexp '\w+@\w+.[a..z/A..Z]{2/3}' -> email

regex mas rapido, no recorren todos los caracteres.

Los + importantes:
^
$
*
+ (al menos una)
\
.
() PARENTESIS -> GRUPOS.
-- Obtener todos los autores cuyo nombre empieza con "M" o termina con "n":
CORRECCION: '^[M|m]|[N|n]$';


-- Obtener todos los autores cuyo nombre no contiene caracteres especiales:
CORRECCION: '^[a-zA-Z ]*$'; (El espacio es pq el nombre puede contener espacios)


SI quisieramos ambas opciones: .* (en medio)

</div>
