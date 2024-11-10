# Selección-Del-Tipo-De-API-Gateway

* Status: Accepted
* Deciders: Jesús, Icíar
* Date: 2024-11-08

## Context and Problem Statement

Se necesita implementar un API Gateway para gestionar el tráfico entre los clientes y los microservicios. La elección de un API Gateway adecuado es esencial para garantizar la escalabilidad, el rendimiento y la seguridad de la arquitectura basada en microservicios.

## Decision Drivers

* RF-02.1 Acceso a la lógica de negocio mediante un API Gateway

## Considered Options

* 0007-1-Kong
* 0007-2-NGINX-Plus
* 0007-3-Spring-Cloud

## Decision Outcome

Chosen option: "0007-1-Kong", because ofrece una arquitectura ligera y escalable, ideal para entornos de microservicios. Además, proporciona múltiples funciones de seguridad y rendimiento que facilitan su adaptación y extensión en un sistema distribuido.

### Positive Consequences

* Es altamente compatible con arquitecturas de microservicios, lo que simplifica la administración y el despliegue en infraestructuras modernas.
* Admite complementos que facilitan la personalización y mejora de sus capacidades, incluyendo almacenamiento en caché y transformaciones, lo que permite una mayor flexibilidad en el manejo del tráfico.

### Negative Consequences

* La configuración y el mantenimiento de Kong pueden ser complejos en entornos grandes o altamente personalizados, lo que puede requerir un equipo con experiencia técnica.
* Kong tiende a consumir bastantes recursos del sistema, lo cual puede ser un desafío en entornos con recursos limitados.

## Pros and Cons of the Options

### 0007-1-Kong

Kong, creado por Kong Inc., es un API Gateway de código abierto optimizado para microservicios, con un diseño de proxy ligero que minimiza la latencia y permite escalar en diversos entornos.

* Good, because se integra fácilmente en arquitecturas de microservicios desplegadas en contenedores.
* Good, because escala horizontalmente con gran facilidad, manejando más tráfico y servicios sin perder rendimiento.
* Good, because ofrece varias funciones de seguridad, que incluyen autenticación, autorización, limitación de velocidad y validación de solicitudes.
* Good, because admite una amplia gama de complementos para registro, almacenamiento en caché, limitación de velocidad y transformación, permitiendo mejorar sus capacidades.
* Good, because distribuye el tráfico de manera uniforme entre instancias de backend, lo que mejora la redundancia y la disponibilidad.
* Bad, because puede ser complejo de configurar y mantener, especialmente en entornos grandes o con muchas personalizaciones.
* Bad, because puede consumir bastantes recursos del sistema.
* Bad, because la curva de aprendizaje es lenta.

### 0007-2-NGINX-Plus

NGINX Plus fue desarrollado como una versión comercial de NGINX, con avances orientados a optimizar el rendimiento de aplicaciones modernas. Este API Gateway está diseñado para arquitecturas de microservicios.

* Good, because es capaz de manejar miles de conexiones concurrentes con un uso mínimo de recursos.
* Good, because ofrece balanceo de carga avanzado y distribución de tráfico eficiente.
* Good, because proporciona métricas en tiempo real y herramientas de diagnóstico que facilitan la optimización del rendimiento.
* Good, because  permite enrutamiento basado en contenido y configuraciones avanzadas para adaptarse a diferentes necesidades.
* Good, because incluye autenticación, filtrado de solicitudes y protección contra ataques DDoS.
* Bad, because no maneja directamente el contenido dinámico, lo que obliga a integrarlo con otros servidores de aplicaciones.
* Bad, because no es tan compatible con aplicaciones web que usen contenido dinámico.
* Bad, because configurarlo y mantenerlo puede ser complejo y requiere un equipo con experiencia técnica.

### 0007-3-Spring-Cloud

Spring Cloud Gateway es una plataforma de enrutamiento y control de acceso basada en Spring Boot. Se utiliza para implementar servicios de Gateway en la arquitectura de microservicios.

* Good, because tiene capacidad de enrutamiento dinámico.
* Good, because puede manejar el tráfico de manera reactiva, optimizando el rendimiento y la disponibilidad.
* Good, because puede integrarse con otras herramientas de seguridad, permitiendo una autenticación y autorización segura en las aplicaciones.
* Good, because incluye compatibilidad con circuit breakers para manejar errores y caídas de servicios.
* Good, because puede escalar horizontalmente de forma fácil, permitiendo adaptarse a las variaciones de tráfico y carga.
* Bad, because bajo cargas muy altas, puede no ser tan eficiente como otros gateways más ligeros.
* Bad, because su configuración puede ser compleja, especialmente en aplicaciones de gran escala.
* Bad, because se integra principalmente con el ecosistema de Spring, lo que puede complicar la conexión con herramientas externas.

## Links

* https://jsour.medium.com/what-the-advantages-of-kong-gateway-8e2b5451b191
* https://es.linkedin.com/pulse/qu%C3%A9-es-kong-gateway-ithreexglobal
* https://www.f5.com/go/product/welcome-to-nginx
* https://www.hostinet.com/formacion/vps-servidores/nginx-que-es-y-como-funciona/
* https://docs.spring.io/spring-cloud-gateway/reference/spring-cloud-gateway/developer-guide.html
* http://developinginspanish.com/2022/12/08/introduccion-a-spring-cloud-gateway/