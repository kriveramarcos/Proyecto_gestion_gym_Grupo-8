## Anexo A — Checklist y Casos de Prueba

A continuación, una checklist de casos de prueba mínimos para validar los requisitos mandatorios:

| ID    |   Caso de prueba   | Procedimiento breve                               | Criterios de aceptación                                         |
| :---- | :----------------: | :------------------------------------------------ | :-------------------------------------------------------------- |
| TC-01 |    Crear socio     | Admin crea socio con datos obligatorios           | Socio aparece en lista; se puede asignar plan.                  |
| TC-02 |   Registrar pago   | Admin registra pago por plan                      | Fecha de vencimiento del socio se actualiza correctamente.      |
| TC-03 |    Crear clase     | Admin crea clase con cupo e instructor            | Clase visible en calendario y aceptable para reservas.          |
| TC-04 |   Reservar plaza   | Cliente/admin reserva plaza en clase              | Reserva confirmada y cupo decrementa; lista de espera si lleno. |
| TC-05 |      Check-in      | Registrar asistencia por reserva (manual)         | Asistencia queda marcada con hora y usuario que registró.       |
| TC-06 |  Generar reporte   | Admin genera reporte de ingresos por mes          | Mostrar datos correctos en tabla.                               |
| TC-07 | Control de accesos | Usuario con rol inadecuado intenta endpoint admin | Respuesta de error en ventanas de dialogo                       |
