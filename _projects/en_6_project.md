---
layout: page
lang: en
permalink: /en/projects/6_project/
title: Image–text semantic search with CLIP
description: Bidirectional retrieval with CLIP ViT-B/32 on Flickr30k; fine-tuning raises Recall@1 from 58.8 % to 68.6 %.
img: assets/img/proj_clip.jpg
stack: ["PyTorch", "CLIP", "Hugging Face", "Recall@1 68.6%"]
featured: true
featured_order: 3
importance: 1
category: artificial intelligence
github: https://github.com/ruribebejarano/clip-flickr30k-deep-learning
---

[Code on GitHub](https://github.com/ruribebejarano/clip-flickr30k-deep-learning) · [Demo on Hugging Face](https://huggingface.co/spaces/ricardo1104/clip-finetuned-flickr30k)

A search engine that works both ways (**text → image** and **image → text**), taking advantage of CLIP projecting images and text into the same 512-dimensional vector space. The **zero-shot** model is compared against **contrastive fine-tuning** of its projection heads, using the standard Karpathy protocol on Flickr30k.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/clip_retrieval.png" title="Text-to-image retrieval examples" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Top-5 retrieved images for free-form queries on the test split, with their cosine similarity.</div>

### Results (text → image, test split)

| Metric | Zero-shot | Fine-tuned | Δ |
| :--- | ---: | ---: | ---: |
| Recall@1 | 58.8 % | **68.6 %** | +9.8 |
| Recall@5 | 83.4 % | **90.1 %** | +6.7 |
| Recall@10 | 90.1 % | **94.9 %** | +4.8 |

For image → text, Recall@1 goes from 79.5 % to **83.2 %**.

**Technologies:** Python · PyTorch · CLIP · Hugging Face · uv
