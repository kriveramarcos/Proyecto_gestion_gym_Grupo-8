# Requisitos Técnicos Mínimos del Software

## Requisitos funcionales

A continuación se transforman los requisitos mandatorios a especificaciones técnicas (endpoints, entidades y pseudocódigo).

**RF-001 Autenticación y gestión de usuarios**

El sistema debe permitir la autenticación de usuarios a partir de los datos almacenados en archivos planos.

- Entradas:
  -Usuario ingresado en el campo de texto.
  -Contraseña ingresada en el campo de texto.
- Salidas:
  -Mensaje de acceso correcto y apertura de la interfaz correspondiente al rol
  -Mensaje de error si las credenciales no son válidas.
- Precondiciones:
  -El archivo de usuarios debe existir y contener registros válidos con los campos: usuario, contraseña y rol (ADMIN, TRAINER, CLIENT).
  -El usuario debe estar previamente registrado en dicho archivo.
- Postcondiciones:
  -El sistema identifica el rol del usuario y habilita las funciones correspondientes.
  -Si la autenticación falla, el acceso es denegado.
- Restricciones técnicas:
  -No se emplea base de datos ni servicios externos de autenticación.
  -Contraseñas almacenadas en texto plano.
  -Validación únicamente mediante lectura del archivo.

---

**RF-002 Gestión de socios**

Entidad Socio: id, nombre, dni, email, telefono, fecha_nacimiento, notas_salud, foto, estado_membresia.

Operaciones: CRUD, búsqueda por nombre/DNI, paginación y filtros.

---

**RF-003 Membresías y cobros**

Entidad Plan: id, nombre, duracion_dias, precio.

Entidad Pago: id, socio_id, plan_id, fecha_pago, monto, metodo_pago, estado.

Regla: al registrar pago, actualizar fecha_vencimiento del socio.

Pseudocódigo (registrar pago):

```
function registrarPago(socioId, planId, fechaPago, monto):
    plan = obtenerPlan(planId)
    socio = obtenerSocio(socioId)
    pago = crearPago(socioId, planId, fechaPago, monto)
    if socio.fecha_vencimiento == null or socio.fecha_vencimiento < fechaPago:
        socio.fecha_vencimiento = fechaPago + plan.duracion_dias
    else:
        socio.fecha_vencimiento = socio.fecha_vencimiento + plan.duracion_dias
    guardarSocio(socio)
    return pago
```

---

**RF-004 Calendario y clases (por validar)**

Entidad Clase: id, nombre, instructor_id, fecha_hora_inicio, duracion_min, cupo, sala, estado.

Reserva: id, clase_id, socio_id, fecha_reserva, estado.

Pseudocódigo (reservar plaza):

```
function reservarPlaza(socioId, claseId):
    clase = obtenerClase(claseId)
    if clase.estado != "activa": return "Clase no activa"
    inscritos = contarReservasActivas(claseId)
    if inscritos >= clase.cupo:
        agregarAListaEspera(socioId, claseId)
        return "En lista de espera"
    else:
        crearReserva(socioId, claseId, ahora())
        return "Reserva confirmada"
```

---

**RF-005 Check-in / asistencia (por validar)**

Registrar asistencia mediante check-in manual. Guarda: reserva_id, hora_checkin, checked_by.

---

**RF-006 Reportes (por validar)**

Reportes: ingresos por periodo, asistencia por clase, socios por plan, próximos vencimientos.Mostrar en tablas.

---

## Requisitos no funcionales

- **Portabilidad**: La aplicacion debe ejecutarse en cualquier sistema operativo que disponga de Java Runtime Environment (JRE 21 o superior) . No requiere instalacion de base de datos ni servicios externos.

- **Facilidad de mantenimiento**: Repositorio Git, README, codigo organizado en package (o similar según conocimiento del equipo).

- **Usabilidad**: Interfaz simple; aprendizaje < 30 minutos para admin.

- **Velocidad de procesamiento**: Listados paginados < 500 ms; check-in < 200 ms en condiciones normales.

- **Seguridad**: credenciales se almacenan en archivos (se recomienda considerar mejoras futuras), archivos de fidelizacion restringidos y autenticación en base a roles.

- **Restricciones técnicas**: Alojamiento en VPS o PaaS; integraciones de pago en fase 2.
