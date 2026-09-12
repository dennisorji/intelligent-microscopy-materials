# Model card — SEM morphology ResNet-18

## Model

Final model: **ImageNet-pretrained ResNet-18**, fine-tuned for 10-class SEM morphology classification.

Input processing in the executed workflow:
- upper 78.125% crop to remove the bottom SEM metadata strip;
- grayscale morphology replicated to three channels;
- resize to 150 × 256;
- ImageNet normalization;
- horizontal/vertical flip augmentation during training.

Stage 1 trained only the final classifier. Stage 2 restored the best Stage 1 checkpoint and unfroze `layer4` plus the classifier. The selected Stage 2 checkpoint was epoch 29.

## Intended use

Research benchmarking and methodological study of SEM morphology classification, leakage control, calibration, explainability, and artifact sensitivity.

This model is **not** validated for autonomous scientific decision-making, process control, clinical use, or safety-critical deployment.

## Held-out performance

- Accuracy: **0.942802**
- Balanced accuracy: **0.930980**
- Macro-F1: **0.931633**
- Test images: **3,112**

The weakest final per-class F1 among the ten classes was Films/Coated Surface at approximately **0.8602**; several classes exceeded 0.93 F1.

## Calibration and uncertainty

A single temperature parameter was fitted on validation logits only (`T = 1.396958`). Test ECE decreased from **0.0189743** to **0.011369**. Temperature scaling did not change predicted classes.

High-confidence errors remain: 27 incorrect predictions had calibrated confidence ≥0.90 and 7 had calibrated confidence ≥0.99.

## Artifact sensitivity

Overall accuracy was similar for non-overlay and overlay-flagged test subsets (0.943174 vs 0.939490), but subgroup composition is uneven and should not be treated as causal evidence.

A controlled Patterned Surface perturbation experiment found a mean absolute probability change of **0.032554** for chromatic annotation-associated regions versus **0.002420** for equal-area translated controls. Four of 172 perturbed images changed predicted class.

The appropriate interpretation is **localized sensitivity in a minority of cases**, not broad dependence on annotation artifacts.

## Limitations

- The artifact detector targets chromatic overlays; grayscale/black annotations may remain.
- Grad-CAM is coarse and is not pixel-level causal localization.
- The source dataset is highly class-imbalanced.
- Dataset labels and acquisition conditions originate from the external source dataset and were not independently relabeled.
- External-domain generalization was not established by this study.
