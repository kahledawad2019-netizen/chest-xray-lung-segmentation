# Chest X-ray Lung Segmentation | Medical Imaging AI

A portfolio demonstration of pixel-level lung segmentation using a **pretrained PSPNet** from [TorchXRayVision](https://github.com/mlmed/torchxrayvision), including left/right lung contour overlays and threshold-sensitivity analysis.

> **Educational/research demonstration only.** This is not a diagnostic device or a clinically validated application. The pretrained network is attributed to the upstream project; no model training from scratch is claimed.

## Task

- Load and preprocess a public sample chest X-ray into a 512×512 grayscale tensor.
- Run TorchXRayVision's pretrained ChestX-Det PSPNet.
- Extract left and right lung score maps, threshold them into binary masks, and visualize contours.
- Compare sensitivity at different thresholds using mask area fractions and mask-to-mask Dice (stability, not accuracy).

## Run

1. Open `Chest_Xray_Lung_Segmentation.ipynb` in Google Colab.
2. Choose **Runtime → Run all**. Initial execution downloads upstream files, packages, and pretrained weights; internet required.
3. Edit `THRESHOLDS` in the plotting cell to explore different cutoffs.

## Reproducibility

The notebook avoids a known import-shadowing issue by cloning upstream as `torchxrayvision-upstream/` and checking the package import location.

**Accuracy is not reported:** segmentation Dice/IoU requires comparison against expert-annotated ground-truth masks on a held-out dataset. Mask-to-mask Dice in this demo only measures sensitivity to threshold changes.

## Files

- `Chest_Xray_Lung_Segmentation.ipynb` — runnable Colab/Jupyter demonstration.
- `requirements.txt` — dependencies.
- `INTERVIEW_GUIDE.md` — technical talking points and limitations.
- `DIGILINK_PROFILE.txt` — portfolio submission fields.

## Attribution

Based on [mlmed/torchxrayvision](https://github.com/mlmed/torchxrayvision) and its [segmentation notebook](https://github.com/mlmed/torchxrayvision/blob/main/scripts/segmentation.ipynb). Upstream model weights and code are not redistributed. Check upstream licenses/usage terms.

**Prepared for an AI engineering portfolio and medical imaging technical interview.**
