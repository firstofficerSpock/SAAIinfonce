# SAAI-InfoNCE

This repository contains an InfoNCE-enhanced extension of the ICCV 2023
SAAI framework for visible-infrared person re-identification. The modification
introduces bidirectional cross-modality contrastive supervision to improve
RGB-IR feature alignment.

## Project Scope

Visible-infrared person re-identification aims to match person images
across RGB and infrared cameras. The original SAAI model provides a strong
semantic alignment and affinity inference baseline. This extension integrates
an InfoNCE-based contrastive objective so that features from the same identity
but different modalities are pulled closer in the embedding space, while
features from different identities are pushed apart.

## Contributions

- Integrates bidirectional cross-modality InfoNCE into the SAAI training
  objective for RGB-IR person re-identification.
- Uses visible-to-infrared and infrared-to-visible contrastive matching to
  encourage modality-invariant identity representations.
- Keeps the original SAAI baseline implementation for direct comparison with
  the InfoNCE-enhanced variant.
- Reports evaluations on SYSU-MM01 and RegDB under standard cross-modality
  Re-ID protocols.

## Code Overview

- `models/baseline.py`: original SAAI baseline model kept for comparison.
- `models/baseline_infonce.py`: modified model with bidirectional
  cross-modality InfoNCE.
- `train.py`: training entry configured to use `baseline_infonce.py`.
- `test.py`: evaluation entry configured for the InfoNCE model checkpoint.
- `configs/`: dataset and training configuration files.

The datasets and pretrained checkpoints are not included in this repository.
Please prepare SYSU-MM01 or RegDB separately and update the paths in the
configuration files before training or evaluation.

## Results

The following results summarize the evaluation of the original SAAI baseline
and the InfoNCE-enhanced variant. Metrics are reported as Rank-1 / mAP (%).

### SYSU-MM01

| Method | All-search single-shot | All-search multi-shot | Indoor-search single-shot | Indoor-search multi-shot |
|---|---:|---:|---:|---:|
| SAAI | 75.90 / 77.03 | 82.86 / 82.39 | 83.20 / 88.01 | 90.73 / 91.30 |
| SAAI with InfoNCE | 75.28 / 76.22 | 82.56 / 81.72 | 83.80 / 88.12 | 92.14 / 92.25 |

### RegDB

| Method | Visible-to-infrared | Infrared-to-visible |
|---|---:|---:|
| SAAI | 91.07 / 91.45 | 92.09 / 92.01 |
| SAAI with InfoNCE | 92.38 / 93.30 | 93.06 / 93.52 |

## Acknowledgement

This work is based on the official implementation of:

**Visible-Infrared Person Re-Identification via Semantic Alignment and
Affinity Inference**, ICCV 2023.

The original SAAI codebase and paper are credited to the original authors.
This repository documents the InfoNCE-based modifications and experiments on
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
