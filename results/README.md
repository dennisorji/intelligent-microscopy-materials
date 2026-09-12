# Results

This directory contains compact, publication-facing outputs distilled from the executed notebooks. The notebooks remain the complete computational record; these files are provided so that headline results can be inspected without opening the larger notebook files.

## Contents

| File | Description |
|---|---|
| `dataset_overview.csv` | Dataset integrity audit and final split sizes. |
| `class_distribution.csv` | Final modelling-set class counts and chromatic-overlay flags. |
| `split_class_counts.csv` | Frozen train/validation/test class counts. |
| `model_comparison.csv` | Direct held-out test metrics for the classical baseline, scratch CNN, and ResNet-18. |
| `resnet_per_class_metrics.csv` | Final ResNet-18 per-class precision, recall, F1, and support. |
| `calibration_metrics.csv` | Test-set NLL, ECE, and Brier score before/after validation-fitted temperature scaling. |
| `selective_prediction.csv` | Coverage, retained accuracy, and error rejection under confidence-based selective prediction. |
| `artifact_perturbation_summary.csv` | Chromatic annotation-region intervention versus equal-area translated controls. |
| `artifact_accuracy_summary.csv` | Overlay-stratified accuracy for the scratch CNN and transfer model. |
| `high_confidence_error_counts.csv` | Incorrect predictions remaining above calibrated-confidence thresholds. |
| `top_confusions.csv` | Most frequent final ResNet-18 confusion directions. |
| `metric_provenance.md` | Provenance and reconciliation note for publication-facing metrics. |

## Headline results

The final ImageNet-pretrained ResNet-18 achieved **0.942802 accuracy**, **0.930980 balanced accuracy**, and **0.931633 macro-F1** on the held-out test split. Temperature scaling fitted only on validation data reduced test ECE from **0.0189743** to **0.011369** without changing class predictions.

Selective prediction improved reliability further: retaining approximately 90% of predictions produced **0.980007 accuracy** while rejecting **68.54% of all test errors**. At approximately 80% coverage, retained accuracy reached **0.991566** while rejecting **88.20% of all errors**.

The controlled chromatic-region perturbation experiment found a larger mean absolute probability change for annotation-associated regions (**0.032554**) than for equal-area translated controls (**0.002420**), with four prediction flips among 172 Patterned Surface overlay-positive test images. This supports **localized artifact sensitivity in a minority of cases**, not broad shortcut dependence.

## Interpretation caution

Artifact subgroup metrics should not be interpreted as causal effects of annotations. Overlay-positive subsets are class-imbalanced and some classes contain very few or no flagged examples. The controlled perturbation analysis narrows the question but still changes image content and therefore does not provide pure causal isolation.
