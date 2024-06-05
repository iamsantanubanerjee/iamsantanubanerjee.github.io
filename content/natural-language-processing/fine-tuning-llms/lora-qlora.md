---
title: "LoRA and QLoRA"
description: ""
summary: ""
date: 2024-06-05T21:09:52+05:30
lastmod: 2024-06-05T21:09:52+05:30
draft: false
menu:
  natural-language-processing:
    parent: ""
    identifier: "lora-qlora"
weight: 7
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

## LoRA (Low-rank Adaptation)

Low-rank Adaptation, or LoRA, allows one to efficiently customize pre-trained neural networks, such as diffusion models or language models. It speeds up training and drastically reduces the size of model checkpoints by training very few parameters compared to the base model, while preserving the performance of full fine-tuning. It has become one of the go-to methods for customizing AI models.

### The need for LoRA

Few-shot promptings are **not good enough** to get even the largest models to perform well enough for production, and thus, fine-tuning through gradient updates is a necessity. However, full fine-tuning is prohibitively **expensive**.