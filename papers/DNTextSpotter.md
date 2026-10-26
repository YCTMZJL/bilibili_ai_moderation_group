---
layout: default
title: DNTextSpotter
permalink: /papers/DNTextSpotter/
---

# DNTextSpotter — Arbitrary-Shaped Scene Text Spotting via Improved Denoising Training

> **Venue** · ACM Multimedia 2024 (ACM MM)  
> **Paper** · [ACM DL](https://doi.org/10.1145/3664647.3680981) · [arXiv:2408.00355](https://arxiv.org/abs/2408.00355)

**Authors** · Yu Xie, Qian Qiao, Jun Gao, Tianxiang Wu, Jiaqing Fan, Yue Zhang, Jielei Zhang, Huyang Sun — *Soochow University & bilibili Inc.*

---

## Why this paper

Transformer-based end-to-end text spotters rely on **bipartite graph matching** to assign predictions to ground truth. The instability of that matching produces inconsistent optimization targets and hurts training. Denoising training has fixed this for plain object detection, but **it does not transfer cleanly to text spotting** — scene text needs irregular shape detection and non-trivial recognition, not just a class label.

## What's new

- **DNTextSpotter** decomposes noised queries into **positional** and **content** parts.
- **Positional queries** are generated from **four Bezier control points on the center curve**, giving a shape prior aligned with arbitrary-shaped text.
- **Content queries** are initialized with a **masked character sliding method** so a fixed-order output stays aligned with its intended position.
- An extra **background-character classification loss** sharpens the model's perception of background.

## Results

- Outperforms state-of-the-art methods on four benchmarks — **Total-Text, SCUT-CTW1500, ICDAR15, Inverse-Text**.
- Especially on **Inverse-Text**, DNTextSpotter achieves an **11.3% improvement** over the previous best approach.

## Why it is on this page

Scene text spotting is upstream of several moderation tasks: subtitle screenshots, screen-recorded game chats, meme overlays. Together with [`TextFlux`](../TextFlux/) (OCR-free DiT text synthesis), DNTextSpotter rounds out the group's **text-in-image** stack from recognition to generation.

## BibTeX

```bibtex
@inproceedings{qiao2024dntextspotter,
  title     = {DNTextSpotter: Arbitrary-Shaped Scene Text Spotting via Improved Denoising Training},
  author    = {Qiao, Qian and Xie, Yu and Gao, Jun and Wu, Tianxiang
               and Huang, Shaoyao and Fan, Jiaqing and Cao, Ziqiang
               and Wang, Zili and Zhang, Yue},
  booktitle = {Proceedings of the 32nd ACM International Conference on Multimedia (MM '24)},
  year      = {2024},
  publisher = {Association for Computing Machinery},
  doi       = {10.1145/3664647.3680981}
}
```
