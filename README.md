# LHCViT: A Lightweight Hybrid Convolutional Vision Transformer with Multi-Scale Feature Fusion and Hierarchical Positional Encoding for Traffic Sign Classification

> **Status — code release pending peer review.**
> This repository is the official code repository for the manuscript *"LHCViT: A Lightweight Hybrid
> Convolutional Vision Transformer with Multi-Scale Feature Fusion and Hierarchical Positional Encoding
> for Traffic Sign Classification"*, currently under review at *Intelligent Automation & Soft Computing*
> (IASC), Tech Science Press. The complete implementation, training/evaluation scripts and pretrained
> weights will be published here upon acceptance of the manuscript. Until then, this page serves as the
> permanent, citable location of the code referenced in the paper.

---

## Overview

LHCViT is a lightweight hybrid architecture for traffic sign classification that combines convolutional
feature extraction with a vision transformer encoder. The design targets the accuracy–efficiency trade-off
required for deployment in autonomous driving and advanced driver-assistance systems, where traffic signs
appear at widely varying scales and under challenging imaging conditions.

**Key components**

- **Hybrid convolutional–transformer backbone** — convolutional stages capture local texture and edge
  detail, while the transformer encoder models long-range dependencies across the sign region.
- **Multi-scale feature fusion (MSFF)** — features from several resolutions are aggregated so that both
  small, distant signs and large, nearby signs are represented.
- **Hierarchical positional encoding (HPE)** — positional information is injected at multiple levels of
  the hierarchy, preserving spatial structure that is otherwise lost in flat patch embeddings.
- **Lightweight design** — the parameter and computation budget is kept low enough for
  resource-constrained, real-time inference.

## Repository contents

| Path | Description |
|---|---|
| `LICENSE` | MIT License |
| `README.md` | This file |

The following will be added at the time of release:

- `models/` — LHCViT architecture (backbone, MSFF and HPE modules)
- `train.py`, `eval.py` — training and evaluation entry points
- `configs/` — experiment configurations reproducing the results reported in the paper
- `data/` — dataset preparation and preprocessing scripts
- `weights/` — pretrained checkpoints
- `requirements.txt` — pinned dependencies

## Datasets

<!-- Replace with the datasets actually used in the paper, e.g. GTSRB / BelgiumTS / CTSD, with links. -->
Experiments are conducted on publicly available traffic sign benchmarks. Download links and the exact
preprocessing used in the paper will be documented here with the code release.

## Requirements

<!-- Replace with your actual versions before the public code release. -->
Python 3.x, PyTorch, torchvision. Exact versions will be pinned in `requirements.txt`.

## Citation

If you find this work useful, please cite:

```bibtex
@article{lhcvit,
  title   = {LHCViT: A Lightweight Hybrid Convolutional Vision Transformer with Multi-Scale
             Feature Fusion and Hierarchical Positional Encoding for Traffic Sign Classification},
  author  = {Somanna, M. and Nagendraswamy, H. S.},
  journal = {Intelligent Automation \& Soft Computing},
  year    = {2026},
  note    = {Under review}
}
```

<!-- Update authors, volume, pages and DOI once the paper is accepted. -->

## License

Released under the [MIT License](LICENSE).

## Contact

Somanna M — Department of Studies in Computer Science, University of Mysore, Mysuru, India
somudotm@gmail.com

Questions about the method or the forthcoming code release are welcome via the repository
[Issues](../../issues) page.
