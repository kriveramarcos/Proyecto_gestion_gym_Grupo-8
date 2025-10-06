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

---

- **RF-003 El sistema debe permitir registrar, consultar, actualizar y eliminar socios, así como realizar búsquedas por DNI.**

---

- **RF-004 El sistema debe permitir registrar, consultar, actualizar y eliminar planes de membresía, incluyendo datos importantes como su nombre, tipo y precio.**

---

- **RF-005 El sistema debe permitir asignar y eliminar restricciones de días y horarios de acceso asociados a cada membresía, de manera que se controle la entrada y salida de los socios según las condiciones definidas.**

---

- **RF-006 El sistema debe permitir gestionar la asignación de una membresía a un socio**

---

- **RF-007 El sistema debe permitir definir la fecha de inicio de la membresía asignada a un socio y calcular automáticamente la fecha de finalización en función de la duración del plan (mensual, bimestral o por días).**

---

- **RF-008 El sistema debe permitir cancelar o eliminar un pago asociado a la membresía de un socio.**

---

- **RF-009 El sistema debe permitir registrar, consultar, actualizar y eliminar el inventario de las maquinas del gimnasio, así como realizar búsquedas por numero de serie.**

---

- **RF-010 El sistema debe permitir modificar el estado de las máquinas registradas.**

---

- **RF-011 El sistema debe permitir mostrar los equipos por categoría (máquina, disco, mancuerna)**

---

- **RF-012 El sistema debe permitir registrar, consultar, actualizar y eliminar empleados del gimnasio, así como realizar búsquedas por id.**

---

- **RF-013 El sistema debe permitir gestionar la asistencia de los empleados mediante el registro, actualización y eliminación, especificando la hora de llegada y la hora de salida .**

---

- **RF-014 El sistema debe generar y mostrar el reporte de asistencia correspondiente al día en curso, indicando para cada empleado su hora de llegada, hora de salida**

---

## Requisitos no funcionales

- **Portabilidad**: La aplicacion debe ejecutarse en cualquier sistema operativo que disponga de Java Runtime Environment (JRE 21 o superior) . No requiere instalacion de base de datos ni servicios externos.

- **Facilidad de mantenimiento**: Repositorio Git, README, codigo organizado en package (o similar según conocimiento del equipo).

- **Usabilidad**: Interfaz simple; aprendizaje < 30 minutos para admin.

- **Velocidad de procesamiento**: Listados paginados < 500 ms; check-in < 200 ms en condiciones normales.

- **Seguridad**: credenciales se almacenan en archivos (se recomienda considerar mejoras futuras), archivos de fidelizacion restringidos y autenticación en base a roles.

- **Restricciones técnicas**: Alojamiento en VPS o PaaS; integraciones de pago en fase 2.
