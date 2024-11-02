# Decisión-del-estilo

* Status: accepted
* Deciders: Jesus, Iciar
* Date: 2024-11-02

## Context and Problem Statement

En el contexto de nuestro proyecto de desarrollo software, hemos decidido adoptar un estilo por capas para permitir la creación de capas independientes que cumplan una función específica de la lógica de negocio.

## Decision Drivers

* RF-01 Arquitectura basada en microservicios
* RD-05 Acceso desde dispositivos Móviles y PC

## Considered Options

* 0002-1-Estilo-Por-Capas
* 0002-2-Arquitectura-Basada-En-Componentes
* 0002-3-Modelo-Vista-Controlador

## Decision Outcome

Chosen option: "0002-1-Estilo-Por-Capas", because el bajo acoplamiento que provoca el uso de este estilo nos ayudará a dividir la lógica de negocio en capas independientes.

### Positive Consequences

* Cada capa tiene una responsabilidad clara, lo cual facilita el mantenimiento y la actualización de componentes específicos sin afectar el sistema en su conjunto.
* Las capas permiten que cada parte del sistema pueda escalarse de manera independiente.
* La estructura de capas permite segmentar la aplicación en diferentes redes o entornos, dificultando ataques que se propaguen de una capa a otra. Esto mejora la seguridad del sistema, ya que cada capa puede tener controles de acceso y restricciones específicas.
* Cada equipo de desarrollo puede trabajar en capas específicas, evitando dependencias directas entre componentes y permitiendo que los desarrolladores se enfoquen en sus especialidades.

### Negative Consequences

* Al requerir comunicación entre capas, el rendimiento puede verse afectado
* Complejidad Incrementada al crear diferentes capas
* Cada capa requiere recursos (memoria, procesamiento), y la necesidad de comunicación entre capas incrementa el consumo general del sistema

## Pros and Cons of the Options

### 0002-1-Estilo-Por-Capas

El estilo arquitectónico por capas es un modelo de diseño de software que organiza el sistema en varias capas separadas, cada una con funciones y responsabilidades específicas. Este enfoque permite dividir la lógica de una aplicación en capas que interactúan entre sí de manera controlada y secuencial.

* Good, because Cada capa funciona como una unidad independiente, lo que facilita la adición, modificación o eliminación de capas.
* Good, because La separación de responsabilidades en diferentes capas hace que el mantenimiento sea más sencillo.
* Good, because Mejora la escalabilidad del sistema. Si la demanda aumenta se puede escalar cada capa de manera independiente.
* Good, because La separación de capas permite el aislamiento de los servidores en subredes diferentes, lo que hace más difícil realizar ataques.
* Bad, because Si una capa falla, todas las capas superiores comienzan a fallar en cascada.
* Bad, because Se aumenta la complejidad del sistema debido a la necesidad de interfaces y comunicación entre las capas.
* Bad, because Aumenta el consumo de recursos del sistema, debido a la necesidad de comunicación entre las capas.
* Bad, because Disminuye el rendimiento del sistema debido a la necesidad de comunicación entre las capas.

### 0002-2-Arquitectura-Basada-En-Componentes

Se enfoca en diseñar sistemas mediante componentes bien definidos que encapsulan funcionalidad específica. Los componentes pueden ser reutilizables y fácilmente reemplazables.

* Good, because Permite reutilizar componentes en diferentes proyectos
* Good, because Facilita la división del sistema en componentes más pequeños y manejables
* Good, because Los cambios pueden realizarse en componentes individuales sin afectar al resto del sistema, lo que reduce el riesgo de errores
* Good, because Los componentes pueden ser escalados de manera independiente según las necesidades del sistema, lo que permite un uso más eficiente de los recursos
* Good, because Diferentes equipos pueden trabajar simultáneamente en distintos componentes
* Good, because Los componentes pueden ser reemplazados o actualizados sin impactar otras partes del sistema
* Bad, because Puede ser difícil garantizar la cohesión entre los componentes y evitar dependencias no deseadas, lo que puede complicar el desarrollo y mantenimiento
* Bad, because La interconexión entre componentes puede generar dependencias complicadas

### 0002-3-Modelo-Vista-Controlador

MVC es un patrón arquitectónico que separa una aplicación en tres componentes principales:

Modelo: Gestiona los datos y la lógica de negocio. Es responsable de la recuperación, almacenamiento y manipulación de los datos y reglas de la aplicación.
Vista: Es la interfaz de usuario que representa la información visualmente. Toma los datos del modelo y los muestra al usuario de manera adecuada.
Controlador: Actúa como intermediario entre el modelo y la vista. Procesa las entradas del usuario, actualiza el modelo, y luego refleja los cambios en la vista.

* Good, because Cada componente tiene una función definida, lo que facilita el mantenimiento y la escalabilidad de la aplicación.
* Good, because Al tener el modelo, vista y controlador separados, es más sencillo probar cada componente por separado.
* Good, because Permite la creación de múltiples vistas para el mismo modelo, adaptándose a diferentes interfaces de usuario.
* Good, because Al separar la lógica de negocio y la interfaz, el modelo puede reutilizarse en diferentes contextos.
* Bad, because El controlador debe mantener sincronización entre el modelo y la vista, lo que puede ser complejo en aplicaciones más grandes.

## Links

* https://latamtech-sac.com/que-es-la-arquitectura-en-capas-descubre-sus-ventajas-y-ejemplos/
* https://reactiveprogramming.io/blog/es/estilos-arquitectonicos/capas
* https://www.linkedin.com/advice/0/what-best-ways-enhance-web-application-modularity-k1fyf?lang=es&originalSubdomain=es
* https://www.linkedin.com/advice/1/how-can-you-ensure-your-web-application-gbhje?lang=es&originalSubdomain=es
* https://keepcoding.io/blog/que-es-la-arquitectura-mvc/
