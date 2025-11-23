# Seguimiento — Cronograma y ejecución real (cierre 24-11-2025)

**Proyecto:** Espartanos Fitness — Prototipo sistema de gestión  
**Periodo de seguimiento:** inicio planificado 18-ago-2025 — cierre 24-nov-2025  
**Responsable del seguimiento:** Equipo de Desarrollo (ED)

---

## 1) Resumen ejecutivo
El cronograma original incluía la entrega del prototipo para el **11/11/2025**; además se agregó formalmente el hito **“Presentación final del prototipo”** para **24/11/2025** (fecha de exposición/defensa final del curso). El equipo completó el desarrollo del prototipo el **17/11/2025**, por lo que la ejecución real finalizó **antes** del hito de presentación (adelanto de **7 días** respecto al hito planificado del 24/11/2025). A pesar de retrasos intermedios en integración y pruebas, el equipo pudo recuperar tiempo y terminar el prototipo con margen para preparar la presentación final.

---

## 2) Tabla de seguimiento (planificado vs real)

| ID | Tarea (resumen) | Planificado Inicio → Fin | Real (ejecución) Inicio → Fin | Estado final | Observaciones breves |
|---:|---|---:|---:|---|---|
| 1 | **Definición del proyecto** | 18/08/2025 → 26/08/2025 | 18/08/2025 → 26/08/2025 | Completada | A tiempo. Acta entregada. |
| 8 | **Análisis de requisitos** | 27/08/2025 → 15/09/2025 | 27/08/2025 → 18/09/2025 | Completada | +3 días por ampliación de observación/encuestas. |
| 15 | **Análisis y diseño de artefactos** | 16/09/2025 → 25/09/2025 | 19/09/2025 → 28/09/2025 | Completada | +3 días por refinamiento de prototipos y CU. |
| 21 | **Implementación (módulos)** | 26/09/2025 → 24/10/2025 | 29/09/2025 → 31/10/2025 | Completada | +7 días; ajustes en autenticación y pagos. |
| 27 | **Integración de módulos** | 20/10/2025 → 24/10/2025 | 01/11/2025 → 07/11/2025 | Completada | Conflictos de datos y concurrencia. |
| 28–31 | **Pruebas (unitarias + integración + correcciones)** | 27/10/2025 → 04/11/2025 | 08/11/2025 → 13/11/2025 | Completada | +6 días en testing y fixes (reservas, pago, asistencia). |
| 32 | **Desarrollo del informe final** | 05/11/2025 → 11/11/2025 | 14/11/2025 → 16/11/2025 | Completada | Redacción tras cierre de correcciones. |
| 33 | **Entrega del prototipo (build / tag v1.0)** | 11/11/2025 | 17/11/2025 | Completada | Entrega del prototipo finalizada el 17/11/2025. |
| 34 | **Presentación final del prototipo (exposición / defensa)** | 24/11/2025 | 24/11/2025 (programado) | Programado | Hito académico / exposición ante docente. |

> **Totales (hitos):** Fin planificado (ahora considerando la presentación) = **24/11/2025** → Fin real (prototipo entregado) = **17/11/2025** → **Resultado: adelantado 7 días respecto al hito final planificado**.

---

## 3) Análisis de variaciones (causas y efectos)

- **Causas de retrasos intermedios:** ajustes técnicos en integración (control de cupos/reservas, reglas de pago y concurrencia), y disponibilidad parcial del equipo por cargas académicas; estas causas provocaron iteraciones extra en la fase de integración y pruebas.  
- **Acciones de mitigación aplicadas:** priorización de defectos críticos, asignación clara de responsables para fixes (especialmente Aaron en correcciones de código), y replanificación de pruebas.  
- **Efectos positivos:** gracias a la mitigación y a trabajo concentrado el equipo completó el prototipo el 17/11/2025, recuperando tiempo frente al hito de presentación (24/11/2025).  
- **Impacto en alcance:** no se eliminaron requisitos mandatorios; únicamente se dejaron para fase 2 mejoras no críticas (integración de pasarelas de pago, notificaciones automáticas, exportes avanzados).

---

## 4) Estado de entregables (al cierre 17/11/2025)

