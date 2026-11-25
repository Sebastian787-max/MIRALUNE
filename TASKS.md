# TASKS.md — Miralune

> **Etapa SDD:** planificación de tareas e implementación  
> **Propósito:** dividir el plan en tareas pequeñas, ordenadas y verificables.

| Campo | Valor |
|---|---|
| Proyecto | Miralune |
| Versión | 1.0.0 |
| Responsables | Luz Karime - Sebastian Morelo |
| Fecha | 2026-11-25 |
| Estado | Borrador |

## 1. Objetivo

Organizar la construcción de Miralune conforme a PLAN.md y PROJECT_SPEC.md, ambos versión 1.0.0 y en borrador. Las cinco fases de este listado separan la validación y entrega que el plan agrupa en su cuarta fase. Las rutas son previstas, no archivos ya creados. No se autoriza implementación hasta aprobar las decisiones pendientes. La asignación individual se acordará entre ambos integrantes.

## 2. Reglas de ejecución

1. Leer `CONSTITUTION.md`, `PROJECT_SPEC.md` y `PLAN.md`.
2. Seguir el orden y las dependencias; completar la aprobación de T03 antes de programar.
3. Implementar una tarea verificable a la vez.
4. No agregar funcionalidades ni dependencias no aprobadas.
5. Ejecutar y registrar las pruebas disponibles, distinguiendo simulaciones de consultas reales.
6. Marcar una tarea completa solo con evidencia y revisión del otro integrante.
7. Registrar bloqueos y defectos; no aprobar cambios propios mediante IA.
8. Aplicar las convenciones de ramas y commits del plan aprobado.

## 3. Estados

- **Pendiente:** aún no iniciada.
- **En progreso:** en desarrollo.
- **Bloqueada:** no puede continuar.
- **En revisión:** requiere validación.
- **Completada:** cumple el criterio y tiene evidencia.

## 4. Fase 1 — Preparación

### T01 — Revisar y aprobar documentos

- **Objetivo:** Resolver las decisiones pendientes antes de programar.
- **Requisitos relacionados:** RNF-05, RNF-12.
- **Archivos afectados:** `CONSTITUTION.md`, `PROJECT_SPEC.md`, `PLAN.md`, `TASKS.md`.
- **Dependencias:** Ninguna.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Confirmar alcance móvil, ausencia de cuentas y base de datos propia; ajustar la constitución.
- [ ] Acordar RN-05, límites de contexto, rendimiento y criterios de prueba.
- [ ] Registrar aprobación de ambos responsables.

**Resultado esperado y criterio de finalización:** Documentos coherentes y decisiones de alcance registradas; aprobación técnica final en T03.

**Evidencia prevista:** Acta de revisión. Pendiente de obtención.

### T02 — Evaluar proveedores externos

- **Objetivo:** Seleccionar proveedores de metadatos e IA.
- **Requisitos relacionados:** RF-05, RF-03, RNF-09.
- **Archivos afectados:** `docs/`.
- **Dependencias:** T01.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Evaluar TMDB y alternativas autorizadas, licencias, atribuciones, cuotas y costos.
- [ ] Revisar retención de mensajes y condiciones de privacidad.

**Resultado esperado y criterio de finalización:** Proveedores seleccionados y condiciones verificadas por el equipo.

**Evidencia prevista:** Registro de evaluación y aprobación. Pendiente de obtención.

### T03 — Seleccionar tecnologías y versiones

- **Objetivo:** Fijar herramientas compatibles.
- **Requisitos relacionados:** RNF-05, RNF-12.
- **Archivos afectados:** `PLAN.md`, `PROJECT_SPEC.md`, `TASKS.md`.
- **Dependencias:** T02.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Confirmar TypeScript, FastAPI, REST, localStorage y herramientas de pruebas.
- [ ] Acordar versiones, estrategia de recomendación y control de versiones.
- [ ] Aprobar plan y tareas antes de iniciar código.

**Resultado esperado y criterio de finalización:** Checklist de inicio de PLAN.md aprobado.

**Evidencia prevista:** Matriz de versiones y aprobación. Pendiente de obtención.

### T04 — Preparar repositorio

- **Objetivo:** Organizar trabajo colaborativo.
- **Requisitos relacionados:** RNF-05.
- **Archivos afectados:** `README.md`, `.gitignore`.
- **Dependencias:** T03.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Crear repositorio y ramas main/develop si se aprueba GitHub.
- [ ] Configurar exclusiones y revisión mediante Pull Request.

