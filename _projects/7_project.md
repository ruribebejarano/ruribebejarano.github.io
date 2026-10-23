---
layout: page
title: Conteo de vehículos con YOLOv8
description: Detección y seguimiento de vehículos en video con YOLOv8 + SORT y métricas de rendimiento.
img: assets/img/proj_yolo.jpg
stack: ["YOLOv8", "SORT", "OpenCV", "Python"]
importance: 2
category: inteligencia artificial
github: https://github.com/ruribebejarano/yolo_car
---

[Código en GitHub](https://github.com/ruribebejarano/yolo_car)

Sistema de **visión por computadora** para contar vehículos (autos, camiones, buses y motos) en video, combinando detección con **YOLOv8** y seguimiento multiobjeto con **SORT**. Usa una máscara de región de interés y registra métricas de rendimiento de la inferencia.


- Filtrado por clases de vehículo y umbral de confianza.
- Seguimiento con IDs persistentes para no contar dos veces el mismo vehículo.
- Monitor de rendimiento (FPS/latencia) exportado a CSV.

Aplicación directa a **sistemas de transporte inteligente**, en línea con mi trabajo en control semafórico.

**Tecnologías:** Python · Ultralytics YOLOv8 · SORT · OpenCV · cvzone
