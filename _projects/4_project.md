---
layout: page
title: "Pachanet: monitoreo inalámbrico de vibraciones"
description: Proyecto de fin de carrera — nodos ESP32 en red mesh que detectan vibraciones estructurales y emiten alertas para prevenir colapsos.
img: assets/img/proj_vib.jpg
stack: ["ESP32", "Wi-Fi mesh", "PCB", "DSP", "IP67"]
featured: true
featured_order: 2
importance: 2
category: IoT y sistemas embebidos
---

**Proyecto Electrónico I y II (PUCP) · ago. 2024 – jul. 2025 · Proyecto en equipo**

**Pachanet** es una red de **nodos inalámbricos basados en ESP32** que monitorean vibraciones estructurales para detectar de forma temprana condiciones de riesgo de colapso. Cada nodo procesa la señal localmente, emite **alertas visuales** (incluidas alertas direccionales para orientar la evacuación) y comparte datos y estado con el resto de la red a través de una **red mesh**, que se centraliza en una laptop para su monitoreo.

<div class="row justify-content-sm-center">
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/vib_instalado.jpg" title="Nodo instalado" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/vib_interior.jpg" title="Interior del nodo" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Nodo montado en la instalación de pruebas, con carcasa estanca y tapa transparente para la señalización LED (izq.), e interior con la PCB principal, el módulo de alimentación AC-DC y el ESP32 (der.).</div>

### Qué hace

- **Detección de vibraciones** con procesamiento digital de señales en el propio nodo.
- **Alertas visuales** con indicadores LED, incluidas alertas **direccionales**; LEDs blancos de alta intensidad para que el nodo funcione también como luminaria.
- **Red Wi-Fi mesh** entre nodos para propagar datos de vibración y estado del sistema hacia una laptop central.
- Conector para **altavoz** (alertas sonoras), ranura **microSD** para registro local y carcasa pensada para entornos **IP67**.

### Hardware

<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/vib_pcb.jpg" title="PCB principal de Pachanet" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/vib_pcb_potencia.jpg" title="PCB de potencia y LEDs" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">PCB principal (zócalos para ESP32-WROOM-32 con USB-C, microSD, batería de respaldo y etapa de audio) y PCB de potencia con convertidores DC-DC y LEDs. Ambas se alimentan desde la red con un módulo AC-DC LZTEC IRM-15-05 (85–305 VAC → 5 V / 3 A).</div>

### Mi aporte

- **Firmware del ESP32** y optimización del software embebido junto al equipo.
- **Comunicación entre nodos** sobre Wi-Fi mesh.
- Adquisición de sensores por **SPI, I2C, I2S** y UART, y **procesamiento digital de señales** para detección temprana y alertas en tiempo real.

### Equipo

Proyecto desarrollado en equipo. El diseño 3D, el diseño de PCB y la integración de componentes estuvieron a cargo de [Jorge Flores Morón](https://jorgeflores.nom.pe/portfolio/portfolio-2/); el software embebido y la red de comunicación se trabajaron en conjunto.

**Tecnologías:** ESP32 · ESP-IDF · FreeRTOS · C/C++ · DSP · Wi-Fi mesh · SPI/I2C/I2S/UART · microSD · PCB
