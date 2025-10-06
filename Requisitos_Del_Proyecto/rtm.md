# Requisitos Técnicos Mínimos del Software

## Requisitos funcionales

A continuación se transforman los requisitos mandatorios a especificaciones técnicas (endpoints, entidades y pseudocódigo).

- **RF-001 El sistema debe permitir la autenticación del administrardor a partir de los datos almacenados en archivos planos.**
**Pseudocódigo:**
  ```
    Funcion autenticarAdministrador(usuarioIngresado, contrasenaIngresada)
    archivoUsuarios ← abrirArchivo("admin.txt", "lectura")
    encontrado ← FALSO
    
    Mientras no finArchivo(archivoUsuarios) Hacer
        registro ← leerLinea(archivoUsuarios)
        [usuario, contrasena] ← dividir(registro, ";")
        Si usuario = usuarioIngresado Y contrasena = contrasenaIngresada Entonces
            encontrado ← VERDADERO
            SalirMientras
        FinSi
    FinMientras
    
    cerrarArchivo(archivoUsuarios)
    Retornar encontrado
  FinFuncion
---

- **RF-002 El sistema debe validar que el usuario y contraseña del administrador coincidan con un registro existente antes de permitir el acceso.**
**Pseudocódigo:**
  ```
  Procedimiento iniciarSesion()
    Escribir "Ingrese usuario:"
    Leer usuario
    Escribir "Ingrese contraseña:"
    Leer contrasena

    valido ← autenticarAdministrador(usuario, contrasena)
    Si valido = VERDADERO Entonces
        mostrarMenuPrincipal()
    Sino
        Escribir "Credenciales incorrectas. Acceso denegado."
    FinSi
  FinProcedimiento
---

- **RF-003 El sistema debe permitir registrar, consultar, actualizar y eliminar socios, así como realizar búsquedas por DNI.**
**Pseudocódigo:**
  ```
  Funcion registrarSocio(dni, nombre, apellido, tipoMembresia)
    nuevoSocio ← crearRegistroSocio(dni, nombre, apellido, tipoMembresia)
    agregarAArchivo("socios.txt", nuevoSocio)
  FinFuncion
 
    Funcion buscarSocioPorDNI(dniBuscado)
    archivo ← abrirArchivo("socios.txt", "lectura")
    Mientras no finArchivo(archivo)
        socio ← leerSocio(archivo)
        Si socio.dni = dniBuscado Entonces
            cerrarArchivo(archivo)
            Retornar socio
        FinSi
    FinMientras
    cerrarArchivo(archivo)
    Retornar NULO
  FinFuncion

  Procedimiento actualizarSocio(dni, nuevosDatos)
    lista ← leerTodos("socios.txt")
    Para cada socio en lista
        Si socio.dni = dni Entonces
            socio ← nuevosDatos
        FinSi
    FinPara
    sobrescribirArchivo("socios.txt", lista)
  FinProcedimiento

  Procedimiento eliminarSocio(dni)
    lista ← leerTodos("socios.txt")
    lista ← eliminarElemento(lista, dni)
    sobrescribirArchivo("socios.txt", lista)
  FinProcedimiento
---

- **RF-004 El sistema debe permitir registrar, consultar, actualizar y eliminar planes de membresía, incluyendo datos importantes como su nombre, tipo y precio.**
**Pseudocódigo:**
  ```
  Funcion registrarPlan(nombre, tipo, precio)
    plan ← crearPlan(nombre, tipo, precio)
    agregarAArchivo("planes.txt", plan)
  FinFuncion
---

- **RF-005 El sistema debe permitir asignar y eliminar restricciones de días y horarios de acceso asociados a cada membresía, de manera que se controle la entrada y salida de los socios según las condiciones definidas.**
**Pseudocódigo:**
  ```
  Funcion asignarRestriccion(planId, diasPermitidos, horaInicio, horaFin)
    restriccion ← crearRestriccion(planId, diasPermitidos, horaInicio, horaFin)
    agregarAArchivo("restricciones.txt", restriccion)
  FinFuncion

  Procedimiento eliminarRestriccion(planId)
    lista ← leerTodos("restricciones.txt")
    lista ← eliminarPorCampo(lista, planId)
    sobrescribirArchivo("restricciones.txt", lista)
  FinProcedimiento
---

- **RF-006 El sistema debe permitir gestionar la asignación de una membresía a un socio**
**Pseudocódigo:**
  ```
  Procedimiento asignarMembresia(dniSocio, idPlan)
    socio ← buscarSocioPorDNI(dniSocio)
    plan ← buscarPlanPorID(idPlan)
    socio.idPlan ← idPlan
    actualizarSocio(socio.dni, socio)
  FinProcedimiento
---

- **RF-007 El sistema debe permitir definir la fecha de inicio de la membresía asignada a un socio y calcular automáticamente la fecha de finalización en función de la duración del plan (mensual, bimestral o por días).**
**Pseudocódigo:**
  ```
  Funcion calcularFinMembresia(fechaInicio, tipoPlan)
    Segun tipoPlan Hacer
        Caso "Mensual": dias ← 30
        Caso "Bimestral": dias ← 60
        Caso "Semestral": dias ← 180
        Caso Otro: dias ← 0
    FinSegun
    fechaFin ← fechaInicio + dias
    Retornar fechaFin
  FinFuncion
---

- **RF-008 El sistema debe permitir cancelar o eliminar un pago asociado a la membresía de un socio.**
**Pseudocódigo:**
  ```
  Procedimiento eliminarPago(idPago)
    lista ← leerTodos("pagos.txt")
    lista ← eliminarPorCampo(lista, idPago)
    sobrescribirArchivo("pagos.txt", lista)
  FinProcedimiento
