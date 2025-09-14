# Categorización Lógica de Requisitos (Organización de los requisitos de usuario)

## 1. Requisitos funcionales mandatorios (Sin ellos el sistema no cumple)

Estos requisitos son esenciales para el funcionamiento básico del sistema. Sin ellos, el sistema no podrá operar correctamente.

- **Registro y autenticación de usuarios**
- **Gestión de socios**  
  - CRUD de fichas de socios (Crear, Leer, Actualizar, Eliminar)
- **Gestión de membresías y registro de pagos**
- **Calendario y gestión de clases**
  - Crear horarios de clases, asignar instructores y definir cupos
- **Reservas y control de asistencias**
  - Reservar, cancelar, y registrar check-ins
- **Reportes básicos**
  - Ingresos, asistencia, y vencimientos de socios
- **Roles y permisos**
  - Definir qué acciones pueden realizar los usuarios según su rol (administrador, entrenador, cliente)

---

## 2. Requisitos de mejora (Recomendados si hay tiempo)

Estos requisitos son mejoras que agregarían valor al sistema, pero no son imprescindibles para su funcionamiento básico.

- **Notificaciones automáticas**
  - Email/SMS/push para alertas de eventos importantes (pago, reservas, vencimientos)
- **Integración con pasarelas de pago**
  - Yape, Plin, y APIs bancarias para facilitar los pagos
- **Módulo de seguimiento con gráficas**
  - Medición de peso, medidas y progreso de los socios
- **Gamificación**
  - Puntos, retos y recompensas para fomentar la fidelización de los usuarios
- **Exportación de reportes a CSV/PDF**
  - Facilitar la exportación de reportes para análisis externo

---

## 3. Requisitos que no generan valor para este proyecto (Se recomiendan excluir)

Estos requisitos no son relevantes para la fase inicial del proyecto y se recomienda no implementarlos en esta etapa.

- **Marketplace avanzado para terceros**
  - No es necesario en el contexto actual del proyecto
- **E-commerce complejo con catálogo amplio**
  - No relevante en este momento, ya que no hay venta de productos masivos
- **Integraciones con ERPs de gran empresa**
  - No relevante ahora; no hay necesidad de integración con sistemas de gestión empresariales a gran escala