**Resultado esperado y criterio de finalización:** Repositorio accesible a ambos integrantes y sin secretos.

**Evidencia prevista:** URL y commit inicial. Pendiente de obtención.

### T05 — Preparar frontend

- **Objetivo:** Configurar React y Vite.
- **Requisitos relacionados:** RF-01, RNF-05.
- **Archivos afectados:** `frontend/package.json`, `frontend/src/`.
- **Dependencias:** T04.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Inicializar proyecto con lenguaje aprobado.
- [ ] Configurar herramientas de formato y pruebas.

**Resultado esperado y criterio de finalización:** Frontend inicial ejecutable y compilable.

**Evidencia prevista:** Registro de ejecución y compilación. Pendiente de obtención.

### T06 — Preparar backend

- **Objetivo:** Configurar Python y servidor aprobado.
- **Requisitos relacionados:** RF-04, RNF-03, RNF-05.
- **Archivos afectados:** `backend/app/main.py`, `backend/requirements.txt`, `backend/.env.example`.
- **Dependencias:** T04.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Preparar entorno virtual y dependencias fijadas.
- [ ] Configurar variables de entorno sin secretos y herramientas de prueba.

**Resultado esperado y criterio de finalización:** Backend inicial ejecutable; configuración reproducible.

**Evidencia prevista:** Registro de arranque y revisión de exclusiones. Pendiente de obtención.

## 5. Fase 2 — Desarrollo del núcleo

### T07 — Definir contratos de intercambio

- **Objetivo:** Definir entradas y salidas REST/JSON.
- **Requisitos relacionados:** RF-02, RF-03, RF-04, RF-08.
- **Archivos afectados:** `backend/app/schemas/`, `docs/`.
- **Dependencias:** T06.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Documentar preferencias, mensajes, contexto, series y errores.
- [ ] Definir campos opcionales y límites aprobados.

**Resultado esperado y criterio de finalización:** Contratos documentados y consistentes entre cliente y servidor.

**Evidencia prevista:** Contratos revisados. Pendiente de obtención.

### T08 — Validar solicitudes

- **Objetivo:** Rechazar entradas inválidas.
- **Requisitos relacionados:** RF-04, RNF-03.
- **Archivos afectados:** `backend/app/schemas/`, `backend/app/api/`, `backend/tests/`.
- **Dependencias:** T07.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Validar tipos, longitudes, formatos y rangos.
- [ ] Probar mensajes vacíos y tipos inválidos.

**Resultado esperado y criterio de finalización:** CP-04 superado; errores comprensibles.

**Evidencia prevista:** Informe CP-04. Pendiente de obtención.

### T09 — Integrar proveedor de series

- **Objetivo:** Consultar metadatos reales.
- **Requisitos relacionados:** RF-05, RNF-11.
- **Archivos afectados:** `backend/app/integrations/`, `backend/tests/`.
- **Dependencias:** T08.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Implementar adaptador del proveedor aprobado.
- [ ] Normalizar identificadores, fechas, origen y carátulas; validar respuestas.

**Resultado esperado y criterio de finalización:** CP-05 superado con datos controlados y origen conservado.

**Evidencia prevista:** Informe CP-05 y consulta autorizada. Pendiente de obtención.

### T10 — Aplicar filtro temporal

- **Objetivo:** Restringir series al rango permitido.
- **Requisitos relacionados:** RF-07, RNF-11.
- **Archivos afectados:** `backend/app/recommendations/`, `backend/tests/`.
- **Dependencias:** T09.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Validar fecha original y calcular año máximo dinámicamente.
- [ ] Excluir fechas no verificables y aplicar RN-05 solo si se aprueba.

**Resultado esperado y criterio de finalización:** CP-07 a CP-11 superados; CP-27 según decisión aprobada.

**Evidencia prevista:** Informe de pruebas con reloj controlado. Pendiente de obtención.

### T11 — Seleccionar y ordenar recomendaciones

- **Objetivo:** Generar recomendaciones fundamentadas.
- **Requisitos relacionados:** RF-06, RF-07, RNF-11.
- **Archivos afectados:** `backend/app/recommendations/`, `backend/tests/`.
- **Dependencias:** T10.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Aplicar filtros explícitos y ordenar por afinidad.
- [ ] Eliminar duplicados y descartar títulos no verificados.

