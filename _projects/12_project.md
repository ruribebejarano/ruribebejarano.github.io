---
layout: page
title: Caracterización de cortadora láser CO₂ para PCB
description: Ventana de parámetros y regla de diseño para fabricar PCB de una cara por máscara ablacionada con láser.
img: assets/img/proj_pcblaser.jpg
stack: ["Corte láser CO2", "Ataque químico", "Diseño de experimentos", "Fabricación de PCB"]
importance: 1
category: diseño de hardware y PCB
---

**LIBRA-PUCP · practicante preprofesional · 2026** · trabajo individual, en proceso

Habilitación de una cortadora láser CO₂ **FLUX Beamo de 30 W** para fabricar PCB de una cara por el método de **máscara ablacionada y ataque químico**, como alternativa al planchado artesanal (transferencia de tóner), que en la práctica tomaba unos dos días entre fabricar y validar una placa y tenía baja repetibilidad.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/pcb_laser_flujo.png" title="Proceso de fabricación de PCB con máscara ablacionada por láser" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Proceso en dos etapas: el láser ablaciona la pintura (máscara) donde el cobre debe eliminarse y luego una solución de ataque disuelve el cobre expuesto.</div>

### Qué hice

Un láser CO₂ emite en 10,6 µm, longitud de onda que el cobre refleja casi por completo, por lo que no puede remover el cobre directamente: en su lugar, ablaciona una pintura orgánica que actúa como máscara frente al ataque químico posterior.

- Diseñé **cuatro matrices de prueba** sobre placas de cobre pintadas, barriendo potencia (5–50 %), velocidad (20–300 mm/s) y resolución (250 y 500 DPI).
- Identifiqué un **umbral de potencia instantánea** (no de dosis de energía): a 17 % y 20 mm/s (255 mJ/mm) la pintura no se removía, mientras que a 21 % y 300 mm/s (21 mJ/mm, más de diez veces menos energía) sí se removía por completo.
- A partir de las matrices, acoté una **ventana de trabajo reproducible**: 21–25 % de potencia, 60–140 mm/s y 250 DPI (45–125 mJ/mm de energía lineal), donde el cobre queda limpio sin rayado ni oxidación.

<div class="row justify-content-sm-center">
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/pcb_laser_placas.jpg" title="Placas de prueba de ablación" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/pcb_laser_energia.png" title="Energía lineal vs. velocidad, con la ventana de trabajo" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Izquierda: matrices de prueba de ablación (barrido de potencia y velocidad, y de resolución). Derecha: energía lineal nominal por potencia, con la ventana de trabajo identificada.</div>

- Con la geometría mínima reproducible y el socavado lateral estimado por el ataque químico (≈35 µm por flanco para cobre de 1 oz), derivé una **regla de diseño preliminar**: pistas de al menos 0,25–0,30 mm y separaciones de al menos 0,20 mm, suficiente para encapsulados SOIC de 1,27 mm de paso.
- Adopté **250 DPI** como resolución de trabajo: reproduce la misma geometría mínima que 500 DPI en la mitad del tiempo de grabado.

### Resultado

Una ventana de parámetros reproducible y una regla de diseño preliminar para fabricar PCB de una cara en minutos en lugar de días. Queda pendiente atacar una placa en el negativo correcto y medir el estrechamiento real de las pistas para cerrar la regla de compensación del ataque.

**Tecnologías:** Corte láser CO₂ (FLUX Beamo) · ataque químico de PCB · diseño de experimentos · análisis de datos
