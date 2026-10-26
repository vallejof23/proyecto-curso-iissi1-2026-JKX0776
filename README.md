![Uploading fig_5_1_diagrama_clases.png…]()
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

Necesitamos de un sistema que cumpla con los siguiente requisitos establecidos:
Aplicación con autenticación y control de acceso por rol.
Gestión de árbitros, partidos, designaciones, resultados, incidencias y contabilidad.
Consulta de partidos con filtros por categoría, género, competición.


### 3.2. Usuarios del sistema

Los usuarios del sistema serán los siguientes:
Administrador: Gestor del comité, se encargará de gestionar usuarios, árbitros, partidos, designaciones y consultar toda la contabilidad.
Árbitro: Usuario con acceso al sistema, podrá consultar sus partidos, registrar resultado e incidencias de sus partidos, consultar su contabilidad.

## 4. Catálogo de requisitos

### 4.1. Requisitos funcionales

#### R.F.01. Filtrar Partidos
Como usuario quiero filtrar los partidos por categoría, género, competición, jornada y fecha, y ver cuántos árbitros tiene designados cada uno, para encontrar rápidamente los que me interesan.
Cada filtro, solo o combinado, devuelve únicamente los partidos que cumplen todas las condiciones.
Se muestra el número de árbitros designados de cada partido, incluidos los que no tienen ninguno.
Sin resultados se muestra un mensaje informativo.
Se debe aplicar la regla de negocio R.N.05.

#### R.F.02. Consultar Partidos con Equipo Arbitral Incompleto
Como administrador quiero consultar los partidos no suspendidos que todavía no tienen cubiertos los tres cargos (principal, auxiliar y mesa), indicando cuántos cargos les faltan, para saber en qué partidos tengo que designar árbitros.
Un partido sin ninguna designación aparece con 3 cargos pendientes.
Un partido con los tres cargos cubiertos no aparece.
Se debe aplicar la regla de negocio R.N.06 y R.N.15.

#### R.F.03. Consultar Árbitros Candidatos para un Partido
Como administrador quiero consultar los árbitros que se pueden designar en un partido concreto para elegir a quién designar sin incumplir las reglas de negocio.
Solo aparecen los árbitros que no están de baja, que no están ya designados en ese partido, que no tienen otro partido que se solape con él y que no han indicado que no están disponibles en esa franja.
Un árbitro que no ha indicado nada se considera disponible.
Se debe aplicar la regla de negocio R.N.06, R.N.07, R.N.14 y R.N.20.

#### R.F.04. Consultar mis Partidos
Como árbitro quiero consultar los partidos que tengo asignados, con mi cargo, mis observaciones y el resultado si ya se ha registrado, para organizar mi agenda.
Se listan sólo los partidos donde el árbitro tiene designación.
Se muestran fecha, lugar, equipos, cargo, observaciones y resultado (si lo tiene).
Los partidos suspendidos aparecen marcados como suspendidos.
Se debe aplicar la regla de negocio R.N.13 y R.N.15.

#### R.F.05. Consultar Partidos Pendientes de Resultado
Como administrador quiero consultar los partidos que ya han comenzado, no están suspendidos y todavía no tienen resultado, junto con su árbitro principal, para reclamar los resultados que faltan.
Si el partido no tiene principal designado aparece igualmente.
Se debe aplicar la regla de negocio R.N.09 y R.N.15.

#### R.F.06. Consultar Incidencias
Como administrador quiero consultar las incidencias de los partidos para hacer seguimiento y tomar decisiones.
Se listan las incidencias con partido, fecha, árbitro que la registró y descripción.
Se puede filtrar por partido, categoría y fecha, y buscar un texto en la descripción.
Se muestran de la más reciente a la más antigua.
Se debe aplicar la regla de negocio R.N.10.

#### R.F.07. Consultar Árbitros con Mayor Carga de Designaciones
Como administrador quiero consultar qué árbitro o árbitros tienen más designaciones en un periodo para repartir la carga de trabajo de forma equilibrada.
Sólo cuentan los partidos no suspendidos del periodo indicado.
Si varios árbitros empatan con el máximo, se muestran todos.
Se debe aplicar la regla de negocio R.N.15.

#### R.F.08. Consultar Agenda de un Árbitro
Como administrador quiero consultar en una única lista, ordenada por fecha y hora, los partidos designados y las franjas en las que no está disponible un árbitro, para ver sus compromisos antes de designarle.
Los partidos suspendidos no aparecen.
Un árbitro sólo puede consultar su propia agenda.
Se debe aplicar la regla de negocio R.N.07 y R.N.13.

