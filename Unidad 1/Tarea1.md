<div align="justify">

#### **Nombre: Jairo Afonso Armas | Curso: 2ºDAW Semipresencial | Asignatura: Bases de Datos** 

## **Unidad 1. Tarea 1: Definición y análisis de SGBD**

| **Nombre del SGBD** | **Tipo** |**Modelo de Datos**|**Caracteristicas Principales**|**Ventajas**|**Limitaciones**|**Casos de uso**|
|-------------------|--------|-------------------|-------------------------------|------------|----------------|----------------|
|MySQL|Relacional|Tablas relacionales|Open Source, soporte SQL|Facil de usar, escalable.|Menor soporte a NoSQL.|Aplicaciones web.|
|PostgreSQL|Relacional|Multimodelo|Soporte JSON, Transacciones ACID, índices avanzados.|Potencia, estabilidad, posibilidad de consultas complejas.|Curva de aprendizaje pronunciada, configuración inicial compleja.|Análisis de datos, apps empresariales, sistemas geoespaciales.|
|Oracle Database|Relacional|Multimodelo|Compatibilidad con SQL, transacciones ACID, integración en la nube.|Escalabilidad, seguridad, rendimiento optimizado, ecosistema oracle.|Coste elevado y complejidad para su configuración.|Sistema de planificacion de recursos empresariales, relaciones con clienetes, Big Data...|
|Microsoft SQL Server|Relacional|JSON, gráficos, XML.|Compatible T-SQL, transacciones ACID.|Integración nativa con ecosistema Microsoft, fácil de usar, seguridad robusta.|Coste y dependencia de Microsoft, menor flexibilidad multimodelo.|Aplicaciones empresariales, almacenamiento de datos, proyectos con arquitectura hibrida en la nube con Azure.|
|SQLite|Relacional|Tablas|Motor embebido, SQL estándar, cero configuración.|Lígero y rápido, simplicidad, autocontenido, multiplataforma.|No es adecuado para grandes entornos, tamaño limitado, menos funcionalidades avanzadas y tipado débil.|Apps móviles o de escritorio, prototipos o desarrollo inicial.|
|MongoDB|NoSQL|Documentos|Almacena datos en formato JSON|Flexible, escalabilidad horizontal|Menos eficiente en consultas complejas|Big Data, aplicaciones móviles|
|Cassandra|NoSQL|Clave-Valor, columna ancha.|Alta disponibilidad, escalabilidad horizontal, diseño distribuido.|Escalabilidad, sin punto único de falla.|No es ideal para datos relacionales y consultas complejas.|RRSS, Sistemas de IoT, servicios de mensajería.|
|Redis|NoSQL|Clave-valor|Almacenamiento en memoria, distribuido, comandos transaccionales básicos.|Velocidad, versatilidad, simplicidad y comunidad.|Dependiente de la memoria, falta de soporte ACID, gestión de la seguridad.|Caché, colas y mensajería, juegos y sistemas en línea.|
|DynamoDB|NoSQL|Clave-valor, documentos.|Cuenta con Amazon Web Services, escalabilidad automática, ACID, AWS, cifrado automático.|Escalabilidad, disponibilidad, administración cero, modelo de costo basado en uso.|Modelo de datos limitado, curva de aprendizaje, más limitado que SQL.|Apps web y móviles, sistemas IoT, gestión de usuarios, catalogos y carritos de compra.|
|CouchBase|NoSQL|JSON, Clave-valor|Modelo distribuido, almacenamiento multimodelo, replicación y sincronización.|SQL para JSON con N1QL, sincronización centrada en memoria, alta disponibilidad nativa|Costo elevado, complejo por N1QL, menor comunidad. |Apps móviles y desconectadas, sistemas de comercio electrónico, sistemas IoT.|
|Neo4j|Orientados a grafos|Nodos, aristas.|Lenguaje Cypher, almacenamiento nativo de grafos, optimizado para relaciones complejas.|Manejo eficiente de datos conectados, consultas rápidas.|Menor rendimiento en operaciones no relacionadas con grafos.|Análisis de RRSS, motores de recomendación, detección de fraudes.|
|ArangoDB|Orientados a grafos|Multimodelo|AQL como lenguaje de consulta, diseño flexible para diferentes tipos de datos.|Versatilidad y soporte para múltiples modelos en una única BBDD.|Menor especialización en cada modelo comparados con soluciones dedicadas.|Apps con múltiples paradigmas, analisis RRSS, almacenamiento datos estructurados.|
|Amazon Neptune|Orientados a grafos|Grafos de propiedad.|Admite Gremlin y SPARQL, AWS se encarga de la administración, soporte para consultas avanzadas.|Múltiples modelos de grafos, optimizado, escalabilidad y rendimiento, AWS, seguridad robusta.|Dependencia de AWS, coste, no soporta Cypher, menor flexibilidad que otros entornos híbridos.|Sistemas de recomendación, RRSS, detección de fraudes.|
|OrientDB|Orientados a grafos|Multimodelo|Con SQL extendido, ACID, compatibilidad con TinkerPop|Multimodelo en una sola base, SQL enriquecido, redimiento, open source.|Compleja en su configuración, menor comunidad, sobrecarga de funcionalidades.|Sistemas de recomendación, RRSS, IoT y analisis de eventos.|
|TigerGraph|Orientados a grafos|Nodos y aristas.|Optimizado para grafos grandes, GSQL, analisis en tiempo real|Grafos a gran escala, arquitectura distribuida, seguridad avanzada.|Compleja confiuraciñon si no conoces SQL, coste y menor comunidad.|RRSS, sistema de recomendación, antifraudes, analisis de redes y rutas.|
|Amazon RDS|Almacenamiento en la Nube|Relacional|Administración automatizada, disponibilidad, escalabilidad flexible, compatibilidad multiples motores.|Alta fiabilidad y soporte nativo en la nube.|Coste relativamente alto, menor personalización frente a opcines locales.|Apps empresariales y web, analisis de datos.|
|Google BigQuery|Almacenamiento en la Nube|Columnas|Analisis masivo en tiempo real, integración con herramientas de Google y SQL.|Velocidad de analisis de datos masivos|Dependencia de Google Cloud, coste de almacenamiento y consulta.|Big Data, analisis tiempo real, aprendizaje automático.|
|Microsoft Azure SQL Database|Almacenamiento en la Nube|Tablas|Azure se encarga de la gestión del hardware, backups automóticos, integración con servicios de Azure.|Gestión simplificada, disponibilidad y recuperación ante errores, seguridad nivel empresarial, ecosistema Azure.|Dependencia de Azure, coste, limitaciones de personalización, rendimiento variable en cargas pesadas.|Apps empresaruales, web y moviles, analisis de datos, e-commerce|
|IBM Db2 on Cloud|Almacenamiento en la Nube|-------------------|-------------------------------|------------|----------------|----------------|
|Snowflake|Almacenamiento en la Nube|-------------------|-------------------------------|------------|----------------|----------------|
|ObjectDB|Especializados|-------------------|-------------------------------|------------|----------------|----------------|
|Apache HBase|Especializados|Columna ancha|Basada en Hadoop, soporte para grandes volúmenes de datos.|Escalabilidad masiva, integración nativa con Hadoop.|Complejo de configurar y operar para principiantes.|Big Data, almacenamiento masivo, sistema de archivos distribuidos.|
|Amazon Timestream|Especializados|-------------------|-------------------------------|------------|----------------|----------------|
|Realm|Especializados|Orientado a objetos|Bases de datos embebida, sincronización en tiempo real, soporte para móviles.|Ligera, rápida, sincronización en tiempo real.|Enfocada solo en plataformas móviles|Aplicaciones de móviles y en tiempo real.|
|MarkLogic|Especializados|-------------------|-------------------------------|------------|----------------|----------------|

#### **Conclusiones**
##### **Hola**

</div>