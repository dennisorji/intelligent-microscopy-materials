# Metric provenance

Publication-facing tables in this repository use the metric reported by each model's **direct final held-out test evaluation** in the notebook where that model was evaluated.

- Classical baseline: Notebook 02 final Histogram Gradient Boosting test evaluation.
- CNN from scratch: Notebook 03 final test evaluation.
- Transfer learning: Notebook 04 final ResNet-18 test evaluation.
- Calibration, uncertainty, perturbation, and selective prediction: Notebook 05.

## Classical macro-F1 reconciliation

Notebook 02 directly reports a Histogram Gradient Boosting test macro-F1 of **0.6890** in both the final test-performance printout and the classification report.

A later manually assembled comparison cell in Notebook 03/04 carries forward **0.6800** for that one value. Because this is a transcribed comparison-table value rather than a recomputation, the publication-facing `model_comparison.csv` uses the direct Notebook 02 result, **0.6890**.

No executed notebook has been rewritten to hide this discrepancy. This note records the source-precedence decision explicitly.
