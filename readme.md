# Metodología — Modelo en Espiral (Espartanos Fitness)

## 1. Justificación

Para el desarrollo del prototipo Espartanos Fitness elegimos el modelo de ciclo de vida en espiral porque:

- El cliente (dueño/administrador) conoce buena parte de sus necesidades pero no todo con detalle — el enfoque iterativo permite validar frecuentemente.

- El equipo es pequeño y con experiencia limitada en algunas áreas (bases de datos), por lo que un enfoque que priorice la reducción de riesgos y aprendizaje gradual es ideal.

- Nos permite entregar versiones parciales (microentregas) y corregir rápido problemas críticos (por ejemplo: cálculo de vencimiento de membresías, persistencia y seguridad).

Referencias usadas: Fernández & Alfaro (2020); Lemus et al. (2022).

## 2. Cómo aplicamos la espiral en este proyecto (visión práctica)

Transformamos los 3 meses en 4 microciclos (cada uno con actividades cortas: 2–3 semanas aprox.). Cada microciclo siguió las cuatro actividades clásicas de la espiral:

- **Determinación de objetivos y restricciones** — (qué se pretende en ese ciclo)
- **Evaluación y reducción de riesgos** — (identificar riesgos técnicos/funcionales y mitigarlos)
- **Desarrollo y pruebas** — (implementar la funcionalidad priorizada y probarla)
- **Planificación** — (definir el siguiente microciclo)

---

### Microciclos y entregables (resumido)

---

### **Microciclo 1 — Análisis y prototipado inicial**

**Objetivo:** definir ERS, casos de uso y prototipos (Figma).

**Riesgos detectados:** ambigüedad en reglas de membresía, falta de esquemas de persistencia.

**Entregables:** ERS, prototipos, lista de requisitos mandatorios.

---

### **Microciclo 2 — Diseño y arquitectura + persistencia**

**Objetivo:** modelo conceptual (MER), patrón MVC y decisión de persistencia en archivos.

**Riesgos tratados:** elección sin base de datos (solución: motor propio con archivos), diseño de clases.

**Entregables:** MER, diseño MVC, clases DAO (ej. SocioDAO).

---

### **Microciclo 3 — Implementación core (módulos mandatorios)**

**Objetivo:** implementar RF mandatorios: autenticación, socios, membresías, pagos manuales, inventario, empleados y asistencia.

**Riesgos tratados:** cálculos de fecha (membresía), concurrencia en reservas, validaciones de seguridad.

**Entregables:** prototipo funcional (NetBeans), pruebas unitarias básicas.

---

### **Microciclo 4 — Integración, pruebas y ajuste final**

**Objetivo:** integrar módulos, pruebas de integración, corrección de defectos críticos y preparación de entrega.

**Riesgos tratados:** errores detectados en integración (p.ej. DEF-05 fechaFin, DEF-06 persistencia), fixes urgentes.

**Entregables:** build final (tag v1.0), informe de pruebas, reporte de errores, documentación y preparación de demo.

