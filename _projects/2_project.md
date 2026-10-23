---
layout: page
title: Centro de control semafórico SNMP
description: Supervisión y programación de controladores semafóricos con SNMP v2c, GUI y decodificador BER.
img: assets/img/proj_snmp.jpg
stack: ["SNMP v2c", "Python", "Tkinter", "BER/ASN.1", "Raspberry Pi"]
importance: 4
category: IoT y sistemas embebidos
github: https://github.com/ruribebejarano/snmp_interfaz_practice
---

**Proyecto compañero de la tesis** · [Código en GitHub](https://github.com/ruribebejarano/snmp_interfaz_practice)

Sistema de supervisión y programación de **controladores semafóricos** (Raspberry Pi) desde un PC usando exclusivamente **SNMP v2c sobre UDP**. El modelo de intersección sigue las tablas de un manual de programación de controladores de tránsito (cruce de ejemplo E06-01).

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/snmp_gui.png" title="Ventana principal del centro de control" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Interfaz del centro de control (Tkinter): operación, fases, planes, horarios, tráfico SNMP y árbol MIB.</div>

### Características

- Agente SNMP en Raspberry Pi con **MIB privada** y máquina de estados del controlador (alarmas, fases, planes, horarios).
- GUI completa con pestañas de operación, fases y grupos, planes, horarios, tráfico SNMP y árbol MIB.
- **Trazas educativas**: cada `GET`, `GETNEXT`, `SET` o `WALK` se desglosa para ver qué ocurre en la red.
- **Decodificador BER byte a byte** de cada mensaje (RFC 3417).
- Control opcional de LEDs por GPIO para simular el semáforo físico.

**Tecnologías:** Python · pysnmp · Tkinter · SNMP v2c · BER/ASN.1 · Raspberry Pi · gpiozero
