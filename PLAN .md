# PLAN.md — Miralune

> **Etapa SDD:** 4. Planificación.
>
> **Propósito:** explicar cómo se implementarán los requisitos aprobados.

| Campo | Valor |
|---|---|
| Proyecto | Miralune |
| Versión | 1.0.0 |
| Responsables | Luz Karime - Sebastian Morelo |
| Fecha | 2026-11-25 |
| Estado | Borrador |
| Metodología | Spec-Driven Development (SDD) |

## 1. Objetivo del plan

Definir una estrategia técnica sencilla para construir Miralune: una aplicación web adaptable a móviles que recomienda series reales estrenadas desde 2017 hasta el año actual mediante un chatbot, filtros y consultas externas. El historial permanecerá local y no se requiere base de datos propia. Este plan no autoriza iniciar la implementación.

## 2. Documentos de referencia

- [CONSTITUTION.md](./CONSTITUTION.md) — versión 1.0.0, borrador disponible en la conversación.
- [PROJECT_SPEC.md](./PROJECT_SPEC.md) — versión 1.0.0, borrador.
- Decisiones de clarificación: no se dispone de un registro aprobado; las decisiones pendientes se enumeran en la sección 13.

## 3. Tecnologías y dependencias

| Tecnología | Uso | Versión acordada |
|---|---|---|
| React | Interfaz | Predefinida |
| Vite | Desarrollo y compilación | Predefinida |
| Python | Backend | Predefinida |
| Git y GitHub | Control de versiones | Predefinida |

Las versiones compatibles se fijarán durante la preparación. Se verificarán licencias, atribuciones, costos, límites de consumo y retención de datos antes de aprobar dependencias y proveedores. No se propone PostgreSQL, ORM, Redis ni una biblioteca global de estado. Las dependencias nuevas requieren autorización conforme a la constitución.

## 4. Arquitectura técnica

Se propone una arquitectura cliente-servidor con un backend monolítico modular. El frontend y el backend serán aplicaciones separadas dentro de un mismo repositorio. El backend se ejecutará como un único servicio, organizado por responsabilidades.

Esta arquitectura facilita el aprendizaje, las pruebas y el mantenimiento, sin introducir microservicios, colas de mensajes, contenedores obligatorios ni infraestructura distribuida.

```text
Usuario (computador o móvil)
          |
Frontend React + Vite ---- Historial local del navegador
          |
      REST / JSON
          |
Backend Python + FastAPI (propuesto)
          |
          +-- Validación y reglas de negocio
          +-- Motor de recomendaciones
          +-- Adaptador de metadatos --> Proveedor de series
          +-- Adaptador conversacional --> Proveedor de IA
```

El backend no conservará sesiones conversacionales ni utilizará una base de datos propia. La interfaz será web adaptable;

| Componente | Finalidad | Requisitos relacionados |
|---|---|---|
| Inicio y navegación | Acceso a las vistas | RF-01 |
| Chatbot | Interacción conversacional | RF-03, RF-12 |
| Preferencias | Filtros de género, año y texto | RF-02 |
| API backend | Recepción y validación de solicitudes | RF-04 |
| Integraciones | Consulta y normalización de datos externos | RF-05 |
| Motor de recomendaciones | Filtrado, selección y ordenamiento | RF-06, RF-07 |
| Tarjetas y detalle | Presentación de series verificadas | RF-08, RF-09 |
| Historial local | Recuperación y eliminación de conversaciones | RF-10, RF-11 |
| Manejo de errores | Estados de carga, fallos y ausencia de resultados | RF-13 |
| Información y privacidad | Atribuciones y explicación del tratamiento de datos | RNF-09 |

## 5. Estructura de carpetas

Se propone simplificar la estructura inicial de la especificación sin perder la separación de responsabilidades. Las carpetas se crearán únicamente cuando sean necesarias.

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
    │   ├── schemas/
    │   ├── services/
    │   ├── recommendations/
    │   ├── integrations/
    │   └── main.py
    ├── tests/
    ├── requirements.txt
    └── .env.example