---

- **RF-009 El sistema debe permitir registrar, consultar, actualizar y eliminar el inventario de las maquinas del gimnasio, así como realizar búsquedas por numero de serie.**
**Pseudocódigo:**
  ```
  Funcion registrarMaquina(numeroSerie, nombre, tipo, estado)
    maquina ← crearMaquina(numeroSerie, nombre, tipo, estado)
    agregarAArchivo("maquinas.txt", maquina)
  FinFuncion

  Funcion buscarMaquinaPorSerie(serie)
    archivo ← abrirArchivo("maquinas.txt", "lectura")
    Mientras no finArchivo(archivo)
        m ← leerMaquina(archivo)
        Si m.numeroSerie = serie Entonces
            cerrarArchivo(archivo)
            Retornar m
        FinSi
    FinMientras
    cerrarArchivo(archivo)
    Retornar NULO
  FinFuncion
---

- **RF-010 El sistema debe permitir modificar el estado de las máquinas registradas.**
**Pseudocódigo:**
  ```
  Procedimiento cambiarEstadoMaquina(numeroSerie, nuevoEstado)
    lista ← leerTodos("maquinas.txt")
    Para cada m en lista
        Si m.numeroSerie = numeroSerie Entonces
            m.estado ← nuevoEstado
        FinSi
    FinPara
    sobrescribirArchivo("maquinas.txt", lista)
  FinProcedimiento
---

- **RF-011 El sistema debe permitir mostrar los equipos por categoría (máquina, disco, mancuerna)**
**Pseudocódigo:**
  ```
  Procedimiento mostrarEquiposPorTipo(tipoBuscado)
    lista ← leerTodos("maquinas.txt")
    Para cada m en lista
        Si m.tipo = tipoBuscado Entonces
            mostrar(m)
        FinSi
    FinPara
  FinProcedimiento
---

- **RF-012 El sistema debe permitir registrar, consultar, actualizar y eliminar empleados del gimnasio, así como realizar búsquedas por id.**
**Pseudocódigo:**
  ```
  Funcion registrarEmpleado(id, dni, nombre, apellido, cargo, estado)
    empleado ← crearEmpleado(id, dni, nombre, apellido, cargo, estado)
    agregarAArchivo("empleados.txt", empleado)
  FinFuncion
---

- **RF-013 El sistema debe permitir gestionar la asistencia de los empleados mediante el registro, actualización y eliminación, especificando la hora de llegada y la hora de salida .**
**Pseudocódigo:**
  ```
  Procedimiento registrarAsistencia(idEmpleado, horaEntrada, horaSalida)
    asistencia ← crearAsistencia(idEmpleado, fechaActual(), horaEntrada, horaSalida)
    agregarAArchivo("asistencias.txt", asistencia)
  FinProcedimiento

  Procedimiento actualizarAsistencia(idAsistencia, nuevaHoraSalida)
    lista ← leerTodos("asistencias.txt")
    Para cada a en lista
        Si a.idAsistencia = idAsistencia Entonces
            a.horaSalida ← nuevaHoraSalida
        FinSi
    FinPara
    sobrescribirArchivo("asistencias.txt", lista)
  FinProcedimiento
---

- **RF-014 El sistema debe generar y mostrar el reporte de asistencia correspondiente al día en curso, indicando para cada empleado su hora de llegada, hora de salida**
**Pseudocódigo:**
  ```
  Procedimiento generarReporteAsistencia(fechaActual)
    lista ← leerTodos("asistencias.txt")
    Escribir "REPORTE DE ASISTENCIA - ", fechaActual
    Para cada a en lista
        Si a.fecha = fechaActual Entonces
            emp ← buscarEmpleadoPorID(a.idEmpleado)
            Escribir emp.nombre, " | Entrada: ", a.horaEntrada, " | Salida: ", a.horaSalida
        FinSi
    FinPara
  FinProcedimiento
---

## Requisitos no funcionales

- **Portabilidad**: La aplicacion debe ejecutarse en cualquier sistema operativo que disponga de Java Runtime Environment (JRE 21 o superior) . No requiere instalacion de base de datos ni servicios externos.

- **Facilidad de mantenimiento**: Repositorio Git, README, codigo organizado en package (o similar según conocimiento del equipo).

- **Usabilidad**: Interfaz simple; aprendizaje < 30 minutos para admin.

- **Velocidad de procesamiento**: Listados paginados < 500 ms; check-in < 200 ms en condiciones normales.

- **Seguridad**: credenciales se almacenan en archivos (se recomienda considerar mejoras futuras), archivos de fidelizacion restringidos y autenticación en base a roles.

- **Restricciones técnicas**: Alojamiento en VPS o PaaS; integraciones de pago en fase 2.
