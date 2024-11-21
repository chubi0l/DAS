# reemplazo-decisión-0009-Adicion-Modulo-Estadisticas

* Status: accepted
* Deciders: Jesus, Iciar
* Date: 2024-11-19

## Context and Problem Statement

Necesitamos un módulo de estadísticas que proporcione información valiosa sobre: el estado de los pedidos, la situación en tiempo real de los camiones y la información de clientes. Sin embargo, en la decisión "0009- Adicion-Modulo-Estadisticas" nos habíamos decantado por utilizar el patrón strategy y el equipo se ha dado cuenta de que la complejidad de utilizar el patrón no lo amerita, por lo que queremos cambiar la decisión y utilizar una única clase para este módulo.

## Decision Drivers

* RF-07 Módulo de estadísticas

## Considered Options

* 0016-1-Clase estadística única
* 0016-2-Clase estadística que seleccione el tipo de estadística con el método strategy

## Decision Outcome

Chosen option: "0016-1-Clase estadística única", because centralizar toda la lógica en una clase que se piensa que no va a modificarse a medio plazo facilita las interacciones entre componentes.

### Positive Consequences

* Centralizar la lógica en una sola clase reduce la complejidad inicial, facilita la comprensión del código y su mantenimiento a corto plazo
* Una única clase ofrece un mejor rendimiento al evitar la sobrecarga asociada con la creación y gestión de múltiples objetos

### Negative Consequences

* Una clase única podría volverse compleja y difícil de mantener si se requieren cambios en ella
* La capacidad de adaptarse a cambios futuros o integrar nuevas funcionalidades se ve limitada

## Pros and Cons of the Options

### 0016-1-Clase estadística única

En este enfoque, se tiene una única clase Estadística que contiene métodos para manejar los 3 tipos de estadísticas. Esta clase sería responsable de determinar cuál de las estadísticas debe usarse y ejecutar la lógica correspondiente.

* Good, because Es fácil de implementar
* Good, because Acceso directo a los datos y propiedades de las estadísticas
* Bad, because Escalabilidad limitada, ya que si queremos añadir más tipos de estadísticas o cambios relacionados con estas va a ser más dificil de manejar si está toda la lógica en una única clase
* Bad, because A medida que se agregan más tipos de estadísticas, la clase puede volverse más compleja y difícil de gestionar

### 0016-2-Clase estadística que seleccione el tipo de estadística con el método strategy

En este enfoque, se tiene una clase Estadística que actúa como contexto y una interfaz para los diferentes tipos de estadísticas. Cada tipo de estadística se implementa en su propia clase que sigue la interfaz de Estadística. La clase Estadística puede cambiar dinámicamente la estrategia para usar el tipo de estadística adecuado. En este enfoque creamos 3 clases que hereden de la interfaz strategy con un método llamado "seleccionarEstadistica()" y cada clase hija tendrá un método para consultar sus estadisticas. La clase base llamada "Estadística" tendrá un método llamado consultarEstadistica() y un método para seleccionar el tipo de estadística. Además de contener una propiedad de tipo Strategy

* Good, because Desacoplamiento, ya que cada clase se centra en un tipo de estadística sin preocuparse por cómo relacionarse con el resto.
* Good, because Se pueden agregar nuevas estadísticas sin modificar la clase Estadística, dotando de flexibilidad y mayor escalabilidad al módulo.
* Bad, because La implementación inicial puede requerir más esfuerzo, al tener un mayor número de clases que configurar y conectar.
