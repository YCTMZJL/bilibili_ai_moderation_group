# MX-Font++ — Mixture of Heterogeneous Aggregation Experts for Few-shot Font Generation

> **Venue** · ICASSP 2025  
> **Paper** · [DOI](https://doi.org/10.1109/icassp49660.2025.10888465)

**Authors** · Weihang Wang, Duolin Sun, Jielei Zhang, Longwen Gao

---

## Summary

Few-shot font generation (FFG) requires disentangling and recomposing style and content signals from only a few reference glyphs. MX-Font++ extends the MX-Font line with a **mixture of heterogeneous aggregation experts**, letting the model specialise different experts to different structural priors of the character before combining them.

## Why it is on this page

Font generation is not a moderation task on its own, but the FFG stack — layered style/content disentanglement with mixture-of-experts aggregation — informs how we build **compact, specialist-combining models** elsewhere in the group, including the coarse-to-fine deployment path of **KUROKO** and the expert-routing design of **VisionWeaver**.

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
