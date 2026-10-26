---
layout: default
title: MX-Font-plus-plus
permalink: /papers/MX-Font-plus-plus/
---

# MX-Font++ — Mixture of Heterogeneous Aggregation Experts for Few-shot Font Generation

> **Venue** · ICASSP 2025  
> **Paper** · [DOI](https://doi.org/10.1109/icassp49660.2025.10888465) · [arXiv:2503.02799](https://arxiv.org/abs/2503.02799)  
> **Code** · <https://github.com/stephensun11/MXFontpp>

**Authors** · Weihang Wang, Duolin Sun, Jielei Zhang, Longwen Gao

---

## Summary

Few-shot font generation (FFG) builds a new font library from only a handful of reference glyphs, which matters for digital accessibility in low-resource languages. MX-Font models a character through its local components and uses a Mixture of Experts to extract them, but without a strong feature extractor it cannot fully separate content from style.

MX-Font++ addresses this with two additions:

- **Heterogeneous Aggregation Experts (HAE)** — feature-extraction experts that aggregate information across both channel and spatial dimensions, giving the downstream decoupling of content and style a stronger starting point.
- **Content-style homogeneity loss** — a new training objective that further disentangles the two.

Experiments on several datasets show better visual quality than prior state-of-the-art FFG methods.

## Role in content safety

OCR models in moderation have to read text in fonts and glyph styles they rarely see during training, and real violating samples written in such styles are sparse. A model only learns to read a style reliably after seeing enough examples of it.

MX-Font++ is part of our **data generation engine** for OCR. From a handful of reference glyphs it produces a complete font library, which lets us diversify the glyph styles in synthetic training data, together with scene-text synthesis from [TextFlux](../TextFlux/).

## BibTeX

```bibtex
@inproceedings{wang2025mxfontpp,
  title     = {MX-Font++: Mixture of Heterogeneous Aggregation Experts for Few-shot Font Generation},
  author    = {Wang, Weihang and Sun, Duolin and Zhang, Jielei and Gao, Longwen},
  booktitle = {ICASSP 2025 -- 2025 IEEE International Conference on Acoustics,
               Speech and Signal Processing (ICASSP)},
  year      = {2025},
  publisher = {IEEE},
  doi       = {10.1109/icassp49660.2025.10888465}
}
```
