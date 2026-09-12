# Data access

This repository does **not** redistribute the raw SEM image dataset.

The notebooks use the public **NFFA-EUROPE 100% SEM Dataset, version 2.0** hosted on B2SHARE:

https://b2share.eudat.eu/records/zja8y-53j14

The source dataset contains 21,169 SEM images across 10 morphology classes.

Notebook 01 performs the integrity audit, exact-duplicate removal, high-confidence near-duplicate screening, chromatic-overlay flagging, and the fixed train/validation/test split used by all downstream analyses.

The final modelling set contains 20,742 images. Compact class/split summaries are included under `results/`, but raw source images are intentionally excluded.

For exact reproduction, run Notebook 01 first so that the derived manifests are generated from the public source dataset rather than relying on redistributed image files.
