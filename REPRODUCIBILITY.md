# Reproducibility

## Execution order

Run the notebooks in numerical order:

1. `notebooks/01_sem_dataset_audit.ipynb`
2. `notebooks/02_classical_baseline.ipynb`
3. `notebooks/03_cnn_from_scratch.ipynb`
4. `notebooks/04_transfer_learning.ipynb`
5. `notebooks/05_explainability_uncertainty.ipynb`

Notebook 01 creates the audited, deduplicated modelling index and the fixed split manifests used by every downstream notebook. Notebooks 04 and 05 also depend on model/results artifacts produced earlier in the workflow.

## Data

The raw images are not redistributed. The notebooks restore the public NFFA-EUROPE 100% SEM Dataset v2.0 from:

https://b2share.eudat.eu/records/zja8y-53j14

Notebook 01 starts from 21,169 valid images and produces a final modelling set of 20,742 images after exact- and high-confidence near-duplicate control.

## Colab/Drive layout

The executed workflow uses Google Colab and persistent assets under:

```text
/content/drive/MyDrive/intelligent-microscopy-materials/
```

The notebooks also restore raw image archives into temporary Colab storage under `/content/sem_data`.

If running outside Colab, update the project paths and replace Colab-specific commands such as Drive mounting and shell-style download cells.

## Environment

The deep-learning notebooks record:

- PyTorch `2.11.0+cu128`
- NVIDIA Tesla T4
- CUDA-enabled Google Colab runtime

Other Python dependencies are listed in `requirements.txt`. Not every transitive package version was recorded during the original research sessions, so the repository does not claim byte-for-byte environment recreation.

## Reproducibility controls

The workflow uses a fixed seed of 42 where applicable, a single frozen stratified 70/15/15 split, train-only fitting of preprocessing/statistical parameters, validation-only model/calibration selection, and one-time held-out test evaluation after model selection.

The test set is not used to tune preprocessing, class weights, architecture, checkpoint selection, or temperature scaling.

## Notebook execution metadata

The notebooks are preserved from their original Colab research sessions. Notebook 01 contains non-sequential counters because selected cells were rerun during analysis. Notebooks 02–05 do not display execution counters in the saved copies. No counters were reconstructed or fabricated.
