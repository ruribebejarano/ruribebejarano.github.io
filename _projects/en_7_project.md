---
layout: page
lang: en
permalink: /en/projects/7_project/
title: Vehicle counting with YOLOv8
description: Vehicle detection and tracking in video with YOLOv8 + SORT and performance metrics.
img: assets/img/proj_yolo.jpg
stack: ["YOLOv8", "SORT", "OpenCV", "Python"]
importance: 2
category: artificial intelligence
github: https://github.com/ruribebejarano/yolo_car
---

[Code on GitHub](https://github.com/ruribebejarano/yolo_car)

A **computer vision** system that counts vehicles (cars, trucks, buses and motorcycles) in video by combining **YOLOv8** detection with **SORT** multi-object tracking. It uses a region-of-interest mask and logs inference performance metrics.

- Filtering by vehicle class and confidence threshold.
- Tracking with persistent IDs so the same vehicle is never counted twice.
- Performance monitor (FPS/latency) exported to CSV.

A direct application to **intelligent transportation systems**, in line with my work on traffic-signal control.

**Technologies:** Python · Ultralytics YOLOv8 · SORT · OpenCV · cvzone
