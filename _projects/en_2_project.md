---
layout: page
lang: en
permalink: /en/projects/2_project/
title: SNMP traffic-signal control center
description: Supervision and programming of traffic-signal controllers over SNMP v2c, with a GUI and a BER decoder.
img: assets/img/proj_snmp.jpg
stack: ["SNMP v2c", "Python", "Tkinter", "BER/ASN.1", "Raspberry Pi"]
importance: 4
category: IoT and embedded systems
github: https://github.com/ruribebejarano/snmp_interfaz_practice
---

**Companion project to my thesis** · [Code on GitHub](https://github.com/ruribebejarano/snmp_interfaz_practice)

System to supervise and program **traffic-signal controllers** (Raspberry Pi) from a PC using only **SNMP v2c over UDP**. The intersection model follows the tables of a traffic-controller programming manual (sample intersection E06-01).

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/snmp_gui.png" title="Control center main window" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Control center GUI (Tkinter): operation, phases, plans, schedules, SNMP traffic and MIB tree.</div>

### Features

- SNMP agent on a Raspberry Pi with a **private MIB** and a controller state machine (alarms, phases, plans, schedules).
- Full GUI with tabs for operation, phases and groups, plans, schedules, SNMP traffic and the MIB tree.
- **Educational traces**: every `GET`, `GETNEXT`, `SET` or `WALK` is broken down to show what happens on the network.
- **Byte-by-byte BER decoder** for every message (RFC 3417).
- Optional GPIO LED control to simulate the physical traffic light.

**Technologies:** Python · pysnmp · Tkinter · SNMP v2c · BER/ASN.1 · Raspberry Pi · gpiozero