**Resultado esperado y criterio de finalización:** CP-06, CP-14 y CP-31 superados.

**Evidencia prevista:** Informe unitario. Pendiente de obtención.

### T12 — Integrar adaptador conversacional

- **Objetivo:** Interpretar preferencias en lenguaje natural.
- **Requisitos relacionados:** RF-03, RF-12, RNF-09.
- **Archivos afectados:** `backend/app/integrations/`, `backend/app/services/`, `backend/tests/`.
- **Dependencias:** T11.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Enviar solo contexto pertinente al proveedor aprobado.
- [ ] Solicitar aclaración ante contradicciones y no aceptar títulos sin verificar.

**Resultado esperado y criterio de finalización:** CP-03 y CP-30 superados.

**Evidencia prevista:** Pruebas con proveedor simulado. Pendiente de obtención.

### T13 — Refinar preferencias

- **Objetivo:** Actualizar criterios con nuevos mensajes.
- **Requisitos relacionados:** RF-12, RF-02.
- **Archivos afectados:** `backend/app/services/`, `backend/tests/`.
- **Dependencias:** T12.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Aplicar nuevas preferencias explícitas sin incumplir restricciones.
- [ ] Verificar cambio de género y conservación del contexto pertinente.

**Resultado esperado y criterio de finalización:** CP-20 superado.

**Evidencia prevista:** Informe CP-20. Pendiente de obtención.

### T14 — Exponer operaciones de recomendación y detalle

- **Objetivo:** Conectar contratos y servicios.
- **Requisitos relacionados:** RF-04, RF-06, RF-09.
- **Archivos afectados:** `backend/app/api/`, `backend/app/services/`.
- **Dependencias:** T13.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Coordinar validación, conversación y recomendaciones.
- [ ] Consultar detalle por identificador y devolver errores definidos.

**Resultado esperado y criterio de finalización:** API devuelve resultados verificables o errores según contrato.

**Evidencia prevista:** Pruebas de integración de API. Pendiente de obtención.

### T15 — Controlar fallos externos

- **Objetivo:** Gestionar errores y tiempos de espera.
- **Requisitos relacionados:** RF-13, RNF-02, RNF-10.
- **Archivos afectados:** `backend/app/core/`, `backend/app/integrations/`, `backend/tests/`.
- **Dependencias:** T14.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Controlar desconexión, cuotas, respuestas inválidas y ausencia de resultados.
- [ ] Evitar trazas internas y datos inventados.

**Resultado esperado y criterio de finalización:** CP-21 y CP-22 superados en backend.

**Evidencia prevista:** Informe de fallos simulados. Pendiente de obtención.

## 6. Fase 3 — Interfaz e integración

### T16 — Construir inicio y navegación

- **Objetivo:** Permitir acceder al chat.
- **Requisitos relacionados:** RF-01, RNF-04.
- **Archivos afectados:** `frontend/src/pages/`, `frontend/src/routes/`.
- **Dependencias:** T05, T07.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Crear vista inicial y navegación.
- [ ] Verificar acceso directo a consulta.

**Resultado esperado y criterio de finalización:** CP-01 superado.

**Evidencia prevista:** Captura y prueba funcional. Pendiente de obtención.

### T17 — Construir filtros de preferencias

- **Objetivo:** Capturar género, año y gustos.
- **Requisitos relacionados:** RF-02.
- **Archivos afectados:** `frontend/src/features/recommendations/`.
- **Dependencias:** T16.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Crear controles y validaciones de interfaz.
- [ ] Verificar criterios preparados para la solicitud.

**Resultado esperado y criterio de finalización:** CP-02 superado.

**Evidencia prevista:** Prueba de controles. Pendiente de obtención.

### T18 — Construir interfaz del chatbot

- **Objetivo:** Permitir conversación y refinamiento.
- **Requisitos relacionados:** RF-03, RF-12.
- **Archivos afectados:** `frontend/src/features/chat/`, `frontend/src/hooks/`.
- **Dependencias:** T17.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Crear entrada de mensajes y representación de respuestas.
- [ ] Administrar contexto y preferencias vigentes con hooks.

**Resultado esperado y criterio de finalización:** Usuario puede enviar mensajes y ajustar preferencias.

**Evidencia prevista:** Prueba de componentes. Pendiente de obtención.

