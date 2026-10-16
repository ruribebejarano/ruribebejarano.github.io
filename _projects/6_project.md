---
layout: page
title: Búsqueda semántica imagen–texto con CLIP
description: Recuperación bidireccional con CLIP ViT-B/32 en Flickr30k; el fine-tuning sube Recall@1 de 58.8 % a 68.6 %.
img: assets/img/proj_clip.jpg
stack: ["PyTorch", "CLIP", "Hugging Face", "Recall@1 68.6%"]
featured: true
featured_order: 3
importance: 1
category: inteligencia artificial
github: https://github.com/ruribebejarano/clip-flickr30k-deep-learning
---

[Código en GitHub](https://github.com/ruribebejarano/clip-flickr30k-deep-learning) · [Demo en Hugging Face](https://huggingface.co/spaces/ricardo1104/clip-finetuned-flickr30k)

Buscador que funciona en ambos sentidos (**texto → imagen** e **imagen → texto**) aprovechando que CLIP proyecta imágenes y textos al mismo espacio vectorial de 512 dimensiones. Se compara el modelo **zero-shot** contra un **fine-tuning contrastivo** de sus cabezas de proyección, con el protocolo estándar de Karpathy sobre Flickr30k.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/clip_retrieval.png" title="Ejemplos de recuperación texto a imagen" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Top-5 recuperado para consultas libres sobre el split de prueba, con su similitud coseno.</div>

### Resultados (texto → imagen, split de prueba)

| Métrica | Zero-shot | Fine-tuned | Δ |
| :--- | ---: | ---: | ---: |
| Recall@1 | 58.8 % | **68.6 %** | +9.8 |
| Recall@5 | 83.4 % | **90.1 %** | +6.7 |
| Recall@10 | 90.1 % | **94.9 %** | +4.8 |

En imagen → texto, Recall@1 sube de 79.5 % a **83.2 %**.

**Tecnologías:** Python · PyTorch · CLIP · Hugging Face · uv
