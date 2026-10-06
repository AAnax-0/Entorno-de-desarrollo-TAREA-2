# BeOnTime

**Tarea Módulo 2: Reconocimiento de elementos en el desarrollo de un programa informático**
Entornos de Desarrollo · DAM · Álvaro González Medina

BeOnTime es una aplicación para llegar a tiempo a cualquier destino, tanto de rutina (clase, trabajo) como puntual (un cine, una cita). Calcula en tiempo real las mejores combinaciones de transporte público y permite que los usuarios compartan el estado de las estaciones mediante comentarios en tiempo real.

## Índice

1. [Selección de la aplicación](#1-selección-de-la-aplicación)
2. [Listado de características](#2-listado-de-características)
3. [Documentación inicial](#3-documentación-inicial)
4. [Análisis de requisitos](#4-análisis-de-requisitos)
5. [Planificación Scrum](#5-planificación-scrum)
6. [Presentación](#6-presentación)
7. [Conclusión](#7-conclusión)

---

## 1. Selección de la aplicación

BeOnTime calcula en tiempo real las mejores combinaciones de transporte público para llegar a un destino a la hora elegida, y deja que los usuarios compartan el estado de las estaciones. Se ha elegido un modelo de desarrollo ágil con **Scrum**.

El producto se divide en fases: primero una versión sencilla (registro, destinos y rutas) y después funciones más complejas (incidencias y comentarios en tiempo real). Cada sprint entrega algo que se puede probar y mejorar con el feedback de los usuarios.

- **Usuarios principales:** cualquier persona que usa transporte público a diario, como estudiantes y trabajadores.
- **Plataformas:** app móvil multiplataforma (Android e iOS), con una versión web de apoyo.
- **Fases del ciclo de vida:** este trabajo cubre la fase de análisis (requisitos) y la planificación; el diseño, la codificación, las pruebas y el despliegue se repiten en cada sprint.

## 2. Listado de características

BeOnTime tiene 12 características: 8 funcionales, que describen lo que hace la app, y 4 no funcionales, que describen con qué calidad debe hacerlo.

| Nº | Característica | Tipo |
|---|---|---|
| 1 | Registro e inicio de sesión con usuario y contraseña | Funcional |
| 2 | Guardar la ubicación de casa usando la localización en tiempo real | Funcional |
| 3 | Crear destinos de rutina (clase a las 8:00 de lunes a viernes) o puntuales (cine el sábado a las 18:00) | Funcional |
| 4 | Calcular rutas combinando transportes públicos, ordenadas de más a menos eficiente | Funcional |
| 5 | Mostrar información de cada transporte: horarios y ubicación de paradas y estaciones | Funcional |
| 6 | Indicar la hora de salida recomendada para llegar a tiempo | Funcional |
| 7 | Avisar de incidencias oficiales (retrasos, cortes, huelgas) | Funcional |
| 8 | Comentarios en tiempo real por estación, con moderación y caducidad de 60 minutos | Funcional |
| 9 | Respuesta rápida: la ruta se calcula en menos de 3 segundos | No funcional |
| 10 | Protección de datos personales (ubicación y cuenta) según el RGPD | No funcional |
| 11 | Interfaz sencilla: consultar la ruta en un máximo de 3 toques | No funcional |
| 12 | Disponibilidad alta en horas punta (7:00 a 9:00) | No funcional |

## 3. Documentación inicial

### 3.1. Nombre de la aplicación

BeOnTime.

### 3.2. Descripción breve

BeOnTime calcula en tiempo real la mejor forma de llegar a cualquier destino en transporte público, con información de horarios, paradas, incidencias y un apartado de comentarios donde intercambiar información con otras personas.

### 3.3. Objetivos

Evitar que el usuario llegue tarde por falta de información: retrasos no comunicados, incidencias o desconocimiento de las alternativas de transporte. La app reúne en un solo lugar las rutas posibles, su estado actual y la hora a la que hay que salir.

### 3.4. Usuarios principales

| Rol | Qué hace |
|---|---|
| Usuario | Se registra, guarda su casa y sus destinos, consulta rutas y publica comentarios. |
| Moderador | Revisa los comentarios denunciados y elimina los falsos o inapropiados. |
| Administrador | Gestiona usuarios, sanciones y la configuración de la app. |

### 3.5. Plataformas

Móvil (Android e iOS, con un desarrollo multiplataforma) como plataforma principal, porque el usuario consulta la ruta mientras se desplaza. Web como apoyo y para el panel de administración y moderación.

### 3.6. Modelo de desarrollo

Se usará **Scrum**. Los requisitos pueden cambiar según lo que pidan los usuarios, y la app tiene partes independientes que se pueden entregar por separado. Se empezará con una versión sencilla pero útil (rutas para un destino) para probarla y mejorarla en cada sprint, aproximadamente cada 15 días.

El modelo en espiral sería menos adecuado, ya que está pensado para proyectos grandes con un análisis de riesgos extenso antes de cada fase. El modelo en cascada tampoco encaja, porque obliga a fijar todos los requisitos al principio y tardaría demasiado en hacer pública la app.

## 4. Análisis de requisitos

Los requisitos funcionales describen qué hace la app; los no funcionales, con qué calidad lo hace.

### 4.1. Requisitos funcionales

| ID | Requisito | Por qué es importante |
|---|---|---|
| RF1 | El usuario puede registrarse e iniciar sesión. | Sin cuenta no se pueden guardar la casa ni los destinos, ni asociar los comentarios a una persona para moderarlos. |
| RF2 | El usuario puede guardar su casa mediante localización en tiempo real. | Es el punto de partida de todas las rutas y evita escribir la dirección cada vez. |
| RF3 | El usuario puede crear destinos de rutina (días y hora de llegada) o puntuales (fecha y hora). | Cubre los dos casos de uso: ir a clase cada día o ir al cine una vez. |
| RF4 | La app calcula rutas en transporte público, incluidas combinaciones, ordenadas de más a menos eficiente. | Es el objetivo principal de la app: llegar a tiempo eligiendo la mejor opción. |
| RF5 | La app muestra horarios, ubicación de paradas e incidencias de cada transporte de la ruta. | El usuario necesita datos concretos para decidir, no solo un trazado en el mapa. |
| RF6 | El usuario puede publicar comentarios en tiempo real sobre una estación, que caducan a los 60 minutos. | Aporta información que los avisos oficiales no dan, y la caducidad evita mostrar datos desactualizados. |
| RF7 | El usuario puede denunciar un comentario y el moderador puede eliminarlo. | Un comentario falso puede hacer que alguien llegue tarde, así que tiene que haber una moderación constante. |

### 4.2. Requisitos no funcionales

| ID | Tipo | Requisito | Por qué es importante |
|---|---|---|---|
| RNF1 | Rendimiento | La ruta se calcula en menos de 3 segundos y los comentarios llegan a los demás en menos de 5. | El usuario consulta la app con prisa; si tarda, deja de ser útil. |
| RNF2 | Seguridad | Contraseñas cifradas y comunicación por HTTPS. | Protege las cuentas frente a accesos no autorizados. |
| RNF3 | Privacidad | La ubicación solo se usa con permiso del usuario y en los comentarios se muestra un alias. | La ubicación de casa es un dato personal sensible, y el nombre también. |
| RNF4 | Usabilidad | La ruta del destino habitual se consulta en un máximo de 3 toques, con textos claros y botones grandes. | Muchos usuarios serán novatos y usarán la app mientras caminan. |
| RNF5 | Disponibilidad | Funcionamiento estable en horas punta (7:00 a 9:00) con muchos usuarios a la vez. | Es justo cuando más se necesita la app. |
| RNF6 | Compatibilidad | Funciona en Android, iOS y en los navegadores principales. | Llega a la mayoría de usuarios sin desarrollar dos apps distintas. |

### 4.3. Condiciones de uso de los comentarios

Para que la sección de comentarios en tiempo real sea fiable, se aplican estas normas:

- Solo pueden comentar usuarios registrados que estén cerca de la estación.
- Cada comentario caduca 60 minutos después de publicarse.
- Hay un límite de publicaciones por usuario para evitar spam (2 como máximo, según cuántas estaciones uses).
- Otros usuarios pueden confirmar un comentario o marcarlo como solucionado.
- Están prohibidos los insultos, los datos personales de terceros y la publicidad.
- Un comentario con varias denuncias se oculta hasta que lo revisa un moderador, y los usuarios pueden ser suspendidos.

## 5. Planificación Scrum

El proyecto se organiza en 3 sprints de 2 semanas. El primero ya entrega una versión sencilla pero útil.

### 5.1. Roles

- **Product Owner:** define y prioriza el Product Backlog según el valor que aporta al usuario.
- **Scrum Master:** vigila que se sigan los eventos de Scrum y elimina bloqueos.
- **Equipo de desarrollo:** diseña, programa y prueba cada incremento.

### 5.2. Product Backlog

Las funcionalidades se recogen como historias de usuario, priorizadas y asignadas a un sprint:

| ID | Historia de usuario | Prioridad | Sprint |
|---|---|---|---|
| HU1 | Como usuario quiero registrarme e iniciar sesión para guardar mis datos. | Alta | 1 |
| HU2 | Como usuario quiero guardar mi casa con mi ubicación actual para no escribirla cada vez. | Alta | 1 |
| HU3 | Como estudiante quiero guardar mi clase con llegada a las 8:00 de lunes a viernes para consultarla rápido. | Alta | 1 |
| HU4 | Como usuario quiero ver las rutas en transporte público ordenadas por eficiencia para elegir la mejor. | Alta | 1 |
| HU5 | Como usuario quiero ver horarios y ubicación de las paradas de mi ruta para no perderme. | Alta | 2 |
| HU6 | Como usuario quiero saber a qué hora salir para llegar a tiempo. | Media | 2 |
| HU7 | Como usuario quiero crear un destino puntual para usar la app fuera de mi rutina. | Media | 2 |
| HU8 | Como usuario quiero recibir avisos de incidencias oficiales en mi ruta. | Media | 2 |
| HU9 | Como usuario quiero leer y publicar comentarios sobre una estación para saber su estado real. | Media | 3 |
| HU10 | Como usuario quiero denunciar comentarios falsos para que la información sea fiable. | Media | 3 |
| HU11 | Como moderador quiero revisar y eliminar comentarios denunciados. | Media | 3 |

### 5.3. Sprints

| Sprint | Objetivo | Contenido |
|---|---|---|
| 1 | Versión básica útil | Registro, casa, destino de rutina y cálculo de rutas ordenadas. |
| 2 | Información detallada | Horarios, paradas, hora de salida, destinos puntuales e incidencias oficiales. |
| 3 | Comunidad | Comentarios en tiempo real con caducidad, denuncias y panel de moderación. |

### 5.4. Eventos

- **Sprint Planning:** al inicio de cada sprint se eligen las historias del backlog.
- **Daily Scrum:** reunión diaria de 15 minutos sobre avances y bloqueos.
- **Sprint Review:** al final se enseña el incremento y se recoge feedback.
- **Sprint Retrospective:** el equipo analiza qué mejorar en el siguiente sprint.

### 5.5. Dependencias y riesgos

Los horarios, paradas e incidencias en tiempo real dependen de APIs externas de mapas y de datos abiertos de transporte. Si una API falla o no tiene datos de una zona, la app mostrará la última información disponible y avisará al usuario.

## 6. Presentación

El trabajo se presenta en clase o en un vídeo de YouTube (público u oculto) de 5 a 7 minutos, con este guion:

1. El problema: llegar tarde por falta de información sobre el transporte.
2. La solución: qué es BeOnTime y a quién va dirigida.
3. Características principales y la sección de comentarios en tiempo real.
4. Requisitos funcionales y no funcionales más importantes.
5. Por qué Scrum y cómo se reparten los sprints.
6. Cierre con el enlace al repositorio.

**Vídeo:** _[https://www.youtube.com/watch?v=OVq55zobE4k]_

## 7. Conclusión

Ha sido un trabajo interesante y me gusta la aplicación propuesta, quizás incluso para desarrollarla y usarla personalmente. El diseño con Scrum permite hacer versiones "beta" de las aplicaciones e ir comprobando qué funciones piden más los usuarios, así que también me ha parecido una forma muy interesante de desarrollar aplicaciones.