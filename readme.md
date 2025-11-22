# Seguimiento — Cronograma y ejecución real (cierre 24-11-2025)

**Proyecto:** Espartanos Fitness — Prototipo sistema de gestión  
**Periodo de seguimiento:** inicio planificado 18-ago-2025 — cierre real 24-nov-2025  
**Responsable del seguimiento:** Equipo de Desarrollo (ED)

---

## 1) Resumen ejecutivo
El cronograma original (Planificado) preveía terminar la entrega final el **11/11/2025**. Durante la ejecución se presentaron retrasos leves y uno moderado en pruebas/integración, por lo que la **fecha real de entrega** se movió al **24/11/2025** (retraso total = **13 días**). Las causas principales fueron: (i) ajustes de código detectados en integración (reserva/concurrencia y reglas de pago), (ii) iteraciones de corrección por errores críticos, y (iii) disponibilidad limitada del equipo por cargas académicas. A continuación se muestra la comparación por bloques de trabajo.

---

## 2) Tabla de seguimiento (planificado vs real)

| ID | Tarea (resumen) | Planificado Inicio → Fin | Real (ejecución) Inicio → Fin | Estado final | Observaciones breves |
|---:|---|---:|---:|---|---|
| 1 | **Definición del proyecto** | 18/08/2025 → 26/08/2025 | 18/08/2025 → 26/08/2025 | Completada | A tiempo. Acta entregada. |
| 8 | **Análisis de requisitos** | 27/08/2025 → 15/09/2025 | 27/08/2025 → 18/09/2025 | Completada | +3 días por ampliación de observación/encuestas. |
| 15 | **Análisis y diseño de artefactos** | 16/09/2025 → 25/09/2025 | 19/09/2025 → 28/09/2025 | Completada | +3 días por refinamiento de prototipos y CU. |
| 21 | **Implementación (módulos)** | 26/09/2025 → 24/10/2025 | 29/09/2025 → 31/10/2025 | Completada | +7 días; ajustes en autenticación y pagos. |
| 27 | **Integración de módulos** | 20/10/2025 → 24/10/2025 | 01/11/2025 → 07/11/2025 | Completada | Conflictos de datos y concurrencia. |
| 28–31 | **Pruebas (unitarias + integración + correcciones)** | 27/10/2025 → 04/11/2025 | 08/11/2025 → 18/11/2025 | Completada | +10 días en testing y fixes (reservas, pago, asistencia). |
| 32 | **Desarrollo del informe final** | 05/11/2025 → 11/11/2025 | 19/11/2025 → 21/11/2025 | Completada | Redacción tras cierre de correcciones. |
| 33 | **Entrega del prototipo** | 11/11/2025 | 24/11/2025 | Completada (entrega final) | Entrega retrasada 13 días respecto al plan. |

> **Totales:** Fin planificado = 11/11/2025 → Fin real = **24/11/2025** → **Retraso total = 13 días**.

---

## 3) Análisis de variaciones (causas y efectos)

- **Causa técnica:** problemas de integración entre módulos (especialmente control de cupos/reservas y regla de anulación de pagos). Fueron necesarios ajustes en transacciones y comprobaciones de negocio, lo que provocó iteraciones adicionales de pruebas.  
- **Causa organizacional:** carga académica de algunos miembros y revisión cruzada (code review limitado al inicio).  
- **Efectos:** pruebas y correcciones se extendieron; se replanificó la redacción final del informe y la sesión de entrega.  
- **Impacto en alcance:** **ninguna funcionalidad mandatoria fue eliminada**; se postergaron mejoras e integraciones no esenciales (pasarelas de pago, notificaciones automáticas) a fase 2.

---

## 4) Estado de entregables (al cierre 24/11/2025)

**Entregados / Completos**
- Acta de proyecto (Definición)  
- ERS (Requisitos de Usuario) — validado con cliente  
- Casos de uso y diagramas (UML)  
- Diagrama de procesos (Bizagi)  
- Modelo Conceptual (MER)  
- Prototipos / mockups (Figma)  
- Código fuente del prototipo (NetBeans) — funcionalidad core (RF mandatorios)  
- Reporte de pruebas (matriz caja negra) y Anexo de errores (reporte-errores.md)  
- Cronograma final (ProjectLibre) actualizado  
- Informe final del proyecto (documento)

**Pendientes / Observaciones**
- Integración con pasarelas de pago: **fase 2** (no priorizada en fase 1).  
- Mejoras UX menores (mensajes y validaciones en cliente).  
- Revisión de seguridad: cifrado de campos sensibles implementado parcialmente; requiere auditoría.

---

## 5) Métricas simples del seguimiento

- **Retraso total (días calendario):** +13 días  
- **Actividades con retraso:** 5/8 bloques principales (análisis, diseño, implementación, integración, pruebas)  
- **% Cumplimiento de RF mandatorios:** 100% implementados (según checklist y pruebas funcionales básicas)  
- **Número de iteraciones de corrección importantes:** 2 (post-integración)

---

## 6) Lecciones aprendidas y recomendaciones

1. **Planificar una ventana de integración más amplia:** la integración suele descubrir fallos de negocio; reservar +1 semana para integración y pruebas.  
2. **Probar concurrencia desde temprano:** escenarios de reservas/concurrencia deben testearse en integración para evitar sobreventas.  
3. **Automatizar validaciones básicas:** cliente + servidor para evitar datos inválidos (DNI duplicado, campos obligatorios).  
4. **Asignar “dueño” claro para fixes críticos:** en este proyecto Aaron asumió la mayor parte de correcciones — esa práctica ayudó a cerrar bugs más rápido; para futuros proyectos repartir on-call.  
5. **Registro de cambios y control de versiones estricto:** vincular cada corrección a un issue y PR para facilitar trazabilidad de bugs.  
6. **Plan de capacitación rápido:** preparar 1 sesión práctica con dueño/administrador para entrega (30–45 min) + guía corta (1–2 páginas).

---

## 7) Acciones de cierre (checklist para el hito “Entrega final”)

- [x] Confirmar cierre de defectos críticos (DEF-03, DEF-04, DEF-07, DEF-08) o registrar pendientes como backlog.  
- [x] Generar build estable y empaquetado para VPS (JRE 21).  
- [x] Subir código al repositorio (tag `v1.0-final`) y guardar snapshot .zip.  
- [x] Entregar informe final y acta de entrega al cliente (firma/aceptación).  
- [x] Sesión de capacitación al administrador (práctica + manual corto).  
- [x] Plan de mantenimiento y puntos de mejora (documentado).  
- [ ] (Opcional) Planificar fase 2: pasarela de pagos, notificaciones, exportar reportes.

---

## 8) Conclusión breve
Se entregó un prototipo funcional que cumple los **requisitos mandatorios** y cuenta con pruebas documentadas. Hubo un retraso de 13 días respecto al plan inicial por problemas de integración y correcciones críticas, pero la entrega final (24/11/2025) incluye: código, prototipos, ERS, pruebas y el informe final. Recomendamos una fase de estabilización (2 semanas) post-entrega para ajustes menores y la planificación de la fase 2 (pagos e integraciones).

