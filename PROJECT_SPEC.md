# PROJECT_SPEC.md — Miralune

> **Etapa SDD:** 2. Especificación.
>
> **Propósito:** definir el alcance, comportamiento, requisitos y condiciones de aceptación del aplicativo.

| Campo | Valor |
|---|---|
| Proyecto | Miralune |
| Versión | 1.0.0 |
| Responsables | Luz Karime - Sebastian Morelo |
| Fecha | 2026-11-25 |
| Metodología | Spec-Driven Development (SDD) |
| Estado | Borrador |

## 1. Descripción general

Miralune es una aplicación web orientada a la recomendación personalizada de series estrenadas desde el año 2017 hasta el año en curso. Incorpora un chatbot que permite solicitar recomendaciones mediante lenguaje natural, considerando géneros, años de estreno, temáticas y gustos personales.

El aplicativo busca resolver la dificultad de descubrir series acordes con los intereses particulares de cada persona, evitando que la búsqueda se limite exclusivamente a categorías o géneros generales. La información se obtendrá de proveedores externos autorizados y se presentará mediante una interfaz adaptable a computadores y dispositivos móviles.

## 2. Objetivos

### Objetivo general

Desarrollar una aplicación web que permita obtener recomendaciones personalizadas de series estrenadas desde 2017 hasta el año actual, considerando los gustos y preferencias del usuario mediante un chatbot.

### Objetivos específicos

1. Implementar una interfaz conversacional que permita expresar preferencias de entretenimiento mediante lenguaje natural.
2. Integrar proveedores externos para consultar y validar información real de series, incluyendo sus carátulas originales.
3. Implementar un mecanismo de recomendaciones que relacione las preferencias del usuario con las características de las series disponibles.
4. Diseñar una interfaz intuitiva, accesible y adaptable a computadores y dispositivos móviles.
5. Permitir la conservación y eliminación local del historial de conversaciones sin requerir almacenamiento centralizado.

## 3. Usuarios y necesidades

**Usuarios principales:** personas interesadas en descubrir series y recibir recomendaciones acordes con sus gustos personales.

**Necesidad identificada:** la cantidad de contenido audiovisual disponible dificulta encontrar series relevantes. Los filtros tradicionales por género pueden resultar insuficientes cuando se buscan temáticas, ambientes narrativos o características específicas.

**Resultado esperado:** reducir el esfuerzo de búsqueda mediante recomendaciones relevantes, verificables y contextualizadas, presentadas de forma clara y acompañadas de información útil para decidir qué serie ver.

## 4. Alcance

### Funcionalidades incluidas

- Acceso a la interfaz principal sin registro obligatorio, como propuesta para la primera versión.
- Chatbot para solicitar recomendaciones mediante lenguaje natural.
- Selección de preferencias mediante filtros de género y año, complementados por texto libre.
- Interpretación de gustos y contexto de la conversación.
- Consulta de información mediante proveedores externos autorizados.
- Validación del rango temporal y de la información recibida.
- Presentación de recomendaciones mediante tarjetas con título, año, géneros, sinopsis y carátula original cuando esté disponible.
- Explicación breve de la relación entre la recomendación y las preferencias expresadas.
- Consulta del detalle de una serie.
- Conservación local y eliminación del historial del chat.
- Interfaz adaptable a computadores, tabletas y teléfonos.
- Manejo de estados de carga, errores y ausencia de resultados.

### Funcionalidades excluidas

- Recomendación de películas, documentales independientes u otros contenidos ajenos al alcance de series.
- Reproducción, descarga o alojamiento de episodios.
- Suscripciones, pagos y contratación de plataformas de streaming.
- Registro, autenticación y perfiles de usuario en la primera versión propuesta.
- Base de datos propia de series o almacenamiento centralizado de conversaciones.
- Sincronización del historial entre dispositivos.
- Redes sociales, comentarios públicos y calificaciones propias.
- Generación artificial de carátulas de series.
- Aplicación móvil nativa independiente, hasta que se apruebe su alcance y tecnología.

## 5. Requisitos funcionales

