# Adición-De-la-clase-Cliente

* Status: accepted
* Deciders: Jesús, Icíar
* Date: 2024-11-13

## Context and Problem Statement

Necesitamos una clase Cliente en la lógica de negocio para poder almacenar y acceder a los datos importantes de estos.

## Decision Drivers

* RF-03 Módulo de Clientes

## Considered Options

* 0010-1- Crear clase Cliente

## Decision Outcome

Chosen option: "0010-1- Crear clase Cliente", because centraliza la lógica y las propiedades de los clientes en un solo lugar.

### Positive Consequences

* Simplicidad de implementación, al tener que configurar únicamente una clase. 
* Acceso directo a funcionalidades, al tener disponible solo una clase para consultar. 

### Negative Consequences

* Menor escalabilidad, al ser una estructura rígida.

## Pros and Cons of the Options

### 0010-1- Crear clase Cliente

La clase debe contar con las propiedades: Id, nombre, apellidos, email y teléfono. Estos últimos campos son necesarios para poder enviar alertas. También tiene que haber métodos para consultar sus datos, realizar pedidos, consultar sus estadísticas y consultar los repartos y rutas.

* Good, because Facilidad de mantenimiento, al encontrarse toda la lógica en una única clase.
* Good, because Simplicidad de implementación, al estar toda la información en una única clase.
* Bad, because Menor escalabilidad, ya que si queremos agregar cambios o modificar la lógica relacionada con el cliente, puede ser complicado al condensar toda la información en una única clase.