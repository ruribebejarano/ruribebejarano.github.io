---
layout: page
title: Controlador semafórico de 4 fases
description: PCB con ATmega328P, RTC, salidas por triac con optoaislamiento y monitoreo de verdes para controlar hasta 4 grupos semafóricos (Municipalidad de Lima).
img: assets/img/proj_semaforo.jpg
stack: ["ATmega328P", "Triac", "RTC", "74HC595", "C/C++", "CBOR"]
importance: 3
category: IoT y sistemas embebidos
---

**Municipalidad Metropolitana de Lima · abr. 2025 – ago. 2025**

Diseño e implementación de una **placa de control para semáforos de 4 fases** (hasta 4 grupos semafóricos), con su firmware en C/C++ y una aplicación de configuración en PC. La placa conmuta directamente las lámparas de 220 VAC y verifica el estado real de las salidas.

<div class="row justify-content-sm-center">
  <div class="col-sm-12 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/sch_full.jpg" title="Esquemático: control, interfaz y alimentación" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Hoja 1 del esquemático: microcontrolador, LCD, reloj de tiempo real, EEPROM, monitoreo de verdes, teclado, registros de desplazamiento y fuente de alimentación.</div>

### Arquitectura de la placa

| Bloque | Implementación |
| :--- | :--- |
| Control | **ATmega328P** a 16 MHz con cabecera ISP para programación |
| Salidas | 10 canales (R/A/V de los grupos 1 y 2; R/V de los grupos 3 y 4) mediante **2 × 74HC595** |
| Etapa de potencia | Transistor MMBT2222A → **optotriac MOC3083 con cruce por cero** → **triac** por lámpara, con red *snubber* (100 nF + 120 Ω) y **fusible por canal** |
| Monitoreo de verdes | 4 optoacopladores **EL357N** que leen la tensión real de cada línea verde (detección de conflictos y lámparas fundidas) |
| Hora y configuración | **RTC DS1307** con cristal de 32,768 kHz y batería de respaldo; **EEPROM AT24C02** para planes y parámetros |
| Interfaz local | **LCD 16×2** por I2C (PCF8574) y 7 pulsadores de configuración |
| Alimentación | Fuente AC-DC **TAS5-5** (5 V), fusible de entrada y **varistor** 10D561K contra sobretensiones |

<div class="row justify-content-sm-center">
  <div class="col-sm-7 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/sch_salidas.jpg" title="Etapa de salida por triac" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Etapa de salida de 5 de los 10 canales: LED indicador, optotriac de cruce por cero, triac con snubber y fusibles hacia las lámparas (L = fase de 220 VAC).</div>

### Mi trabajo

- **Diseño del esquemático y la PCB**, y fabricación de la placa.
- **Firmware en C/C++** para la secuencia de fases, la gestión de entradas y salidas digitales, el reloj y la interfaz local.
- **Aplicación de configuración en PC** que envía los planes a la placa como estructuras **JSON** codificadas en **CBOR**.

### Decisiones de diseño

- **Aislamiento galvánico** entre la lógica de 5 V y la red de 220 VAC en las salidas (optotriacs) y en las entradas de monitoreo (optoacopladores).
- **Conmutación en cruce por cero** para reducir picos de corriente e interferencias al encender las lámparas.
- **Verificación de verdes**: el microcontrolador lee el estado real de cada verde para detectar fallas o verdes en conflicto.
- **Registros de desplazamiento** para manejar 10 salidas con solo 3 pines del microcontrolador.

**Tecnologías:** ATmega328P · C/C++ · I2C · RTC · EEPROM · 74HC595 · Triacs y optotriacs · JSON/CBOR · Diseño de PCB · Soldadura SMD/THT
