---
layout: page
lang: en
permalink: /en/projects/12_project/
title: CO2 laser cutter characterization for PCB prototyping
description: Parameter window and design rule for fabricating single-sided PCBs with a laser-ablated mask.
img: assets/img/proj_pcblaser.jpg
stack: ["CO2 laser cutting", "Chemical etching", "Design of experiments", "PCB fabrication"]
importance: 1
category: hardware design and PCB
---

**LIBRA-PUCP · pre-professional intern · 2026** · individual work, in progress

Set up a **30 W FLUX Beamo CO₂ laser cutter** to fabricate single-sided PCBs by **laser-ablated mask and chemical etching**, as an alternative to hand ironing (toner transfer), which in practice took about two days between fabricating and validating a single board and had poor repeatability.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/pcb_laser_flujo.png" title="PCB fabrication process with a laser-ablated mask" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Two-stage process: the laser ablates the paint mask where copper must be removed, then an etching solution dissolves the exposed copper.</div>

### What I did

A CO₂ laser emits at 10.6 µm, a wavelength copper reflects almost entirely, so it cannot remove copper directly; instead, it ablates an organic paint that acts as a mask for the later chemical etch.

- Designed **four test matrices** on painted copper boards, sweeping power (5–50 %), speed (20–300 mm/s) and resolution (250 and 500 DPI).
- Identified an **instantaneous-power threshold** (not an energy-dose effect): at 17 % and 20 mm/s (255 mJ/mm) the paint did not ablate, while at 21 % and 300 mm/s (21 mJ/mm, over ten times less energy) it ablated completely.
- From the matrices, bounded a **reproducible working window**: 21–25 % power, 60–140 mm/s and 250 DPI (45–125 mJ/mm linear energy), where the copper comes out clean with no raster striping or oxidation.

<div class="row justify-content-sm-center">
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/pcb_laser_placas.jpg" title="Ablation test boards" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/pcb_laser_energia.png" title="Linear energy vs. speed, with the working window" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Left: ablation test matrices (power/speed sweep and resolution sweep). Right: nominal linear energy by power setting, with the identified working window.</div>

- Using the minimum reproducible geometry and the lateral undercut estimated for the chemical etch (≈35 µm per edge for 1 oz copper), derived a **preliminary design rule**: traces of at least 0.25–0.30 mm and 0.20 mm minimum spacing, enough for 1.27 mm-pitch SOIC packages.
- Adopted **250 DPI** as the working resolution: it reproduces the same minimum geometry as 500 DPI in half the engraving time.

### Result

A reproducible parameter window and a preliminary design rule to fabricate single-sided PCBs in minutes instead of days. Next step: etch a board with the correct negative artwork and measure the actual trace narrowing to close the etch-compensation rule.

**Technologies:** CO₂ laser cutting (FLUX Beamo) · PCB chemical etching · design of experiments · data analysis
