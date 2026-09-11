# Data access

This repository does **not** redistribute the raw SEM image dataset.

The notebooks use the public **NFFA-EUROPE 100% SEM Dataset, version 2.0** hosted on B2SHARE:

https://b2share.eudat.eu/records/zja8y-53j14

The source dataset contains 21,169 SEM images distributed across 10 morphology categories. Notebook 01 performs the integrity audit, exact-duplicate removal, near-duplicate screening, artifact flagging, and fixed train/validation/test split used by all downstream analyses.

Derived manifests and compact analysis tables may be included in later repository releases when they are needed for reproducibility and do not duplicate the original image archive.
