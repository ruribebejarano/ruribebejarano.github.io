---
layout: page
title: Robot móvil autónomo con control PID
description: Robot basado en ESP32 que recorre un laberinto con control PID de velocidad por encoders y telemetría MQTT.
img: assets/img/proj_robot.jpg
stack: ["ESP32", "Control PID", "Encoders", "MQTT", "PCB"]
importance: 2
category: control y robótica
---

**Curso de Sistemas de Control (PUCP) · Proyecto en equipo**

Diseño e implementación de un **robot móvil autónomo** capaz de recorrer un laberinto predefinido con un movimiento controlado y estable. La velocidad de cada motor DC se regula en **lazo cerrado con un controlador PID** usando la realimentación de **encoders**, compensando las diferencias entre ruedas.

<div class="row justify-content-sm-center">
  <div class="col-sm-7 mt-3 mt-md-0">
    <img src="https://jorgeflores.nom.pe/images/Carrito.jpg" alt="Prototipo final del robot móvil" class="img-fluid rounded z-depth-1" loading="lazy">
  </div>
  <div class="col-sm-5 mt-3 mt-md-0">
    <img src="https://jorgeflores.nom.pe/images/PCBDisenado.png" alt="Modelo 3D de la PCB de control" class="img-fluid rounded z-depth-1" loading="lazy">
  </div>
</div>
<div class="caption">Prototipo final (izq.) y modelo 3D de la PCB de control con el ESP32, acondicionamiento de señal, control de motores y alimentación (der.). Fotos: <a href="https://jorgeflores.nom.pe/portfolio/portfolio-6/">Jorge Flores</a>.</div>

### Arquitectura

- **ESP32** como controlador central.
- Etapas dedicadas de **actuación de motores** (driver), **regulación de voltaje**, **adquisición de encoders** y comunicación.
- **PCB a medida** que integra los componentes principales y simplifica el cableado en la plataforma.
- **Telemetría por MQTT** hacia una computadora para monitorear el robot durante las pruebas.

### Control

- PID de velocidad por motor con realimentación de encoders.
- Ajuste continuo de los comandos de los motores para compensar diferencias entre ruedas y mantener la trayectoria.

<div class="row justify-content-sm-center">
  <div class="col-sm-4 mt-3 mt-md-0">
    <img src="https://jorgeflores.nom.pe/images/Piezas.jpg" alt="Componentes del robot" class="img-fluid rounded z-depth-1" loading="lazy">
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    <img src="https://jorgeflores.nom.pe/images/PCB.jpg" alt="PCB fabricada y ensamblada" class="img-fluid rounded z-depth-1" loading="lazy">
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    <img src="https://jorgeflores.nom.pe/images/Pruebas.jpg" alt="Pruebas con instrumentación de laboratorio" class="img-fluid rounded z-depth-1" loading="lazy">
  </div>
</div>
<div class="caption">Componentes (ESP32, motores DC con encoder, driver y baterías), PCB ensamblada y verificación de señales de control con instrumentación de laboratorio. Fotos: Jorge Flores.</div>

### Validación

Las señales de control se verificaron con instrumentación de laboratorio antes de la integración final, y el prototipo se probó navegando el laberinto con el control PID activo.

**Tecnologías:** ESP32 · C/C++ · Control PID · Encoders · Driver de motores DC · MQTT · Diseño de PCB
