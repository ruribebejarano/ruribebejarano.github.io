---
layout: page
lang: en
permalink: /en/projects/4_project/
title: "Pachanet: wireless vibration monitoring"
description: Capstone project — ESP32 nodes on a mesh network that detect structural vibrations and raise alerts to help prevent collapses.
img: assets/img/proj_vib.jpg
stack: ["ESP32", "Wi-Fi mesh", "PCB", "DSP", "IP67"]
featured: true
featured_order: 2
importance: 2
category: IoT and embedded systems
---

**Electronic Project I & II (PUCP) · Aug 2024 – Jul 2025 · Team project**

**Pachanet** is a network of **ESP32-based wireless nodes** that monitor structural vibrations to detect early signs of collapse risk. Each node processes the signal locally, raises **visual alerts** (including directional alerts to guide evacuation) and shares data and status with the rest of the network through a **mesh network**, which is collected on a laptop for monitoring.

<div class="row justify-content-sm-center">
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/vib_instalado.jpg" title="Installed node" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/vib_interior.jpg" title="Inside the node" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Node mounted on the test installation, with a sealed enclosure and transparent lid for LED signaling (left), and the inside with the main PCB, the AC-DC power module and the ESP32 (right).</div>

### What it does

- **Vibration detection** with digital signal processing on the node itself.
- **Visual alerts** with LED indicators, including **directional** alerts; high-intensity white LEDs so the node also works as a light fixture.
- **Wi-Fi mesh network** between nodes to propagate vibration data and system status to a central laptop.
- **Speaker** connector (audible alerts), **microSD** slot for local logging and an enclosure designed for **IP67** environments.

### Hardware

<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/vib_pcb.jpg" title="Pachanet main PCB" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/vib_pcb_potencia.jpg" title="Power and LED PCB" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Main PCB (sockets for ESP32-WROOM-32 boards with USB-C, microSD, backup battery and audio stage) and power PCB with DC-DC converters and LEDs. Both are powered from the mains through an LZTEC IRM-15-05 AC-DC module (85–305 VAC → 5 V / 3 A).</div>

### My contribution

- **ESP32 firmware** and embedded software optimization together with the team.
- **Node-to-node communication** over Wi-Fi mesh.
- Sensor acquisition over **SPI, I2C, I2S** and UART, and **digital signal processing** for early detection and real-time alerts.

### Team

Team project. 3D design, PCB design and component integration were led by [Jorge Flores Morón](https://jorgeflores.nom.pe/portfolio/portfolio-2/); the embedded software and the communication network were developed jointly.

**Technologies:** ESP32 · ESP-IDF · FreeRTOS · C/C++ · DSP · Wi-Fi mesh · SPI/I2C/I2S/UART · microSD · PCB
