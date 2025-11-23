# Anexo 2 — Informe de errores encontrados

---

## DEF-01
**Título:** Login acepta contraseña vacía (validación ausente)  
**Descripción del defecto:** El formulario de autenticación permite enviar con el campo contraseña vacío; el sistema devuelve un error genérico en vez de un mensaje claro de "contraseña requerida".  
**Pasos para reproducir:**
1. Ir a la pantalla de login.  
2. Introducir `usuario = admin_test` y dejar `contraseña = ` vacío.  
3. Pulsar **Ingresar**.  
**Resultado observado:** Se muestra un diálogo de error genérico ("Error de autenticación") y no se indica que la contraseña es obligatoria.  
**Resultado esperado:** Validación del formulario en cliente/servidor mostrando "La contraseña es obligatoria" y no enviar petición al backend.  
**Fecha del defecto:** 2025-10-12  
**Detectado por (Tester):** Jeanpiere Burga Montesinos  
**Estado del defecto:** Abierto  
**Corregido por:** Aaron Bejar Mallma  
**Fecha de cierre:** 2025-10-18  
**Prioridad:** Media  
**Evidencia:** `evidencias/DEF-01_login_contrasena_vacia.png`

---

## DEF-02
**Título:** Registro de socio permite DNI duplicado (no valida existencia)  
**Descripción del defecto:** Al registrar un socio nuevo, el sistema no impide crear un registro con DNI ya existente; genera duplicados en la lista.  
**Pasos para reproducir:**
1. Ir a **Socios → Nuevo socio**.  
2. Introducir `DNI = 70123456`, nombre y demás campos. Guardar.  
3. Repetir el proceso con el mismo DNI.  
**Resultado observado:** Se crean dos fichas con el mismo DNI sin advertencia.  
**Resultado esperado:** Mostrar mensaje "DNI ya registrado" y bloquear la creación.  
**Fecha del defecto:** 2025-10-13  
**Detectado por (Tester):** Nicolas Garcia Avalos  
**Estado del defecto:** Abierto  
**Corregido por:** Aaron Bejar Mallma  
**Fecha de cierre:** 2025-10-20  
**Prioridad:** Alta  
**Evidencia:** `evidencias/DEF-02_socios_dni_duplicado_1.png`, `evidencias/DEF-02_socios_dni_duplicado_2.png`

---

## DEF-03
**Título:** Anulación de pago fuera de 24h permite eliminar registro (regla no aplicada)  
**Descripción del defecto:** La regla de negocio indica que pagos no deben poder anularse pasadas 24 horas. En pruebas, la anulación fue permitida aun cuando la fecha del pago era de hace 3 días.  
**Pasos para reproducir:**
1. Ir a **Pagos** y seleccionar un pago con fecha `2025-10-11`.  
2. Pulsar **Anular pago**.  
3. Confirmar la anulación.  
**Resultado observado:** El sistema permite anular y en la ficha del socio se actualizan estados como si se hubiera anulado correctamente.  
**Resultado esperado:** Bloquear anulación con mensaje "No es posible anular pagos mayores a 24h" y dejar histórico marcado como no anulable.  
**Fecha del defecto:** 2025-10-14  
**Detectado por (Tester):** Kevin Rivera Marcos  
**Estado del defecto:** Abierto  
**Corregido por:** Aaron Bejar Mallma  
**Fecha de cierre:** 2025-10-22  
**Prioridad:** Crítico  
**Evidencia:** `evidencias/DEF-03_anular_pago_fuera_24h.png`

---

