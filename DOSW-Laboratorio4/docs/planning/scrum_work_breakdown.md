# 📄 Planeación del Sistema

## Desglose de trabajo: Épicas, Historias de Usuario y Tareas

La implementación de los requerimientos identificados de TechCup se desglosa de la siguiente manera:

### 1. Épica:

| Campo | Descripción |
|------|-------------|
| **ID** | EP-01 |
| **Título** | Crear torneo o equipo |
| **Descripción** | Permitir a los usuarios con el rol indicado poder gestionar los torneos y equipos de una manera cómoda y adecuada. El sistema debe permitir que un organizador cree un nuevo torneo especificando sus reglas básicas, y que un capitán cree un nuevo equipo para participar en el torneo que estaactivo. Es la funcionalidad base de la que dependen el pago, la validación de inscripciones y los informes |
| **Stakeholder** | Organizadores y los capitanes de los equipos |

### 2. Historias de usuario:

| Campo | Descripción |
|------|-------------|
| **ID** | HU-01 |
| **Título** | Pagar la cuota de un equipo |
| **Descripción** | *Como capitán del equipo quiero pagar la cuota de inscripción de un equipo para poder registrar el pago como completado e inscribir el equipo en el torneo* |
| **Prioridad** | Media |
| **Justificación** | Sin este flujo ningún equipo puede completar su inscripción y esto es parte del camino que el enunciado exige (los equipos deben poder pagar la cuota de inscripción a través de PSE) |
| **Estimación** | 5 |

| Campo | Descripción |
|------|-------------|
| **ID** | HU-02 |
| **Título** | Creación de un torneo |
| **Descripción** | *Como organizador quiero crear un torneo de estado pendiente para permitir que los equipos se inscriban en el* |
| **Prioridad** | Alta |
| **Justificación** | Es el prerrequisito de todo el sistema porque sin un torneo creado no hay torneo activo en el cual inscribirse, ni equipos, ni pagos, ni informes que para poder generar :v |
| **Estimación** | 9.7 |

| Campo | Descripción |
|------|-------------|
| **ID** | HU-03 |
| **Título** | Creación de un equipo |
| **Descripción** | *Como capitán del equipo quiero crear un nuevo equipo con su información básica para poder registrarlo en el sistema antes de inscribirlo en el torneo activo* |
| **Prioridad** | Alta |
| **Justificación** | Es el paso previo que es importante para HU-01: sin un equipo creado no hay sobre qué registrar un pago ni qué inscribir. |
| **Estimación** | 9.7 |

| Campo | Descripción |
|------|-------------|
| **ID** | HU-04 |
| **Título** | Validar que solo exista un torneo activo al crearlo |
| **Descripción** | *Como organizador del torneo quiero que el sistema impida crear un torneo si ya existe otro activo para poder garantizar que solo haya un torneo activo a la vez* |
| **Prioridad** | Baja |
| **Justificación** | Protege la regla central de "solo puede haber un torneo activo a la vez", pero solo se pone a prueba cuando alguien intenta crear o activar un segundo torneo. |
| **Estimación** | 3 |

### 3. Tareas:

| Campo | Descripción |
|------|-------------|
| **ID** | TR-01 |
| **Título** | Definir modelo de Pago |
| **ID de la Historia de Uso asociada** | HU-01 |
| **Descripción** | Diseñar y crear la entidad/modelo de Pago (equipo asociado, monto, estado, fecha) que soporte el registro de la cuota de inscripción |
| **Tareas requisito** | Ninguna |

| Campo | Descripción |
|------|-------------|
| **ID** | TR-02 |
| **Título** | Integrar pasarela de pago PSE |
| **ID de la Historia de Uso asociada** | HU-01 |
| **Descripción** | Implementar la integración con PSE para procesar el pago de la cuota, incluyendo el manejo de la respuesta (Si fallo o no) |
| **Tareas requisito** | TR-01 |

| Campo | Descripción |
|------|-------------|
| **ID** | TR-03 |
| **Título** | Actualizar estado del equipo tras el pago |
| **ID de la Historia de Uso asociada** | HU-01 |
| **Descripción** | Actualizar el estado del equipo a "pago registrado, pendiente de validación" cuando el pago por PSE se complete exitosamente. |
| **Tareas requisito** | TR-02 |

| Campo | Descripción |
|------|-------------|
| **ID** | TR-04 |
| **Título** | Definir modelo de Torneo |
| **ID de la Historia de Uso asociada** | HU-02 |
| **Descripción** | Diseñar y crear la entidad/modelo de Torneo con código, fechas, cuota de inscripción y estado |
| **Tareas requisito** | Ninguna |

| Campo | Descripción |
|------|-------------|
| **ID** | TR-05 |
| **Título** | Generar código único de torneo |
| **ID de la Historia de Uso asociada** | HU-02 |
| **Descripción** | Implementar la generación automática del código de 5 dígitos, basado en el año y el semestre en el que se esta |
| **Tareas requisito** | TR-04 |

| Campo | Descripción |
|------|-------------|
| **ID** | TR-06 |
| **Título** | Crear torneo en estado Pendiente |
| **ID de la Historia de Uso asociada** | HU-02 |
| **Descripción** | Implementar la creación del torneo en estado "Pendiente", viendo que la duración configurada no exceda un día |
| **Tareas requisito** | TR-04, TR-05 |

| Campo | Descripción |
|------|-------------|
| **ID** | TR-07 |
| **Título** | Definir modelo de Equipo |
| **ID de la Historia de Uso asociada** | HU-03 |
| **Descripción** | Diseñar y crear la entidad/modelo de Equipo (nombre, integrantes, programa académico) |
| **Tareas requisito** | Ninguna |

| Campo | Descripción |
|------|-------------|
| **ID** | TR-08 |
| **Título** | Servicio para registrar equipo |
| **ID de la Historia de Uso asociada** | HU-03 |
| **Descripción** | Implementar el servicio que permite a un capitán registrar un nuevo equipo en el sistema. |
| **Tareas requisito** | TR-07 |

| Campo | Descripción |
|------|-------------|
| **ID** | TR-09 |
| **Título** | Validar campos obligatorios del equipo |
| **ID de la Historia de Uso asociada** | HU-03 |
| **Descripción** | Agregar las validaciones de los campos obligatorios (nombre, integrantes) al crear el equipo |
| **Tareas requisito** | TR-08 |

| Campo | Descripción |
|------|-------------|
| **ID** | TR-10 |
| **Título** | Consultar torneos por estado |
| **ID de la Historia de Uso asociada** | HU-04 |
| **Descripción** | Implementar la consulta que permite verificar si existe algún torneo "Activo" |
| **Tareas requisito** | TR-04 |

| Campo | Descripción |
|------|-------------|
| **ID** | TR-11 |
| **Título** | Regla: bloquear creación si ya hay un torneo activo |
| **ID de la Historia de Uso asociada** | HU-04 |
| **Descripción** | Implementar la regla de negocio que impide crear/activar un torneo si ya existe otro en "Activo" |
| **Tareas requisito** | TR-10 |

| Campo | Descripción |
|------|-------------|
| **ID** | TR-12 |
| **Título** | Pruebas de la regla de torneo único activo |
| **ID de la Historia de Uso asociada** | HU-04 |
| **Descripción** | Escribir pruebas unitarias que verifiquen que el sistema rechaza un segundo torneo activo |
| **Tareas requisito** | TR-11 |



Historia de usuario 1: 5 - 5 - 5
historia de ususario 2: 13 - 8 - 8

