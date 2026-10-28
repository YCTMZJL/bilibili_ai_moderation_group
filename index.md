---
layout: default
title: Content Safety Study Group
---

<!-- ============================================================ -->
<!--  Content Safety Study Group (informal, member-organized)                        -->
<!--  风纪委员会 · 内容安全学习小组                                -->
<!-- ============================================================ -->

<p align="center" class="page-disclaimer"><sub>
This page is maintained by an informal, member-organized study group and is not an official bilibili team. Its content is shared for academic exchange only and may not be used for any commercial purpose. The views expressed here are solely those of the group.<br/>
本小组由成员自发组织，非 bilibili 官方团队。本页内容仅供学术交流，不得用于任何商业用途，观点仅代表小组立场。
</sub></p>

<div align="center">

<h1 style="margin: 0; border: none; padding: 0;">Content Safety Study Group</h1>
<sub>风纪委员会 · 内容安全学习小组</sub>

<p>
  <a href="#-research-highlights--研究亮点"><img alt="EMNLP" src="https://img.shields.io/badge/EMNLP-2025%20·%202026%20·%203%20papers-6D28D9?style=flat-square"></a>
  <a href="#-under-review--在审工作"><img alt="Under review" src="https://img.shields.io/badge/Under%20review-ongoing-0EA5E9?style=flat-square"></a>
  <a href="#-publications"><img alt="Publications" src="https://img.shields.io/badge/Publications-2024%E2%80%932026-10B981?style=flat-square"></a>
  <a href="papers/TextFlux/"><img alt="Eurographics 2026" src="https://img.shields.io/badge/Eurographics-2026%20·%20TextFlux-DB2777?style=flat-square"></a>
</p>

<p><em>Making content moderation reasoning-aware, severity-aware, and culture-aware.</em></p>
<p><em>让审核更会思考、更懂程度、更懂文化。</em></p>

</div>

---

## 💻 About · 关于我们

We are the **Content Safety Study Group**, an informal study group formed by researchers from the bilibili safety team. Our research sits at the intersection of **large multimodal models**, **content moderation**, and **culture-grounded reasoning**. We build foundation models and benchmarks that help platforms protect minors and users while preserving legitimate expression on an open video community.

我们是 bilibili 安全团队的研究者自发组成的学习小组「风纪委员会」，专注于**大模型内容安全**方向，围绕 bilibili 的视频、图像、文本审核场景，研究如何让多模态推理模型真正"看懂"内容、"分清"程度、"听懂"文化。

Our work spans six directions:<br/>我们的研究涵盖六个方向：

