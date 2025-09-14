# Espartanos Fitness - Sistema de Gestion

<p align="center">
  <img src="imagen/logo.png" alt="Logo Espartanos Fitness" width="200"/>
</p>

## Introduccion

Este documento recoge los requisitos de usuario y la especificación técnica inicial para el sistema de gestión del gimnasio Espartanos Fitness (Fase 01). Está orientado principalmente al administrador/propietario, e incluye necesidades de entrenadores y clientes. Se basa en la información del proyecto (info.pdf) y la guía del curso (curso-procesos-software).

## Tecnicas de obtencion de requisitos (Anexo A)

Técnicas utilizadas (previstas):

- Cuestionarios / Encuestas (Google Forms) para admin, entrenadores y clientes.
- Observación directa (flujo de recepción, cobros, clases, rutinas).
- Prototipos en Figma (wireframes) para validar pantallas clave.
- Entrevistas grabadas por Google Meet con el cliente (por confirmar).

## Stakeholders

Partes interesadas principales:

- Administrador / Dueño (usuario principal): gestiona socios, membresías, pagos, horarios y reportes.
- Entrenadores / Instructores: gestionan clases, registran progreso y consultan su agenda.
- Socios: información personal, visualizar rutinas , ven su membresía y progreso, reciben notificaciones.

## Requisitos de usuario

Resumen de los requisitos principales en lenguaje sencillo (orientado al admin):

- **Registro y autenticación de usuarios**: Poder crear cuentas de administrador, entrenadores y usuario común (para visualizacion); iniciar sesión seguro.

- **Gestión de socios**: Registrar y editar ficha de cada socio: datos personales, contacto, notas de salud y estado de membresía.

- **Gestión de membresías y cobros**: Crear planes (mensual, trimestral...), registrar pagos y actualizar fecha de vencimiento.

- **Calendario y horarios de clases**: Crear horarios, asignar instructores, definir cupos y gestionar lista de espera.

- **Reservas y control de asistencia**: Permitir reservar/cancelar plazas, registrar check-in y manejar listas de espera.

- **Reportes y métricas**: Ver ingresos, asistencia y socios próximos a vencer; exportar reportes.

- **Roles y permisos**: Definir quién puede ver/editar cada cosa (admin, entrenador, cliente).
