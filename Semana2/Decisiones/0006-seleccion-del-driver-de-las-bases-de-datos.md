# Selección-Del-Driver-De-Las-Bases-De-Datos

* Status: Accepted
* Deciders: Jesús, Icíar
* Date: 2024-11-08

## Context and Problem Statement

La capa de acceso a datos contiene dos bases de datos SQL: una para gestionar los datos de pedidos (identificador único, productos, precio total, fecha de creación, dirección de entrega y estado del pedido) y otra para los datos de clientes (identificador, nombre y apellidos, dirección, correo electrónico y número de teléfono). Se necesita un driver que permita la conexión eficiente y segura entre la lógica de negocio y ambas bases de datos.

## Decision Drivers

* RF-05 Acceso a los datos almacenados
* RD-01 Bases de datos SQL

## Considered Options

* 0006-1-MySQL
* 0006-2-MariaDB
* 0006-3-PostgreSQL

## Decision Outcome

Chosen option: "0004-1-MySQL", because su arquitectura cliente-servidor y su enfoque en la disponibilidad permiten gestionar las dos bases de datos de manera confiable, asegurando un rendimiento estable. Además, ofrece herramientas para mantener la base de datos accesible incluso ante fallos, lo cual es crucial para el sistema de pedidos.

### Positive Consequences

* Ofrece una arquitectura que facilita el escalado en la capa de acceso a datos, permitiendo soportar mayores volúmenes de usuarios.
* Su alta adopción en la industria proporciona acceso a recursos y soporte técnico extensivo.

### Negative Consequences

* El modelo cliente-servidor de MySQL puede incrementar la carga del servidor, especialmente en aplicaciones de alta concurrencia.
* Puede carecer de algunas características avanzadas de bases de datos, como el soporte completo para JSON o capacidades de replicación compleja.

## Pros and Cons of the Options

### 0006-1-MySQL

MySQL es un sistema de gestión de bases de datos relacionales de código abierto con un modelo cliente-servidor. Está desarrollado bajo licencia dual: Licencia pública general/Licencia comercial por Oracle Corporation.

* Good, because proporciona herramientas y características que permiten manejar grandes volúmenes de datos.
* Good, because garantiza una alta disponibilidad de la base de datos y minimiza el riesgo de pérdida de datos.
* Good, because la velocidad de procesamiento es alta.
* Good, because ha sido ampliamente adoptado por la comunidad y la industria, por lo que ofrece abundante documentación, recursos y soporte.
* Good, because al haber sido probado en producción durante muchos años es una opción confiable.
* Bad, because no incluye algunas funcionalidades avanzadas específicas.
* Bad, because debido a su estructura de desarrollo puede tardar más en implementar nuevas características y mejoras.
* Bad, because no es tan rápido como otros administradores de bases de datos.
* Bad, because es difícil de escalar.

### 0006-2-MariaDB

MariaDB Server es una popular base de datos relacional de código abierto, creada por los desarrolladores de MySQL. Se centra en el alto rendimiento, la estabilidad y la transparencia.

* Good, because permite replicación sincrónica y asincrónica, y soporta clústeres distribuidos (Galera Cluster) para alta disponibilidad.
* Good, because ofrece agrupación de hilos, permitiendo soportar hasta 200000 conexiones, mejorando la estabilidad y el rendimiento del sistema.
* Good, because es totalmente libre, con una comunidad activa que mejora constantemente el software.
* Good, because es compatible con MySQL, lo que facilita la migración desde MySQL sin problemas de compatibilidad.
* Good, because  al ser gratuito, es una opción económica y adaptable a diferentes necesidades.
* Bad, because aunque existen versiones comerciales, MariaDB no ofrece el mismo nivel de soporte empresarial que otros sistemas.
* Bad, because en ciertos entornos de gran escala, su rendimiento puede ser inferior al de otras bases de datos.
* Bad, because no está tan optimizado para escalado automático en la nube.
* Bad, because sólo soporta tipos de datos JSON a partir de la versión 10.2.

### 0006-3-PostgreSQL

PostgreSQL es un sistema de gestión de bases de datos relacional de objetos y de código abierto, reconocido por su fiabilidad y robustez en sus características.

* Good, because  es completamente gratuito y de código abierto, lo que permite una amplia personalización.
* Good, because soporta JSON, vistas materializadas, consultas paralelas, tipos de datos personalizados y extensibilidad con PL/pgSQL.
* Good, because  ofrece replicación, sharding y escalabilidad horizontal, siendo adecuado para manejar cargas de trabajo intensivas.
* Good, because implementa el estándar ISO/IEC 9075:2011, facilitando consultas e integración con otros motores de bases de datos.
* Good, because tiene capacidad para crear un entorno de alta disponibilidad.
* Bad, because no es ideal para aplicaciones con altas tasas de inserción frente a bases de datos optimizadas para escritura.
* Bad, because su versión de código abierto no ofrece una estructura de soporte empresarial formal.
* Bad, because puede ser más complejo de administrar que otras bases de datos.
* Bad, because requiere un mayor esfuerzo en la optimización de rendimiento.

## Links

* https://cloud.google.com/mysql?hl=es
* https://oxygenacademy.es/mongo-db-vs-mysql-diferencias-ventajas-y-desventajas/#Desventajas
* https://www.dongee.com/tutoriales/mysql-caracteristicas-ventajas-y-desventajas/
* https://aldeahost.com.mx/que-es-mysql-ventajas-y-desventajas/
* https://mariadb.org/
* https://mariadb.com/kb/en/
* https://github.com/MariaDB
* https://www.postgresql.org/docs/
* https://www.hostinger.es/tutoriales/mariadb-vs-mysql
* https://www.todopostgresql.com/ventajas-y-desventajas-de-postgresql/