#### R.F.09. Consultar Árbitros Polivalentes
Como administrador quiero consultar los árbitros que han sido designados alguna vez como principal, como auxiliar y como oficial de mesa para identificar a los que pueden cubrir cualquier vacante del equipo arbitral.
Un árbitro al que le falta alguno de los tres cargos no aparece.
No aparecen los árbitros de baja.
Se debe aplicar la regla de negocio R.N.06 y R.N.14.

#### R.F.10. Consultar Gasto del Comité por Categoría
Como administrador quiero consultar, por categoría y en un periodo, el número de partidos contabilizados, el gasto total y los honorarios mínimo, máximo y medio, mostrando solo las categorías cuyo gasto supera un presupuesto indicado, para controlar los costes del comité.
Sólo cuentan los partidos con resultado y no suspendidos del periodo indicado.
El gasto de una categoría es la suma de los honorarios de todos los árbitros designados en sus partidos.
Las categorías se muestran de mayor a menor gasto.
Se debe aplicar la regla de negocio R.N.11, R.N.12 y R.N.15.

#### R.F.11. Consultar Contabilidad
Como árbitro quiero consultar mi salario acumulado y el desglose de partidos para conocer lo que se me debe.
Se muestra el salario y la lista de partidos que lo componen.
Los partidos suspendidos no suman.
Un árbitro solo ve su propia contabilidad.
Se debe aplicar la regla de negocio R.N.12, R.N.13 y R.N.15.

#### R.F.12. Consultar Contabilidad General
Como administrador quiero consultar la contabilidad de todos los árbitros para controlar los pagos del comité.
Se muestra el salario por árbitro y el total general.
Se puede filtrar por árbitro y por rango de fechas.
La suma de totales individuales coincide con el total general.

#### R.F.13. Gestionar mi Disponibilidad
Como árbitro quiero indicar mi disponibilidad por fecha y franja horaria para que el comité no me designe cuando no pueda arbitrar.
Se puede crear una disponibilidad con fecha, hora de inicio, hora de fin, disponible (sí/no) y observaciones opcionales.
La hora de fin debe ser posterior a la de inicio.
Un árbitro puede modificar o eliminar sus disponibilidades, y sólo las suyas.
Se debe aplicar la regla de negocio R.N.13 y R.N.19.

#### R.F.14. Consultar Disponibilidad de los Árbitros
Como administrador quiero consultar la disponibilidad de los árbitros para elegir a quién designar en cada partido.
Se puede filtrar por fecha y franja horaria y ver que árbitros están disponibles.
Los árbitros con otra designación en esa franja aparecen como no disponibles.
Se debe aplicar la regla de negocio R.N.07 y R.N.13.

#### R.F.15. Consultar Pedidos de los Árbitros
Como administrador quiero consultar los pedidos de los árbitros para saber quién a pedido ropa y cual. 
Se puede filtrar por tipo de prenda.


### 4.1.1. Requisitos de información

#### R.I.01. Información de usuario
Como administrador quiero almacenar los datos de acceso de cada usuario para autenticarlos.
Se almacenan email (único) y contraseña (cifrada).
Un usuario es Admin o Árbitro; el Admin tiene un atributo rol.

#### R.I.02. Información de árbitro
Como administrador quiero almacenar los datos personales y de contacto de cada árbitro para gestionarlo.
Se almacenan nombre completo, DNI (único), ciudad y número de teléfono.
Cada árbitro está asociado a un único usuario.

#### R.I.03. Información de partido
Como administrador quiero almacenar los datos de cada partido para planificarlo y arbitrarlo.
Se almacenan: identificador, categoría, género, competición, jornada, lugar, fecha (y hora), equipo local, equipo visitante, suspendido (sí/no) y precio.
El resultado se almacena aparte (R.I.08) y no existe hasta que se juega el partido.
Suspendido es falso por defecto.

#### R.I.04. Información de asignación
Como administrador quiero almacenar la designación de un árbitro en un partido para saber quién arbitra y con qué función.
Se almacenan el árbitro, el partido, el cargo y las observaciones (opcionales).
Un partido puede tener varias designaciones y un árbitro varias.
La pareja árbitro–partido es única.

#### R.I.05. Información de incidencia
Como árbitro quiero almacenar la descripción de una incidencia para dejar constancia de lo ocurrido.
Se almacenan la descripción y el partido al que pertenece.
Se recomienda almacenar también fecha de registro y autor.

