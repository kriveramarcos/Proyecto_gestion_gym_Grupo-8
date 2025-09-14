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

python
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

  
## Requisitos no funcionales
- Portabilidad del software
- Facilidad de mantenimiento: Que implica el grado de conocimiento de la herramienta de desarrollo del software, así como de la disponibilidad de personal técnico apropiado entre otros.
- Usabilidad del software
- Velocidad de procesamiento de datos
- Restricciones técnicas del software: Por ejemplo, restricciones de diseño debido al sistema operativo utilizado, el entorno de la plataforma, problemas de compatibilidad con alguna aplicación interna o
  externa a la organización, estándar para alguna aplicación determinada, entre otros.


# Tips para mayor claridad
## Propósito
Definir los requisitos técnicos mínimos (RTM) del proyecto de software.

## Qué se espera
- Que sea el imput para el desglose de tareas de la planificación del proyecto, para su posterior diseño e implementación.