## DEF-04
**Título:** Cálculo de fecha de fin de membresía con meses distintos falla en meses de 30/31 días  
**Descripción del defecto:** El cálculo de fecha final agrega 30 días fijos para mensual, pero la regla del sistema debería sumar 1 mes en términos de calendario (ej.: 31 de ene → 28/29 feb). Resultado: fechas incorrectas en algunos ejemplos.  
**Pasos para reproducir:**
1. Asignar membresía mensual con fecha de inicio `2025-01-31`.  
2. Ver fecha de fin calculada.  
**Resultado observado:** Fecha fin calculada = `2025-03-02` (suma 30 días) en vez de `2025-02-28` (o 29).  
**Resultado esperado:** Fecha fin debe respetar la duración esperada del plan (si se define "1 mes", agregar 1 mes calendario).  
**Fecha del defecto:** 2025-10-18  
**Detectado por (Tester):** Kevin Rivera Marcos  
**Estado del defecto:** Abierto  
**Corregido por:** Aaron Bejar Mallma  
**Fecha de cierre:** 2025-10-25  
**Prioridad:** Media  
**Evidencia:** `evidencias/DEF-05_fecha_fin_memb_incorrecta.png`

---

## DEF-05
**Título:** Inventario: al cambiar estado a "mantenimiento" no se guarda el cambio (error en persistencia)  
**Descripción del defecto:** En la pantalla de inventario, al cambiar el estado de un equipo a "mantenimiento" y guardar, la interfaz muestra actualización, pero al recargar o buscar por serie el estado vuelve a "activo".  
**Pasos para reproducir:**
1. Ir a **Inventario**, seleccionar equipo `SN003`.  
2. Cambiar estado a `mantenimiento` y guardar.  
3. Actualizar página o buscar `SN003` de nuevo.  
**Resultado observado:** Tras actualizar, el estado vuelve a `activo`.  
**Resultado esperado:** Estado persistente en almacenamiento; al recargar, debe permanecer `mantenimiento`.  
**Fecha del defecto:** 2025-10-19  
**Detectado por (Tester):** Nicolas Garcia Avalos  
**Estado del defecto:** Corregido
**Corregido por:** Aaron Bejar Mallma  
**Fecha de cierre:** 2025-10-30  
**Prioridad:** Media  
**Evidencia:** `evidencias/DEF-06_inventario_mantenimiento_before.png`, `evidencias/DEF-06_inventario_mantenimiento_after.png`

---

## DEF-06
**Título:** Reporte diario de asistencia muestra registros incompletos cuando se filtra por DNI  
**Descripción del defecto:** Al generar el reporte diario y filtrar por DNI, algunos registros del día aparecen repetidos o faltan datos (por ejemplo hora de salida vacía) aun cuando en la vista de asistencias los tiempos están correctos. Posible error en la consulta de filtrado o en el join.  
**Pasos para reproducir:**
1. Ir a **Reportes → Asistencia diaria**.  
2. Seleccionar fecha = hoy y filtro `DNI = 70456789`.  
3. Generar reporte.  
**Resultado observado:** El reporte muestra entradas duplicadas y algunas filas con `horaSalida` vacía.  
**Resultado esperado:** Mostrar una fila por registro de asistencia con ambos campos (`horaEntrada`, `horaSalida`) llenos.  
**Fecha del defecto:** 2025-10-25  
**Detectado por (Tester):** Kevin Rivera Marcos  
**Estado del defecto:** Abierto  
**Corregido por:** Aaron Bejar Mallma  
**Fecha de cierre:** 2025-11-08  
**Prioridad:** Alta  
**Evidencia:** `evidencias/DEF-08_reporte_asistencia_filtrado_dni.png`

---

## Observaciones generales y recomendaciones
- Priorizar la **anulación de pagos** (DEF-03) y la **reserva concurrente** (DEF-04) por su impacto en negocio y experiencia de usuario (crítico/alto).  
- Implementar validaciones del lado cliente **y** servidor (DEF-01 y DEF-02) para evitar datos inválidos y ataques simples.  
- Revisar la lógica de fechas (usar librería de fechas robusta para sumar meses en lugar de sumar días) (DEF-05).  
- Para las condiciones concurrentes de reserva, aplicar bloqueo optimista/pesimista en la transacción que decremente cupo.  
- Mantener un issue tracker (GitHub Issues / Trello) con los IDs anteriores y vincular PRs/commits que solucionen cada defecto.

---
