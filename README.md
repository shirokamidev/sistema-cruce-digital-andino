# 🛂 Sistema Cruce Digital Andino (C.D.A.)

![Versión](https://img.shields.io/badge/Versión-v2.0-blue.svg) ![Metodología](https://img.shields.io/badge/Metodología-Prototipado_Ágil-orange.svg) ![Calidad](https://img.shields.io/badge/Calidad-ISO%2FIEC%2025010-brightgreen.svg) [![Figma](https://img.shields.io/badge/Prototipo-Figma-ff69b4.svg)](https://www.figma.com/make/42HidHCFNZmC2ggXfrZams/Sistema-Cruce-Digital-Andino?fullscreen=1&t=Ey7H3fw9QE5ryBoY-1&code-node-id=0-9)

El Sistema Cruce Digital Andino (C.D.A.) es una solución digital de alta fidelidad enfocada en la autogestión y el control fronterizo integrado (Aduanas, PDI, SAG y Registro Civil). Este prototipo de interfaz interactiva, diseñado íntegramente en **Figma**, permite visualizar, probar y validar la experiencia de usuario para mitigar los tiempos críticos de espera mediante el registro anticipado de declaraciones y trámites.

🔗 **[Clic aquí para ver el Prototipo Interactivo en Figma](https://www.figma.com/make/42HidHCFNZmC2ggXfrZams/Sistema-Cruce-Digital-Andino?fullscreen=1&t=Ey7H3fw9QE5ryBoY-1&code-node-id=0-9)**

## 👥 Equipo de Desarrollo (SysDev Team)
* [@shirokamidev](https://github.com/shirokamidev) - Benjamín Aliste
* [@Jesusamayap](https://github.com/Jesusamayap) - Jesús Amaya
* [@AriannyLunaA](https://github.com/AriannyLunaA) - Arianny Luna
* [@MichaelMeza-AM](https://github.com/MichaelMeza-AM) - Michael Meza
* [@jeeennifer](https://github.com/jeeennifer) - Jennifer Mochi

---

## 1. Alcance del Sistema y Módulos Funcionales

El diseño de este prototipo v2.0 abarca la construcción de las interfaces para los módulos funcionales del sistema, cubriendo la vista ciudadana y las consolas institucionales, en estricto cumplimiento con el levantamiento de requisitos (IEEE 830) y la arquitectura lógica (UML):

| Módulo | Descripción Funcional | Requisitos Vinculados |
| :--- | :--- | :--- |
| **Módulo 1: Gestión de Usuarios** | Control de ciclo de vida de cuentas, autenticación centralizada y deshabilitación mediante borrado lógico. | RF-01 a RF-04 |
| **Módulo 2: Identidad y PDI** | Validación en tiempo real (API Registro Civil) y alertas migratorias para derivación a fiscalización. | RF-05, RF-06, RF-16, RF-37 |
| **Módulo 3: Tránsito de Menores** | Formulario para la carga de autorizaciones notariales (PDF) y extracción automatizada de códigos. | RF-07 a RF-15 |
| **Módulo 4: SAG y Mascotas** | Registro anticipado de productos orgánicos y validación de titularidad para el ingreso de mascotas. | RF-17 a RF-20 |
| **Módulo 5: Gestión Vehicular** | Vinculación transaccional de patentes y equipaje acompañado directamente al RUT del propietario. | RF-21 a RF-25 |
| **Módulo 6: Plazos y Alertas** | Monitoreo automatizado de plazos de permanencia con alertas visuales inmediatas para Aduanas. | RF-26 a RF-32 |
| **Módulo 7: Admisión Extranjera** | Procesamiento aduanero para el reconocimiento y visado de vehículos internacionales (API Argentina). | RF-33 a RF-36 |
| **Módulo 8: Dashboard y Reportes** | Consola administrativa para la visualización de KPIs, control de APIs y exportación de manifiestos. | RF-38 a RF-41 |

---

## 2. Enfoque de Prototipado y Arquitectura

El desarrollo de estas interfaces en Figma se rige por los principios del **Prototipado Ágil** y el **Modelo 4+1**, buscando iterar rápidamente para eliminar ambigüedades antes del desarrollo de código. Las decisiones técnicas proyectadas son:

- **Persistencia y Resiliencia (Offline-First):** Se diseñaron flujos de contingencia ("Guardado Local Exitoso") indicando el uso de caché, garantizando la continuidad operativa ante caídas de red o desconexiones con las APIs externas.
- **Seguridad e Integridad:** Las interfaces reflejan la aplicación del protocolo ACID, enmascaramiento de campos sensibles y auditoría de perfiles.
- **Extracción Inteligente:** Interfaces preparadas para procesamiento mediante motor OCR con validación *Human-in-the-loop*.

---

## 3. Calidad Ágil y Normativa (ISO/IEC 25010)

Aplicando el **Manifiesto del Testing Ágil**, el diseño de la interfaz en su versión 2.0 busca *prevenir bugs en lugar de encontrarlos*, aplicando estrictamente el modelo de calidad **ISO 25010**:

1. **Usabilidad:** Incorporación de *auto-formatting* en campos críticos (RUT, patentes) y mitigación de la carga cognitiva mediante flujos seccionados para prevenir errores de digitación del pasajero.
2. **Seguridad:** Invalidación visual de sesiones expiradas (límite de 20 min) y prevención en la carga de archivos maliciosos mostrando alertas tempranas.
3. **Fiabilidad:** Manejo claro de errores mediante la paleta institucional (alertas rojas, amarillas y verdes), informando al usuario el estado del sistema sin bloquear la interacción.

---

## 4. Testing de Usabilidad y Control de Versiones

Se aplicó una validación temprana (UAT) y un estricto control de cambios para iterar las soluciones hacia esta versión final. La trazabilidad completa se encuentra documentada en la matriz oficial.

*   Construcción de Mockups de alta fidelidad en Figma.
*   Integración de estados alternativos (pantallas de carga, errores de APIs, modo offline).
*   Generación de Plan de Pruebas y Casos de Prueba basados en ISO 25010.
*   Registro y análisis de hallazgos para corrección de flujos lógicos en futuras iteraciones.

---
*Documentación oficial generada por SysDev Team - Ingeniería de Software.*