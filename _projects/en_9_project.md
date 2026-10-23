---
layout: page
lang: en
permalink: /en/projects/9_project/
title: Autonomous mobile robot with PID control
description: ESP32-based robot that navigates a maze with encoder-based PID speed control and MQTT telemetry.
img: assets/img/proj_robot.jpg
stack: ["ESP32", "PID control", "Encoders", "MQTT", "PCB"]
importance: 2
category: control and robotics
---

**Control Systems course (PUCP) · Team project**

Design and implementation of an **autonomous mobile robot** that navigates a predefined maze with controlled and stable motion. Each DC motor's speed is regulated in **closed loop with a PID controller** using **encoder** feedback, compensating for differences between the wheels.

<div class="row justify-content-sm-center">
  <div class="col-sm-7 mt-3 mt-md-0">
    <img src="https://jorgeflores.nom.pe/images/Carrito.jpg" alt="Final mobile robot prototype" class="img-fluid rounded z-depth-1" loading="lazy">
  </div>
  <div class="col-sm-5 mt-3 mt-md-0">
    <img src="https://jorgeflores.nom.pe/images/PCBDisenado.png" alt="3D model of the control PCB" class="img-fluid rounded z-depth-1" loading="lazy">
  </div>
</div>
<div class="caption">Final prototype (left) and 3D model of the control PCB with the ESP32, signal conditioning, motor control and power circuitry (right). Photos: <a href="https://jorgeflores.nom.pe/portfolio/portfolio-6/">Jorge Flores</a>.</div>

### Architecture

- **ESP32** as the main controller.
- Dedicated stages for **motor actuation** (driver), **voltage regulation**, **encoder acquisition** and communication.
- **Custom PCB** that integrates the main components and simplifies wiring on the platform.
- **MQTT telemetry** to a computer to monitor the robot during tests.

### Control

- Per-motor PID speed control with encoder feedback.
- Continuous adjustment of motor commands to compensate for wheel differences and keep the trajectory.

<div class="row justify-content-sm-center">
  <div class="col-sm-4 mt-3 mt-md-0">
    <img src="https://jorgeflores.nom.pe/images/Piezas.jpg" alt="Robot components" class="img-fluid rounded z-depth-1" loading="lazy">
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    <img src="https://jorgeflores.nom.pe/images/PCB.jpg" alt="Manufactured and assembled PCB" class="img-fluid rounded z-depth-1" loading="lazy">
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    <img src="https://jorgeflores.nom.pe/images/Pruebas.jpg" alt="Tests with lab instruments" class="img-fluid rounded z-depth-1" loading="lazy">
  </div>
</div>
<div class="caption">Components (ESP32, DC motors with encoders, driver and batteries), assembled PCB and verification of control signals with lab instruments. Photos: Jorge Flores.</div>

### Validation

Control signals were verified with lab instruments before final integration, and the prototype was tested navigating the maze with PID control enabled.

**Technologies:** ESP32 · C/C++ · PID control · Encoders · DC motor driver · MQTT · PCB design
