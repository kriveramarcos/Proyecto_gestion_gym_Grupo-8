# Desglose del Trabajo (WBS)

## 1. Inicio y planificación — 3 días
- Reunión de lanzamiento con el cliente (dueño).
- Definir alcance final de Fase 1 (lo que sí/no se hará).
- Crear repositorio Git, plantilla de documentación y cronograma en ProjectLibre.
- Dependencia: ninguna (primer paso).
- Entregable: Acta de inicio + ProjectLibre base.

## 2. Obtención de requisitos (Elicitación) — 9 días
- Preparar encuesta (Google Forms) y plantilla de entrevista.
- Aplicar encuesta y programar/realizar 1 entrevistas con el dueño.
- Recopilar resultados y transcribir respuestas a un documento
- Dependencia: Inicio y planificación.
- Entregable: Registro de requisitos crudos (respuestas de encuesta + actas de entrevista + observación).

## 3. Análisis y especificación de requisitos de usuario — 4 días
- Consolidar requisitos en lenguaje natural.
- Categorización (mandatorios/mejora/sin valor).
- Mapear reglas de negocio conflictivas y acuerdos (penalizaciones, salud, cobros).
- Dependencia: Obtención de requisitos.
- Entregable: Documento “Requisitos de Usuario (Fase 1)”.

## 4. Validación de requisitos con cliente — 2 días
- Reunión con el administrador para validar y firmar requisitos.
- Ajustes rápidos según feedback.
- Dependencia: Análisis y especificación.
- Entregable: Requisitos validados / acta de aceptación.

## 5. Diseño UI / Prototipos (Figma) — 6 días
- Bocetos rápidos de pantallas clave (dashboard admin, ficha socio, membresía, calendario de sesiones, check-in).
- Mockups en Figma con interacciones básicas.
- Revisión con admin y 1 prueba de usabilidad (tarea: crear socio, registrar pago, reservar clase).
- Dependencia: Requisitos validados.
- Entregable: Figma link + capturas y feedback recogido.

## 6. Diseño técnico / Arquitectura (DB + APIs) — 5 días
- Definir stack tecnológico (Java / Netbeans, frontend web).
- Modelo de datos (ER conceptual → físico), endpoints principales y pseudocódigo (RFs).
- Plan de despliegue (VPS) y backups.
- Dependencia: Requisitos validados.
- Entregable: Documento de arquitectura 

## 7. Preparación del entorno y control de versiones — 2 días
- Crear repositorio, ramas (main/dev), issues iniciales.
- Configurar ambiente de desarrollo (JRE, servidor local), scripts de ejecución.
- Dependencia: Diseño técnico.
- Entregable: Repo inicial + guía de ejecución (README).

## 8. Implementación Backend (core funcional) — 15 días
- Implementar autenticación local (archivos planos), hashing mínimo. (RF-001,R-002).
- CRUD Socios (buscar por DNI) y Membresías (RF-003..RF-007).
- Registro y gestión de pagos manuales (RF-008).
- CRUD Inventario de máquinas/equipos, estados y categorías (RF-009..RF-011).
- CRUD Empleados + asistencia de empleados (RF-012..RF-013).
- Endpoints para reportes básicos (ingresos, asistencia, vencimientos) (RF-014).
- Dependencia: Preparación entorno + Diseño técnico.
- Entregable: API backend funcional con tests básicos.

## 9. Implementación Frontend (interfaz mínima, responsive) — 12 días
- Pantallas: Login, Dashboard Admin, Lista/Ficha Socio, Módulo Membresías, Inventario, Empleados y Asistencia, Calendario/Sesiones, Módulo Pagos (registro manual), Reportes básicos.
- Validaciones de formulario, navegación
- Conectar con API backend y probar flujos completos.
- Dependencia: Diseño UI (para look) y Backend (para endpoints; puede empezar en paralelo cuando backend tenga endpoints base).
- Entregable: Frontend operable en entorno de desarrollo.

