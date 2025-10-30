# Requisitos no funcionales

*(Definen la calidad del sistema — hay que cumplirlos desde el inicio)*

## Portabilidad
La aplicación debe ejecutarse en sistemas que tengan Java Runtime Environment (JRE 21+). No requiere DB externa (uso de archivos planos o DB embebida).

## Facilidad de mantenimiento
Código organizado en repositorios (Git), con README, estructura de paquetes y comentarios. Uso de control de versiones.

## Usabilidad
Interfaz simple y clara; el administrador debe aprender a usar el sistema en menos de 30 minutos. Diseño responsive para uso en navegador móvil.

## Rendimiento / Velocidad
Listados paginados deben cargar en < 500 ms en condiciones normales. Operaciones de check-in deben realizarse en < 200 ms.

## Seguridad
Contraseñas con hashing, control de acceso por roles (al menos admin y entrenador), cifrado de campos sensibles (p. ej. datos de salud); backups automáticos recomendados. Credenciales y datos sensibles no deben exponerse.

## Confiabilidad / Disponibilidad
Mecanismo de backup/restauración de archivos; la app debe permitir recuperarse de pérdida de datos mínima sin intervención compleja.

## Restricciones técnicas
Despliegue previsto en VPS/PaaS con JRE 21. Integraciones bancarias y servicios externos quedan para Fase 2.

## Mantenibilidad / Documentación
Tests unitarios básicos, documentación mínima (README, guía de instalación, manual de usuario) y checklist de aceptación por requisito.

## Legal / Privacidad
Datos personales y de salud tratados conforme a principios de minimización: solo datos necesarios, con cifrado y visibilidad restringida.
