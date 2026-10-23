---
layout: page
lang: en
permalink: /en/projects/1_project/
title: Intelligent Roadside Unit (RSU) with NTCIP
description: Bachelor's thesis — SNMPv3/NTCIP middleware and V2I link to give traffic-signal priority to critical vehicles.
img: assets/img/proj_rsu.jpg
stack: ["Raspberry Pi", "SNMPv3", "NTCIP 1202/1211", "MQTT", "Wi-SUN", "Python"]
featured: true
featured_order: 1
importance: 1
category: IoT and embedded systems
github: https://github.com/ruribebejarano/ntcip_middleware
---

**Bachelor's thesis · Aug 2025 – present** · [Code on GitHub](https://github.com/ruribebejarano/ntcip_middleware)

Design of an **open-hardware Roadside Unit (RSU)** for low-latency **V2I** (vehicle-to-infrastructure) communication aimed at critical vehicles: public transport and emergency units. The RSU acts as middleware between the traffic management center, the traffic controller and the vehicles.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/rsu_panel.png" title="Control center supervision panel" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Supervision panel: traffic-light state and <code>priorityRequestTable</code> (NTCIP 1211) queried over SNMPv3 on the Raspberry Pi.</div>

### What it does

- **Control center ↔ RSU (SNMPv3, USM):** continuous monitoring and `GET`/`SET` commands on NTCIP 1202/1211 objects for **dynamic traffic-signal priority** (TSP/EVP).
- **RSU → controller:** adapter that requests forcing or releasing the green phase on a traffic controller (emulated on the test bench).
- **OBU → RSU (V2I over MQTT):** a simulated OBU publishes the priority request when the vehicle enters a geofence around the stop line.
- **Propagation between intersections:** design of a **Wi-SUN (IEEE 802.15.4g)** mesh network for cascading emergency alerts.

### Test bench architecture

| Process | Machine | Role |
| :--- | :--- | :--- |
| `controller_emulator.py` | Raspberry Pi | Traffic controller (emulated) |
| `rsu_middleware.py` | Raspberry Pi | SNMPv3 agent + adapter + V2I subscriber |
| `mosquitto` | Raspberry Pi | MQTT broker (V2I channel) |
| `software_gestion.py` | PC | Control center: monitoring and commands |
| `obu_simulator.py` | PC | Simulated OBU |

**Technologies:** Python · pysnmp · SNMPv3 · NTCIP 1202/1211 · MQTT · Raspberry Pi · TI LaunchPad · Wi-SUN
