---
layout: page
title: Sistema biométrico de control de aforo y asistencia
description: Registro por huella dactilar basado en ESP32, con PCB propia y app de escritorio en Python.
img: assets/img/proj_aforo.jpg
stack: ["ESP32", "UART", "SPI", "I2C", "EasyEDA", "Arduino IDE", "Python"]
importance: 6
category: IoT y sistemas embebidos
---

**LIBRA-PUCP · practicante preprofesional · 2026** · en equipo con un practicante de Ingeniería Mecatrónica

Diseño e implementación de un sistema de registro de asistencia por **huella dactilar** basado en **ESP32**, que reemplazó el registro manual por firmas de unos 40 integrantes de un laboratorio de investigación. A mi cargo: el diseño electrónico, las pruebas de firmware del lector y la pantalla, la fabricación de la PCB y la integración del sistema.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/aforo_sistema.jpg" title="Sistema de control de aforo en operación" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Dispositivo de ingreso (lector de huella AS608 y pantalla TFT táctil) y estación de monitoreo. Los nombres de usuarios y rostros de terceros se difuminaron por confidencialidad.</div>

### Qué hace

- Lector de huella **AS608** (UART) con enrolamiento y búsqueda 1:N, pantalla **TFT táctil de 3,5″** (SPI, controlador HX8357D) y reloj de tiempo real **DS3231** (I²C) para registrar fecha y hora de cada evento.
- Firmware en **Arduino IDE**: *debounce* de 150 ms en la detección de la tarjeta microSD, *wake-on-touch* del panel resistivo y asignación de pines según las restricciones del ADC del ESP32.
- **PCB diseñada en EasyEDA** y fabricada por transferencia de tóner y ataque químico, con validación de continuidad y montaje en una carcasa impresa en 3D.
- Diagnóstico y corrección de un *brownout* causado por alimentar la retroiluminación de la pantalla desde el regulador de 3,3 V del ESP32.
- Aplicación de escritorio en **Python** (pySerial) que muestra el aforo en tiempo real, enrola usuarios y exporta los registros a Excel, con respaldo doble en microSD y PC.
- Cierre automático de jornada que evita arrastrar horas no medidas cuando alguien olvida marcar su salida.

En operación desde octubre de 2026, reemplazó un registro manual por firmas que no permitía verificar la hora real de ingreso ni conocer el aforo del laboratorio en tiempo real.

**Tecnologías:** ESP32 · Arduino IDE · UART · SPI · I2C · EasyEDA · Python (pySerial)
