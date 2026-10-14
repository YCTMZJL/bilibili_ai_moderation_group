---
layout: default
title: VisionWeaver
permalink: /papers/VisionWeaver/
---

# VisionWeaver — Diving into Mitigating Hallucinations from a Vision Perspective for LVLMs

> **Venue** · EMNLP 2025 (Findings)  
> **Paper** · [ACL Anthology](https://aclanthology.org/2025.findings-emnlp.936/) · [DOI](https://doi.org/10.18653/v1/2025.findings-emnlp.936)  
> **Code** · <https://github.com/whwangovo/VisionWeaver>

**Authors** · Weihang Wang, Xinhao Li, Ziyue Wang, Yan Pang, Jielei Zhang, Peiyi Li, Qiang Zhang, Longwen Gao

---

## Why this paper

Object hallucinations materially limit the real-world usability of **Large Vision-Language Models (LVLMs)**. Because the vision encoder is the primary channel through which an LVLM reads visual information, its choice is pivotal. We hypothesize that **different vision encoders instill distinct inductive biases through their training paradigms**, which in turn produce distinct hallucination behaviors. Existing hallucination benchmarks mostly operate at a coarse granularity and cannot capture this diversity.

## Contributions

- **VHBench-10** — a comprehensive hallucination benchmark across **10 fine-grained categories**, used to systematically profile where each popular vision encoder fails.
- Our evaluations confirm the hypothesis: different encoders exhibit distinct hallucination fingerprints, and simple feature fusion is suboptimal.
- **VisionWeaver** — a novel **Context-Aware Routing Network** that uses global visual features to generate routing signals, then **dynamically aggregates visual features from multiple specialized experts**.
- Experiments show VisionWeaver meaningfully reduces hallucinations and improves overall model performance.

## Why it matters for content safety

Hallucinations in LVLMs translate directly into **false positives / false negatives** when the model is used for moderation, severity scoring, or policy explanations. VisionWeaver is an upstream fix: a hallucination-aware vision stack that later moderation layers (OREKI, KUROKO) can sit on top of without inheriting an encoder's blind spots.

## BibTeX

```bibtex
@inproceedings{wang2025visionweaver,
  title     = {Diving into Mitigating Hallucinations from a Vision Perspective
               for Large Vision-Language Models},
  author    = {Wang, Weihang and Li, Xinhao and Wang, Ziyue and Pang, Yan
               and Zhang, Jielei and Li, Peiyi and Zhang, Qiang and Gao, Longwen},
  booktitle = {Findings of the Association for Computational Linguistics: EMNLP 2025},
  year      = {2025},
  publisher = {Association for Computational Linguistics},
  doi       = {10.18653/v1/2025.findings-emnlp.936}
}
```
