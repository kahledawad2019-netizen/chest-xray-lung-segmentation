# Medical Imaging AI — Interview Guide

## Project pitch (30 seconds)

I integrated a pretrained PSPNet from TorchXRayVision for segmenting left and right lungs on chest X-rays. I built the image preprocessing and segmentation visualization pipeline and compared mask sensitivity to different confidence thresholds. My next step is to evaluate Dice and IoU against annotated ground-truth masks on an independent, patient-disjoint dataset.

## Explain the pipeline

1. Read the example chest X-ray and convert it to a single-channel image.
2. Normalize intensity values, center crop and resize to 512×512.
3. Run pretrained PSPNet (14 anatomical output maps).
4. Select the Left Lung and Right Lung maps, apply sigmoid, then apply a threshold.
5. Render lung contour overlays and compare mask-area fraction and mask-to-mask Dice for different thresholds.

## Typical interview questions

**Why segmentation instead of classification?** Segmentation yields pixel-level regions or organ contours, while classification predicts a label for an entire image.

**Why PSPNet?** Pyramid pooling brings multiscale context into pixel-level predictions.

**What does a higher threshold do?** A stricter threshold usually reduces foreground mask area; it does not prove improved accuracy.

**What is Dice?** Dice(A,B) = 2|A ∩ B| / (|A| + |B|). Dice calculated between two model-generated masks is a stability comparison, *not* ground-truth accuracy.

**How would you validate performance?** Evaluate against expert masks on patient-disjoint validation and test sets, report per-lung Dice and IoU, assess AP/PA view variation, image quality, different hospital equipment, and external generalization.

**Can the model diagnose pneumonia?** No. It segments lung anatomy; it is not a diagnostic system.

**What about DICOM?** Add metadata-aware pixel decoding, photometric handling, windowing when appropriate, and patient privacy protections. The current notebook uses a public JPEG example.

**What did you personally contribute?** Integrating the pretrained pipeline, outlining both lungs, threshold comparison, and explaining metrics and limitations. Model architecture, training, and pretrained weights come from upstream TorchXRayVision.

## Future milestones

- Ground-truth validation with annotated, licensed datasets.
- Robust DICOM input handling.
- Latency measurements and reusable inference module.
- Simple demo app for nonclinical visualization.

## Acknowledgement

Original library and pretrained model: https://github.com/mlmed/torchxrayvision
