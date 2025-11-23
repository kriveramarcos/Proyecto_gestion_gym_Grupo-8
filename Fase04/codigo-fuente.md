# Código Fuente Principal

A continuación se presentan los fragmentos de código más representativos que demuestran la arquitectura del sistema, la lógica de negocio y el manejo de persistencia de datos sin gestores de base de datos externos.

## 1. Lógica de Negocio: Cálculo de Membresías
**Ubicación:** `Controlador/SocioInscrip/InscripcionController.java`

Este módulo es el núcleo del negocio. Se encarga de validar que el socio no tenga deudas pendientes y calcula automáticamente la fecha de vencimiento según el tipo de plan elegido (Mensual, Anual, etc.) utilizando la clase `Calendar`.

```java
// Método para registrar una nueva inscripción
private void agregarInscripcion() {
    try {
        // ... validaciones previas de interfaz ...

        // 1. Validar si el socio ya tiene una inscripción activa
        List<Inscripcion> inscripcionesExistentes = inscripcionDAO.listarPorSocio(socioSelect.getIdSocio());
        if (!inscripcionesExistentes.isEmpty()) {
            JOptionPane.showMessageDialog(null, "El socio ya tiene una inscripción registrada...");
            return;
        }

        // 2. Calcular fecha de vencimiento según tipo de membresía (Lógica de Negocio)
        Calendar calendar = Calendar.getInstance();
        calendar.setTime(fechaInicio);
        switch (m.getTipo().toLowerCase()) {
            case "diario": calendar.add(Calendar.DAY_OF_MONTH, 1); break;
            case "mensual": calendar.add(Calendar.MONTH, 1); break;
            case "trimestral": calendar.add(Calendar.MONTH, 3); break;
            case "anual": calendar.add(Calendar.YEAR, 1); break;
            // ... otros casos
        }
        Date fechaFin = calendar.getTime();

        // 3. Crear objeto y guardar
        Inscripcion ins = new Inscripcion(id, socioSelect.getIdSocio(), ..., fechaInicio, fechaFin, ...);
        
        if (inscripcionDAO.agregar(ins)) {
            JOptionPane.showMessageDialog(null, "Inscripción agregada correctamente.");
        }
    } catch (Exception ex) {
        ex.printStackTrace();
    }
}
```
sss