**Entregados / Completos**
- Acta de proyecto (Definición).  
- ERS (Requisitos de Usuario) — validado con cliente.  
- Casos de uso y diagramas (UML).  
- Diagrama de procesos (Bizagi).  
- Modelo Conceptual (MER).  
- Prototipos / mockups (Figma).  
- Código fuente del prototipo (NetBeans) — funcionalidad core (RF mandatorios).  
- Reporte de pruebas (matriz caja negra) y Anexo de errores (reporte-errores.md).  
- Cronograma final (ProjectLibre) actualizado.  
- Informe final del proyecto (documento).

**Pendientes / Programados**
- Preparar material de **presentación final** (diapositivas, demo en vivo, guion) — programado para 24/11/2025.  
- Integración con pasarelas de pago y notificaciones automáticas — planificadas para fase 2 / backlog.  
- Auditoría de seguridad (revisión de cifrado campos sensibles) — recomendada post-entrega.

---

## 5) Métricas simples del seguimiento

- **Adelanto respecto al hito final (días calendario):** +7 días (prototipo listo 17/11 frente a presentación 24/11).  
- **Actividades con retraso en el plan:** 5/8 bloques principales (análisis, diseño, implementación, integración, pruebas) — todos recuperados.  
- **% Cumplimiento de RF mandatorios:** 100% implementados (según checklist y pruebas funcionales básicas).  
- **Número de iteraciones de corrección importantes:** 2 (post-integración).  
- **Tiempo de recuperación (desde fin de pruebas hasta entrega):** 4 días (13/11 → 17/11) para fixes finales y empaquetado.

---

## 6) Lecciones aprendidas y recomendaciones

1. **Reservar margen para integración y pruebas:** asignar al menos una semana extra para integración en proyectos con reglas de negocio (reservas, pagos).  
2. **Probar escenarios concurrentes temprano:** pruebas de concurrencia en reservas evitan sobreventas y ajustes tardíos.  
3. **Responsables claros para fixes críticos:** la asignación de “dueños” (on-call) acelera la resolución.  
4. **Preparar la presentación con antelación:** terminar el prototipo con margen permite ensayar la demo y corregir fallas de última hora (esto se logró: 7 días de margen).  
5. **Documentación y trazabilidad:** vincular cada corrección a un issue/PR facilita auditoría y seguimiento.  
6. **Planificar fase 2 desde la entrega:** priorizar integraciones (pagos, notificaciones) y pruebas de seguridad.

---

## 7) Acciones de cierre (checklist para el hito “Entrega final” y preparación de presentación)

- [x] Confirmar cierre de defectos críticos (DEF-03, DEF-04, DEF-07, DEF-08) o registrar pendientes como backlog.  
- [x] Generar build estable y empaquetado para VPS (JRE 21).  
- [x] Subir código al repositorio (tag `v1.0-final`) y guardar snapshot .zip.  
- [x] Entregar informe final y acta de entrega al cliente (firma/aceptación).  
- [x] Sesión de capacitación al administrador (práctica + manual corto).  
- [x] Plan de mantenimiento y puntos de mejora (documentado).  
- [x] Preparar **presentación final** (diapositivas, demo, guion y pruebas en entorno) — Responsable: Equipo ED (alinear roles). **Fecha de presentación:** 24/11/2025.  
- [ ] (Opcional) Planificar fase 2: pasarela de pagos, notificaciones, exportar reportes.

---

## 8) Conclusión breve
Aunque se registraron retrasos técnicos durante la fase de integración y pruebas, las acciones de mitigación permitieron completar el prototipo el **17/11/2025**; esto dejó un margen de **7 días** antes de la **presentación final programada para el 24/11/2025**, tiempo suficiente para preparar la demo y la exposición. El prototipo cumple los **requisitos mandatorios** y está listo para ser mostrado; las mejoras y las integraciones externas se planifican para una fase 2.

---

### ¿Quieres que genere ahora:
- la **versión .docx** de este seguimiento lista para entregar (Word), o  
- una **mini-gráfica Gantt** comparando el plan (con hito 24/11) vs la ejecución real (fechas reales) para insertar en el informe?

Dime cuál y lo preparo.
