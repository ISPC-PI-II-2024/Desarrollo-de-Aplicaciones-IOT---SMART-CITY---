![logo](/e_assets/images/logoISPC.png)

<div align="center">

## ILUMINET — Sistema de Alumbrado Público Inteligente (IoT)

Proyecto educativo y de prototipo cuyo objetivo es diseñar una plataforma para monitorizar y regular luminarias públicas mediante sensores y comunicación IoT. Está orientado a uso docente: explicar protocolos (MQTT, LoRa, HTTP), arquitectura de sistemas y prácticas de sensorización y visualización de datos.

</div>

### Contenido de esta página
- Resumen del proyecto
- Estructura del repositorio
- Hardware y componentes principales
- Resultados esperados
- Hoja de Ruta y Mejoras a Futuro
- Enlaces y documentación del equipo

---

## 📖 Resumen del Proyecto
ILUMINET es un proyecto de Internet de las Cosas (IoT) diseñado para modernizar el alumbrado público tradicional. El sistema aborda el alto costo energético y el mantenimiento ineficiente mediante una red de luminarias inteligentes que ajustan su intensidad en tiempo real según la presencia de peatones o vehículos.

Toda la red es gestionada desde una plataforma centralizada que monitorea el estado, predice fallos y optimiza el mantenimiento, mejorando la seguridad ciudadana y sentando las bases para el desarrollo de futuras aplicaciones de Smart City.

## ✨ Características Principales
- Iluminación Adaptativa: Ahorro energético de hasta un 80% al regular la intensidad de la luz según la demanda real.

- Monitoreo Remoto 24/7: Visualización del estado y consumo de cada luminaria en tiempo real a través de dashboards en Grafana.

- Conectividad Celular: Los gateways utilizan módulos GPRS (SIM800L) para garantizar la comunicación desde cualquier ubicación, sin depender de redes WiFi.

- Arquitectura Escalable: Diseño modular basado en Nodos, Gateways y un Backend centralizado que permite un crecimiento orgánico y controlado.

- Seguridad End-to-End: Comunicación cifrada con TLS entre los gateways y el servidor, y autenticación por credenciales para cada dispositivo.

## 🏗️ Arquitectura del Sistema
El sistema se divide en tres capas lógicas bien diferenciadas, asegurando una clara separación de responsabilidades y una alta modularidad.

- Capa de Nodos (ESP8266): Dispositivos de bajo costo instalados en cada luminaria. Miden la luz ambiental (BH1750), detectan presencia (PIR), monitorean el consumo (SCT-013) y se comunican por RF con su gateway.

- Capa de Gateway (ESP32): Actúa como el cerebro local. Centraliza la comunicación de múltiples nodos por RF, se conecta a internet vía GPRS y envía los datos de forma segura al backend usando MQTT sobre TLS.

- Capa de Backend (Docker): Un conjunto de servicios contenerizados que se ejecutan en un servidor en la nube para recibir, procesar, almacenar y visualizar toda la información del sistema.

---

## 🎯 Objetivo
Permitir a estudiantes y docentes experimentar con conceptos de IoT aplicado a ciudades inteligentes: recopilación de datos desde sensores, comunicación con brokers MQTT, almacenamiento en series temporales e interpretación mediante dashboards.

## 👥 Equipo

| Nombre                        | GitHub                                 |
|------------------------------|----------------------------------------|
| Jose Marquez                | [@marquezjose](https://github.com/marquezjose) |
| Tiziano Adrian Paez                   | [@tpaez](https://github.com/tpaez) |
| María Lilen Guzmán         | [@lilenguzman01](https://github.com/lilenguzman01) |
| Macarena Aylèn Carballo      | [@MacarenaAC](https://github.com/MacarenaAC) |
| Paola Pantoja            | [@PaolaaPantoja](https://github.com/PaolaaPantoja) |
| Juan Diego Gonzalez Antoniazzi | [@JDGA1997](https://github.com/JDGA1997) |
---

## 📂 Estructura del repositorio
- `a_requisitos/` — Definición del problema, objetivos y material curricular.
- `b_investigacion/` — Investigación, protocolos y datasheets (carpeta `Datasheets/`).
- `c_prototipo/` — Documentación técnica, decisiones de diseño y pruebas.
- `d_presentacion/` — Materiales para la presentación y manual de usuario.
- `e_assets/` — Imágenes y recursos gráficos usados en el proyecto.


---

## 📦 Hardware y componentes (resumen)
Tabla resumida de los elementos usados en el prototipo:

| Dispositivo | Componente Clave | Función |
| :--- | :--- | :--- |
| **Gateway** | ESP32 | Procesador central del gateway |
| | SIM800L | Conectividad a internet por red celular GPRS |
| | Hi-Link HLK-20M05 | Fuente de alimentación (220V AC a 5V 4A DC) |
| | Receptor RF 433MHz | Recibe datos de los nodos |
| **Nodo Sensor**| ESP8266 | Microcontrolador de la luminaria |
| | BH1750 | Sensor digital de luminosidad (Lux) |
| | Sensor PIR | Detección de presencia por infrarrojos |
| | SCT-013-005 (5A) | Medición no invasiva del consumo eléctrico AC |
| | Transmisor RF 433MHz| Envía datos al gateway |

En `b_investigacion/Datasheets/` encontrarás los datasheets de los componentes consultados.

---

## 📚 Resultados esperados
La implementación del sistema de alumbrado público inteligente ILUMINET busca generar un impacto positivo y medible en tres áreas fundamentales: Económica, Operativa y Social.

---

## 🔧 Desarrollo y colaboración
- Sigue las normas en `CONTRIBUTING.md` para ramas y commits.
- Antes de abrir un Pull Request, asegúrate de incluir: descripción, pasos para reproducir y screenshots si aplica.

Para pruebas locales y contribuciones sugeridas:
- Añadir scripts de simulación MQTT en `c_prototipo/`.
- Incluir `docker-compose.yml` de ejemplo en una carpeta `examples/`.

---

## 🔮 Hoja de Ruta y Mejoras a Futuro
Para evolucionar el prototipo a una solución de grado industrial, se proponen dos mejoras sinérgicas clave:

Evolución del Gateway a "Edge Controller" con Raspberry Pi Zero 2 W: Reemplazar el ESP32 por una Raspberry Pi permitirá ejecutar un broker MQTT local, dotando al sistema de autonomía operativa ante fallos de internet y habilitando capacidades de cómputo en el borde.

Implementación de Actualizaciones OTA (Over-The-Air): Aprovechando la potencia del gateway Raspberry Pi, se implementará un sistema para actualizar el firmware de los nodos ESP8266 de forma remota, una funcionalidad indispensable para el mantenimiento y la escalabilidad a largo plazo.

---

## 📚 Enlaces y recursos
- `CONTRIBUTING.md` — guía de colaboración.
- `a_requisitos/2_objetivos.md` — objetivo y alcance del proyecto.
- `b_investigacion/1_estado_del_arte.md`, `b_investigacion/2_protocolos_iot.md` — documentación técnica.
- Datasheets: `b_investigacion/Datasheets/` (BH1750, INA219, SX1278, etc.).

---

## ⚖️ Licencia
Este proyecto usa la licencia indicada en `LICENSE` (MIT).

---