| Pillar · 方向 | What we tackle · 研究问题 | Representative work · 代表工作 |
| --- | --- | --- |
| 🧠 **Reasoning for Moderation**<br/>审核推理 | When does CoT help, when does it over-fire?<br/>思维链何时有帮助，何时会过度推理导致误判 | [`OREKI`](papers/OREKI/) · EMNLP 2026 |
| 📏 **Severity, not Binary**<br/>风险分级 | Replace 0/1 labels with a human-aligned risk spectrum<br/>用与人工判断对齐的连续风险等级替代 0/1 二分类 | [`KUROKO`](papers/KUROKO/) · EMNLP 2026 |
| 🖼️ **Culture-Aware VLMs**<br/>文化感知多模态模型 | Memes, subcultures, retrieval-augmented interpretation<br/>梗图、亚文化与检索增强的语义理解 | [`MemeBench`](https://arxiv.org/abs/2607.27798) · [`MemeMind`](https://arxiv.org/abs/2608.09316) · under review |
| ✒️ **Scene-Text Understanding**<br/>场景文字理解 | OCR for text in images, plus synthesis engines that generate its scarce training data<br/>图像文字识别（OCR），以及为其生成稀缺训练数据的合成引擎 | [`DNTextSpotter`](papers/DNTextSpotter/) · MM 2024 · [`TextFlux`](papers/TextFlux/) · Eurographics 2026 |
| 👁️ **Hallucination-Aware Vision**<br/>视觉幻觉缓解 | Fine-grained hallucination profiling and expert routing<br/>细粒度幻觉评测与多视觉专家路由 | [`VisionWeaver`](papers/VisionWeaver/) · EMNLP 2025 Findings |
| 🔍 **Retrieval for Moderation**<br/>违规检索 | Large-scale multimodal retrieval and recall over risky content<br/>面向风险内容的大规模多模态检索与召回 | Technical report *coming soon* |

---

## 🌟 Research Highlights · 研究亮点

> Three EMNLP papers (2025–2026) on content moderation and multimodal reliability, plus one Eurographics 2026 paper on multilingual scene-text synthesis.<br/>
> 三篇 EMNLP 论文（2025–2026）聚焦内容审核与多模态可靠性，另有一篇 Eurographics 2026 论文研究多语种场景文字合成。

### 1. OREKI — *When Not to Think: Mitigating the Overthinking Effect in Content Moderation*

<p align="center"><sub>EMNLP 2026 · Main</sub></p>

<p align="center">
  <img src="assets/figures/OREKI_overthinking2.png" alt="OREKI — Chain-of-Thought talks itself into a false violation" width="88%"/>
</p>

> **TL;DR**  Chain-of-Thought isn't "at worst harmless." On boundary-dense moderation data, extended reasoning amplifies weak surface signals into **false evidence of violation**. We introduce the **overthinking effect**, formalize it with K-fold cross-probing, and propose **OREKI**, an adaptive-CoT fine-tuning recipe that **keeps CoT's recall gains while cutting its false-positive inflation**.
>
> **一句话总结**  思维链并非“最坏也无害”。在边界样本密集的审核数据上，过长的推理会把微弱的表面信号放大成**虚假的违规证据**。我们提出并刻画了**过度思考效应**（overthinking effect），用 K 折交叉探测对其形式化，并提出自适应思维链微调方法 **OREKI**，在**保留思维链召回收益的同时压低其误报膨胀**。

- **Headline result (toxicity detection):** low-agreement FPR **0.467 → 0.257**, overall F1 **0.792 → 0.851**.<br/>核心结果（毒性检测）：低一致性样本误报率 **0.467 → 0.257**，整体 F1 **0.792 → 0.851**。
- Four base models · video moderation + multi-label toxicity · beats *Always-CoT* **and** *Never-CoT*.<br/>覆盖 4 个基座模型，在视频审核与多标签毒性检测上同时优于 *Always-CoT* 和 *Never-CoT*。
- 📄 [Paper (PDF) · 论文](assets/pdfs/OREKI-When-Not-to-Think.pdf) · [Details & BibTeX · 详情](papers/OREKI/)

<p align="center">
  <img src="assets/figures/OREKI_case9.png" alt="Case study: CoT turns an ear-cleaning ASMR clip into a false 'violation'" width="92%"/>
  <br/><sub>Case: with CoT off, the model answers correctly. With CoT on, it reasons itself into a violation that isn't there.<br/>案例：关闭思维链时模型判断正确；开启后，模型一步步推理出了并不存在的违规。</sub>
</p>

### 2. KUROKO — *Rethinking Content Moderation via Severity-Aware Ranking*

<p align="center"><sub>EMNLP 2026 · Main</sub></p>

<p align="center" style="margin: 0.5rem auto;">
<img src="assets/figures/KUROKO_fig1.png" alt="KUROKO — from binary classification to severity-aware ranking"/>
</p>

> **TL;DR**  Real-world content lives on a **continuous risk spectrum**, not a binary wall. **KUROKO** is a severity-aware moderation system: a verifiable RL recipe + severity data engine + a coarse-to-fine deployment stack that lets a compact VLM rival proprietary APIs at a fraction of the cost.
>
> **一句话总结**  真实内容的风险是**连续分布**的，而不是非黑即白。**KUROKO** 是一套风险分级审核系统：可验证强化学习 + 风险分级数据引擎 + 由粗到精的部署架构，让小型多模态模型以极低成本达到可比商用 API 的效果。

**1. Human-Centric Severity Ranking** — nuanced, expert-level rationales aligned with human judgement, replacing rigid binary divides.<br/>以人为中心的风险排序：给出细致、专家级且与人工判断一致的理由，取代僵硬的二分类。

**2. Verifiable Alignment & Interpretability** — a severity-aware data engine plus verifiable RL turns black-box verdicts into transparent diagnostics.<br/>可验证的对齐与可解释性：风险分级数据引擎结合可验证强化学习，把黑盒判定变成透明的诊断。

<p align="center" style="margin: 0.5rem auto;">
<img src="assets/figures/KUROKO_fig2.png" alt="KUROKO severity-aware data engine" width="60%"/>
</p>
<p align="center" style="margin: 0.25rem auto;"><sub>Severity-aware data engine driving verifiable alignment<br/>驱动可验证对齐的风险分级数据引擎</sub></p>

**3. Cost-Efficient Deployment** — a coarse-to-fine inference stack with a lightweight recall classifier; **compact models rival proprietary VLMs**.<br/>低成本部署：由粗到精的推理架构配合轻量召回分类器，**小模型即可比肩商用多模态大模型**。

<p align="center" style="margin: 0.5rem auto;">
<img src="assets/figures/KUROKO_fig4.png" alt="KUROKO coarse-to-fine deployment" width="55%"/>
</p>
<p align="center" style="margin: 0.25rem auto;"><sub>Coarse-to-fine deployment with a lightweight recall classifier<br/>配合轻量召回分类器的由粗到精部署</sub></p>

- Extensive offline + **online A/B** evidence over traditional binary baselines.<br/>大量离线评测与**线上 A/B 实验**表明其优于传统二分类基线。
- 🌐 Project page · 项目主页: <https://bilibili-kuroko.github.io>
- 📄 [Paper (PDF) · 论文](assets/pdfs/KUROKO-Severity-Aware-Ranking.pdf) · [Details & BibTeX · 详情](papers/KUROKO/)

### 3. VisionWeaver — *Diving into Mitigating Hallucinations from a Vision Perspective for LVLMs*

<p align="center"><sub>EMNLP 2025 · Findings</sub></p>

> **TL;DR**  Different vision encoders carry different inductive biases, so each **hallucinates differently**. We release **VHBench-10** — a fine-grained 10-category hallucination benchmark — and propose **VisionWeaver**, a **Context-Aware Routing Network** that aggregates visual features from multiple specialist encoders. Fewer hallucinations, better overall LVLM performance, and a cleaner upstream for every moderation stack we build on top.
>
> **一句话总结**  不同视觉编码器带有不同的归纳偏置，因此**各自的幻觉方式也不同**。我们发布了细粒度、覆盖 10 类幻觉的评测集 **VHBench-10**，并提出**上下文感知路由网络 VisionWeaver**，动态聚合多个专长编码器的视觉特征。幻觉更少、整体表现更好，也为上层的审核系统提供了更可靠的视觉基础。

- 10-category hallucination profiling exposes per-encoder weaknesses that coarse benchmarks miss.<br/>10 类细粒度幻觉评测揭示了粗粒度基准发现不了的各编码器弱点。
- Context-aware routing beats naive feature fusion.<br/>上下文感知路由优于简单的特征融合。
- 💻 Code · 代码: <https://github.com/whwangovo/VisionWeaver> · 📄 [ACL Anthology](https://aclanthology.org/2025.findings-emnlp.936/) · [Details & BibTeX · 详情](papers/VisionWeaver/)

### 4. TextFlux — *An OCR-Free DiT Model for High-Fidelity Multilingual Scene Text Synthesis*

<p align="center"><sub>Eurographics 2026 · with Peking University (Wangxuan Institute) · 与北京大学王选计算机研究所合作</sub></p>

<p align="center">
  <img src="assets/figures/TextFlux_showcase.jpg" alt="TextFlux multilingual scene-text editing across English, Chinese, Korean, and Japanese" width="92%"/>
  <br/><sub>Multilingual scene-text synthesis across English, Chinese, Korean, and Japanese — each row edits the masked region into a new word while preserving background, font, and lighting.<br/>英、中、韩、日多语种场景文字合成：每一行把遮挡区域改写成新的文字，同时保留背景、字体与光照。</sub>
</p>

> **TL;DR**  Diffusion-based scene text synthesis has leaned on extra visual-conditioning modules and large annotated corpora to go multilingual. **TextFlux** shows a cleaner path: a DiT-based framework with **no OCR encoder**, trained on **~1% of the data** competing methods need, that still handles **low-resource languages with <1,000 samples** and gives precise **multi-line layout control**.
>
> **一句话总结**  以往基于扩散的场景文字合成依赖额外的视觉条件模块和大规模标注数据来支持多语种。**TextFlux** 给出更简洁的方案：基于 DiT、**无需 OCR 编码器**，训练数据仅为同类方法的**约 1%**，用**不到 1,000 个样本即可支持新的低资源语种**，并能精确控制**多行排版**。

- **Role in content safety:** TextFlux works as a data engine for our OCR models. Real violating text-in-image samples are sparse, while OCR models need large amounts of labeled data to learn; synthesis fills that gap at scale, including for low-resource languages.<br/>**在内容安全中的作用：** TextFlux 是我们 OCR 模型的数据引擎。真实的图文违规样本很稀疏，而 OCR 模型需要大量标注数据才能学会；合成数据能大规模补上这一缺口，低资源语种也同样适用。
- 📄 [DOI](https://doi.org/10.1111/cgf.70342) · 💻 Code · 代码: <https://github.com/yyyyyxie/textflux> · [Details & BibTeX · 详情](papers/TextFlux/)

---

## 🧪 Under Review · 在审工作

We are also working on **meme understanding** — teaching multimodal models to read images whose meaning lives outside the pixels: cultural entities, community conventions, and the background knowledge a meme assumes its audience already shares. A meme rarely means what it literally shows; its meaning comes from the context it is used in, the source it references, and the way a community has come to use it.

我们也在研究**梗图（meme）理解**：让多模态模型读懂画面之外的含义——文化指涉、社区共识，以及梗图默认观众已经知道的背景知识。一张梗图想表达的，往往不是画面字面上的内容，而取决于它所处的语境、引用的出处，以及社区里约定俗成的用法。

Several threads are in progress:<br/>目前在推进的方向包括：

- **Diagnostic evaluation** — decomposing "did the model get it" into what it sees, which entities it recognizes, what it knows, and how it connects them, so a failure can be located instead of merely scored.<br/>**诊断式评测**：把“模型懂没懂”拆解为看到了什么、认出了哪些实体、知道什么、如何关联，让失败可以被定位，而不只是被打分。
- **Autonomous visual investigation** — letting an agent decide what is worth looking up about an image, gather evidence, and ground its explanation in that evidence rather than in fluent guesswork.<br/>**自主视觉探究**：让智能体自己决定一张图该查什么、收集证据，并把解释建立在证据上，而不是流畅的猜测上。

Several manuscripts from this line are under double-blind review. Venues and drafts are withheld until decisions are released.<br/>这一方向有多篇论文正在双盲评审中，会议与稿件将在结果公布后公开。

---

## 📚 Publications

> Papers from the group (2024–2026). Chronological, latest first. Starred rows ⭐ are current highlights.

| Year | Venue | Paper | Links |
| :---: | :---: | --- | :---: |
| **2026** | **EMNLP** ⭐ | **When Not to Think: Mitigating the Overthinking Effect in Content Moderation** (OREKI) | [PDF](assets/pdfs/OREKI-When-Not-to-Think.pdf) · [page](papers/OREKI/) |
| **2026** | **EMNLP** ⭐ | **Rethinking Content Moderation via Severity-Aware Ranking** (KUROKO) | [PDF](assets/pdfs/KUROKO-Severity-Aware-Ranking.pdf) · [page](papers/KUROKO/) |
| 2026 | *Under review* | *Title withheld during double-blind review* | _withheld_ |
| 2026 | *Under review* | MemeBench: What LVLMs Miss When Interpreting Culture-Dependent Memes | [arXiv:2607.27798](https://arxiv.org/abs/2607.27798) |
| **2026** | **Eurographics** ⭐ | **TextFlux: An OCR-Free DiT Model for High-Fidelity Multilingual Scene Text Synthesis** | [DOI](https://doi.org/10.1111/cgf.70342) · [page](papers/TextFlux/) |
| 2026 | *Under review* | MemeMind: Reference-Guided Trace Construction for Offline Context Optimization | [arXiv:2608.09316](https://arxiv.org/abs/2608.09316) |
| **2025** | **EMNLP Findings** ⭐ | **Diving into Mitigating Hallucinations from a Vision Perspective for LVLMs** (VisionWeaver) | [Anthology](https://aclanthology.org/2025.findings-emnlp.936/) · [page](papers/VisionWeaver/) |
| 2025 | ICASSP | MX-Font++: Mixture of Heterogeneous Aggregation Experts for Few-shot Font Generation | [DOI](https://doi.org/10.1109/icassp49660.2025.10888465) · [arXiv](https://arxiv.org/abs/2503.02799) · [page](papers/MX-Font-plus-plus/) |
| 2024 | ACM MM | DNTextSpotter: Arbitrary-Shaped Scene Text Spotting via Improved Denoising Training | [DOI](https://doi.org/10.1145/3664647.3680981) · [arXiv](https://arxiv.org/abs/2408.00355) · [page](papers/DNTextSpotter/) |

> 📌 This list reflects papers the group has publicly released or had accepted. If an older preprint or workshop paper is missing, see [`CHANGELOG.md`](CHANGELOG.md) or open an issue.

---


## 🤝 Collaborate & Contact · 合作与联系

We're actively open-sourcing data engines, evaluation harnesses, and model checkpoints that stand behind the papers above. If you're a researcher working on **moderation evaluation**, **culture-aware VLMs**, or **reasoning-aware safety**, we'd love to compare notes.

我们正在开源论文背后的数据引擎、评测工具和模型权重。如果你也在研究**审核评测**、**文化感知多模态模型**或**推理驱动的安全**，欢迎交流。

- 📬 Research contact · 联系邮箱 · [yctmzjl@gmail.com](mailto:yctmzjl@gmail.com)
- 🏢 Members based in Shanghai · 成员位于上海

<sub>© Content Safety Study Group members. Figures in this profile are from our papers linked above.<br/>本页图片均来自上方链接的论文。</sub>