| ID | Nombre | Descripción | Entrada | Resultado |
|---|---|---|---|---|
| RF-01 | Acceso a la aplicación | Permitir acceder a la interfaz principal y sus opciones. | Solicitud de acceso desde el navegador. | Interfaz principal disponible. |
| RF-02 | Definición de preferencias | Permitir seleccionar géneros, años y expresar gustos mediante texto. | Filtros y preferencias del usuario. | Criterios preparados para la consulta. |
| RF-03 | Conversación con el chatbot | Recibir mensajes y responder considerando el contexto de la conversación. | Mensaje y contexto local pertinente. | Respuesta conversacional o solicitud de aclaración. |
| RF-04 | Validación de solicitudes | Validar tipos, longitudes, formatos y rangos en el backend. | Solicitud de recomendación. | Solicitud válida o error comprensible. |
| RF-05 | Consulta externa | Obtener información de series desde proveedores aprobados. | Criterios de búsqueda. | Datos externos validados y normalizados. |
| RF-06 | Generación de recomendaciones | Seleccionar series reales que correspondan a los criterios y reglas de negocio. | Preferencias y candidatos verificados. | Recomendaciones relevantes o aviso de ausencia de resultados. |
| RF-07 | Filtrado temporal | Excluir series estrenadas antes de 2017 o después del año actual. | Fecha de estreno original. | Únicamente candidatos dentro del rango permitido. |
| RF-08 | Presentación de resultados | Mostrar información verificable, carátulas originales y motivo de recomendación. | Recomendaciones validadas. | Tarjetas de series y respuesta del chatbot. |
| RF-09 | Detalle de serie | Permitir consultar información adicional de una serie seleccionada. | Identificador de la serie. | Vista de detalle o aviso de información no disponible. |
| RF-10 | Historial local | Guardar y recuperar conversaciones en el almacenamiento local del navegador. | Mensajes y respuestas. | Historial disponible al volver a abrir la aplicación en el mismo navegador y perfil. |
| RF-11 | Eliminación del historial | Permitir eliminar el chat previa confirmación. | Solicitud y confirmación del usuario. | Historial y contexto activo eliminados. |
| RF-12 | Refinamiento de recomendaciones | Permitir ajustar las recomendaciones mediante nuevos mensajes o filtros. | Nuevas preferencias y contexto pertinente. | Resultados actualizados conforme a los criterios vigentes. |
| RF-13 | Manejo de errores | Informar errores de validación, conexión, proveedores o ausencia de resultados. | Error o respuesta vacía. | Mensaje claro y opción de reintentar cuando corresponda. |

## 6. Requisitos no funcionales

Los siguientes umbrales son objetivos propuestos, sujetos a aprobación y validación durante la planificación.

| ID | Categoría | Condición verificable |
|---|---|---|
| RNF-01 | Rendimiento | La interfaz principal deberá estar utilizable en un máximo de 3 segundos en el entorno de prueba acordado. |
| RNF-02 | Tiempo de respuesta | Mostrar estado de carga en menos de 1 segundo y finalizar o informar un tiempo de espera agotado en un máximo propuesto de 30 segundos por solicitud. |
| RNF-03 | Seguridad | Mantener secretos en el backend, validar entradas, restringir CORS a orígenes autorizados y utilizar HTTPS en producción. |
| RNF-04 | Usabilidad | Permitir iniciar una consulta desde la interfaz principal sin navegación innecesaria y mostrar mensajes comprensibles. |
| RNF-05 | Mantenibilidad | Separar interfaz, lógica de negocio, recomendaciones e integraciones; aplicar las convenciones de CONSTITUTION.md. |
| RNF-06 | Compatibilidad | Funcionar en las dos versiones estables más recientes de Chrome, Edge, Firefox y Safari disponibles al realizar las pruebas. |
| RNF-07 | Adaptabilidad | Funcionar sin desplazamiento horizontal involuntario en anchos de pantalla de 360, 768 y 1280 píxeles. |
| RNF-08 | Accesibilidad | Permitir navegación por teclado, foco visible, etiquetas accesibles y contraste conforme a WCAG 2.2 AA en los componentes aplicables. |
| RNF-09 | Privacidad | No almacenar conversaciones en servidores propios ni transmitir datos personales innecesarios a terceros. |
| RNF-10 | Fiabilidad | Controlar fallos externos sin presentar datos inventados ni dejar la interfaz bloqueada. |
| RNF-11 | Calidad de datos | Todas las series recomendadas deberán contar con identificador verificable y fecha de estreno original válida. |
| RNF-12 | Capacidad de prueba | Los requisitos obligatorios deberán tener casos de prueba trazables y resultados documentados. |

## 7. Tecnologías