## 10. Integración & pruebas unitarias — 6 días
- Escribir y correr pruebas unitarias básicas (backend y frontend).
- Pruebas de integración (crear socio → asignar membresía → registrar pago → ver reporte).
- Pruebas de carga ligera (comprobación de tiempos: listados < 500 ms, check-in < 200 ms).
- Dependencia: Implementaciones frontend y backend.
- Entregable: Informe de pruebas y lista de bugs críticos.

## 11. Pruebas de usabilidad con cliente y ajustes — 4 días
- Entregar prototipo funcional al admin y al entrenador; realizar 1–2 sesiones de prueba (tareas concretas).
- Recoger feedback y aplicar ajustes críticos (prioridad alta).
- Dependencia: Integración & pruebas unitarias.
- Entregable: Informe de usabilidad y versión corregida.

## 12. Despliegue en VPS y capacitación breve — 3 días
- Desplegar el programa, configurar backup de archivos.
- Sesión de capacitación con el administrador (manual básico + 1 sesión práctica).
- Dependencia: Pruebas de usabilidad y ajustes.
- Entregable: guía de usuario corta.

## 13. Pruebas finales, documentación y entrega — 3 días
- Pruebas finales de aceptación (casos de la checklist).
- Preparar entrega: Documentación (README, manual de usuario, actas), paquete entregable (.zip con código, instrucciones).
- Reunión final de entrega con firma de aceptación.
- Dependencia: Despliegue.
- Entregable: Entrega formal y documentación.

## 14. Buffer / Contingencia — 1 día
- Tiempo reservado para imprevistos o ajustes de último minuto.
- Dependencia: Disponible a lo largo del proyecto.
- Entregable: Registro de uso


# Qué se espera? - Desglose de tareas y responsables

| ID   | Tarea (resumen)                                    | Entregable (resumen)                                         | Responsable |
|------|----------------------------------------------------|-------------------------------------------------------------|-------------|
| 1.1  | Inicio y planificación                            | Acta de inicio + Cronograma (ProjectLibre)                   | Alumno 1    |
| 1.2  | Recopilar requisitos (encuestas/entrev.)           | Documento de requisitos crudos / actas de entrevista         | Alumno 2    |
| 1.3  | Análisis y especificación de requisitos            | Documento de Requisitos validado                             | Alumno 3    |
| 1.4  | Validación con cliente (revisión)                 | Acta de validación / ajustes                                 | Alumno 2    |
| 2.1  | Diseño UI / Prototipos (Figma)                    | Prototipos Figma (pantallas clave)                           | Alumno 4    |
| 2.2  | Diseño técnico / Modelo de datos (ER)             | Diagrama ER + esquema técnico (DDL o esquema de archivos)    | Alumno 3    |
| 3.1  | Preparación de repositorio y entorno              | Repo inicial + README + scripts                              | Alumno 1    |
| 3.2  | Implementación Backend (core funcional)           | API / código backend funcional                               | Alumno 2    |
| 3.3  | Implementación Frontend (interfaz)                | Frontend operativo (pantallas principales)                   | Alumno 3    |
| 3.4  | Integración y pruebas (unitarias/integr.)         | Informe de pruebas e incidencias                             | Alumno 4    |
| 3.5  | Pruebas de usabilidad con cliente                  | Informe de usabilidad + lista de ajustes                     | Alumno 1    |
| 4.1  | Despliegue en VPS + backups                       | App desplegada en VPS + backups configurados                 | Alumno 1    |
| 4.2  | Capacitación y guía de usuario                    | Manual corto + sesión de capacitación grabada                | Alumno 4    |
| 4.3  | Documentación final y entrega                     | Paquete entregable (.zip) + acta de entrega                  | Alumno 2    |
| 4.4  | Seguimiento/Buffer y cierre                       | Registro de cambios / cierre del proyecto                    | Alumno 3    |


