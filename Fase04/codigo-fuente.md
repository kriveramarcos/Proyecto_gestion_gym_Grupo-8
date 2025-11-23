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
## 2. Persistencia de Datos (Archivos de Texto)
**Ubicación:** `Modelo/SocioDAO.java`

El sistema implementa un motor de persistencia propio. En lugar de usar SQL, se serializan los objetos y se almacenan en archivos planos (.txt). Este fragmento muestra cómo se recuperan y "parsean" los datos desde el almacenamiento físico.

```java
// Método para leer el archivo plano y convertirlo en objetos Java
public void cargarSocios() {
    socios.clear();
    File file = new File("src/main/resources/Files/Socios.txt");

    try (BufferedReader br = new BufferedReader(new FileReader(file))) {
        String linea;
        // Lectura línea por línea
        while ((linea = br.readLine()) != null) {
            String[] partes = linea.split(";"); // Separador definido
            
            // Reconstrucción del objeto Socio
            if (partes.length == 7) {
                Date fecha = sdf.parse(partes[5]);
                Socio s = new Socio(
                        partes[0], // ID
                        partes[1], // DNI
                        partes[2], // Nombres
                        partes[4], // Correo
                        fecha,     
                        partes[6]  // Estado
                );
                socios.add(s);
            }
        }
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```
## 3. Seguridad y Validación de Credenciales
**Ubicación:** `Controlador/InfoAdmin/DataAdminController.java`

Módulo encargado de la gestión de seguridad del administrador. El siguiente código demuestra las validaciones estrictas antes de permitir un cambio de contraseña sensible.

```java
private void modificarPass() {
    try {
        // ... obtención de datos de la vista ...

        // 1. Validar contraseña actual contra la almacenada
        if (!inputPassActual.equals(adminLogueado.getPass())) {
            throw new Exception("❌ La contraseña actual no es correcta.");
        }

        // 2. Reglas de complejidad y coincidencia
        if (inputNewPass.length() < 6) {
            throw new Exception("⚠️ La nueva contraseña debe tener al menos 6 caracteres.");
        }
        if (!inputNewPass.equals(inputConfirmarPass)) {
            throw new Exception("❌ Las contraseñas nuevas no coinciden.");
        }

        // 3. Confirmación y actualización
        int confirm = JOptionPane.showConfirmDialog(dataAdminView, "¿Deseas actualizar tu contraseña?");
        
        if (confirm == JOptionPane.YES_OPTION) {
            boolean actualizado = usuarioDAO.modificarUsuarioConDNI(..., inputNewPass, "ADMIN");
            if (actualizado) {
                adminLogueado.setPass(inputNewPass); // Actualización en sesión
                JOptionPane.showMessageDialog(dataAdminView, "✅ Contraseña actualizada.");
            }
        }
    } catch (Exception e) {
        JOptionPane.showMessageDialog(dataAdminView, e.getMessage());
    }
}