### T19 — Mostrar tarjetas de series

- **Objetivo:** Presentar recomendaciones verificadas.
- **Requisitos relacionados:** RF-08.
- **Archivos afectados:** `frontend/src/features/series/`, `frontend/src/components/`.
- **Dependencias:** T18.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Mostrar metadatos y motivo de recomendación.
- [ ] Mostrar carátula original o marcador neutro.

**Resultado esperado y criterio de finalización:** CP-12 y CP-13 superados.

**Evidencia prevista:** Capturas y pruebas. Pendiente de obtención.

### T20 — Construir vista de detalle

- **Objetivo:** Consultar información adicional.
- **Requisitos relacionados:** RF-09.
- **Archivos afectados:** `frontend/src/pages/`, `frontend/src/features/series/`.
- **Dependencias:** T19.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Mostrar detalle y gestionar datos no disponibles.
- [ ] Conservar conversación al regresar al chat.

**Resultado esperado y criterio de finalización:** CP-15 superado.

**Evidencia prevista:** Prueba de navegación. Pendiente de obtención.

### T21 — Guardar y recuperar historial local

- **Objetivo:** Conservar conversaciones por navegador y perfil.
- **Requisitos relacionados:** RF-10, RNF-09.
- **Archivos afectados:** `frontend/src/features/chat/`, `frontend/src/utils/`.
- **Dependencias:** T18.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Guardar y recuperar mensajes localmente.
- [ ] Gestionar almacenamiento bloqueado y continuar en memoria cuando sea posible.

**Resultado esperado y criterio de finalización:** CP-16, CP-17 y CP-23 superados.

**Evidencia prevista:** Pruebas de almacenamiento. Pendiente de obtención.

### T22 — Eliminar historial y contexto

- **Objetivo:** Borrar conversaciones de forma controlada.
- **Requisitos relacionados:** RF-11, RNF-09.
- **Archivos afectados:** `frontend/src/features/chat/`, `frontend/src/hooks/`.
- **Dependencias:** T21.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Solicitar confirmación y limpiar almacenamiento y estado activo.
- [ ] Impedir que respuestas tardías restauren mensajes eliminados.

**Resultado esperado y criterio de finalización:** CP-18 y CP-19 superados.

**Evidencia prevista:** Prueba de recarga y respuesta tardía. Pendiente de obtención.

### T23 — Integrar frontend y backend

- **Objetivo:** Completar recorrido de consulta.
- **Requisitos relacionados:** RF-02, RF-03, RF-04, RF-06, RF-08, RF-09, RF-12.
- **Archivos afectados:** `frontend/src/services/`, `frontend/src/features/`.
- **Dependencias:** T15, T20, T22.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Conectar solicitudes REST con servicios del backend.
- [ ] Mostrar resultados validados y actualizar preferencias.

**Resultado esperado y criterio de finalización:** Consulta, refinamiento y detalle funcionan de extremo a extremo.

**Evidencia prevista:** Registro de integración. Pendiente de obtención.

### T24 — Mostrar estados de carga y errores

- **Objetivo:** Informar estados sin bloquear la interfaz.
- **Requisitos relacionados:** RF-13, RNF-02, RNF-10.
- **Archivos afectados:** `frontend/src/components/`, `frontend/src/features/`.
- **Dependencias:** T23.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Mostrar carga, errores, ausencia de resultados y reintento cuando corresponda.
- [ ] Finalizar carga ante errores o espera agotada.

**Resultado esperado y criterio de finalización:** CP-21 y CP-22 superados en recorrido completo.

**Evidencia prevista:** Pruebas de interfaz con fallos simulados. Pendiente de obtención.

### T25 — Adaptar interfaz y accesibilidad

- **Objetivo:** Garantizar uso en computador y móvil web.
- **Requisitos relacionados:** RNF-04, RNF-06, RNF-07, RNF-08.
- **Archivos afectados:** `frontend/src/components/`, `frontend/src/pages/`, `frontend/src/features/`.
- **Dependencias:** T24.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Ajustar vistas a 360, 768 y 1280 px.
- [ ] Revisar teclado, foco, etiquetas y contraste.

**Resultado esperado y criterio de finalización:** CP-24 y CP-29 superados en entornos aprobados.

**Evidencia prevista:** Capturas y registro de accesibilidad. Pendiente de obtención.

