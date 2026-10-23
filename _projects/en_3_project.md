---
layout: page
lang: en
permalink: /en/projects/3_project/
title: Matter controller on ESP32
description: Control and automation of a Matter light on an ESP32 with chip-tool and Python; basis for an IEEE INTERCON 2026 paper.
img: assets/img/proj_matter.jpg
stack: ["ESP32", "Matter", "esp-matter", "chip-tool", "Python"]
importance: 5
category: IoT and embedded systems
github: https://github.com/ruribebejarano/matter-esp32-controller
related_publications: true
---

[Code on GitHub](https://github.com/ruribebejarano/matter-esp32-controller)

Control of a **Matter** device (on/off light) running on an **ESP32** with `esp-matter` firmware, driven from Python through **chip-tool** on WSL2. The firmware enables **Multi-Admin**, so the same device is managed at the same time by a commercial ecosystem (Alexa) and by chip-tool.

### Highlights

- ESP32 commissioning and control over Matter on Wi-Fi.
- Scheduled automations (on/off by time) from Python.
- WSL2 networking fixes: interface patch in `PlatformManagerImpl.cpp` and mDNS setup.
- Firmware with Multi-Admin enabled and Wi-Fi power save disabled for better stability.

This work was the basis for the experimental evaluation of Matter Multi-Admin scalability and interoperability published at IEEE INTERCON 2026 {% cite esquiagola2026matter %}.

**Technologies:** ESP32 · esp-matter · Matter · chip-tool · Python · WSL2
