# Notebook sequence

The computational study is organized as five linked notebooks. The **original executed notebooks** are retained as the source of truth so that saved outputs and genuine execution metadata are preserved.

1. `01_sem_dataset_audit.ipynb` — dataset audit, artifact screening, exact and near-duplicate control, and leakage-safe split construction.
2. `02_classical_baseline.ipynb` — engineered image descriptors and classical machine-learning baselines.
3. `03_cnn_from_scratch.ipynb` — class-weighted convolutional neural network trained from scratch.
4. `04_transfer_learning.ipynb` — ImageNet-pretrained ResNet-18 transfer learning and held-out evaluation.
5. `05_explainability_uncertainty.ipynb` — calibration, uncertainty, failure analysis, Grad-CAM, controlled artifact perturbation, and selective prediction.

All modelling notebooks use the same fixed split generated in Notebook 01. Model selection is validation-based; the held-out test set is reserved for final evaluation and post hoc robustness analysis.
