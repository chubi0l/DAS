# Adición-Del-Módulo-De-Estadísticas

* Status: accepted
* Deciders: Jesús, Icíar
* Date: 2024-11-11

## Context and Problem Statement

Necesitamos un módulo de estadísticas que proporcione información valiosa sobre: el estado de los pedidos, la situación en tiempo real de los camiones y la información de clientes.

## Decision Drivers

* RF-07 Módulo de estadísticas

## Considered Options

* Clase estadística única
* Clase estadística que seleccione el tipo de estadística con el método strategy

## Decision Outcome

Chosen option: "Clase estadística que seleccione el tipo de estadística con el método strategy", because queremos tener unidades autónomas para conseguir una arquitectura basada en microservicios.

### Positive Consequences

* La clase Estadística no necesita conocer los detalles de implementación de cada tipo de estadística, lo que reduce el acoplamiento entre las clases.
* Agregar nuevos tipos de estadísticas es sencillo.

### Negative Consequences

* El uso del patrón Strategy implica crear una clase para cada tipo de estadística, lo que puede resultar en un mayor número de archivos y clases en el proyecto.

## Pros and Cons of the Options

### Clase estadística única

En este enfoque, se tiene una única clase Estadística que contiene métodos para manejar los 3 tipos de estadísticas. Esta clase sería responsable de determinar cuál de las estadísticas debe usarse y ejecutar la lógica correspondiente.

* Good, because Es fácil de implementar
* Good, because Acceso directo a los datos y propiedades de las estadísticas
* Bad, because Escalabilidad limitada, ya que si queremos añadir más tipos de estadísticas o cambios relacionados con estas va a ser más dificil de manejar si está toda la lógica en una única clase
* Bad, because A medida que se agregan más tipos de estadísticas, la clase puede volverse más compleja y difícil de gestionar

### Clase estadística que seleccione el tipo de estadística con el método strategy

En este enfoque, se tiene una clase Estadística que actúa como contexto y una interfaz para los diferentes tipos de estadísticas. Cada tipo de estadística se implementa en su propia clase que sigue la interfaz de Estadística. La clase Estadística puede cambiar dinámicamente la estrategia para usar el tipo de estadística adecuado. En este enfoque creamos 3 clases que hereden de la interfaz strategy con un método llamado "seleccionarEstadistica()" y cada clase hija tendrá un método para consultar sus estadisticas. La clase base llamada "Estadística" tendrá un método llamado consultarEstadistica() y un método para seleccionar el tipo de estadística. Además de contener una propiedad de tipo Strategy

* Good, because Desacoplamiento, ya que cada clase se centra en un tipo de estadística sin preocuparse por cómo relacionarse con el resto.
* Good, because Se pueden agregar nuevas estadísticas sin modificar la clase Estadística, dotando de flexibilidad y mayor escalabilidad al módulo.
* Bad, because La implementación inicial puede requerir más esfuerzo, al tener un mayor número de clases que configurar y conectar.
