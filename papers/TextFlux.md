---
layout: default
title: TextFlux
permalink: /papers/TextFlux/
---

# TextFlux — An OCR-Free DiT Model for High-Fidelity Multilingual Scene Text Synthesis

> **Venue** · Eurographics 2026 (published in Computer Graphics Forum)  
> **Paper** · [DOI](https://doi.org/10.1111/cgf.70342) · [arXiv](https://arxiv.org/abs/2505.17778)  
> **Code** · <https://github.com/yyyyyxie/textflux>

**Authors** · Yu Xie, Jielei Zhang, Pengyu Chen, Weihang Wang, Longwen Gao, Peiyi Li, Qian Qiao, Zhouhui Lian — *bilibili Inc. · Wangxuan Institute of Computer Technology, Peking University*

---

## Why this paper

Diffusion-based scene text synthesis has moved fast, but existing methods lean on **extra visual-conditioning modules** and need **large-scale annotated data** to go multilingual. We revisit whether that complexity is actually necessary, and show that a cleaner **DiT-based** design, together with the diffusion model's own contextual reasoning, already supports high-fidelity multilingual scene text synthesis.

## Four highlights

1. **OCR-free architecture.** No extra OCR encoder is needed to extract text-related features — the DiT backbone handles it directly.
2. **Strong scalability.** New languages can be added with **fewer than 1,000 training samples**, making low-resource languages practical to support.
3. **Streamlined training.** TextFlux reaches competitive quality with roughly **1% of the training data** required by competing methods.
4. **Controllable multi-line text.** Flexible, precise line-level control, beating methods restricted to single-line output or rigid layouts.

Extensive qualitative and quantitative experiments show TextFlux outperforms prior methods on both axes.

## Role in content safety

Text embedded in images has to be read before it can be judged, so OCR models sit at the front of the moderation pipeline. Training them takes a large amount of labeled data, but real violating samples are sparse, unevenly spread across languages and styles, and costly to annotate.

TextFlux serves as a **data generation engine** for these OCR models. It renders arbitrary target text into real scenes while preserving background, font, and lighting, so we can produce labeled training data at scale. Because it needs fewer than 1,000 samples to support a new language, it also extends coverage to low-resource languages where real data is hardest to collect.

## BibTeX

```bibtex
@article{xie2026textflux,
  title     = {TextFlux: An OCR-Free DiT Model for High-Fidelity Multilingual Scene Text Synthesis},
  author    = {Xie, Yu and Zhang, Jielei and Chen, Pengyu and Wang, Weihang
               and Gao, Longwen and Li, Peiyi and Qiao, Qian and Lian, Zhouhui},
  journal   = {Computer Graphics Forum},
  year      = {2026},
  publisher = {Wiley},
  doi       = {10.1111/cgf.70342}
}
```
