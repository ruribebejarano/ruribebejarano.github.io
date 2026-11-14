---
layout: page
lang: en
permalink: /en/projects/11_project/
title: Biometric attendance and headcount system
description: Fingerprint-based attendance system on ESP32, with an in-house PCB and a Python desktop app.
img: assets/img/proj_aforo.jpg
stack: ["ESP32", "UART", "SPI", "I2C", "EasyEDA", "Arduino IDE", "Python"]
importance: 6
category: IoT and embedded systems
---

**LIBRA-PUCP · pre-professional intern · 2026** · built with a Mechatronics Engineering intern

Design and implementation of a **fingerprint-based** attendance and headcount system on **ESP32**, replacing a paper sign-in sheet used by about 40 members of a research laboratory. I was responsible for the electronic design, firmware testing for the reader and display, PCB fabrication and system integration.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/aforo_sistema.jpg" title="Headcount system in operation" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Entry device (AS608 fingerprint reader and touch TFT screen) and monitoring station. User names and third-party faces were blurred for confidentiality.</div>

### What it does

- **AS608** fingerprint reader (UART) with enrollment and 1:N matching, a **3.5″ touch TFT** screen (SPI, HX8357D controller) and a **DS3231** real-time clock (I²C) to timestamp every event.
- Firmware written in **Arduino IDE**: 150 ms debounce on the microSD card-detect line, a *wake-on-touch* scheme for the resistive panel, and pin assignment constrained by the ESP32's ADC limitations.
- **PCB designed in EasyEDA** and fabricated by toner transfer and chemical etching, with continuity validation and assembly into a 3D-printed enclosure.
- Diagnosed and fixed a brownout caused by powering the screen's backlight from the ESP32's 3.3 V regulator.
- Desktop app in **Python** (pySerial) showing the real-time headcount, enrolling users and exporting records to Excel, with a dual backup on microSD and PC.
- Automatic end-of-day closing that avoids crediting unmeasured hours when someone forgets to check out.

In operation since October 2026, it replaced a manual sign-in sheet that could neither verify real check-in times nor show the lab's headcount in real time.

**Technologies:** ESP32 · Arduino IDE · UART · SPI · I2C · EasyEDA · Python (pySerial)
