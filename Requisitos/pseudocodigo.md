## Pseudocódigos de Requisitos Funcionales del Sistema

A continuación se muestran los procesos más importantes del sistema en forma de pseudocódigo. Estos describen las operaciones clave para la gestión de asistencia de empleados, la inscripción de socios en membresías y el pago de dichas inscripciones.

---

### 1. Registrar asistencia del empleado

```pseudocode
PROCESO RegistrarAsistencia
    opcion ← obtenerOpcionSeleccionada()    // "Entrada" o "Salida"
    fechaActual ← obtenerFechaActual()

    SI opcion = "Seleccionar" ENTONCES
        mostrarMensaje("Seleccione una opción válida (Entrada o Salida)")
        TERMINAR PROCESO
    FIN SI

    SI opcion = "Entrada" ENTONCES
        asistenciaExistente ← buscarAsistenciaPorEmpleadoYFecha(idEmpleado, fechaActual)
        SI asistenciaExistente ≠ NULL ENTONCES
            mostrarMensaje("Ya existe un registro de entrada para hoy")
        SINO
            horaEntrada ← obtenerHoraActual()
            nuevaAsistencia ← crearAsistencia(idGenerado(), idEmpleado, horaEntrada, "Hora no registrada", fechaActual)
            guardarAsistencia(nuevaAsistencia)
            mostrarMensaje("Entrada registrada exitosamente")
        FIN SI

    SINO SI opcion = "Salida" ENTONCES
        asistenciaExistente ← buscarAsistenciaPorEmpleadoYFecha(idEmpleado, fechaActual)
        SI asistenciaExistente = NULL ENTONCES
            mostrarMensaje("No existe una entrada previa para hoy")
        SINO SI asistenciaExistente.horaSalida ≠ "Hora no registrada" ENTONCES
            mostrarMensaje("La salida ya fue registrada hoy")
        SINO
            horaSalida ← obtenerHoraActual()
            actualizarHoraSalida(idEmpleado, fechaActual, horaSalida)
            mostrarMensaje("Salida registrada correctamente")
        FIN SI
    FIN SI

    actualizarTablaAsistencias()
FIN PROCESO


```

---

### 2. Inscripción de socio a una membresía

```pseudocode
PROCESO RegistrarInscripcionSocio
    socioSeleccionado ← obtenerSocioSeleccionadoDesdeTabla()
    SI socioSeleccionado = NULL ENTONCES
        mostrarMensaje("Debe seleccionar un socio para inscribir")
        TERMINAR PROCESO
    FIN SI

    mostrarVentanaInscripcion()

    membresiaSeleccionada ← obtenerMembresiaSeleccionada()
    fechaInicio ← obtenerFechaInicioDesdeFormulario()

    SI membresiaSeleccionada = NULL O fechaInicio = VACÍO ENTONCES
        mostrarMensaje("Seleccione una membresía y una fecha de inicio")
        TERMINAR PROCESO
    FIN SI

    fechaVencimiento ← calcularFechaVencimiento(fechaInicio, membresiaSeleccionada.duracion)
    nuevaInscripcion ← crearInscripcion(
        idGenerado(),
        socioSeleccionado.id,
        membresiaSeleccionada.id,
        fechaInicio,
        fechaVencimiento,
        membresiaSeleccionada.nombre,
        membresiaSeleccionada.precio,
        obtenerFechaActual(),
        "NO PAGADA"
    )

    guardarInscripcion(nuevaInscripcion)
    actualizarTablaInscripciones()
    mostrarMensaje("Inscripción registrada exitosamente")
FIN PROCESO

```

---

### 3. Pago de inscripción

```pseudocode
PROCESO RegistrarPagoInscripcion
    inscripcionSeleccionada ← obtenerInscripcionSeleccionadaDesdeTabla()
    SI inscripcionSeleccionada = NULL ENTONCES
        mostrarMensaje("Debe seleccionar una inscripción para realizar el pago")
        TERMINAR PROCESO
    FIN SI

    mostrarVentanaPago(inscripcionSeleccionada)

    monto ← inscripcionSeleccionada.precio
    tipoPago ← obtenerTipoPagoSeleccionado()    // Ej: "Efectivo", "Tarjeta", etc.

    SI tipoPago = VACÍO ENTONCES
        mostrarMensaje("Seleccione un tipo de pago válido")
        TERMINAR PROCESO
    FIN SI

    nuevoPago ← crearPago(
        idGenerado(),
        inscripcionSeleccionada.id,
        monto,
        tipoPago,
        obtenerFechaActual()
    )

    guardarPago(nuevoPago)
    actualizarEstadoInscripcion(inscripcionSeleccionada.id, "PAGADA")

    actualizarTablaPagos()
    actualizarTablaInscripciones()
    mostrarMensaje("Pago realizado exitosamente")
FIN PROCESO

```
