---
layout: default
title: OREKI
permalink: /papers/OREKI/
---

# OREKI — When Not to Think: Mitigating the Overthinking Effect in Content Moderation

> **Venue** · EMNLP 2026 (Main)  
> **PDF** · [`assets/pdfs/OREKI-When-Not-to-Think.pdf`](../assets/pdfs/OREKI-When-Not-to-Think.pdf)

**Authors** · Yu Dai, Jielei Zhang, Yang Ou, Zian Yang, Run Yang, Xiang Li, Qingyao Zhuang, Peiyi Li, Longwen Gao — *bilibili Inc.*

---

## Hero figure

<p align="center">
  <img src="../assets/figures/OREKI_overthinking2.png" alt="The Overthinking Effect — Chain-of-Thought talks itself into a false violation" width="92%"/>
</p>

## Why this paper

Chain-of-Thought (CoT) has become the default knob for every "hard" task. The field's implicit stance has been *reasoning is, at worst, harmless*. On **boundary-dense classification** such as content moderation and toxicity detection, we show that stance is wrong.

We define the **overthinking effect**: on ambiguous *non*-violating inputs, extended reasoning amplifies weak surface signals into **false evidence of violation**, inflating false-positive rate. Gains on ambiguous *violating* samples mask the harm in aggregate metrics, so simply looking at F1 hides a systematic quality failure.

## What's new

- **Diagnosis** · An agreement-stratified evaluation that isolates CoT's behaviour on low- vs. high-agreement subsets, exposing the overthinking effect that aggregate numbers hide.
- **OREKI framework** · K-fold **cross-probing** labels per-sample reasoning necessity, then fine-tunes a mixture of *full-reasoning* and *reasoning-skipped* formats. The model learns *when to think* and *when not to*.
- **Deployment-ready** · Preserves CoT's recall on ambiguous violations, suppresses its false-positive inflation on ambiguous benigns. Beats both Always-CoT and Never-CoT across four base models.

## Headline numbers

| Setting | Metric | Always-CoT | **OREKI** |
| --- | --- | :---: | :---: |
| Toxicity · low-agreement | FPR ↓ | 0.467 | **0.257** |
| Toxicity · overall | F1 ↑ | 0.792 | **0.851** |

Full tables, ablations, and base-model sweeps are in the paper.

## Case

<p align="center">
  <img src="../assets/figures/OREKI_case9.png" alt="Case: CoT-off correct, CoT-on hallucinates a violation" width="94%"/>
</p>

Two benign inputs (an ear-cleaning ASMR clip and a digital-drawing app screenshot). With CoT off, the model answers correctly. With CoT on, the chain reasons itself into "disgust-relief" or "exposed genitalia" and flips to a false positive. OREKI learns to skip the chain here.

## BibTeX

```bibtex
@inproceedings{dai2026oreki,
  title     = {When Not to Think: Mitigating the Overthinking Effect in Content Moderation},
  author    = {Dai, Yu and Zhang, Jielei and Ou, Yang and Yang, Zian and Yang, Run
               and Li, Xiang and Zhuang, Qingyao and Li, Peiyi and Gao, Longwen},
  booktitle = {Proceedings of the 2026 Conference on Empirical Methods in Natural Language Processing (EMNLP)},
  year      = {2026},
  publisher = {Association for Computational Linguistics}
}
```
