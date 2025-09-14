# Negociación y Discusión de Requisitos

## 1. Conflictos/Ambigüedades detectadas y acuerdos propuestos

## Negociación y Discusión de Requisitos

### Conflictos/ambigüedades detectadas y acuerdos propuestos:

#### Política de penalización por no asistir:
- **Conflicto**: El administrador quiere penalizar a los usuarios por no asistir, mientras que los clientes temen ser cobrados sin previo aviso.
- **Acuerdo**: La regla será configurable, y el comportamiento por defecto será:
  - **Aviso** + bloqueo de reservas por 1 día después de **2 no-shows sin aviso**.

#### Acceso a datos de salud:
- **Ambigüedad** sobre qué detalle se debe almacenar y quién puede ver esos datos.
- **Acuerdo**: Solo se almacenarán los datos relevantes (como alergias y restricciones), y estos campos serán **cifrados**.
  - La visibilidad de estos datos estará **limitada al administrador y al entrenador asignado**.

#### Automatización de cobros:
- **Conflicto**: Existe un debate entre la comodidad de automatizar el proceso y la complejidad legal que podría generar.
- **Acuerdo**: La implementación será por fases:
  - **Fase 1**: Pagos manuales + recordatorios.
  - **Fase 2**: Integración automática.

#### Autonomía de entrenadores:
- **Pregunta**: ¿Pueden los entrenadores crear clases directamente?
- **Acuerdo**: Los entrenadores pueden **proponer** o **solicitar clases**.
  - El administrador será el encargado de **aprobar o delegar permisos** para crear las clases.