| Tecnología | Uso | Obligatoria |
|---|---|---|
| React | Biblioteca de interfaz de usuario | Sí |
| Vite | Entorno de desarrollo y compilación frontend | Sí |
| Python | Lenguaje del backend | Sí |
| TypeScript | Lenguaje frontend recomendado | No; pendiente de aprobación |
| FastAPI | Framework backend propuesto | No; pendiente de aprobación |
| API REST / JSON | Comunicación frontend-backend propuesta | No; pendiente de aprobación |
| TMDB API | Proveedor propuesto de información y carátulas | No; pendiente de aprobación |
| Modelo o proveedor de IA | Interpretación de lenguaje natural y asistencia en recomendaciones | Por definir; la capacidad conversacional sí es obligatoria |
| localStorage | Almacenamiento local del chat, mecanismo propuesto | No; la persistencia local sí es obligatoria |
| Git y GitHub | Control de versiones y repositorio | No; pendiente de aprobación |
| Pytest | Pruebas backend | No; propuesto |
| Vitest | Pruebas frontend | No; propuesto |
| ESLint, Prettier y Ruff | Análisis y formato de código | No; propuesto |

No se requiere PostgreSQL ni otra base de datos centralizada para el alcance actual. Su incorporación futura exigirá aprobación y actualización de los documentos afectados. Se deberán verificar las licencias, atribuciones, términos y políticas de retención de los proveedores antes de utilizarlos.

## 8. Arquitectura

**Tipo de arquitectura:** cliente-servidor con backend monolítico modular, propuesta para aprobación.

**Justificación:** permite separar la interfaz de usuario de la lógica de negocio y centralizar las consultas externas, proteger las credenciales y mantener una estructura sencilla para un equipo pequeño.

**Componentes principales:**

- Frontend React: interfaz, filtros, chat, tarjetas, detalle y estados visuales.
- Backend Python: validación, coordinación de consultas y aplicación de reglas de negocio.
- Motor de recomendaciones: selección y ordenamiento de candidatos verificables.
- Adaptador conversacional: interpretación de preferencias y elaboración de respuestas fundamentadas.
- Integraciones externas: consulta de metadatos y servicios de IA aprobados.
- Almacenamiento local: historial del chat en el navegador.

Flujo conceptual: Usuario → Frontend → Backend → Proveedores externos → Validación y recomendaciones → Frontend. El historial permanece en el navegador; únicamente el contexto necesario se transmite para procesar cada solicitud. No se propone una base de datos propia.

## 9. Estructura de carpetas

Estructura inicial propuesta, coherente con la constitución y ajustada a la ausencia de persistencia centralizada:

```text
miralune/
├── CONSTITUTION.md
├── PROJECT_SPEC.md
├── PLAN.md
├── TASKS.md
├── README.md
├── .gitignore
├── docs/
├── frontend/
│   ├── src/
│   │   ├── assets/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── features/
│   │   │   ├── chat/
│   │   │   ├── series/
│   │   │   └── recommendations/
│   │   ├── hooks/
│   │   ├── services/
│   │   ├── routes/
│   │   ├── utils/
│   │   └── tests/
│   └── package.json
└── backend/
    ├── app/
    │   ├── api/
    │   ├── core/
    │   ├── models/
    │   ├── schemas/
    │   ├── services/
    │   ├── recommendations/
    │   ├── integrations/
    │   └── main.py
    ├── tests/
    └── .env.example
```

Los modelos representan estructuras de datos en memoria, no tablas persistentes. La estructura definitiva se aprobará en PLAN.md; no deberán crearse carpetas innecesarias.

## 10. Módulos

| Módulo | Responsabilidad | Funciones principales |
|---|---|---|
| Interfaz y navegación | Facilitar la interacción | Inicio, navegación, adaptación móvil y estados visuales. |
| Chatbot | Gestionar la conversación | Recibir mensajes, interpretar preferencias, solicitar aclaraciones y responder. |
| Preferencias | Gestionar criterios de búsqueda | Géneros, años, texto libre y actualización de criterios. |
| Integraciones externas | Obtener información real | Consultar proveedores, normalizar respuestas, controlar tiempos de espera y errores. |
| Recomendaciones | Seleccionar series relevantes | Filtrar fechas, aplicar preferencias, eliminar duplicados y ordenar resultados. |
| Información de series | Presentar datos verificables | Tarjetas, carátulas originales, sinopsis y vista de detalle. |
| Historial local | Administrar conversaciones en el dispositivo | Guardar, recuperar y eliminar historial y contexto. |

## 11. Entidades y datos principales

