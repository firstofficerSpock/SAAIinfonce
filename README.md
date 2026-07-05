# SAAI-InfoNCE

This repository is prepared as part of my MSc research project on
visible-infrared person re-identification. It is based on the ICCV 2023
SAAI framework and explores an additional bidirectional cross-modality
InfoNCE objective for RGB-IR feature alignment.

## Project Scope

Visible-infrared person re-identification aims to match person images
across RGB and infrared cameras. The original SAAI model provides a strong
semantic alignment and affinity inference baseline. My extension studies
whether an explicit cross-modality contrastive loss can further reduce the
RGB-IR feature gap.

## My Contributions

- Reproduced and analyzed the SAAI baseline codebase for visible-infrared
  person re-identification.
- Added a bidirectional cross-modality InfoNCE loss between visible and
  infrared features.
- Compared the modified training objective with the original baseline design.
- Organized the code and documentation for MSc research and PhD application
  portfolio review.

## Code Overview

- `models/baseline.py`: original SAAI baseline model kept for comparison.
- `models/baseline_infonce.py`: my modified model with bidirectional
  cross-modality InfoNCE.
- `train.py`: training entry configured to use `baseline_infonce.py`.
- `test.py`: evaluation entry configured for the InfoNCE model checkpoint.
- `configs/`: dataset and training configuration files.

The datasets and pretrained checkpoints are not included in this repository.
Please prepare SYSU-MM01 or RegDB separately and update the paths in the
configuration files before training or evaluation.

## Results

The following results compare the original SAAI baseline with my
InfoNCE-enhanced version. Metrics are reported as Rank-1 / mAP (%).

### SYSU-MM01

| Setting | SAAI | SAAI + InfoNCE | Change |
|---|---:|---:|---:|
| All-search, single-shot | 75.90 / 77.03 | 75.28 / 76.22 | -0.62 / -0.81 |
| All-search, multi-shot | 82.86 / 82.39 | 82.56 / 81.72 | -0.30 / -0.67 |
| Indoor-search, single-shot | 83.20 / 88.01 | 83.80 / 88.12 | +0.60 / +0.11 |
| Indoor-search, multi-shot | 90.73 / 91.30 | 92.14 / 92.25 | +1.41 / +0.95 |

### RegDB

| Setting | SAAI | SAAI + InfoNCE | Change |
|---|---:|---:|---:|
| Visible-to-infrared | 91.07 / 91.45 | 92.38 / 93.30 | +1.31 / +1.85 |
| Infrared-to-visible | 92.09 / 92.01 | 93.06 / 93.52 | +0.97 / +1.51 |

## Acknowledgement

This work is based on the official implementation of:

**Visible-Infrared Person Re-Identification via Semantic Alignment and
Affinity Inference**, ICCV 2023.

The original SAAI codebase and paper are credited to the original authors.
This repository documents my own research modifications and experiments on
top of that baseline.

## Citation

If you use the original SAAI framework, please cite:

```bibtex
@InProceedings{Fang_2023_ICCV,
    author    = {Fang, Xingye and Yang, Yang and Fu, Ying},
    title     = {Visible-Infrared Person Re-Identification via Semantic Alignment and Affinity Inference},
    booktitle = {Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV)},
    month     = {October},
    year      = {2023},
    pages     = {11270-11279}
}
```
