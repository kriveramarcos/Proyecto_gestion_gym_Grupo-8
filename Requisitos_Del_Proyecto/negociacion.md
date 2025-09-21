## Negociación y discusión de requisitos

Conflictos/ambigüedades detectadas y acuerdos propuestos:

- **Política de penalización por no asistir:**

  - Conflicto entre admin (quiere penalizar) y clientes (miedo a cargos).
  - Acuerdo: regla configurable.
  - Default: aviso + bloqueo de reservas por 1 día tras 2 no-shows sin aviso.

- **Acceso a datos de salud:**

  - Ambigüedad sobre detalle y visibilidad.
  - Acuerdo: almacenar solo datos relevantes (alergias, restricciones) y cifrar estos campos.
  - Visibilidad limitada a admin y entrenador asignado.

- **Automatización de cobros:**

  - Conflicto por comodidad vs. complejidad legal.
  - Acuerdo: fase 1 = pagos manuales + recordatorios;
  - Integración automática = fase 2.
