---
layout: page
lang: en
permalink: /en/projects/5_project/
title: 4-phase traffic-signal controller
description: PCB with an ATmega328P, RTC, opto-isolated triac outputs and green-signal monitoring to drive up to 4 signal groups (Municipality of Lima).
img: assets/img/proj_semaforo.jpg
stack: ["ATmega328P", "Triac", "RTC", "74HC595", "C/C++", "CBOR"]
importance: 3
category: IoT and embedded systems
---

**Metropolitan Municipality of Lima · Apr 2025 – Aug 2025**

Design and implementation of a **4-phase traffic-signal control board** (up to 4 signal groups), with its C/C++ firmware and a PC configuration application. The board switches the 220 VAC lamps directly and verifies the actual state of its outputs.

<div class="row justify-content-sm-center">
  <div class="col-sm-12 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/sch_full.jpg" title="Schematic: control, interface and power supply" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Schematic sheet 1: microcontroller, LCD, real-time clock, EEPROM, green-signal monitoring, keypad, shift registers and power supply.</div>

### Board architecture

| Block | Implementation |
| :--- | :--- |
| Control | **ATmega328P** at 16 MHz with an ISP header for programming |
| Outputs | 10 channels (R/Y/G for groups 1 and 2; R/G for groups 3 and 4) through **2 × 74HC595** |
| Power stage | MMBT2222A transistor → **zero-crossing MOC3083 opto-triac** → **triac** per lamp, with an RC snubber (100 nF + 120 Ω) and a **fuse per channel** |
| Green monitoring | 4 **EL357N** optocouplers that read the actual voltage on each green line (conflict and burnt-lamp detection) |
| Time & settings | **DS1307 RTC** with a 32.768 kHz crystal and backup battery; **AT24C02 EEPROM** for plans and parameters |
| Local interface | **16×2 LCD** over I2C (PCF8574) and 7 configuration push buttons |
| Power supply | **TAS5-5** AC-DC module (5 V), input fuse and 10D561K **varistor** for surge protection |

<div class="row justify-content-sm-center">
  <div class="col-sm-7 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/sch_salidas.jpg" title="Triac output stage" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Output stage for 5 of the 10 channels: indicator LED, zero-crossing opto-triac, triac with snubber and fuses towards the lamps (L = 220 VAC line).</div>

### My work

- **Schematic and PCB design**, and board manufacturing.
- **C/C++ firmware** for the phase sequence, digital I/O management, the clock and the local interface.
- **PC configuration application** that sends the plans to the board as **JSON** structures encoded in **CBOR**.

### Design decisions

- **Galvanic isolation** between the 5 V logic and the 220 VAC mains on the outputs (opto-triacs) and on the monitoring inputs (optocouplers).
- **Zero-crossing switching** to reduce inrush current and interference when the lamps turn on.
- **Green verification**: the microcontroller reads the real state of each green to detect faults or conflicting greens.
- **Shift registers** to drive 10 outputs with only 3 microcontroller pins.

**Technologies:** ATmega328P · C/C++ · I2C · RTC · EEPROM · 74HC595 · Triacs and opto-triacs · JSON/CBOR · PCB design · SMD/THT soldering
