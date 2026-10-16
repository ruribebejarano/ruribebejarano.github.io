---
layout: page
title: Unidad Vial Inteligente (RSU) con NTCIP
description: Tesis de bachillerato — middleware SNMPv3/NTCIP y enlace V2I para priorizar semáforos a vehículos críticos.
img: assets/img/proj_rsu.jpg
stack: ["Raspberry Pi", "SNMPv3", "NTCIP 1202/1211", "MQTT", "Wi-SUN", "Python"]
featured: true
featured_order: 1
importance: 1
category: IoT y sistemas embebidos
github: https://github.com/ruribebejarano/ntcip_middleware
---

**Tesis de bachillerato · ago. 2025 – actualidad** · [Código en GitHub](https://github.com/ruribebejarano/ntcip_middleware)

Diseño de una **Unidad Vial Inteligente (RSU, _Roadside Unit_) de hardware abierto** para comunicación **V2I** (vehículo–infraestructura) de baja latencia, orientada a vehículos críticos: transporte público y unidades de emergencia. La RSU actúa como middleware entre el centro de control, el controlador de tránsito y los vehículos.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/rsu_panel.png" title="Panel de supervisión del centro de control" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Panel de supervisión: estado del semáforo y <code>priorityRequestTable</code> (NTCIP 1211) consultados por SNMPv3 sobre la Raspberry Pi.</div>

### Qué hace

- **Centro de control ↔ RSU (SNMPv3, USM):** monitoreo continuo y comandos `GET`/`SET` sobre objetos NTCIP 1202/1211 para **priorización dinámica de semáforos** (TSP/EVP).
- **RSU → controlador:** adaptador que solicita forzar o liberar la fase verde a un controlador de tránsito (emulado en el banco de pruebas).
- **OBU → RSU (V2I sobre MQTT):** una OBU simulada publica la solicitud de prioridad cuando el vehículo entra en una geocerca alrededor de la línea de detención.
- **Propagación entre intersecciones:** diseño de red de malla **Wi-SUN (IEEE 802.15.4g)** para alertas de emergencia en cascada.

### Arquitectura del banco de pruebas

| Proceso | Máquina | Rol |
| :--- | :--- | :--- |
| `controller_emulator.py` | Raspberry Pi | Controlador de tránsito (emulado) |
| `rsu_middleware.py` | Raspberry Pi | Agente SNMPv3 + adaptador + suscriptor V2I |
| `mosquitto` | Raspberry Pi | Broker MQTT (canal V2I) |
| `software_gestion.py` | PC | Centro de control: monitoreo y comandos |
| `obu_simulator.py` | PC | OBU simulada |

**Tecnologías:** Python · pysnmp · SNMPv3 · NTCIP 1202/1211 · MQTT · Raspberry Pi · LaunchPad TI · Wi-SUN
