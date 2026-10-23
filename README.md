# LHCViT: A Lightweight Hybrid Convolutional Vision Transformer with Multi-Scale Feature Fusion and Hierarchical Positional Encoding for Traffic Sign Classification

> **Status — code release pending peer review.**
> This is the official code repository for the manuscript *"LHCViT: A Lightweight Hybrid Convolutional
> Vision Transformer with Multi-Scale Feature Fusion and Hierarchical Positional Encoding for Traffic
> Sign Classification"*, currently under review at *Intelligent Automation & Soft Computing* (IASC),
> Tech Science Press. The complete implementation, training/evaluation scripts and pretrained weights
> will be published here upon acceptance of the manuscript. Until then, this page serves as the
> permanent, citable location of the code referenced in the paper.

**1.34 M parameters · 97.60 % mean test accuracy across seven public benchmarks from four countries**

---

## Authors

Somanna M<sup>1,\*</sup>, H. S. Nagendraswamy<sup>1</sup>, Thejashwini B. L<sup>1</sup>,
Manjuchethan N<sup>1</sup>, Rajashekara M<sup>1</sup>, Chethana Kumara B M<sup>2</sup>

<sup>1</sup> Department of Studies in Computer Science, University of Mysore, Mysuru, Karnataka, India
<sup>2</sup> Research and Development Division, Samsung Electro-Mechanics, Bangalore, Karnataka, India

<sup>\*</sup> Corresponding author: Somanna M — somudotm@gmail.com

## Overview

Traffic sign recognition for intelligent transportation systems must contend with intra-class variation,
scale differences, and the strict computational limits of edge deployment — constraints that make accuracy
and compactness competing goals in most existing architectures. LHCViT is designed to reconcile the two.

The model pairs a mobile-friendly convolutional backbone with a compact Transformer encoder, linked by
three task-specific modules.

## Key components

- **Spatial-Channel Attention Module (SCAM)** — suppresses irrelevant background regions in early feature
  maps through joint channel and spatial recalibration, so that downstream stages operate on the sign
  rather than the scene around it.

- **Progressive Receptive Field Expansion (PRFE)** — integrated into the inverted residual stage, PRFE
  broadens the effective receptive field by fusing three parallel dilated convolutional branches through
  learnable weights. This captures fine symbol edges and broad shape patterns simultaneously, giving the
  multi-scale feature fusion behaviour the architecture depends on.

- **Hierarchical Positional Encoding (HPE)** — replaces the flat positional embedding table of standard
  Vision Transformers with a three-level hierarchy encoding global scene context, regional sub-grid
  structure, and per-patch absolute position.

Ablation experiments confirm that **PRFE and HPE together account for most of the accuracy gain** over the
pure convolutional baseline.

## Training protocol

The complete model contains **1.34 million parameters** and is trained with warm-up scheduling, cosine
annealing, automatic mixed precision, and patience-based early stopping.

## Results

Evaluated on seven public benchmark datasets, LHCViT reaches a **mean test accuracy of 97.60 %**.

| Dataset | Region | Test accuracy |
|---|---|---|
| GTSRB-v2 — German Traffic Sign Recognition Benchmark | Germany | **99.83 %** |
| ITSDD — Indian Traffic Sign Detection Dataset | India | 99.46 % |
| BTSD — Belgium Traffic Sign Dataset | Belgium | 99.44 % |
| ICTS — Indian Cautionary Traffic Sign Dataset | India | 99.33 % |
| ArTS-v1 — Arabic Traffic Sign Dataset (2,790 images) | — | 92.86 % |
| <!-- dataset 6 --> | | |
| <!-- dataset 7 --> | | |
| **Mean across all seven** | | **97.60 %** |

Generalization gaps between training and validation accuracy remain **below one percentage point on all
seven datasets**. On GTSRB and BTSD, LHCViT matches the accuracy of models roughly **ten times its size**,
making it the most compact architecture among those surveyed.

**Limitations.** Under an identical training protocol LHCViT achieves higher accuracy than four mobile
baselines on BTSD, but at a higher computational cost and CPU latency. The lowest accuracy (92.86 %)
occurs on ArTS-v1, the smallest dataset in the evaluation at 2,790 images.

## Repository contents

| Path | Description |
|---|---|
| `LICENSE` | MIT License |
| `README.md` | This file |

The following will be added at the time of release:

- `models/` — LHCViT architecture (backbone, SCAM, PRFE and HPE modules)
- `train.py`, `eval.py` — training and evaluation entry points
- `configs/` — experiment configurations reproducing the results reported in the paper
- `data/` — dataset preparation and preprocessing scripts
- `weights/` — pretrained checkpoints
- `requirements.txt` — pinned dependencies

## Datasets

<!-- Add the two remaining dataset names, plus download links for all seven. -->
All seven benchmarks are publicly available. Download links and the exact preprocessing and train/val/test
splits used in the paper will be documented here with the code release.

## Requirements

<!-- Replace with your actual versions before the public code release. -->
Python 3.x, PyTorch, torchvision. Exact versions will be pinned in `requirements.txt`.

## Citation

If you find this work useful, please cite:

```bibtex
@article{somanna2026lhcvit,
  title   = {LHCViT: A Lightweight Hybrid Convolutional Vision Transformer with Multi-Scale
             Feature Fusion and Hierarchical Positional Encoding for Traffic Sign Classification},
  author  = {{Somanna M} and {H. S. Nagendraswamy} and {Thejashwini B. L} and
             {Manjuchethan N} and {Rajashekara M} and {Chethana Kumara B M}},
  journal = {Intelligent Automation \& Soft Computing},
  year    = {2026},
  note    = {Under review}
}
```

<!-- Update volume, pages and DOI once the paper is accepted. -->

## License

Source code is released under the [MIT License](LICENSE).
Pretrained weights, when published, will be released under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

## Contact

Somanna M — Department of Studies in Computer Science, University of Mysore, Mysuru, India
somudotm@gmail.com

Questions about the method or the forthcoming code release are welcome via the repository
[Issues](../../issues) page.