#### R.I.06. Información de contabilidad
Como administrador quiero almacenar el salario (derivado) de cada árbitro para controlar los pagos.
Cada árbitro tiene una contabilidad con su salario (/salario).
El salario es un atributo derivado y se calcula a partir de los partidos no suspendidos en que ha sido designado.

#### R.I.07. Información de valores enumerados
Como administrador quiero que ciertos campos tomen valores cerrados para evitar datos incoherentes.
Categoría: Senior, Junior, Cadete, Infantil, Mini.
Competición: A, B, C.
Género: Masculino, Femenino, Mixto.
Cargo: Principal, Auxiliar, Mesa.

#### R.I.08. Información de resultado
Como árbitro quiero almacenar el resultado de un partido para dejar constancia de su marcador.
Se almacenan los puntos de local y los puntos de visitante.
Cada resultado pertenece a un único partido y un partido tiene como máximo un resultado.

#### R.I.09. Información de disponibilidad
Como árbitro quiero almacenar mis franjas de disponibilidad para que el comité las tenga en cuenta al designar.
Se almacenan fecha, hora de inicio, hora de fin, disponible (sí/no) y observaciones (opcional).
Cada disponibilidad pertenece a un único árbitro y un árbitro puede tener varias.


### 4.1.2. Reglas de negocio

### R.N.01. Email único.
 Como administrador, quiero que cada usuario tenga un email único, aportado por él mismo y no asignado por el comité, para identificar sin confusión a cada persona al iniciar sesión.
Prueba: no se puede crear un usuario con un email ya registrado.
Prueba: se rechaza un email con formato incorrecto (por ejemplo, sin @).

### R.N.02. Contraseña segura.
 Como administrador, quiero que la contraseña tenga al menos 8 caracteres y que nunca se guarde tal cual la escribe el usuario, sino de forma protegida, para que nadie pueda verla ni siquiera si accede a la base de datos.
Prueba: una contraseña de menos de 8 caracteres se rechaza.
Prueba: al consultar los datos de un usuario, la contraseña no aparece de forma legible.

### R.N.03. Gestión de usuarios.
 Como administrador, quiero ser quien cree y dé de baja a los usuarios y quien modifique su DNI, nombre completo y ciudad, mientras que cada árbitro solo pueda modificar su contraseña, teléfono y email, para que el comité controle quién accede al sistema y nadie pueda alterar su identidad ni descuadrar los pagos.
Prueba: un árbitro que intenta crear o dar de baja a un usuario recibe un error de permisos.
Prueba: un árbitro puede cambiar su contraseña, su teléfono y su email.
Prueba: un árbitro que intenta cambiar su DNI, nombre o ciudad recibe un error de permisos.
Prueba: un árbitro no puede poner un email que ya pertenece a otro usuario.

### R.N.04. DNI único y válido.
 Como administrador, quiero que el DNI de un árbitro sea único, con 8 dígitos y letra de control correcta, para evitar duplicados que afecten a los pagos.
Prueba: se rechaza un DNI que ya está registrado en otro árbitro.
Prueba: se rechaza un DNI con más o menos de 8 dígitos.
Prueba: se rechaza un DNI cuya letra no corresponde a sus números.
Prueba: un DNI correcto y no repetido se acepta.

### R.N.05. Partidos válidos.
 Como administrador, quiero que todo partido tenga fecha y hora, lugar, jornada, equipo local, equipo visitante, categoría (Senior, Junior, Cadete, Infantil, Mini), género (masculino, femenino, mixto) y competición (A, B, C), que los dos equipos sean distintos y que no haya dos partidos en el mismo lugar con horarios solapados (se estima una duración de 2 horas), sea cual sea su categoría o género, para poder filtrar, designar y pagar sin conflictos de instalaciones.
Prueba: no se puede crear un partido sin alguno de esos datos.
Prueba: se rechaza un partido cuyo equipo local y visitante son el mismo.
Prueba: se rechaza un partido en el mismo lugar, fecha y hora que otro.
Prueba: se rechaza un partido en el mismo lugar que empiece dentro de las 2 horas de otro (por ejemplo, 10:00 y 11:00).
Prueba: se acepta un partido en el mismo lugar que empiece cuando el anterior ya ha terminado (10:00 y 12:00).
Prueba: se acepta un partido a la misma fecha y hora en un lugar distinto.

### R.N.06. Composición del equipo arbitral.
 Como administrador, quiero que un partido solo se considere completo cuando tenga un árbitro principal, un auxiliar y un oficial de mesa, y que cada árbitro tenga un único cargo en el mismo partido, para evitar partidos sin cubrir y que nadie figure con dos cargos y cobre dos veces.