Las entidades son modelos lógicos de intercambio y estado; no implican tablas de base de datos.

### Entidad: Serie

| Atributo | Tipo | Descripción |
|---|---|---|
| id | string | Identificador del proveedor. |
| source | string | Proveedor de origen. |
| title | string | Título disponible de la serie. |
| originalTitle | string opcional | Título original. |
| firstAirDate | date | Fecha de estreno original verificada. |
| genres | array de string | Géneros asociados. |
| synopsis | string opcional | Sinopsis proporcionada por la fuente. |
| posterUrl | URL opcional | Referencia autorizada a la carátula original. |
| rating | number opcional | Valoración externa, con escala identificada. |
| sourceUrl | URL opcional | Referencia a la fuente, cuando esté disponible. |

### Entidad: Preferencias

| Atributo | Tipo | Descripción |
|---|---|---|
| genres | array de string | Géneros solicitados. |
| minYear | integer opcional | Año mínimo solicitado, dentro del rango permitido. |
| maxYear | integer opcional | Año máximo solicitado, dentro del rango permitido. |
| description | string opcional | Gustos, temáticas o características expresadas. |
| excludedGenres | array de string opcional | Géneros que el usuario desea evitar. |

### Entidad: Mensaje

| Atributo | Tipo | Descripción |
|---|---|---|
| id | string | Identificador local. |
| role | enum | user o assistant. |
| content | string | Contenido del mensaje. |
| createdAt | datetime | Fecha y hora del mensaje. |
| recommendations | array opcional | Referencias a recomendaciones asociadas. |

### Entidad: Recomendación

| Atributo | Tipo | Descripción |
|---|---|---|
| series | Serie | Serie verificada. |
| reason | string | Explicación fundamentada de su relación con las preferencias. |

### Entidad: Conversación local

| Atributo | Tipo | Descripción |
|---|---|---|
| id | string | Identificador local de conversación. |
| messages | array de Mensaje | Historial conversacional. |
| preferences | Preferencias | Criterios activos. |
| updatedAt | datetime | Última actualización. |
| schemaVersion | integer | Versión del formato de almacenamiento. |

Los nombres representan el contrato frontend/JSON propuesto. Python utilizará snake_case internamente conforme a CONSTITUTION.md. Los datos opcionales ausentes no deberán inventarse.

## 12. Gestión de estado

**Información que cambia:** mensajes, preferencias, recomendaciones, serie seleccionada, estado de carga, errores y disponibilidad del almacenamiento local.

**Administración propuesta:** useState y useReducer para estado local de React; Context cuando sea necesario compartir estado entre componentes. No se incorporará una biblioteca global adicional sin justificación.

El backend procesará cada solicitud sin mantener sesiones conversacionales persistentes. El frontend enviará únicamente el contexto pertinente y limitado. Los resultados de consultas y detalles se mantendrán temporalmente en memoria; el historial local conservará los mensajes y las referencias necesarias, sujeto a los términos de los proveedores.

## 13. Interfaz de usuario

**Tipo de aplicación:** web adaptable a computadores y dispositivos móviles. Una aplicación móvil nativa independiente requiere confirmación.

### Vista 1. Inicio

- Identidad visual de Miralune y explicación breve del aplicativo.
- Acceso al chatbot y ejemplos de consultas.
- Controles opcionales de género y año.

### Vista 2. Chat y recomendaciones

- Historial de mensajes y campo de texto.
- Botón de envío y controles de preferencias.
- Indicadores de carga y mensajes de error.
- Tarjetas de series con carátula, título, año, géneros y motivo de recomendación.
- Acción para consultar detalles y eliminar el historial.

### Vista 3. Detalle de serie

- Carátula original, título, fecha de estreno, géneros y sinopsis disponibles.
- Valoración y fuente cuando estén disponibles.
- Acción para regresar al chat conservando su contexto.

### Vista 4. Información y privacidad

- Explicación del almacenamiento local y procesamiento mediante terceros.
- Créditos y atribuciones exigidos por los proveedores.
- Información sobre eliminación del historial.

En pantallas pequeñas, los controles y tarjetas deberán reorganizarse sin perder funcionalidades. La distribución visual definitiva se establecerá en la planificación y el diseño de interfaz.

## 14. Navegación y flujo del usuario

