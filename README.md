# Intelligent Microscopy for Materials

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22720838.svg)](https://doi.org/10.5281/zenodo.22720838)
[![ChemRxiv](https://img.shields.io/badge/ChemRxiv-10.26434%2Fchemrxiv.15008876%2Fv1-blue.svg)](https://doi.org/10.26434/chemrxiv.15008876/v1)

A reproducible materials-informatics study of **scanning electron microscopy (SEM) morphology classification**, designed around dataset integrity, leakage control, class imbalance, transfer learning, uncertainty calibration, explainability, and artifact robustness.

## ChemRxiv preprint

**Dennis Obinna Orji (2026). _Intelligent Microscopy for Materials: Leakage-Controlled SEM Morphology Classification with Calibration, Explainability, and Artifact Perturbation._ ChemRxiv, Version 1.**

**DOI:** [10.26434/chemrxiv.15008876/v1](https://doi.org/10.26434/chemrxiv.15008876/v1)

Published: **15 September 2026**

## Scientific question

How much can SEM morphology classification improve when the workflow treats **data integrity and model reliability** as first-class research problems rather than optimizing accuracy alone?

The project therefore combines duplicate control, fixed leakage-safe splits, classical and deep-learning baselines, calibration, Grad-CAM, controlled annotation-region perturbation, and selective prediction.

## Headline results

| Model | Test accuracy | Balanced accuracy | Macro-F1 |
|---|---:|---:|---:|
| Histogram Gradient Boosting | 0.7789 | 0.6713 | 0.6890 |
| CNN from scratch | 0.7947 | 0.8421 | 0.7425 |
| **ResNet-18 transfer learning** | **0.942802** | **0.930980** | **0.931633** |

The final ResNet-18 improves substantially over both the handcrafted classical baseline and the CNN trained from scratch. Temperature scaling fitted **only on validation data** reduced test ECE from **0.0189743** to **0.011369** without changing predicted classes.

At approximately **90% selective coverage**, retained predictions reached **0.980007 accuracy** while **68.54% of all test errors** were rejected for review. At approximately 80% coverage, retained accuracy reached **0.991566**.

The controlled chromatic-region experiment found measurable decision sensitivity in a small subset of images, but the evidence supports **localized artifact sensitivity rather than broad shortcut dependence**.

## Dataset and integrity controls

The study uses the **NFFA-EUROPE 100% SEM Dataset, version 2.0** from B2SHARE:

https://b2share.eudat.eu/records/zja8y-53j14

Raw images are **not redistributed** in this repository.

Notebook 01 audits all 21,169 source images. After exact-duplicate removal and high-confidence near-duplicate control, the final modelling set contains **20,742 images**. A single stratified split is frozen for all downstream work:

- Train: 14,519
- Validation: 3,111
- Test: 3,112

Chromatic overlay candidates are retained as an analysis variable rather than automatically discarded.

## Repository structure

```text
intelligent-microscopy-materials/
├── notebooks/
│   ├── 01_sem_dataset_audit.ipynb
│   ├── 02_classical_baseline.ipynb
│   ├── 03_cnn_from_scratch.ipynb
│   ├── 04_transfer_learning.ipynb
│   ├── 05_explainability_uncertainty.ipynb
│   └── README.md
├── data/
│   └── README.md
├── results/
│   ├── *.csv
│   ├── metric_provenance.md
│   └── README.md
├── MODEL_CARD.md
├── REPRODUCIBILITY.md
├── CHANGELOG.md
├── requirements.txt
├── CITATION.cff
├── .zenodo.json
├── LICENSE
└── README.md
```

## Notebook workflow

1. **Dataset audit** — integrity checks, chromatic-overlay screening, exact duplicates, near duplicates, and the fixed train/validation/test split.
2. **Classical baseline** — handcrafted intensity, edge/gradient, LBP, GLCM, and HOG descriptors with classical classifiers.
3. **CNN from scratch** — weighted-loss convolutional baseline under the same frozen split.
4. **Transfer learning** — staged ResNet-18 fine-tuning and one-time held-out evaluation.
5. **Explainability and uncertainty** — temperature scaling, confidence/error analysis, Grad-CAM, controlled chromatic-region perturbation, and selective prediction.

See [`notebooks/README.md`](notebooks/README.md) for notebook-specific notes.

## Reproducibility design

The workflow maintains:

- exact and high-confidence near-duplicate control before modelling;
- one frozen stratified 70/15/15 split;
- train-only fitting of preprocessing/statistical parameters and class weights;
- validation-only model/checkpoint and calibration selection;
- held-out test evaluation only after model selection;
- balanced accuracy and macro-F1 alongside ordinary accuracy;
- explicit artifact-stratified and intervention-based checks;
- transparent preservation of the original Colab notebook state.

See [`REPRODUCIBILITY.md`](REPRODUCIBILITY.md) for execution details.

## Results package

Compact publication-facing tables are available in [`results/`](results/). The executed notebooks remain the complete computational record.

A metric-provenance note is included because the direct Notebook 02 final evaluation reports classical test macro-F1 = **0.6890**, while a later manually assembled comparison cell carries forward 0.6800. Publication-facing results use the direct final evaluation value and document that choice explicitly.

## Model reliability

The final model is not presented as an autonomous scientific decision system. Calibration improves probability quality, but high-confidence errors remain. Grad-CAM provides coarse spatial evidence rather than causal localization, and artifact perturbation should not be interpreted as pure causal isolation.

See [`MODEL_CARD.md`](MODEL_CARD.md) for intended use and limitations.

## Software environment

The deep-learning notebooks record **PyTorch 2.11.0+cu128** on an **NVIDIA Tesla T4** in Google Colab. Python dependencies are listed in `requirements.txt`.

## Citation and archival release

The first archival software release is **v1.0.0**, preserved on Zenodo with DOI **10.5281/zenodo.22720838**:

https://doi.org/10.5281/zenodo.22720838

Associated ChemRxiv preprint: **[10.26434/chemrxiv.15008876/v1](https://doi.org/10.26434/chemrxiv.15008876/v1)**.

For the scientific study, cite the ChemRxiv preprint; for the frozen computational snapshot, cite the Zenodo archive. Machine-readable citation metadata are provided in `CITATION.cff`.

## Author

**Dennis Obinna Orji**

## License

Code and repository-authored documentation are released under the MIT License. The external NFFA-EUROPE SEM dataset is not redistributed and remains subject to its source repository terms.