Prueba: un partido con principal y auxiliar pero sin mesa aparece como “incompleto”.
Prueba: un partido con los tres cargos cubiertos aparece como “completo”.
Prueba: se rechaza asignar un segundo cargo al mismo árbitro en el mismo partido.
Prueba: se rechaza designar un segundo árbitro con un cargo ya cubierto en ese partido.

### R.N.07. Sin solapamientos y respeto de la disponibilidad.
 Como administrador, quiero que un árbitro no pueda ser designado en dos partidos cuyos horarios se solapen (se estima una duración de 2 horas más 30 minutos de margen de desplazamiento) ni en una franja en la que haya indicado que no está disponible, para evitar los solapamientos de las hojas de cálculo y no designar a quien no puede acudir. Si el árbitro no ha indicado nada, se le considera disponible.
Prueba: con un partido a las 10:00, se rechaza designarlo a las 11:00 y a las 12:15.
Prueba: con un partido a las 10:00, se acepta designarlo a las 12:30.
Prueba: se rechaza designar a un árbitro en una franja marcada como no disponible.
Prueba: se acepta designar a un árbitro que no ha registrado ninguna disponibilidad.

### R.N.08. Designaciones solo por el administrador.
 Como administrador, quiero ser el único que cree, modifique o anule designaciones, mientras que los árbitros solo las consultan, para mantener un criterio único.
Prueba: un árbitro que intenta crear, modificar o anular una designación recibe un error de permisos.
Prueba: el administrador puede crear, modificar y anular designaciones.

### R.N.09. Registro del resultado.
 Como administrador, quiero que solo el árbitro principal designado en un partido registre su resultado, una única vez, después de la hora de inicio y solo si el partido no está suspendido, y que solo yo pueda corregirlo, para tener un origen fiable del resultado.
Prueba: un auxiliar o un oficial de mesa no puede registrar el resultado.
Prueba: el principal no puede registrarlo antes de la hora de inicio ni por segunda vez.
Prueba: no se puede registrar el resultado de un partido suspendido ni con puntos negativos.
Prueba: el principal puede registrarlo una vez iniciado el partido, y solo el administrador puede corregirlo después.

### R.N.10. Incidencias.
 Como administrador, quiero que las incidencias de un partido solo las registren los árbitros designados en él, con una descripción obligatoria y un máximo de una incidencia por partido, para que todo lo ocurrido quede centralizado y el comité pueda revisarlo.
Prueba: un árbitro no designado en el partido no puede registrar una incidencia.
Prueba: se rechaza una incidencia sin descripción.
Prueba: se rechaza una segunda incidencia en un partido que ya tiene una.
Prueba: un árbitro designado puede registrar la incidencia de su partido.

### R.N.11. Precio del partido.
 Como administrador, quiero que cada partido tenga un precio fijado por mí al crearlo, no negativo, y que ese precio sea el honorario de cada árbitro designado en él, para que el pago no dependa de cálculos manuales.
Prueba: no se puede crear un partido sin precio.
Prueba: se rechaza un precio negativo.
Prueba: un árbitro designado ve el precio de su partido.

### R.N.12. Salario del árbitro.
 Como administrador, quiero que el salario de cada árbitro se calcule automáticamente como la suma de los precios de los partidos que ha arbitrado y que ya tienen resultado, sin contar los suspendidos, y que no se pueda escribir a mano, para evitar errores de cálculo.
Prueba: un árbitro con dos partidos con resultado, de 30 € y 40 €, tiene un salario de 70 €.
Prueba: un partido sin resultado no suma al salario.
Prueba: un partido suspendido no suma al salario.
Prueba: nadie puede modificar el salario manualmente.

### R.N.13. Visibilidad de datos.
 Como árbitro, quiero ver y gestionar solo mis propios datos (partidos, disponibilidad y contabilidad), mientras que el administrador accede a todo, para proteger la privacidad económica y personal.
Prueba: al consultar la contabilidad de otro árbitro, el sistema deniega el acceso.
Prueba: un árbitro no puede modificar la disponibilidad de otro árbitro.
Prueba: el administrador puede consultar los datos de todos los árbitros.

### R.N.14. Baja lógica.
 Como administrador, quiero que la baja de un usuario no borre sus datos, que el usuario de baja no pueda iniciar sesión y que no se pueda dar de baja a un árbitro con designaciones futuras sin reasignarlas antes, para conservar el historial y no dejar partidos huérfanos.
