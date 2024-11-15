# Adición-de-la-clase-Pedido

* Status: accepted
* Deciders: Jesús, Icíar
* Date: 2024-11-13

## Context and Problem Statement

Necesitamos una clase pedido en la lógica de negocio para poder almacenar y acceder a los datos importantes de estos.

## Decision Drivers

* RF-04 Modulo de pedidos

## Considered Options

* Crear Una única clase Pedido

## Decision Outcome

Chosen option: "Crear Una única clase Pedido", because nos de mayor control sobre los datos y funciones de los pedidos al estar todo concentrado en una única clase.

### Positive Consequences

* Cohesión Alta: Todas las propiedades y métodos están relacionados entre sí dentro de la clase.

### Negative Consequences

* Menor flexibilidad si queremos cambiar en un futuro la lógica relacionada con los pedidos.

## Pros and Cons of the Options

### Crear Una única clase Pedido

La clase debe contar con las propiedades: Id, nombre, apellidos, email, telefono. Estos últimos para poder enviar alertas. También tiene que haber métodos para consultar sus datos, realizar pedidos, consultar sus estadísticas y consultar los repartos y rutas.

* Good, because Facilidad de Mantenimiento: Al tener todo en una única clase, no tendremos que consultar diferentes clases durante la fase de mantenimiento.
* Good, because Simplicidad de Implementación: Al estar todo en una única clase, solo tendremos que crear una clase para manejar la lógica de pedidos desde ahí.
* Bad, because Menor Escalabilidad: Es menos flexible a la hora de escalar si en un futuro queremos añadir cambios a los pedidos.