```

Los esquemas representarán datos en memoria y contratos de intercambio, no tablas. No se requiere una capa de repositorios de base de datos. Esta simplificación deberá aprobarse como parte del plan.

## 6. Módulos y responsabilidades

Cada módulo tendrá una responsabilidad concreta. Los contratos son conceptuales y no constituyen código de implementación.

| Módulo | Responsabilidad | Entradas | Procesamiento | Salidas | Requisitos |
|---|---|---|---|---|---|
| Interfaz y navegación | Facilitar el acceso | Acciones del usuario | Navegar y gestionar estados visuales | Vistas adaptables | RF-01, RF-13 |
| Preferencias | Capturar criterios | Géneros, años y texto | Preparar y actualizar filtros | Preferencias vigentes | RF-02, RF-12 |
| Chatbot | Gestionar conversación | Mensaje y contexto pertinente | Interpretar gustos y aclarar contradicciones | Respuesta conversacional | RF-03, RF-12 |
| API y validación | Coordinar solicitudes | JSON e identificadores | Validar y dirigir al servicio correspondiente | Respuesta o error | RF-04, RF-13 |
| Integraciones externas | Obtener datos reales | Criterios e identificadores | Consultar, normalizar y validar proveedores | Candidatos verificables | RF-05 |
| Recomendaciones | Seleccionar series | Preferencias y candidatos | Filtrar fechas, deduplicar y ordenar por afinidad | Recomendaciones fundamentadas | RF-06, RF-07 |
| Información de series | Presentar resultados | Series verificadas | Mostrar tarjetas y consultar detalle | Carátulas originales y metadatos | RF-08, RF-09 |
| Historial local | Conservar y eliminar chat | Mensajes y confirmación | Guardar, recuperar y limpiar contexto | Historial local actualizado | RF-10, RF-11 |

### 3.1. Frontend

- Presentar inicio, chat, filtros, tarjetas, detalle e información de privacidad.
- Administrar mensajes, preferencias, estados de carga y errores mediante hooks de React.
- Validar entradas para mejorar la experiencia, sin sustituir la validación del servidor.
- Enviar solicitudes al backend y mostrar únicamente recomendaciones validadas.
- Guardar y eliminar el historial local; conservar el contexto al navegar al detalle.
- Evitar que respuestas tardías restauren conversaciones eliminadas.

### 3.2. Backend

- Validar solicitudes, formatos, longitudes y rangos.
- Coordinar las integraciones y aplicar las reglas de negocio.
- Verificar identificadores, fechas originales y origen de las series.
- Filtrar candidatos, eliminar duplicados y construir respuestas fundamentadas.
- Proteger credenciales y controlar tiempos de espera y errores externos.
- Procesar cada solicitud de manera independiente, sin persistir conversaciones.

### 3.3. Motor de recomendaciones

Se propone una estrategia inicial basada en contenido: comparar géneros, fechas, sinopsis y temáticas disponibles con las preferencias expresadas. Los filtros explícitos serán obligatorios; las preferencias flexibles servirán para ordenar candidatos. No se requiere entrenar un modelo propio.

### 3.4. Adaptador conversacional

Interpretará lenguaje natural y solicitará aclaraciones cuando existan contradicciones. El modelo de IA no será la fuente de verdad de los títulos: toda serie sugerida deberá verificarse mediante el proveedor de metadatos antes de presentarse. Las explicaciones se limitarán a atributos comprobados.

### 3.5. Integraciones externas

Cada proveedor tendrá un adaptador sencillo para encapsular sus consultas, autenticación, normalización y errores. La lógica de negocio no dependerá directamente del formato particular de un proveedor.

## 7. Flujo técnico

1. El usuario abre Miralune y el frontend recupera el historial local, si existe.
2. El usuario escribe una consulta o selecciona filtros.
3. El frontend prepara el mensaje, las preferencias y únicamente el contexto pertinente; muestra el indicador de carga.
4. El backend valida tipos, longitudes, fechas y rangos. Si la entrada es inválida, devuelve un error comprensible.
5. El adaptador conversacional interpreta los gustos. Si hay criterios contradictorios, solicita aclaración sin inventar resultados.
6. El backend consulta el proveedor de series y normaliza su respuesta.
7. Se verifican identificadores, fechas originales y origen; se descartan candidatos inválidos, duplicados y títulos no verificables.
8. El motor aplica los filtros explícitos y ordena los candidatos según su relación con las preferencias.
9. Se construye una respuesta con series verificadas y motivos fundamentados. Si interviene IA en la redacción, se comprueba que no introduzca títulos o datos ajenos a los candidatos validados.
10. El frontend presenta mensajes y tarjetas con carátulas originales o marcadores neutros.
11. El historial se actualiza localmente, siempre que la conversación siga vigente.
12. El usuario puede consultar detalles, refinar preferencias o eliminar el historial previa confirmación.

Si no existen coincidencias, se informa y se permite ajustar criterios opcionales. Si falla un proveedor, se informa el fallo sin sustituir datos reales por datos inventados.

## 8. Diseño de datos

| Dato | Tipo | Origen | Destino |
|---|---|---|---|
| Mensaje | Texto | Usuario | Backend y adaptador conversacional |
| Preferencias | Objeto con géneros, años y texto | Usuario y chatbot | Motor de recomendaciones |
| Contexto pertinente | Lista de mensajes | Historial local | Backend, temporalmente |
| Serie | Objeto con ID, fuente, título, fecha original y metadatos | Proveedor externo | Motor y frontend |
| Recomendación | Serie y motivo verificable | Motor | Chat y tarjetas |
| Conversación local | Objeto con mensajes y preferencias | Frontend | Almacenamiento del navegador |
| Error | Código y mensaje | Backend o frontend | Interfaz |

**Validaciones:** tipos, longitudes, identificadores, fechas originales, rango dinámico, origen de datos y campos opcionales. No se inventarán valores faltantes.

Se propone REST con JSON. Los siguientes contratos son conceptuales, no código implementado.

| Método y ruta propuesta | Entrada | Resultado |
|---|---|---|
| POST /api/recommendations | Mensaje, preferencias y contexto limitado | Respuesta conversacional, aclaración o recomendaciones verificadas |
| GET /api/series/{source}/{id} | Proveedor e identificador | Detalle validado o error controlado |

Las entidades Serie, Preferencias, Mensaje, Recomendación y Conversación local conservarán los atributos de la sección 11 de PROJECT_SPEC.md. Se utilizará camelCase en JSON y snake_case internamente en Python. Los campos opcionales ausentes no se inventarán.

Los límites de mensajes, contexto y cantidad de resultados se acordarán antes de implementar. Los errores tendrán un código y un mensaje comprensible; se propone utilizar estados HTTP coherentes con la naturaleza del fallo.

Se propone useState para estados sencillos y useReducer para la conversación si su complejidad lo requiere. Context se utilizará solo cuando sea necesario compartir información entre vistas.

El historial conservará mensajes, preferencias y referencias necesarias, sujeto a los términos de los proveedores. Se propone localStorage por su sencillez, con un formato versionado y manejo de errores de lectura, escritura y capacidad.

La persistencia será independiente por navegador, perfil y origen. No habrá sincronización entre dispositivos ni catálogo propio. Al eliminar el historial se limpiarán el almacenamiento y el contexto en memoria, se invalidarán solicitudes pendientes y se impedirá que una respuesta tardía lo restaure. Si falla el almacenamiento, se continuará temporalmente en memoria y se informará al usuario.

El backend no persistirá mensajes ni respuestas. La eliminación local no implica eliminación de datos retenidos por proveedores externos.

## 9. Diseño de interfaz

| Vista | Responsabilidad |
|---|---|
| Inicio | Explicar el propósito y permitir iniciar una consulta |
| Chat y recomendaciones | Mensajes, filtros, carga, errores, tarjetas y eliminación del historial |
| Detalle de serie | Mostrar información verificada y permitir regresar al chat |
| Información y privacidad | Explicar almacenamiento, terceros y atribuciones |

Se diseñará una interfaz responsive con navegación por teclado, foco visible y etiquetas accesibles. Se comprobarán los anchos de 360, 768 y 1280 píxeles y los navegadores definidos en RNF-06. No se propone una aplicación nativa en esta versión; debe confirmarse que el alcance móvil responsive satisface al equipo.

## 10. Fases de implementación

### Fase 1 — Preparación
- **Objetivo:** acordar alcance y herramientas.
- **Actividades:** aprobar documentos, resolver clarificaciones, verificar proveedores y licencias, fijar versiones compatibles, preparar repositorio y entornos.
- **Entregable:** configuración inicial reproducible y decisiones aprobadas.

### Fase 2 — Núcleo funcional
- **Objetivo:** construir la lógica de recomendaciones verificables.
- **Actividades:** definir contratos, validaciones, integración de metadatos, filtros temporales, ordenamiento y adaptador conversacional.
- **Entregable:** backend funcional con pruebas unitarias y proveedores simulados.

### Fase 3 — Interfaz e integración
- **Objetivo:** conectar la experiencia de usuario con el backend.
- **Actividades:** desarrollar inicio, chat, filtros, tarjetas, detalle, historial local, estados de carga y errores; integrar la API y verificar diseño responsive.
- **Entregable:** recorrido completo desde consulta hasta recomendación y eliminación del historial.

### Fase 4 — Validación y entrega
- **Objetivo:** comprobar requisitos y preparar la entrega.
- **Actividades:** ejecutar pruebas funcionales, integración, seguridad, rendimiento y accesibilidad; corregir fallos y actualizar README y atribuciones.
- **Entregable:** aplicación ejecutable con evidencias de pruebas y revisión del equipo.

Las tareas concretas y sus responsables se definirán en TASKS.md.

## 11. Estrategia de pruebas

Se utilizarán datos controlados y adaptadores simulados para evitar depender de servicios externos durante las pruebas habituales. Las pruebas reales de integración se ejecutarán únicamente con proveedores y credenciales autorizados.

| Tipo | Qué se verificará | Referencia de la especificación |
|---|---|---|
| Unitaria backend | Validación, normalización, fechas, filtros, duplicados | CP-04 a CP-11, CP-14, CP-27, CP-31 |
| Unitaria frontend | Estado, carátulas, almacenamiento y eliminación | CP-12, CP-13, CP-16, CP-18, CP-19, CP-23 |
| Integración | API, proveedores simulados, chat y refinamiento | CP-02, CP-03, CP-05, CP-20, CP-21, CP-22, CP-30 |
| Funcional | Inicio, navegación, detalle e historial independiente | CP-01, CP-15 a CP-18 |
| Seguridad y privacidad | Ausencia de secretos y persistencia de mensajes en servidor | CP-25, CP-26 |
| Rendimiento | Carga inicial, indicador y tiempo máximo | CP-28 |
| Compatibilidad y accesibilidad | Navegadores, tamaños de pantalla, teclado y contraste | CP-24, CP-29 |

### Casos prioritarios

- Excluir estrenos de 2016 y aceptar candidatos elegibles desde el 1 de enero de 2017.
- Excluir series del próximo año y comprobar el cambio dinámico del año máximo mediante un reloj controlado.
- Excluir fechas futuras dentro del año actual si se aprueba RN-05.
- Rechazar títulos inventados y series sin fecha verificable.
- Respetar filtros explícitos y solicitar aclaración ante contradicciones.
- Mostrar marcadores neutros si faltan carátulas originales.
- Recuperar el historial en el mismo navegador y eliminarlo sin que reaparezca tras recargar o recibir una respuesta tardía.
- Controlar fallos externos, ausencia de resultados y almacenamiento bloqueado.

Cada prueba registrará ID, requisito, datos de entrada, resultado esperado, resultado obtenido y estado. Los 31 casos CP-01 a CP-31 y los criterios CA-01 a CA-18 de PROJECT_SPEC.md serán la referencia de verificación; los condicionados a decisiones pendientes se ajustarán tras su aprobación. Ninguna prueba se considera ejecutada en esta etapa.

| Requisito | Prueba | Evidencia prevista |
|---|---|---|
| RF-01 | CP-01: acceso al inicio | Captura y registro funcional |
| RF-07 | CP-07 a CP-11 y CP-27 condicionado | Informe de pruebas unitarias |
| RF-11 | CP-18 y CP-19: eliminación | Registro de prueba y recarga |
| RF-13 | CP-21 y CP-22 | Informe de integración |
| RNF-03 | CP-25 | Registro de inspección sin secretos |

## 12. Seguridad y errores

- Mantener claves y tokens privados exclusivamente en el backend, mediante variables de entorno; excluir .env del repositorio y documentar variables sin secretos en .env.example.
- Considerar públicas todas las variables VITE_. Restringir CORS a orígenes autorizados y utilizar HTTPS en producción.
- Validar entradas y respuestas externas, limitar solicitudes y contexto, establecer tiempos de espera y evitar registrar conversaciones o credenciales.
- Tratar mensajes y contenido externo como datos, no como instrucciones capaces de alterar las reglas del aplicativo.
- Mostrar mensajes claros ante fallos de red, validación, límites de proveedor, datos incompletos y ausencia de resultados. No exponer trazas internas al usuario.
- Verificar términos, licencias, atribuciones y retención de datos de terceros antes de integrar servicios; aplicar la normativa de privacidad pertinente.

Los objetivos propuestos de la especificación son carga inicial en 3 segundos, indicador en menos de 1 segundo y respuesta o aviso de espera agotada en máximo 30 segundos. El entorno de medición y estos umbrales deben aprobarse. La ausencia de autenticación en la primera versión también debe confirmarse.

## 13. Riesgos técnicos

| Riesgo o incertidumbre | Impacto | Mitigación |
|---|---|---|
| Datos inventados por IA | Alto | Verificar candidatos y limitar respuestas a información comprobada |
| Caídas, cuotas o costos externos | Alto | Revisar condiciones, controlar tiempos de espera y fallos |
| Retención de conversaciones por terceros | Alto | Evaluar políticas y comunicar límites de eliminación local |
| Pérdida de almacenamiento del navegador | Medio | Informar limitación y continuar en memoria cuando sea posible |
| Complejidad técnica innecesaria | Medio | Mantener un backend modular único y dependencias mínimas |
| Diferencia entre web móvil y app nativa | Alto | Confirmar alcance antes de implementar |
| PostgreSQL propuesto en la constitución | Medio | Actualizar la propuesta para reflejar que no se requiere base de datos propia |

Antes de iniciar, confirmar TypeScript, FastAPI, proveedor de series, modelo de IA, estrategia basada en contenido, almacenamiento local, límites de contexto, objetivos de rendimiento, control de versiones, ausencia de cuentas, alcance móvil y RN-05 sobre estrenos futuros dentro del año actual. La selección de proveedores depende de comprobar sus condiciones reales; este plan no afirma haberlas verificado.

## 14. Control de versiones

**Repositorio:** Miralune (nombre propuesto; URL pendiente).

**Rama principal:** main (propuesta).

**Estrategia de trabajo:** colaborativa, Luz Karime y Sebastian Morelo.

### Convenciones

- Utilizar Git y GitHub, sujetos a aprobación.
- Mantener main para versiones estables y develop para integración, conforme a la constitución.
- Crear ramas feature/, fix/, hotfix/, docs/ o refactor/ según la naturaleza de la tarea.
- Usar Conventional Commits con el formato tipo(alcance): descripción. Ejemplo: docs(plan): definir arquitectura inicial.
- Realizar commits pequeños y relacionados con una tarea verificable.
- Integrar al finalizar cada tarea, mediante Pull Request, resolución de conflictos, pruebas aplicables y revisión por el otro integrante.
- No modificar main directamente ni permitir que un agente de IA apruebe sus propios cambios o publique sin autorización.
- Excluir secretos, node_modules, entornos virtuales, cachés y archivos temporales.

## 15. Criterios para iniciar la implementación

- [ ] La constitución está aprobada y refleja la ausencia de base de datos propia.
- [ ] Los requisitos están claros y la especificación está aprobada.
- [ ] Se resolvieron las ambigüedades importantes, incluyendo alcance móvil y autenticación.
- [ ] La arquitectura está definida y aprobada.
- [ ] Las tecnologías y proveedores están seleccionados y sus condiciones verificadas.
- [ ] Los módulos tienen responsabilidades claras.
- [ ] Se definieron las pruebas necesarias y sus condiciones de ejecución.
- [ ] El plan fue revisado y aprobado por ambos integrantes.
- [ ] TASKS.md contiene las tareas autorizadas para comenzar.

## 16. Decisiones técnicas

Todas las decisiones de esta tabla son propuestas de planificación, salvo las tecnologías ya definidas en los documentos de referencia.

| Fecha | Decisión | Justificación | Responsable |
|---|---|---|---|
| 2026-11-25 | React + Vite y Python (Definidas) | Tecnologías establecidas en la constitución | Equipo: Luz Karime y Sebastian Morelo |
| 2026-11-25 | Cliente-servidor monolítico modular (Propuesta) | Simplicidad y separación de responsabilidades | Equipo: Luz Karime y Sebastian Morelo |
| 2026-11-25 | TypeScript y FastAPI (Propuesta) | Tipado y validación de contratos | Equipo: Luz Karime y Sebastian Morelo |
| 2026-11-25 | REST y JSON (Propuesta) | Comunicación sencilla entre aplicaciones | Equipo: Luz Karime y Sebastian Morelo |
| 2026-11-25 | TMDB API (Propuesta) | Fuente candidata de metadatos y carátulas | Equipo: Luz Karime y Sebastian Morelo |
| 2026-11-25 | Recomendaciones basadas en contenido (Propuesta) | Evita entrenamiento propio y almacenamiento de perfiles | Equipo: Luz Karime y Sebastian Morelo |
| 2026-11-25 | Modelo de IA desacoplado (Propuesta; proveedor pendiente) | Permite seleccionar un proveedor sin modificar reglas de negocio | Equipo: Luz Karime y Sebastian Morelo |
| 2026-11-25 | Sin base de datos propia (Alcance especificado; ajuste constitucional pendiente) | Consultas externas y conversaciones locales según especificación | Equipo: Luz Karime y Sebastian Morelo |
| 2026-11-25 | localStorage (Propuesta) | Persistencia local sencilla | Equipo: Luz Karime y Sebastian Morelo |
| 2026-11-25 | Web responsive (Propuesta) | Una interfaz para computador y móvil | Equipo: Luz Karime y Sebastian Morelo |
| 2026-11-25 | Pytest y Vitest (Propuesta) | Verificación reproducible | Equipo: Luz Karime y Sebastian Morelo |
| 2026-11-25 | Git y GitHub (Propuesta) | Colaboración y trazabilidad | Equipo: Luz Karime y Sebastian Morelo |


## 17. Resultado esperado

Miralune quedará organizada en un frontend React y un backend Python modular, conectados mediante una API. Los usuarios podrán expresar preferencias, conversar con el chatbot, recibir recomendaciones de series reales estrenadas desde 2017 hasta el año actual, consultar detalles y conservar o eliminar su historial local.

La implementación deberá proteger las credenciales, validar datos externos, mostrar carátulas originales cuando estén disponibles, gestionar fallos sin inventar información y cumplir los requisitos, criterios de aceptación y pruebas aprobados en PROJECT_SPEC.md. No se incorporará persistencia centralizada ni funcionalidades fuera del alcance.

El resultado técnico deberá poder instalarse y ejecutarse siguiendo README.md, mantener documentación actualizada y contar con evidencias de pruebas y revisión del equipo.

---

**Estado final:** Borrador. Pendiente de aprobación. No se ha generado código de implementación ni ejecutado pruebas.
