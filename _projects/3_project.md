---
layout: page
title: Controlador Matter sobre ESP32
description: Control y automatización de una luz Matter en ESP32 con chip-tool y Python; base de un paper en IEEE INTERCON 2026.
img: assets/img/proj_matter.jpg
stack: ["ESP32", "Matter", "esp-matter", "chip-tool", "Python"]
featured: true
featured_order: 2
importance: 3
category: IoT y sistemas embebidos
github: https://github.com/ruribebejarano/matter-esp32-controller
related_publications: true
---

[Código en GitHub](https://github.com/ruribebejarano/matter-esp32-controller)

Control de un dispositivo **Matter** (luz _on/off_) implementado en un **ESP32** con firmware `esp-matter`, desde Python mediante **chip-tool** en WSL2. El firmware habilita **Multi-Admin**, de modo que el mismo dispositivo es administrado a la vez por un ecosistema comercial (Alexa) y por chip-tool.

### Puntos clave

- Comisionamiento del ESP32 y control por Matter sobre Wi-Fi.
- Automatizaciones programadas (encendido/apagado por horario) desde Python.
- Solución de problemas de red en WSL2: parche de interfaz en `PlatformManagerImpl.cpp` y configuración de mDNS.
- Firmware con Multi-Admin habilitado y Wi-Fi power save deshabilitado para mayor estabilidad.

Este trabajo sirvió de base para la evaluación experimental de escalabilidad e interoperabilidad de Matter Multi-Admin publicada en IEEE INTERCON 2026 {% cite esquiagola2026matter %}.

**Tecnologías:** ESP32 · esp-matter · Matter · chip-tool · Python · WSL2