Prueba: tras dar de baja a un árbitro, sus partidos y su contabilidad siguen consultables por el administrador.
Prueba: un usuario de baja no puede iniciar sesión.
Prueba: dar de baja a un árbitro con un partido futuro se rechaza hasta reasignarlo.

### R.N.15. Partidos suspendidos.
 Como administrador, quiero poder marcar un partido como suspendido, de modo que no admita resultado ni cuente para el salario, aunque conserve sus designaciones por si se reprograma, para no pagar partidos que no se han jugado.
Prueba: solo el administrador puede marcar un partido como suspendido.
Prueba: un partido suspendido rechaza el registro de resultado.
Prueba: un partido suspendido no suma al salario de los árbitros.
Prueba: el árbitro sigue viendo el partido en su lista, marcado como suspendido.

### R.N.16. Precio inalterable tras contabilizar el partido.
 Como administrador, quiero que no se pueda cambiar el precio de un partido que ya tiene resultado, para que el salario de los árbitros no cambie con efecto retroactivo.
Prueba: se rechaza modificar el precio de un partido con resultado.

### R.N.17. Designaciones inalterables tras contabilizar el partido.
 Como administrador, quiero que no se pueda modificar ni eliminar una designación de un partido que ya tiene resultado, para conservar el historial de quién arbitró cada partido y no descuadrar los pagos.
Prueba: se rechaza cambiar el cargo o eliminar una designación de un partido con resultado.

### R.N.18. Suspender un partido anula su resultado.
 Como administrador, quiero que al marcar un partido como suspendido se elimine su resultado si lo tenía, para que un partido que no se ha jugado no conserve marcador ni cuente para el salario.
Prueba: al suspender un partido con resultado, el resultado se elimina.

### R.N.19. Disponibilidades sin solapamiento.
 Como árbitro, quiero que mis franjas de disponibilidad de un mismo día no se puedan solapar entre sí, para no constar a la vez como disponible y como no disponible.
Prueba: se rechaza crear una franja que se solape con otra del mismo árbitro y la misma fecha.

### R.N.20. Árbitros de baja no designables.
 Como administrador, quiero que no se pueda designar a un árbitro de baja, para no asignar partidos a quien ya no puede acceder al sistema.
Prueba: se rechaza designar a un árbitro cuyo usuario está de baja.

### R.N.21. Incidencias solo desde el inicio del partido.
 Como administrador, quiero que una incidencia solo se pueda registrar a partir de la hora de inicio del partido, para que recoja sucesos del encuentro y no previsiones.
Prueba: se rechaza registrar una incidencia en un partido que todavía no ha empezado.


### 4.2. Requisitos no funcionales

### R.N.F.01. Seguridad de acceso
 Como administrador, quiero que el acceso al sistema sea solo con email y contraseña, que la sesión se cierre tras 30 minutos de inactividad, que la cuenta se bloquee temporalmente tras 5 intentos fallidos y que cada acción se compruebe según el rol en el servidor, y no solo ocultando botones, para que nadie acceda a datos que no le corresponden.

### R.N.F.02. Protección de datos personales
 Como administrador, quiero que los datos personales (DNI, email y teléfono) se traten conforme a las leyes del Reglamento General de Protección de Datos y solo los vea quien los necesite, para cumplir la ley y proteger a los árbitros.

### R.N.F.03. Usabilidad y uso en móvil
 Como árbitro, quiero que la interfaz se adapte al móvil y que consultar mis partidos o registrar un resultado lleve menos de 1 minuto, para poder usarla desde el pabellón.

### R.N.F.04. Rendimiento
 Como administrador, quiero que las consultas y los listados respondan en menos de 2 segundos con 50 usuarios a la vez, para que el sistema siga siendo ágil cuando se publican las designaciones.

### R.N.F.05. Compatibilidad y localización
 Como árbitro, quiero que el sistema funcione en Chrome, Firefox, Edge y Safari sin instalar nada, con la interfaz en español, las fechas en formato dd/mm/aaaa y los importes en euros, para usarlo desde cualquier dispositivo.

### R.N.F.06. Integridad de los datos
 Como administrador, quiero que las operaciones importantes (designar y registrar un resultado) se completen enteras o no se hagan, y que los importes se guarden con 2 decimales exactos, para evitar datos a medias y errores de cálculo.

### R.N.F.07. Copias de seguridad
 Como administrador, quiero una copia de seguridad diaria que se pueda recuperar en un máximo de 24 horas, para no perder resultados ni contabilidad.


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