### T26 — Presentar privacidad y atribuciones

- **Objetivo:** Informar origen de datos y tratamiento del chat.
- **Requisitos relacionados:** RNF-09, RF-08.
- **Archivos afectados:** `frontend/src/pages/`, `docs/`.
- **Dependencias:** T02, T25.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Mostrar atribuciones exigidas por proveedores.
- [ ] Explicar almacenamiento local y límites de eliminación frente a terceros.

**Resultado esperado y criterio de finalización:** Información visible y conforme a condiciones aprobadas.

**Evidencia prevista:** Revisión de textos y capturas. Pendiente de obtención.

## 7. Fase 4 — Pruebas

### T27 — Verificar seguridad y privacidad

- **Objetivo:** Comprobar protección de datos y credenciales.
- **Requisitos relacionados:** RNF-03, RNF-09.
- **Archivos afectados:** `backend/app/core/`, `frontend/`, `backend/tests/`.
- **Dependencias:** T26.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Inspeccionar compilación, solicitudes y almacenamiento sin revelar secretos.
- [ ] Verificar CORS, HTTPS en producción y ausencia de persistencia de conversaciones en servidor.

**Resultado esperado y criterio de finalización:** CP-25 y CP-26 superados; controles aplicables verificados.

**Evidencia prevista:** Informe de seguridad sin secretos. Pendiente de obtención.

### T28 — Ejecutar pruebas unitarias y de integración

- **Objetivo:** Consolidar pruebas automatizadas.
- **Requisitos relacionados:** RNF-12, RF-02 a RF-13.
- **Archivos afectados:** `backend/tests/`, `frontend/src/tests/`, `docs/`.
- **Dependencias:** T27.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Ejecutar casos con proveedores simulados y pruebas reales autorizadas.
- [ ] Registrar resultados y defectos; no confundir simulación con datos reales.

**Resultado esperado y criterio de finalización:** Casos unitarios e integración aplicables registrados.

**Evidencia prevista:** Informes de ejecución. Pendiente de obtención.

### T29 — Verificar rendimiento

- **Objetivo:** Medir tiempos acordados.
- **Requisitos relacionados:** RNF-01, RNF-02.
- **Archivos afectados:** `docs/`.
- **Dependencias:** T28.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Medir carga inicial, indicador y tiempo máximo de solicitud.
- [ ] Comparar con umbrales aprobados y registrar entorno.

**Resultado esperado y criterio de finalización:** CP-28 ejecutado y resultados comparados con objetivos aprobados.

**Evidencia prevista:** Registro de mediciones. Pendiente de obtención.

### T30 — Ejecutar aceptación y regresión

- **Objetivo:** Validar la totalidad del alcance.
- **Requisitos relacionados:** RF-01 a RF-13, RNF-01 a RNF-12.
- **Archivos afectados:** `docs/`, `backend/tests/`, `frontend/src/tests/`.
- **Dependencias:** T29.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Completar matriz CP-01 a CP-31 y CA-01 a CA-18, respetando casos condicionados.
- [ ] Corregir defectos bloqueantes en tareas vinculadas y repetir pruebas afectadas.

**Resultado esperado y criterio de finalización:** Todos los requisitos obligatorios aprobados tienen evidencia satisfactoria; casos no aplicables justificados.

**Evidencia prevista:** Matriz de pruebas y aceptación. Pendiente de obtención.

## 8. Fase 5 — Documentación y entrega

### T31 — Completar documentación

- **Objetivo:** Documentar instalación y funcionamiento.
- **Requisitos relacionados:** RNF-05, RNF-12, RNF-09.
- **Archivos afectados:** `README.md`, `docs/`.
- **Dependencias:** T30.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Registrar versiones, configuración, ejecución y pruebas.
- [ ] Documentar atribuciones, privacidad y limitaciones conocidas.

**Resultado esperado y criterio de finalización:** Otro integrante puede ejecutar la aplicación siguiendo README.md.

**Evidencia prevista:** README revisado y registro de ejecución. Pendiente de obtención.

### T32 — Preparar entrega final

- **Objetivo:** Entregar aplicación revisada.
- **Requisitos relacionados:** RF-01 a RF-13, RNF-01 a RNF-12.
- **Archivos afectados:** `README.md`, `TASKS.md`, `docs/`.
- **Dependencias:** T31.
- **Responsable:** Por asignar (equipo).
- **Estado:** Pendiente.

