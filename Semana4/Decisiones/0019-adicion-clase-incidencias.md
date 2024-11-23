# Adición-Clase-Incidencias

* Status: Accepted
* Deciders: Icíar, Jesús
* Date: 2024-11-21

## Context and Problem Statement

Se necesita que el sistema alerte sobre las incidencias que ocurran durante la gestión de los repartos.

## Decision Drivers

* RF-08 Gestión de Incidencias
* RF-10 Notificación de incidencias

## Considered Options

* 0019-1-Añadir-Clase-Incidencias-Con-Un-Método-Para-Notificarlas

## Decision Outcome

Chosen option: "0019-1-Añadir-Clase-Incidencias-Con-Un-Método-Para-Notificarlas", because es necesario incorporar una clase específica para gestionar las incidencias.

### Positive Consequences

* Esta clase permitiría centralizar la lógica de gestión de incidencias.
* El método que se añade a la clase permite notificar las incidencias sin aumentar significativamente la complejidad del sistema.
* Desarrollar esta clase permitiría que en el futuro se pudiese extender fácilmente para soportar nuevos tipos de incidencias o integrarse con otros sistemas.