1. El usuario accede a Miralune desde su navegador.
2. Inicia una consulta mediante texto libre o filtros.
3. El frontend envía la solicitud y el contexto pertinente al backend.
4. El backend valida la entrada e interpreta las preferencias.
5. Si falta información indispensable, el chatbot solicita una aclaración.
6. El backend consulta proveedores externos y valida los candidatos.
7. El motor selecciona series dentro del rango permitido y genera recomendaciones fundamentadas.
8. El frontend presenta los resultados y guarda localmente la conversación.
9. El usuario consulta detalles, refina sus preferencias o continúa conversando.
10. Cuando lo desee, puede eliminar el historial previa confirmación.

Si no existen coincidencias, se informa al usuario y se propone ajustar los criterios sin modificar restricciones obligatorias.

## 15. Persistencia de datos

**Información almacenada:** mensajes del usuario, respuestas del chatbot, preferencias activas y referencias necesarias para recuperar el historial. No se almacenará un catálogo propio de series.

**Ubicación:** almacenamiento local del navegador, mediante localStorage como propuesta inicial. No se utilizará una base de datos centralizada.

**Duración:** hasta que el usuario elimine el historial, borre los datos del sitio o el navegador retire el almacenamiento. La conservación está sujeta a la disponibilidad y límites del navegador.

**Reglas:**

- Cada navegador, perfil y origen mantiene su propio historial; no existe sincronización automática entre dispositivos.
- El usuario podrá eliminar el historial y el contexto activo mediante una acción explícita con confirmación.
- Una respuesta pendiente no deberá restaurar un historial eliminado.
- No se guardarán credenciales, tokens privados ni información personal innecesaria en el almacenamiento local.
- Si el almacenamiento falla, se permitirá continuar temporalmente en memoria y se informará que el historial no podrá conservarse.
- El backend no persistirá mensajes ni incluirá conversaciones en registros técnicos.
- Los proveedores externos podrán procesar o retener información conforme a sus condiciones. Se deberán verificar y comunicar estas condiciones antes de aprobar su integración. Eliminar el historial local no equivale a eliminar datos retenidos por terceros.

## 16. Reglas de negocio

| ID | Regla |
|---|---|
| RN-01 | Solo se recomendarán series cuya fecha de estreno original sea igual o posterior al 1 de enero de 2017. |
| RN-02 | No se presentarán datos inventados como información real. |
| RN-03 | La información de servicios externos deberá validarse antes de utilizarse. |
| RN-04 | El año máximo permitido será el año actual, calculado dinámicamente en el backend. |
| RN-05 | Se excluirán series cuya fecha de estreno original sea posterior a la fecha actual, incluso dentro del año en curso, como criterio propuesto para recomendar únicamente series estrenadas. |
| RN-06 | Una serie estrenada antes de 2017 no será elegible por tener temporadas posteriores. |
| RN-07 | Las series sin fecha original verificable no se incluirán en las recomendaciones. |
| RN-08 | Solo se utilizarán carátulas originales obtenidas de fuentes autorizadas; si no existe una, se mostrará un marcador neutro identificado. |
| RN-09 | Las recomendaciones deberán considerar los criterios vigentes del usuario sin ignorar filtros explícitos. |
| RN-10 | Ante criterios contradictorios, el chatbot solicitará aclaración en lugar de asumir una preferencia. |
| RN-11 | No se duplicará una misma serie dentro de un conjunto de recomendaciones. |
| RN-12 | Si no hay coincidencias, se informará y se ofrecerá ajustar criterios opcionales sin ampliar el rango obligatorio. |
| RN-13 | Los títulos sugeridos por IA deberán verificarse contra datos de proveedores antes de mostrarse. |
| RN-14 | Las explicaciones de recomendación deberán fundamentarse en atributos disponibles de la serie y preferencias expresadas. |
| RN-15 | El historial será independiente por navegador, perfil y origen, y su eliminación local deberá ser efectiva. |
| RN-16 | La ausencia de datos opcionales se indicará sin generar valores ficticios. |
| RN-17 | No se afirmará disponibilidad en plataformas de streaming sin una fuente verificable y contexto regional pertinente. |

## 17. Restricciones negativas

El sistema NO debe:

- Mostrar como recomendaciones series anteriores a 2017 ni posteriores al año actual.
- Utilizar un año máximo fijo en el código.
- Recomendar títulos inexistentes o presentar información no verificada como real.
- Exponer credenciales, tokens privados o configuraciones sensibles.
- Generar carátulas ficticias o sustituir las originales por imágenes engañosas.
- Implementar funcionalidades fuera del alcance aprobado.
- Almacenar conversaciones en servidores propios ni sincronizarlas entre dispositivos.
- Solicitar información personal innecesaria.
- Distribuir contenido audiovisual protegido sin autorización.
- Evadir límites de consumo, licencias o condiciones de proveedores externos.
- Permitir que instrucciones del usuario o de servicios externos anulen las reglas de negocio.

