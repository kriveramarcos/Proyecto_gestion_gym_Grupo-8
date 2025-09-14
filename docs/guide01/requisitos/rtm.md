# Especificación de requisitos de software

A continuación se transforman los requisitos mandatorios a especificaciones técnicas (endpoints, entidades y pseudocódigo).

## Requisitos funcionales


## RF-001 Autenticación y Gestión de Usuarios

El sistema debe permitir la autenticación de usuarios a partir de los datos almacenados en archivos planos.

### Entradas:
- Usuario ingresado en el campo de texto.
- Contraseña ingresada en el campo de texto.

### Salidas:
- **Acceso correcto**: Mensaje de acceso correcto y apertura de la interfaz correspondiente al rol.
- **Error**: Mensaje de error si las credenciales no son válidas.

### Precondiciones:
- El archivo de usuarios debe existir y contener registros válidos con los campos: `usuario`, `contraseña`, y `rol` (ADMIN, TRAINER, CLIENT).
- El usuario debe estar previamente registrado en dicho archivo.

### Postcondiciones:
- El sistema identifica el rol del usuario y habilita las funciones correspondientes.
- Si la autenticación falla, el acceso es denegado.

### Restricciones técnicas:
- No se emplea base de datos ni servicios externos de autenticación.
- Contraseñas almacenadas en texto plano.
- Validación únicamente mediante lectura del archivo.

---

## RF-002 Gestión de Socios

### Entidad Socio:
- `id`, `nombre`, `dni`, `email`, `telefono`, `fecha_nacimiento`, `notas_salud`, `foto`, `estado_membresia`.

### Operaciones:
- CRUD: Crear, Leer, Actualizar, Eliminar.
- Búsqueda por `nombre` o `DNI`.
- Paginación y filtros.

---

## RF-003 Membresías y Cobros

### Entidades:
- **Plan:**
  - `id`, `nombre`, `duracion_dias`, `precio`.
  
- **Pago:**
  - `id`, `socio_id`, `plan_id`, `fecha_pago`, `monto`, `metodo_pago`, `estado`.

### Regla:
- Al registrar un pago, se debe actualizar la `fecha_vencimiento` del socio.

### Pseudocódigo (registrar pago):

```python
function registrarPago(socioId, planId, fechaPago, monto):
    plan = obtenerPlan(planId)
    socio = obtenerSocio(socioId)
    pago = crearPago(socioId, planId, fechaPago, monto)
    
    # Si no hay fecha de vencimiento o la fecha actual es mayor que la fecha de vencimiento
    if socio.fecha_vencimiento == null or socio.fecha_vencimiento < fechaPago:
        socio.fecha_vencimiento = fechaPago + plan.duracion_dias
    else:
        socio.fecha_vencimiento = socio.fecha_vencimiento + plan.duracion_dias
    
    guardarSocio(socio)
    return pago
```
## RF-004 Calendario y Clases (por validar)

### Entidad Clase:
- `id`, `nombre`, `instructor_id`, `fecha_hora_inicio`, `duracion_min`, `cupo`, `sala`, `estado`.

### Reserva:
- `id`, `clase_id`, `socio_id`, `fecha_reserva`, `estado`.

### Pseudocódigo (reservar plaza):

```python
function reservarPlaza(socioId, claseId):
    clase = obtenerClase(claseId)
    if clase.estado != "activa": 
        return "Clase no activa"
    
    inscritos = contarReservasActivas(claseId)
    
    if inscritos >= clase.cupo:
        agregarAListaEspera(socioId, claseId)
        return "En lista de espera"
    else:
        crearReserva(socioId, claseId, ahora())
        return "Reserva confirmada"
```
  
## Requisitos no funcionales

### Portabilidad:
- La aplicación debe ejecutarse en cualquier sistema operativo que disponga de **Java Runtime Environment (JRE 21 o superior)**. 
- No requiere instalación de base de datos ni servicios externos.

### Facilidad de mantenimiento:
- Repositorio **Git**.
- **README** con documentación.
- Código organizado en **paquetes** (o similar según conocimiento del equipo).

### Usabilidad:
- Interfaz **simple**.
- Aprendizaje de uso para el administrador en menos de **30 minutos**.

### Velocidad de procesamiento:
- Listados paginados deben cargar en menos de **500 ms**.
- El proceso de check-in debe ser inferior a **200 ms** en condiciones normales.

### Seguridad:
- Las credenciales se almacenan en archivos (se recomienda considerar mejoras futuras).
- Archivos de fidelización restringidos.
- Autenticación en base a **roles**.

### Restricciones técnicas:
- Alojamiento en **VPS** o **PaaS**.
- Integraciones de pago en **fase 2**.


