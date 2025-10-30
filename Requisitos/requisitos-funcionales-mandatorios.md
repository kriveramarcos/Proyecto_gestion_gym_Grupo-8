# Requisitos funcionales mandatorios

*(Estos deben implementarse en Fase 1; sin ellos el sistema no cumple su propósito)*

## RF-001 — Autenticación
El sistema debe permitir que el administrador inicie sesión con credenciales y bloquear el acceso si no son válidas. (Ya definido en pseudocódigo).

## RF-002 — Validación de credenciales
Verificar usuario/contraseña contra el almacenamiento (archivos planos) antes de permitir acceso.

## RF-003 — Gestión de socios (CRUD)
Registrar, consultar, actualizar y eliminar fichas de socios. Búsqueda por DNI.

**Datos mínimos:** DNI, nombre, apellidos, teléfono/email, tipo de membresía, fecha inicio/fin.

## RF-004 — Gestión de planes de membresía (CRUD)
Crear, consultar, editar y eliminar planes (nombre, tipo, duración, precio).

## RF-005 — Restricciones de acceso por plan
Definir y asignar restricciones de días y horarios a los planes (controlar accesos).

## RF-006 — Asignación de membresía a socio
Asignar/quitar una membresía a un socio; registrar fecha de inicio.

## RF-007 — Cálculo automático de vencimiento
Calcular fecha de fin según tipo de plan (mensual, bimestral, semestral, etc.).

## RF-008 — Gestión de pagos
Registrar pagos manuales, consultar historial, y permitir la cancelación/eliminación de un pago.

## RF-009 — Inventario de equipos (CRUD)
Registrar, consultar, actualizar y eliminar máquinas/equipos; búsqueda por número de serie.

## RF-010 — Cambio de estado de equipos
Modificar estado de un equipo (activo, en mantenimiento, retirado).

## RF-011 — Mostrar equipos por categoría
Filtrar y listar equipos por tipo (máquina, disco, mancuerna, etc.).

## RF-012 — Gestión de empleados (CRUD)
Registrar, consultar, actualizar y eliminar empleados; búsqueda por id.

## RF-013 — Gestión de asistencia de empleados
Registrar hora de entrada y salida; actualizar/Eliminar registros de asistencia.

## RF-014 — Reportes básicos
Generar reporte diario de asistencia (empleados) y reportes de ingresos, asistencia de socios y vencimientos.
