# SPARNet: Semantically Guided Spatial–Frequency Arbitration with Overlapping Frequency Bands for Remote Sensing Image Segmentation

This repository will host the official PyTorch implementation of SPARNet.

> Status: The manuscript is currently under review. To keep the submitted results tied to the published version, the complete source code, configuration files, and trained weights are temporarily withheld and will be released after the review process concludes.

## 🔷 Overview

SPARNet (Semantic-guided Partition–Arbitration–Recovery Network) is a top-down segmentation decoder built on ConvNeXt-Base features for remote sensing semantic segmentation. It treats the frequency-band decomposition and the relevance of frequency evidence as two separate problems: the decomposition is fixed, and only the arbitration is learned.

Frequency-aware segmentation models typically fuse spatial and frequency cues without a criterion for deciding, per pixel, which evidence is semantically relevant, and they learn the weights placed on frequency responses, so the decomposition they rely on cannot be inspected independently of training. SPARNet fixes three overlapping Gaussian bands whose masks form a partition of unity and stay bounded away from zero, so the bands reconstruct their input exactly and no frequency position is a learned parameter. Spatial–frequency arbitration (SFAM) then assigns per-pixel weights from semantic alignment and inter-domain discrepancy against a shared semantic reference; global–local semantic modeling (GLSM) supplies that reference, and detail recovery (DR) restores the structure removed by downsampling. All three stages share one gated-residual interface.

Across Vaihingen, UAVid, and LoveDA, with one decoder and one training protocol, SPARNet reaches the highest mean F1 on Vaihingen and the highest mean IoU on the other two benchmarks.

## 📦 Release Plan

Open science and reproducibility are strictly upheld. The codebase is withheld only while the manuscript is under review. Immediately after the review process concludes, a complete repository will be made public, containing the following:

- [ ] Core Architecture: Full implementation of the SPARNet decoder, including the fixed three-band spectral partition, the SFAM arbitration network, GLSM, and DR.
- [ ] Data Preparation: Patch splitting and mask conversion for the ISPRS Vaihingen, UAVid, and LoveDA benchmarks, together with the fixed scene-disjoint split manifest used for the reported Vaihingen results.
- [ ] Training & Evaluation: Reproducible training configurations for all three benchmarks, metric code, and D4 test-time-augmentation inference scripts.
- [ ] Experiment Drivers: Scripts for the eight-configuration module ablation, the bandwidth-sensitivity sweep (5 widths × 4 seeds), and the 25-condition perturbation suite with rAUC scoring.
- [ ] Pre-trained Models: Checkpoints for the training seeds reported in the paper, for the ConvNeXt-Base decoder configuration.
- [ ] Environment Setup: Environment configuration guides and the complete dependency list, including the optional selective state-space kernels used by GLSM.


