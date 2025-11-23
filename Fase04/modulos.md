# Módulos del Sistema "Espartanos Fitness"

El sistema está estructurado en una arquitectura modular accesible a través de un menú lateral de navegación. A continuación, se detallan los módulos funcionales y las rutinas operativas disponibles en cada interfaz.

## 1. Módulo de Seguridad y Acceso
Gestiona la entrada al sistema para garantizar que solo personal autorizado (Administradores) pueda manipular la información.

* **Login (Autenticación):** Rutina de validación de credenciales (Usuario y Contraseña).
* **Register (Registro de Admin):** Permite dar de alta a nuevos administradores en el sistema.
* **Gestión de Perfil:** Dentro de la opción "Inicio", el administrador puede visualizar sus datos personales y ejecutar la rutina de **Cambio de Contraseña** para mantener la seguridad de su cuenta.

## 2. Módulo de Gestión de Socios (Clientes)
**Acceso:** Botón `Socios`
Es el núcleo operativo del gimnasio. Permite administrar la base de datos de los clientes y su estado actual.

* **Gestión de Directorio (CRUD):** Botones para agregar (`New`), editar información de contacto (`Edit`) o eliminar (`Delete`) registros de clientes.
* **Gestión de Inscripciones:** A través del botón `Membresía`, se accede a las sub-rutinas de:
    * **Asignar Membresía:** Vincular un socio con un plan (Mensual, Anual, etc.).
    * **Control de Pagos:** Registrar el abono de la inscripción y cambiar el estado de "No Pagado" a "Pagado".
    * **Estado de Vigencia:** Visualización automática del estado del socio (Activo/Inactivo/Vencido) mediante código de colores.

## 3. Módulo de Configuración de Membresías
**Acceso:** Botón `Membresías`
Permite al administrador definir los productos y servicios que ofrece el gimnasio.

* **Administración de Planes:** Creación y modificación de tipos de membresía (Ej. Diario, Mensual, Semestral).
* **Control de Disponibilidad:** Rutinas de `Habilitar` o `Deshabilitar` planes para que aparezcan o no en las opciones de venta sin necesidad de eliminarlos de la base de datos.
* **Gestión de Horarios:** Botón dedicado para definir las franjas horarias permitidas para cada tipo de membresía.

## 4. Módulo de Logística e Inventario
**Acceso:** Botón `Inventario`
Módulo encargado del control de activos fijos del gimnasio (Máquinas, Pesas, Accesorios).

* **Registro de Maquinaria:** Alta de nuevos equipos con número de serie y nombre.
* **Control de Estado:** Capacidad de catalogar el equipo según su operatividad funcional. Los estados visualizados incluyen:
    * *Activo* (Verde)
    * *En Mantenimiento* (Amarillo)
    * *Inutilizable/Dañado* (Rojo)

## 5. Módulo de Recursos Humanos (Trabajadores)
**Acceso:** Botón `Trabajadores`
Administración del personal contratado por el gimnasio (Entrenadores, Limpieza, Recepción).

* **Directorio de Personal:** Registro y edición de los datos de los empleados y sus cargos.
* **Registro de Asistencia Manual:** Botón `Registrar Asistencia` que permite marcar la hora de entrada o salida de un empleado específico directamente desde el sistema.

## 6. Módulo de Reportes y Asistencias
**Acceso:** Botón `Asistencias`
Módulo de consulta para la supervisión operativa.

* **Historial de Entradas/Salidas:** Visualización tabular de los registros de asistencia con detalle de hora y fecha.
* **Búsqueda Filtrada:** Barra de búsqueda para filtrar el historial por nombre o DNI, facilitando la ubicación de eventos específicos de asistencia.

---

## Diagrama de Navegación del Sistema

*(Se recomienda adjuntar aquí la captura compuesta de las pantallas para ilustrar el flujo)*
![Interfaz de Usuario - Gestor de Gimnasio](ruta/a/tu/imagen_compuesta.jpg)
