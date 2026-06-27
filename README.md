# Sistema Cruce Digital Andino (C.D.A.)

![](https://img.shields.io/badge/Versión-MVP_1.0-blue.svg) ![](https://img.shields.io/badge/Metodología-Prototipado_Ágil-orange.svg) ![](https://img.shields.io/badge/Calidad-ISO%2FIEC%2025010-brightgreen.svg) ![](https://img.shields.io/badge/Licencia-MIT-green.svg)

> El Sistema Cruce Digital Andino (C.D.A.) es un sistema digital enfocado en la autogestión y el control fronterizo integrado (Aduanas, PDI, SAG y Registro Civil). Este Producto Mínimo Viable (MVP) permite visualizar, probar y validar la experiencia de usuario para mitigar los tiempos críticos de espera mediante el registro anticipado de declaraciones y trámites.

**Tabla de Contenidos**

* [1. Alcance del Sistema y Módulos Funcionales](#1-alcance-del-sistema-y-módulos-funcionales)
* [2. Enfoque de Prototipado y Arquitectura](#2-enfoque-de-prototipado-y-arquitectura)
* [3. Repositorio de Prototipos de Interfaz](#3-repositorio-de-prototipos-de-interfaz)
* [4. Calidad Ágil y Normativa (ISO/IEC 25010)](#4-calidad-ágil-y-normativa-isoiec-25010)
* [5. Testing de Usabilidad y Estado de Avance](#5-testing-de-usabilidad-y-estado-de-avance)

---

## 1. Alcance del Sistema y Módulos Funcionales

El diseño de este MVP abarca la construcción de los prototipos de interfaz para los 8 módulos funcionales del sistema, cubriendo tanto la vista ciudadana como las consolas institucionales:

| Módulo | Descripción Funcional | Requisitos Vinculados |
| :--- | :--- | :--- |
| **Módulo 1: Gestión de Usuarios y Acceso** | Controla el ciclo de vida de las cuentas del sistema, autenticación centralizada (incluyendo ClaveÚnica) y deshabilitación mediante borrado lógico. | RF-01 a RF-04 |
| **Módulo 2: Control de Pasajeros e Identidad** | Validación de identidad en tiempo real con alertas migratorias integradas para derivación inmediata a fiscalización manual de la PDI. | RF-05, RF-06, RF-16, RF-37 |
| **Módulo 3: Tránsito y Validación de Menores** | Gestiona el formulario ciudadano para la carga de autorizaciones notariales (PDF) y la posterior extracción automatizada de códigos de verificación. | RF-07 a RF-15 |
| **Módulo 4: Declaraciones Juradas (SAG y Mascotas)** | Registro anticipado de productos de origen animal/vegetal y validación de titularidad mediante microchips para el ingreso de mascotas. | RF-17 a RF-20 |
| **Módulo 5: Registro y Gestión Vehicular** | Vinculación transaccional de patentes, números de motor/chasis y equipaje acompañado directamente al RUT del propietario del vehículo. | RF-21 a RF-25 |
| **Módulo 6: Control de Plazos y Alertas de Salida** | Monitoreo automatizado de plazos de permanencia vehicular con alertas visuales inmediatas para el inspector de Aduanas. | RF-26 a RF-32 |
| **Módulo 7: Admisión de Vehículos Extranjeros** | Procesamiento aduanero para el reconocimiento, visado e ingreso de vehículos internacionales con control interinstitucional. | RF-33 a RF-36 |
| **Módulo 8: Reportes, Estadísticas y Exportación** | Consola administrativa para la visualización de volúmenes de trámites por institución y emisión de copias impresas de manifiestos. | RF-38 a RF-41 |

---

## 2. Enfoque de Prototipado y Arquitectura

El desarrollo de estas interfaces se rige por los principios del **Prototipado Ágil**, buscando aprender e iterar rápidamente para eliminar ambigüedades antes del desarrollo a nivel de código. Las decisiones técnicas proyectadas en la interfaz son:

- **Persistencia y Resiliencia (Offline-First):** Se diseñaron notificaciones de "Guardado Local Exitoso" indicando el uso de caché. Esto garantiza la continuidad operativa ante caídas de red o desconexiones con las APIs de PDI/Registro Civil.
- **Seguridad e Integridad:** Las interfaces reflejan la aplicación del protocolo ACID, enmascaramiento de campos sensibles y el uso de borrado lógico (estado "Inactivo") para la auditoría de perfiles.
- **Extracción Inteligente:** Interfaces preparadas para procesamiento mediante motor OCR con validación *Human-in-the-loop*, delegando la revisión final al funcionario fronterizo.

---

## 3. Repositorio de Prototipos de Interfaz

*(Nota: Las imágenes en alta fidelidad de los prototipos se encuentran cargadas en la estructura de archivos de este repositorio).*

### Interfaces Ciudadanas (Pasajeros)
* **Módulo 1:** Pantallas de Login, Creación de Cuenta y Perfil de Usuario.
* **Módulo 3:** Formulario de Salida/Entrada de Menores y carga segura de documentos PDF.
* **Módulo 4:** Formularios paso a paso para la Declaración Jurada SAG y Registro de Mascotas.
* **Módulo 5:** Interfaz de vinculación de datos vehiculares y equipaje acompañado.

### Consolas Institucionales (Funcionarios)
* **Módulo 2:** Monitor de alertas migratorias e impedimentos críticos (PDI).
* **Módulo 6:** Panel de fiscalización con indicadores de plazos vencidos (Aduanas).
* **Módulo 7:** Interfaz de validación y escaneo de comprobantes para vehículos extranjeros.
* **Módulo 8:** Dashboard analítico con filtros por institución y opciones de exportación.

---

## 4. Calidad Ágil y Normativa (ISO/IEC 25010)

Aplicando el manifiesto del testing ágil, **la calidad es responsabilidad de todo el equipo** y el diseño de la interfaz busca *prevenir bugs en lugar de encontrarlos*. 

1. **Usabilidad:** Incorporación de *auto-formatting* en campos críticos (RUT, patentes) para disminuir la carga cognitiva y prevenir errores de digitación del pasajero.
2. **Seguridad:** Invalidación visual de sesiones expiradas, prevención en la carga de archivos maliciosos mostrando alertas tempranas en la interfaz de subida (Módulo 3).
3. **Fiabilidad:** Manejo claro de errores, informando al usuario cuando el sistema opera en modo offline sin bloquear la interacción.
4. **Eficiencia de Rendimiento:** Estructura visual diseñada para reflejar consultas asíncronas optimizadas (< 500ms).

---

## 5. Testing de Usabilidad y Estado de Avance

Se aplicó una validación temprana para iterar las soluciones. Los hallazgos se categorizaron según su severidad para su posterior corrección:

- [x] Construcción de Mockups de alta fidelidad y flujos documentados.
- [x] Integración de estados alternativos (pantallas de carga, errores, offline).
- [x] Testing de usabilidad ejecutado.
- [x] **Resolución de Hallazgos Críticos (P0/P1):** Corrección de flujos que bloqueaban la interacción en la validación de identidades y alertas de la PDI.
- [ ] **Backlog (P2/P3):** Mejoras de contraste y micro-interacciones diferidas para la V2.

---
*Documentación oficial generada por **SysDev Team** para la Evaluación Parcial N° 3 de Ingeniería de Software.*


---
## Estado Actual: Versión Final (V.3):

### Refactorización Módulo 3: Tránsito y Validación de Menores
Este módulo del Sistema Cruce Digital Andino (C.D.A.) procesa y autoriza el tránsito transfronterizo de personas menores de edad. En esta iteración final, se ha optimizado radicalmente la experiencia del usuario (UX) unificando el proceso en una sola vista.

**Principales Actualizaciones de la V.3:**
1. Consolidación de Interfaz: El usuario completa los datos de identidad del menor, la información del adulto acompañante, carga la autorización notarial (PDF) y recibe el feedback de la solicitud enviada; **todo dentro de una única pantalla**, reduciendo la fricción y el tiempo de trámite.
2. Validación y Extracción Simultánea: El sistema procesa la carga del archivo PDF y ejecuta la validación OCR para extraer el código notarial sin forzar al pasajero a recargar la página o cambiar de módulo.
3. Feedback: La confirmación de "Solicitud enviada a la PDI para validación" se despliega dinámicamente en la base de la misma pantalla.

#### Interfaz Unificada del Formulario de Menores (V.3)



## Historial de Versiones y Evolución del Prototipo Modulo 3: 

*Refactorización módulo 3 Tránsito y Validación de Menores*

**Módulo 3: Tránsito y Validación de Menores.**
Descripción General:
Este módulo del Sistema Cruce Digital Andino (C.D.A.) procesa y autoriza el tránsito transfronterizo de personas menores de edad.
Su objetivo principal es digitalizar el control legal, asegurando el cumplimiento de las normativas vigentes mediante validaciones automatizadas y exigiendo la documentación notarial cuando corresponde.

Características y Funcionalidades:
 1. Gestión de Formularios: Autogestión anticipada para la creación, llenado y almacenamiento seguro de los formularios de tránsito de menores.
 2. Validación de Identidad y Relación Legal: Integración con la PDI y Registro Civil para comprobar la vigencia de documentos y evaluar la relación con el o los acompañantes.
 3. Tratamiento Seguro de Archivos: Carga de autorizaciones notariales en formato PDF con escaneo perimetral de seguridad y validación de tamaño/integridad.
 4. Integración OCR (Inteligencia Artificial): Extracción automatizada de códigos notariales (CVE o QR) desde los documentos cargados para certificar su autenticidad institucional.
 5. Casos Especiales: Validación estructurada de resoluciones legales para la salida de menores adoptados.

Diseño e Interfaz de Usuario (UI):
Implementación de flujos visuales independientes y refactorizados para el Formulario de Entrada de Menores y el Formulario de Salida de Menores, mejorando la precisión y claridad para el pasajero.Diseño de pantallas de retroalimentación para el guardado temporal de datos y confirmación de validación.
