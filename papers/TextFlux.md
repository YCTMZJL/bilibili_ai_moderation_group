---
layout: default
title: TextFlux
permalink: /papers/TextFlux/
---

# TextFlux — An OCR-Free DiT Model for High-Fidelity Multilingual Scene Text Synthesis

> **Venue** · Computer Graphics Forum 2026  
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

## Why it is on this page

Scene-text synthesis is a core piece of the group's **multimodal content stack**: it feeds data generation for culture-aware VLMs (memes, posters, UI screenshots) and underpins the visual-generation pipelines used in moderation data augmentation. Keeping the architecture **OCR-free** and the training **data-efficient** matters directly for how we scale coverage into long-tail languages and subcultures that moderation systems like **KUROKO** have to deal with.

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