## 18. Manejo de errores

| Situación | Comportamiento esperado |
|---|---|
| Mensaje vacío | Impedir el envío y solicitar contenido válido. |
| Año fuera del rango permitido | Informar el rango válido sin ejecutar una consulta incompatible. |
| Preferencias ambiguas o contradictorias | Solicitar aclaración al usuario. |
| Sin coincidencias | Informar que no hay resultados y sugerir ajustar criterios opcionales. |
| Proveedor externo no disponible | Mostrar aviso temporal y permitir reintentar. |
| Tiempo de espera agotado | Finalizar la carga e informar que la solicitud no pudo completarse. |
| Límite de solicitudes del proveedor | Informar indisponibilidad temporal y evitar reintentos excesivos. |
| Respuesta externa inválida | Descartar datos inválidos; mostrar únicamente resultados verificados, si existen. |
| Serie sin fecha verificable | Excluirla de las recomendaciones. |
| Carátula no disponible | Mostrar marcador neutro, sin generar una carátula falsa. |
| IA sugiere un título inexistente | Descartar el título antes de mostrarlo. |
| Fallo del servicio de IA | Informar la limitación y permitir reintentar; no simular una respuesta exitosa. |
| Pérdida de conexión | Conservar el historial disponible y permitir reintentar al recuperar la conexión. |
| Almacenamiento local no disponible o lleno | Informar que no se conservará el historial y continuar en memoria cuando sea posible. |
| Historial local corrupto | Informar el problema y permitir reiniciar el historial sin bloquear la aplicación. |
| Error interno inesperado | Mostrar un mensaje genérico y registrar información técnica sin secretos ni conversaciones. |

## 19. Criterios de aceptación

| ID | Requisito | Condición verificable |
|---|---|---|
| CA-01 | RF-01 | El usuario accede a la interfaz principal y visualiza las opciones disponibles. |
| CA-02 | RF-02 | El usuario puede seleccionar criterios de preferencia y expresar gustos mediante texto. |
| CA-03 | RF-04 | El backend recibe y valida correctamente los criterios enviados desde el frontend. |
| CA-04 | RF-06 | Las recomendaciones respetan los criterios explícitos y se fundamentan en atributos verificables. |
| CA-05 | RF-07 | Ninguna serie estrenada antes de 2017 aparece en las recomendaciones. |
| CA-06 | RF-07 | El límite superior se actualiza automáticamente al cambiar el año del reloj de prueba. |
| CA-07 | RF-07 | Ninguna serie estrenada después del año actual aparece en los resultados. |
| CA-08 | RF-05, RF-08 | Los datos presentados corresponden a fuentes verificables. |
| CA-09 | RF-03 | El chatbot interpreta una solicitud en lenguaje natural y solicita aclaración ante criterios contradictorios. |
| CA-10 | RF-08 | Se muestran carátulas originales o marcadores neutros cuando no estén disponibles. |
| CA-11 | RF-09 | El usuario puede consultar el detalle de una serie y regresar al chat. |
| CA-12 | RF-10 | Al recargar el mismo navegador y perfil se recupera el historial local disponible. |
| CA-13 | RF-11 | Tras confirmar la eliminación y recargar, el historial y el contexto anterior no reaparecen. |
| CA-14 | RF-12 | Una nueva preferencia explícita modifica los resultados sin incumplir restricciones. |
| CA-15 | RF-13 | Ante un fallo externo o ausencia de coincidencias se muestra un mensaje claro y finaliza la carga. |
| CA-16 | RNF-07 | Las funciones principales están disponibles en los tres anchos de pantalla definidos. |
| CA-17 | RNF-03, RNF-09 | No se exponen secretos en el frontend ni se persisten conversaciones en servidores propios. |
| CA-18 | RF-07 | Una serie con estreno futuro dentro del año actual se excluye, conforme a RN-05 propuesta. |

## 20. Casos de prueba

Los casos siguientes son especificaciones de pruebas pendientes de ejecución. Se utilizarán datos controlados y proveedores simulados cuando corresponda, además de pruebas de integración autorizadas.

