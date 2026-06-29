# RefSpatial-Expand · I/O Viewer

An interactive dataset browser for **RefSpatial-Expand**, the large-scale spatial-referring benchmark introduced in the NeurIPS 2025 paper [*RoboRefer: Towards Spatial Referring with Reasoning in Vision-Language Models for Robotics*](https://arxiv.org/abs/2506.04308).

**[🔗 Live Viewer](https://algorythmsz.github.io/refspatial/)** · **[📄 Paper](https://arxiv.org/abs/2506.04308)**

---

## About RefSpatial-Expand

RefSpatial-Expand is a large-scale dataset for spatial referring with multi-step reasoning, designed to train and evaluate vision-language models (VLMs) on real-world robotic spatial understanding.

| Stat | Value |
|------|-------|
| QA pairs | 20 million (2× prior scale) |
| Spatial relations | 31 (vs. 15 previously) |
| Max reasoning steps | 5 |
| Splits | Location, Placement |
| Evaluation metric | Point-in-Mask |

> **Task:** Given an image and a referring expression, predict the normalized (x, y) coordinate of the target object. A prediction is correct if the predicted point lies within the ground-truth segmentation mask.

### Benchmark: RefSpatial-Bench

The companion benchmark evaluates VLMs on multi-step spatial reasoning with metric-sensitive grounding:

- **RoboRefer (SFT):** 89.6% average success rate
- **RoboRefer (RFT):** +17.4% over Gemini-2.5-Pro

---

## Viewer Overview

The viewer exposes 80 curated samples across **8 categories** (10 per category):

| Category | Reasoning Steps | Description |
|----------|----------------|-------------|
| Location · step 1 | 1 | Single-hop location queries |
| Location · step 2 | 2 | Two-hop location queries |
| Location · step 3 | 3 | Three-hop location queries |
| Placement · step 1 | 1 | Single-hop placement (free-space) queries |
| Placement · step 2 | 2 | Two-hop placement queries |
| Placement · step 3 | 3 | Three-hop placement queries |
| Placement · step 4 | 4 | Four-hop placement queries |
| Placement · step 5 | 5 | Five-hop placement queries |

Each sample card shows:
- **Input:** raw image + referring expression + answer-format suffix
- **Output:** ground-truth mask overlay + expected model output (GT point) + evaluation criterion
- **Raw record:** source JSON entry from `question.json`

### Navigation

| Key | Action |
|-----|--------|
| `←` / `→` | Previous / next sample (Browse mode) |
| `↑` / `↓` | Previous / next category |
| `1` – `8` | Jump to category |
| Click **Gallery** | Grid view of all samples in the current category |
| Click thumbnail | Open that sample in Browse mode |

---

## Usage

The viewer is self-contained — all images are embedded as base64 in `index.html`. No server or local image files required.

```
git clone https://github.com/Algorythmsz/refspatial.git
open index.html   # or deploy to GitHub Pages
```

---

## Citation

If you use RefSpatial-Expand or RefSpatial-Bench in your research, please cite:

```bibtex
@inproceedings{zhou2025roboref,
  title     = {RoboRefer: Towards Spatial Referring with Reasoning in Vision-Language Models for Robotics},
  author    = {Enshen Zhou and Jingkun An and Cheng Chi and Yi Han and Shanyu Rong and
               Chi Zhang and Pengwei Wang and Zhongyuan Wang and Tiejun Huang and
               Lu Sheng and Shanghang Zhang},
  booktitle = {Advances in Neural Information Processing Systems (NeurIPS)},
  year      = {2025}
}
```

---

*Viewer built by [@Algorythmsz](https://github.com/Algorythmsz). Dataset and benchmark by the RoboRefer team.*
