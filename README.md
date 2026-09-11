# Intelligent Microscopy for Materials

A reproducible machine-learning study of scanning electron microscopy (SEM) morphology classification, with emphasis on **dataset integrity, leakage control, class imbalance, transfer learning, uncertainty calibration, explainability, and artifact robustness**.

> **Project status:** pre-release research repository. The computational study is complete; repository packaging and preprint preparation are in progress.

## Research scope

This project evaluates a progressively stronger set of SEM image-classification approaches while keeping the train/validation/test partitions fixed across experiments:

1. dataset audit, duplicate control, artifact screening, and leakage-safe splitting;
2. classical image descriptors with machine-learning baselines;
3. a convolutional neural network trained from scratch;
4. ImageNet-pretrained ResNet-18 transfer learning;
5. uncertainty calibration, Grad-CAM, failure analysis, artifact perturbation, and selective prediction.

The goal is not only to obtain high classification performance, but to assess whether the resulting model behaviour is **reliable, interpretable, and robust to acquisition-related image artifacts**.

## Dataset

The study uses the **NFFA-EUROPE 100% SEM Dataset, version 2.0**, published by Aversa, Modarres, Cozzini, and Ciancio. The source dataset contains 21,169 SEM images assigned to 10 morphology classes and is available from B2SHARE:

https://b2share.eudat.eu/records/zja8y-53j14

Raw images are **not redistributed in this repository**. The notebooks restore the public dataset from the official record when needed.

## Repository structure

```text
intelligent-microscopy-materials/
├── notebooks/
│   ├── 01_sem_dataset_audit.ipynb
│   ├── 02_classical_baseline.ipynb
│   ├── 03_cnn_from_scratch.ipynb
│   ├── 04_transfer_learning.ipynb
│   └── 05_explainability_uncertainty.ipynb
├── data/
│   └── README.md
├── results/                 # selected lightweight tables/figures for the release
├── requirements.txt
├── CITATION.cff
├── LICENSE
└── README.md
```

## Reproducibility principles

The analysis was designed around several controls that are maintained throughout the notebook sequence:

- exact and near-duplicate screening before modelling;
- a single frozen stratified train/validation/test split;
- training-only fitting of preprocessing parameters and class weights;
- validation-only model and calibration selection;
- one-time held-out test evaluation after model freezing;
- explicit class-imbalance reporting with balanced accuracy and macro-F1;
- post hoc artifact-stratified evaluation and controlled perturbation experiments;
- saved outputs and execution history retained in the original computational notebooks.

## Software environment

The deep-learning notebooks were executed in Google Colab with PyTorch 2.11.0+cu128 and an NVIDIA Tesla T4 GPU. Additional Python dependencies are listed in `requirements.txt`.

## Citation

Citation metadata are provided in `CITATION.cff`. A versioned archival DOI will be added through Zenodo when the first public release is created.

## Preprint

A ChemRxiv preprint is planned. The manuscript DOI and citation will be added here after posting.

## Author

**Dennis Obinna Orji**

## License

Code in this repository is released under the MIT License. The external NFFA-EUROPE SEM dataset is not redistributed here and remains subject to the terms of its source repository.
