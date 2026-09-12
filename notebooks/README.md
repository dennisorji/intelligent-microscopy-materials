# Notebook guide

These notebooks form a single scientific workflow and should be read in numerical order.

1. **01_sem_dataset_audit.ipynb** — dataset integrity audit, chromatic-overlay screening, exact-duplicate removal, near-duplicate analysis, and construction of the fixed train/validation/test split.
2. **02_classical_baseline.ipynb** — handcrafted image descriptors and classical machine-learning baselines under the frozen split.
3. **03_cnn_from_scratch.ipynb** — convolutional neural network trained from scratch using the same partitioning scheme.
4. **04_transfer_learning.ipynb** — ImageNet-pretrained ResNet-18 transfer learning, staged fine-tuning, and held-out test evaluation.
5. **05_explainability_uncertainty.ipynb** — post hoc calibration, confidence/error analysis, Grad-CAM, controlled annotation-region perturbation, and selective prediction.

## Execution metadata

The files are preserved from their original Google Colab research sessions. Notebook 1 contains non-sequential execution counters because some cells were rerun during development. Notebooks 2–5 do not display execution counters in the saved copies. These counters were deliberately **not** reconstructed or renumbered.

The scientific record should be interpreted from the ordered code, retained outputs, figures, tables, saved artifacts, and the documented leakage-control protocol rather than from cosmetic cell numbering.
