# GesReferee

## Miembros del grupo L8-AM-G6

1. Bardín Díaz, Simón
2. Fernández Vallejo, Rubén
3. Braulio Reyes, Abel


## 1. Introducción al problema

El comité de árbitros de baloncesto organiza el arbitraje de partidos de distintas categorías (Senior, Junior, Cadete, Infantil, Mini), géneros (masculino, femenino, mixto) y competiciones (A, B, C). Cada partido necesita un equipo arbitral compuesto por varios árbitros con diferentes cargos (principal, auxiliar, mesa). 
Como clientes estarán nuestros árbitros a quienes designaremos y por supuesto pagaremos, además tendremos como usuarios administradores a todos los designadores que contamos en nuestro equipo de administración en el comité.
La situación actual la podemos explicar brevemente, las designaciones, los resultados, las incidencias y los pagos se gestionan mediante hojas de cálculo, mensajes por correo electrónico o telegram e incluso por papel en los peores casos. Mediante hojas de cálculo los designadores organizan la jornada y posteriormente son enviadas por correo electrónico y telegram. Tras el fin de la jornada cada árbitro principal debe enviar el resultado por correo adjuntando si lo hubiera las incidencias.	Esta situación nos genera solapamiento o huecos sin cubrir en las designaciones, dificultad para que cada árbitro consulte sus partidos, errores en el cálculo de contabilidad de cada árbitro e incidencias que se quedaban sin solventar.
Las expectativas son de centralizar en una aplicación la gestión de árbitros, partidos, designaciones, incidencias y contabilidad, con acceso diferenciado según tu rol, árbitro o designador.


## 2. Glosario de términos

Árbitro auxiliar: Miembro del equipo arbitral que asiste durante el desarrollo del encuentro.
                                      
Árbitro principal: Máxima autoridad del equipo arbitral en un partido y único responsable autorizado para registrar el resultado final.




Cargo: Rol específico que asume un árbitro (Principal, Auxiliar u Oficial de mesa).

Categoría: Clasificación de los partidos (Senior, Junior, Cadete, Infantil y Mini).
      

Comité de árbitros: Entidad organizadora encargada de gestionar el arbitraje.

         
Designación / Asignación: Asignación formal de un árbitro a un partido específico.

Disponibilidad: Franjas horarias y fechas en las que un árbitro puede ser designado.

Equipo arbitral: Conjunto de árbitros asignados a un mismo partido.

Honorario (o Precio): Importe económico fijado por el administrador al crear un partido.

Incidencia: Registro formal de cualquier suceso destacable durante un encuentro.

Oficial de mesa: Miembro del equipo arbitral encargado de las labores de control (acta, tiempos).
        
Partido suspendido: Estado de un encuentro que ha sido cancelado o interrumpido.

## 3. Visión general del sistema

### 3.1. Requisitos generales

### 3.2. Usuarios del sistema

## 4. Catálogo de requisitos

### 4.1. Requisitos funcionales

#### R.F.01. Título requisito funcional

Como [tipo de usuario]
quiero [servicio]
para [razón]

**Prueba de aceptación**
- Descripción de la primera comprobación a realizar
- Descripción de la segunda comprobación a realizar
- Se debe aplicar la regla de negocio R.N.XX.
- ...

#### 4.1.1. Requisitos de información

##### R.I.01. Título requisito de información

Como [tipo de usuario]
quiero [servicio]
para [razón]

**Prueba de aceptación**
- Descripción de la primera comprobación a realizar
- Descripción de la segunda comprobación a realizar
- ...

#### 4.1.2. Reglas de negocio

##### R.N.01. Título regla negocio

Descripción de la regla de negocio.

### 4.2. Mapa de historias de usuario (opcional)

### 4.3. Requisitos no funcionales (opcional)

**R.N.F. 01. Título requisito no funcional**
Como [tipo de usuario]
quiero [servicio]
para [razón]

-- fin entregable 1 --

## 5. Modelo conceptual

### 5.1. Diagramas de clases UML

- con restricciones.

### 5.2. Escenarios de prueba

- con descripción textual y diagrama de objetos UML.

## 6. Matrices de trazabilidad

- Matriz de trazabilidad entre los elementos del modelo conceptual y los requisitos.

|       | EntidadX   | AsociaciónX  | RestricciónX  | Entidad2 ...   | 
|:------|:-----------|:-----------|:-----------|:-----------|
| RI-1  | X          | X          | X          | X          |
| RI-2  |            | X          |            | X          |
| RF-1  |            | X          |            | X          |
| RF-2  | X          |            | X          | X          |
| RN-1  |            | X          |            |            |
| RN-2  | X          | X          | X          |            |
| ...   |            |            |            |            |

-- fin entregable 2 --

## 7. Modelo relacional en 3FN

- Relaciones obtenidas al aplicar la transformación del modelo conceptual.

### 7.1.  Justificación de la estrategia de transformación de jerarquías

- si se identificaron jerarquías en el MC.


### 8. Matriz de trazabilidad MC/SQL (opcional):

- Restricciones sobre el MC / Elementos del modelo tecnológico (SQL) (Triggers, checks, etc.)
- Incluir Reglas de negocio — Constraints/Triggers en las matrices de trazabilidad para el entregable 3

|       | EntidadX   | AsociaciónX  | RestricciónX  | Entidad2 ...   | 
|:-------|:-------|:-------|:-------|:-------|
| TABLA-1 |        |        |        |        |
| TABLA-2 |        |        |        |        |
| TABLA-3 |        |        |        |        |
| TABLA-4 |        |        |        |        |
| TRIG-1 |        |        |        |        |
| TRIG-2 | X      | X      |        | X      |
| TRIG-3 |        | X      |        | X      |
| TRIG-4 |        |        | X      |        |
| CONST-1 |        |        |        |        |
| CONST-2 | X      | X      |        | X      |
| CONST-3 |        | X      |        | X      |
| CONST-4 |        |        | X      |        |

Se consideran todo tipo de constraints declarativas (aquellas definidas durante el CREATE TABLE).
-- fin entregable 3 --

## Referencias


