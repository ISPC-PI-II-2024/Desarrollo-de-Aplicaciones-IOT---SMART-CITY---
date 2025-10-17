![logo](/e_assets/images/logoISPC.png)

<div align="center">

# 🌐 ILUMINET

# Sistema de Alumbrado Público Inteligente basado en IoT

</div>

  
> Documentacion del proyecto
>
> 
## 🎯 Objetivo
Diseñar y desarrollar un frontend educativo que permita a estudiantes visualizar datos en tiempo real, simular redes IoT y comprender protocolos de telecomunicaciones.

## 👥 Equipo
- Jose Marquez -[GitHub: marquezjose](https://github.com/marquezjose)
- Lisandro JUncos - [GitHub: Lisandro-05](https://github.com/Lisandro-05)
- Pantoja, Paola Natalia Alejandra - [GitHub: PaolaaPantoja](https://github.com/PaolaaPantoja)
- Paez, Tiziano Adrian - [GitHub: tpaez](https://github.com/tpaez)
- María Lilen Guzmán- [GitHub: lilenguzman01](https://github.com/lilenguzman01)
- Macarena Carballo - [GitHub: completar](https:// github.com/xxxx)
- María Lilen Guzmán- [GitHub:lilenguzman01](https://github.com/lilenguzman01)
- Juan Diego Gonzalez Antoniazzi - [GitHub:JDGA1997](https://github.com/JDGA1997)

## 📂 Estructura del repositorio
| Carpeta | Contenido |
|--------|---------|
| `a_requisitos/` | Definición del problema, objetivos y funcionalidades |
| `b_investigacion/` | Fundamentos técnicos, protocolos y arquitectura |
| `c_prototipo/` | Código del frontend, pruebas y evidencias |
| `d_presentacion/` | Presentación final, guion y reflexión |
| `assets/` | Imágenes, diagramas y recursos multimedia |

## ILUMINET: Sistema de Alumbrado Público Inteligente basado en IoT
📖 Resumen del Proyecto
ILUMINET es un proyecto de Internet de las Cosas (IoT) diseñado para modernizar el alumbrado público tradicional. El sistema aborda el alto costo energético y el mantenimiento ineficiente mediante una red de luminarias inteligentes que ajustan su intensidad en tiempo real según la presencia de peatones o vehículos.

Toda la red es gestionada desde una plataforma centralizada que monitorea el estado, predice fallos y optimiza el mantenimiento, mejorando la seguridad ciudadana y sentando las bases para el desarrollo de futuras aplicaciones de Smart City.

✨ Características Principales
Iluminación Adaptativa: Ahorro energético de hasta un 80% al regular la intensidad de la luz según la demanda real.

Monitoreo Remoto 24/7: Visualización del estado y consumo de cada luminaria en tiempo real a través de dashboards en Grafana.

Conectividad Celular: Los gateways utilizan módulos GPRS (SIM800L) para garantizar la comunicación desde cualquier ubicación, sin depender de redes WiFi.

Arquitectura Escalable: Diseño modular basado en Nodos, Gateways y un Backend centralizado que permite un crecimiento orgánico y controlado.

Seguridad End-to-End: Comunicación cifrada con TLS entre los gateways y el servidor, y autenticación por credenciales para cada dispositivo.

🏗️ Arquitectura del Sistema
El sistema se divide en tres capas lógicas bien diferenciadas, asegurando una clara separación de responsabilidades y una alta modularidad.

Capa de Nodos (ESP8266): Dispositivos de bajo costo instalados en cada luminaria. Miden la luz ambiental (BH1750), detectan presencia (PIR), monitorean el consumo (SCT-013) y se comunican por RF con su gateway.

Capa de Gateway (ESP32): Actúa como el cerebro local. Centraliza la comunicación de múltiples nodos por RF, se conecta a internet vía GPRS y envía los datos de forma segura al backend usando MQTT sobre TLS.

Capa de Backend (Docker): Un conjunto de servicios contenerizados que se ejecutan en un servidor en la nube para recibir, procesar, almacenar y visualizar toda la información del sistema.

## Hardware y componentes

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
    
## 🔮 Hoja de Ruta y Mejoras a Futuro
Para evolucionar el prototipo a una solución de grado industrial, se proponen dos mejoras sinérgicas clave:

Evolución del Gateway a "Edge Controller" con Raspberry Pi Zero 2 W: Reemplazar el ESP32 por una Raspberry Pi permitirá ejecutar un broker MQTT local, dotando al sistema de autonomía operativa ante fallos de internet y habilitando capacidades de cómputo en el borde.

Implementación de Actualizaciones OTA (Over-The-Air): Aprovechando la potencia del gateway Raspberry Pi, se implementará un sistema para actualizar el firmware de los nodos ESP8266 de forma remota, una funcionalidad indispensable para el mantenimiento y la escalabilidad a largo plazo.


    
## 📚 Resultados esperados
Resultados Esperados del Proyecto ILUMINET
La implementación del sistema de alumbrado público inteligente ILUMINET busca generar un impacto positivo y medible en tres áreas fundamentales: Económica, Operativa y Social.

### 1. Resultados Económicos y Ambientales 📉
El objetivo principal del proyecto es generar una optimización drástica del uso de la energía.

Reducción del Consumo Energético: Se espera alcanzar un ahorro de energía significativo contra el sistema de alumbrado tradicional, se estima al rededor del 50%. Este ahorro se logra mediante la regulación inteligente de la intensidad lumínica, manteniendo las luces a un nivel bajo (ej. 20%) y elevándolas al 100% solo cuando se detecta presencia.

Disminución de la Huella de Carbono: Como consecuencia directa del ahorro energético, se proyecta una reducción significativa en las emisiones de CO₂, contribuyendo a las metas de sostenibilidad ambiental del municipio.

Retorno de la Inversión (ROI): Se espera que el ahorro generado en la factura eléctrica permita amortizar el costo del hardware y la instalación en un plazo de tiempo competitivo, haciendo el proyecto financieramente viable.

### 2. Resultados Operativos y de Mantenimiento ⚙️
El sistema transformará la gestión del alumbrado público de un modelo reactivo a uno proactivo.

Optimización del Mantenimiento: La plataforma de monitoreo permitirá reducir los costos operativos de mantenimiento al eliminar la necesidad de patrullas de inspección nocturnas. El sistema reportará fallos (ej. una luminaria que no responde o cuyo consumo es anómalo) de forma automática e instantánea.

Mantenimiento Predictivo: El análisis de datos históricos de consumo y horas de funcionamiento permitirá predecir el fin de la vida útil de las luminarias, programando su reemplazo antes de que fallen y minimizando el tiempo que una zona permanece a oscuras.

Gestión Centralizada: Se obtendrá un inventario digital y un mapa en tiempo real de toda la infraestructura de alumbrado, permitiendo una gestión centralizada y eficiente desde un único panel de control.

### 3. Resultados Sociales y de Seguridad Ciudadana 🚶‍♀️
Más allá de la tecnología, el proyecto busca mejorar la calidad de vida de los ciudadanos.

Mejora de la Percepción de Seguridad: Al garantizar una iluminación adecuada y funcional en todo momento, especialmente en zonas peatonales, paradas de transporte público y parques, se espera aumentar la sensación de seguridad de los transeúntes.

Reducción de Tiempos de Inactividad: El sistema de alertas automáticas asegurará que las reparaciones se realicen en un tiempo mucho menor, reduciendo drásticamente los períodos en que calles o barrios enteros quedan a oscuras.

Base para una "Smart City": ILUMINET no es solo un sistema de iluminación; es una plataforma de infraestructura IoT. Los gateways desplegados podrían, en el futuro, servir como base para conectar otros servicios inteligentes, como sensores de calidad del aire, gestión de residuos o puntos de acceso Wi-Fi público.

## 📎 Enlaces útiles
- [Definir los enlaces a la informacion correcta (Solicitado por el profesor para mejor legibilidad)] (pendiente)
- [Guía de contribución](CONTRIBUTING.md)