**Actividades:**

- [ ] Revisar restricciones, evidencias y repositorio.
- [ ] Preparar demostración y obtener aprobación de ambos responsables.

**Resultado esperado y criterio de finalización:** Definición de terminado de PROJECT_SPEC.md satisfecha y entrega aprobada.

**Evidencia prevista:** Acta de entrega y demostración. Pendiente de obtención.

## 9. Registro de errores

No se han ejecutado pruebas ni registrado defectos todavía. Agregar una fila por cada defecto detectado.

| ID | Error | Tarea relacionada | Estado |
|---|---|---|---|

## 10. Resumen de avance

| Tarea | Responsable | Estado | Evidencia |
|---|---|---|---|
| T01 — Revisar y aprobar documentos | Por asignar | Pendiente | Pendiente |
| T02 — Evaluar proveedores externos | Por asignar | Pendiente | Pendiente |
| T03 — Seleccionar tecnologías y versiones | Por asignar | Pendiente | Pendiente |
| T04 — Preparar repositorio | Por asignar | Pendiente | Pendiente |
| T05 — Preparar frontend | Por asignar | Pendiente | Pendiente |
| T06 — Preparar backend | Por asignar | Pendiente | Pendiente |
| T07 — Definir contratos de intercambio | Por asignar | Pendiente | Pendiente |
| T08 — Validar solicitudes | Por asignar | Pendiente | Pendiente |
| T09 — Integrar proveedor de series | Por asignar | Pendiente | Pendiente |
| T10 — Aplicar filtro temporal | Por asignar | Pendiente | Pendiente |
| T11 — Seleccionar y ordenar recomendaciones | Por asignar | Pendiente | Pendiente |
| T12 — Integrar adaptador conversacional | Por asignar | Pendiente | Pendiente |
| T13 — Refinar preferencias | Por asignar | Pendiente | Pendiente |
| T14 — Exponer operaciones de recomendación y detalle | Por asignar | Pendiente | Pendiente |
| T15 — Controlar fallos externos | Por asignar | Pendiente | Pendiente |
| T16 — Construir inicio y navegación | Por asignar | Pendiente | Pendiente |
| T17 — Construir filtros de preferencias | Por asignar | Pendiente | Pendiente |
| T18 — Construir interfaz del chatbot | Por asignar | Pendiente | Pendiente |
| T19 — Mostrar tarjetas de series | Por asignar | Pendiente | Pendiente |
| T20 — Construir vista de detalle | Por asignar | Pendiente | Pendiente |
| T21 — Guardar y recuperar historial local | Por asignar | Pendiente | Pendiente |
| T22 — Eliminar historial y contexto | Por asignar | Pendiente | Pendiente |
| T23 — Integrar frontend y backend | Por asignar | Pendiente | Pendiente |
| T24 — Mostrar estados de carga y errores | Por asignar | Pendiente | Pendiente |
| T25 — Adaptar interfaz y accesibilidad | Por asignar | Pendiente | Pendiente |
| T26 — Presentar privacidad y atribuciones | Por asignar | Pendiente | Pendiente |
| T27 — Verificar seguridad y privacidad | Por asignar | Pendiente | Pendiente |
| T28 — Ejecutar pruebas unitarias y de integración | Por asignar | Pendiente | Pendiente |
| T29 — Verificar rendimiento | Por asignar | Pendiente | Pendiente |
| T30 — Ejecutar aceptación y regresión | Por asignar | Pendiente | Pendiente |
| T31 — Completar documentación | Por asignar | Pendiente | Pendiente |
| T32 — Preparar entrega final | Por asignar | Pendiente | Pendiente |

## 11. Checklist final

- [ ] Tareas obligatorias terminadas y comprobadas.
- [ ] Requisitos implementados.
- [ ] Restricciones respetadas.
- [ ] Pruebas documentadas.
- [ ] Errores críticos resueltos.
- [ ] Código y documentación entregados.

## 12. Cierre

- **Estado del proyecto:** Pendiente.
- **Tareas completadas:** 0 de 32.
- **Pruebas ejecutadas:** 0.
- **Errores pendientes:** ninguno registrado; no implica ausencia de defectos.
- **Observaciones:** tecnologías propuestas, proveedores, alcance móvil, RN-05 y demás decisiones pendientes requieren aprobación. No se ha generado código de implementación.