| ID | Requisito | Escenario | Resultado esperado |
|---|---|---|---|
| CP-01 | RF-01 | Abrir la aplicación. | Se visualiza el inicio y el acceso al chat. |
| CP-02 | RF-02 | Seleccionar ciencia ficción y año 2020. | Los criterios se reflejan en la solicitud. |
| CP-03 | RF-03 | Escribir «Quiero series de misterio con viajes en el tiempo». | Se interpretan las preferencias o se solicita aclaración pertinente. |
| CP-04 | RF-04 | Enviar un mensaje vacío o de tipo inválido directamente al backend. | Se rechaza la solicitud con error de validación. |
| CP-05 | RF-05 | Simular respuesta externa válida. | Se normalizan los datos y se conserva su origen. |
| CP-06 | RF-06 | Proporcionar candidatos de géneros distintos con filtro explícito de misterio. | Solo se recomiendan candidatos compatibles con el filtro. |
| CP-07 | RF-07 | Consultar una serie estrenada el 31/12/2016. | Se excluye. |
| CP-08 | RF-07 | Consultar una serie estrenada el 01/01/2017 que cumple los demás criterios. | Es elegible. |
| CP-09 | RF-07 | Simular un candidato estrenado el próximo año. | Se excluye. |
| CP-10 | RF-07 | Simular cambio de año de 2026 a 2027. | El límite máximo pasa a 2027 sin modificar el código. |
| CP-11 | RF-07 | Recibir una serie sin fecha original verificable. | Se excluye. |
| CP-12 | RF-08 | Recibir una carátula original válida. | Se muestra la carátula autorizada. |
| CP-13 | RF-08 | Recibir una serie sin carátula. | Se muestra un marcador neutro. |
| CP-14 | RF-06 | Simular un título inventado por el chatbot. | Se descarta por falta de verificación. |
| CP-15 | RF-09 | Seleccionar una tarjeta y regresar al chat. | Se muestra el detalle y se conserva la conversación. |
| CP-16 | RF-10 | Conversar y recargar el mismo navegador. | Se recupera el historial disponible. |
| CP-17 | RF-10 | Abrir la aplicación en otro perfil o dispositivo sin datos locales. | No aparece el historial del primer dispositivo. |
| CP-18 | RF-11 | Confirmar eliminación y recargar. | No reaparecen mensajes ni contexto anterior. |
| CP-19 | RF-11 | Eliminar historial mientras existe una respuesta pendiente. | La respuesta tardía no restaura el historial. |
| CP-20 | RF-12 | Cambiar el género solicitado en un nuevo mensaje. | Las recomendaciones se ajustan al nuevo criterio. |
| CP-21 | RF-13 | Simular un proveedor que no responde. | Se informa el error y termina el estado de carga. |
| CP-22 | RF-13 | Simular una búsqueda sin coincidencias. | Se informa que no hay resultados y se permite ajustar preferencias. |
| CP-23 | RF-10, RF-13 | Bloquear el almacenamiento local. | Se informa la limitación y se continúa en memoria cuando sea posible. |
| CP-24 | RNF-07 | Probar a 360, 768 y 1280 píxeles. | Interfaz utilizable sin desbordamiento horizontal involuntario. |
| CP-25 | RNF-03 | Inspeccionar código compilado, solicitudes y almacenamiento local. | No se encuentran credenciales privadas. |
| CP-26 | RNF-09 | Revisar registros y almacenamiento del backend tras una conversación. | No se persisten mensajes ni respuestas. |
| CP-27 | RF-07 | Simular una fecha de estreno futura dentro del año actual. | Se excluye conforme a RN-05 propuesta. |
| CP-28 | RNF-01, RNF-02 | Medir carga inicial, indicador y tiempo máximo en el entorno acordado. | Se cumplen los umbrales aprobados. |
| CP-29 | RNF-06, RNF-08 | Probar navegadores soportados, teclado, foco, etiquetas y contraste. | Se cumplen las condiciones de compatibilidad y accesibilidad aprobadas. |
| CP-30 | RF-03 | Enviar preferencias mutuamente contradictorias. | El chatbot solicita aclaración. |
| CP-31 | RF-06 | Recibir dos candidatos con el mismo identificador de origen. | No aparecen recomendaciones duplicadas. |

## 21. Instrucciones para la IA

