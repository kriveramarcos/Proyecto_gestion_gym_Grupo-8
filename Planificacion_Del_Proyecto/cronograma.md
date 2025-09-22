# CRONOGRAMA DEL PROYECTO: SISTEMA DE GESTIÓN DE GIMNASIO

## Propósito del cronograma

El cronograma establece la planificación inicial de las actividades del proyecto de prototipo de software, mostrando los tiempos, dependencias e hitos.  
Este documento servirá como base para medir el avance y compararlo con la versión final del proyecto.

---

## Listado de actividades principales

Estas actividades deben cubrir todo el ciclo del proyecto.

### DEFINICIÓN DEL PROYECTO

- Definir la idea del proyecto
- Definir objetivo y alcance
- Confirmar acceso al cliente (validar datos, reuniones)
- Elaborar documento inicial (Acta de proyecto)
- **Acta de proyecto entregada**

### ANÁLISIS DE REQUISITOS

- Estudio de factibilidad
- Proceso de obtención de requisitos
- Reunión inicial con cliente
- Especificación de requisitos (ERS)
- Validación de requisitos con cliente
- **ERS entregada**

### ANÁLISIS Y DISEÑO DE ARTEFACTOS

- Diseño de prototipo de interfaces (Figma)
- Diagramas procesos de negocio
- Modelado de casos de uso (UML)
- Diseño conceptual ER de la base de datos
- **Validación de diseño con el cliente**

### IMPLEMENTACIÓN

- Configuración del entorno de desarrollo
- Desarrollo del módulo de autenticación
- Desarrollo del módulo de gestión de socios y membresías
- Desarrollo del módulo de gestión de inventario de equipos
- Desarrollo del módulo de gestión de empleados y asistencia
- **Integración de todos los módulos**

### PRUEBAS

- Pruebas unitarias (por módulo)
- Pruebas de integración (flujo completo del sistema)
- Correcciones de errores encontrados

### DESARROLLO DEL INFORME FINAL DEL PROYECTO

- Elaboración y revisión del informe

### ENTREGA DEL PROTOTIPO

- **Prototipo final entregado**

---

## Dependencias entre actividades

- **Definir objetivos y alcance** y **Confirmar acceso al cliente (validar datos, reuniones)** dependen de **Definir la idea del proyecto**
- **Elaborar documento inicial (Acta de proyecto)** depende de **Definir objetivo y alcance** y **Definir la idea del proyecto**
- **Acta de proyecto entregada** depende de **Elaborar documento inicial (Acta de proyecto)**
- **Análisis de requisitos** y **Estudio de factibilidad** dependen de **Acta de proyecto entregada**
- **Proceso de obtención de requisitos** depende de **Estudio de factibilidad**
- **Reunión inicial con cliente** depende de **Proceso de obtención de requisitos** y **Confirmar acceso al cliente (validar datos, reuniones)**
- **Especificación de requisitos (ERS)** depende de **Proceso de obtención de requisitos** y **Reunión inicial con cliente**
- **Validación de requisitos con cliente** depende de **Especificación de requisitos (ERS)**
- **ERS entregada** depende de **Validación de requisitos con cliente**
- **Análisis y diseño de artefactos**, **Diseño de prototipo de interfaces (Figma)**, **Diagramas procesos de negocio** y **Diseño conceptual ER de la base de datos** dependen de **ERS entregada**
- **Modelado de casos de uso (UML)** depende de **Diagramas procesos de negocio**
- **Validación de diseño con el cliente** depende de todos los diagramas
- **Implementación** y **Configuración del entorno de desarrollo** dependen de **Validación de diseño con el cliente**
- **Desarrollo del módulo de autenticación** depende de **Configuración del entorno de desarrollo**
- **Desarrollo del módulo de gestión de socios y membresías**, **gestión de inventario de equipos** y **gestión de empleados y asistencia** dependen del **módulo de autenticación**
- **Integración de todos los módulos** depende de todos los módulos anteriores
- **Pruebas unitarias (por módulo)** y **Pruebas de integración (flujo completo del sistema)** dependen de **Integración de todos los módulos**
- **Correcciones de errores encontrados** depende de las dos pruebas hechas
- **Desarrollo del informe final del proyecto** depende de **Correcciones de errores encontrados**
- **Entrega del prototipo final** depende de **Desarrollo del informe final del proyecto**

---

## Hitos

- **Hito 1:** Acta de proyecto entregada
- **Hito 2:** ERS entregada
- **Hito 3:** Validación de diseño con el cliente
- **Hito 4:** Entrega del prototipo final

---

## Cronograma en tabla

| Actividad                                 | Duración |
| ----------------------------------------- | -------- |
| DEFINICIÓN DEL PROYECTO                   | 7 días   |
| ANÁLISIS DE REQUISITOS                    | 14 días  |
| ANÁLISIS Y DISEÑO DE ARTEFACTOS           | 8 días   |
| IMPLEMENTACIÓN                            | 21 días  |
| PRUEBAS                                   | 7 días   |
| DESARROLLO DEL INFORME FINAL DEL PROYECTO | 5 días   |
| ENTREGA DEL PROTOTIPO                     | Hito     |