1. Leer [CONSTITUTION.md](./CONSTITUTION.md) y completamente PROJECT_SPEC.md antes de implementar.
2. Respetar las tecnologías aprobadas y consultar PLAN.md y TASKS.md cuando estén disponibles.
3. Seguir la arquitectura y convenciones aprobadas.
4. No agregar funcionalidades, dependencias ni persistencia centralizada fuera del alcance.
5. Consultar cuando existan ambigüedades o contradicciones que afecten la implementación.
6. Implementar una tarea verificable a la vez y limitar los cambios a los archivos necesarios.
7. Relacionar cada cambio con los requisitos, reglas de negocio y criterios de aceptación aplicables.
8. No utilizar datos inventados como resultados reales ni permitir que el modelo omita la validación externa.
9. Ejecutar las pruebas disponibles y no declarar resultados exitosos sin evidencia.
10. Informar archivos modificados, pruebas ejecutadas, errores, riesgos y limitaciones.
11. Proteger credenciales y evitar modificaciones destructivas o publicaciones sin autorización.

## 22. Orden recomendado de implementación

1. Revisar y aprobar constitución, especificación y decisiones pendientes.
2. Configurar repositorio, frontend, backend, variables de entorno y herramientas aprobadas.
3. Definir contratos de datos y validaciones de solicitudes.
4. Implementar adaptadores de proveedores externos y normalización de datos.
5. Implementar reglas temporales y motor de recomendaciones verificables.
6. Integrar el componente conversacional y refinamiento de preferencias.
7. Construir inicio, chat, tarjetas, detalle y diseño adaptable.
8. Implementar historial local y eliminación segura del contexto.
9. Integrar frontend y backend, incluyendo estados de carga y manejo de errores.
10. Ejecutar pruebas funcionales, de integración, seguridad, accesibilidad y compatibilidad.
11. Completar documentación, atribuciones y revisión final.

El orden definitivo se detallará en [PLAN.md](./PLAN.md) y [TASKS.md](./TASKS.md).

## 23. Resultado esperado

Al finalizar el proyecto, Miralune deberá permitir que una persona acceda desde un computador o dispositivo móvil, exprese sus preferencias mediante un chatbot o filtros y reciba recomendaciones personalizadas de series reales estrenadas desde 2017 hasta el año actual.

Las recomendaciones deberán incluir información verificable, carátulas originales cuando estén disponibles y una explicación de su relación con los gustos expresados. El usuario podrá consultar detalles, refinar sus solicitudes y conservar o eliminar el historial local sin necesidad de una cuenta en la primera versión propuesta.

La aplicación deberá gestionar fallos de servicios externos sin inventar información y respetar las restricciones de seguridad, privacidad y licenciamiento.

## 24. Definición de terminado

- [ ] Se aprobaron las decisiones técnicas pendientes y el alcance móvil.
- [ ] Se implementaron todos los requisitos funcionales obligatorios.
- [ ] Se verificaron los requisitos no funcionales aprobados.
- [ ] Se respetaron las reglas de negocio y restricciones negativas.
- [ ] Se verificaron los criterios de aceptación.
- [ ] Se ejecutaron y documentaron los casos de prueba aplicables.
- [ ] Se verificó el rango temporal dinámico y la autenticidad de las recomendaciones.
- [ ] Se comprobó la recuperación y eliminación del historial local.
- [ ] Se comprobó la ausencia de persistencia centralizada de conversaciones.
- [ ] Se verificaron las condiciones de uso, licencias, atribuciones y privacidad de proveedores.
- [ ] Se documentaron errores conocidos y se resolvieron los bloqueantes.
- [ ] La aplicación puede instalarse y ejecutarse siguiendo README.md.
- [ ] El código cumple las convenciones de CONSTITUTION.md.
- [ ] La documentación se encuentra actualizada.
- [ ] Ambos responsables revisaron y aprobaron el resultado.

## 25. Registro de cambios

| Versión | Fecha | Cambio | Responsable |
|---|---|---|---|
| 1.0.0 | 2026-11-25 | Creación inicial de la especificación; pendiente de revisión y aprobación. | Luz Karime - Sebastian Morelo |

---

**Estado final:** Borrador.

**Decisiones pendientes de aprobación:** lenguaje frontend, framework backend, proveedores de datos e IA, estrategia de recomendaciones, almacenamiento local concreto, límites de mensajes y contexto, objetivos de rendimiento, estrategia de control de versiones, alcance móvil y exclusión de estrenos futuros dentro del año actual. Confirmar también la ausencia de cuentas de usuario en la primera versión y el ajuste de CONSTITUTION.md para reflejar que no se requiere una base de datos propia.
