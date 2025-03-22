# Automatic Pith Detection in Tree Cross-Section Images Using Deep Learning

This repository supports the research project:

> **Automatic Pith Detection in Tree Cross-Section Images Using Deep Learning**  
> Tzu-I Liao, Mahmoud Fakhry, Jibin Yesudas Varghese  
> Oregon State University, 2024

This work investigates the use of deep learning models to automate **pith detection** — the process of locating the center of a tree cross-section. Accurate pith detection is essential in forestry, dendrochronology, and industrial wood processing. The project aims to replace manual, error-prone methods with scalable, data-driven solutions.

---

##  Project Overview

- Evaluate five state-of-the-art deep learning models.
- Compare object detection vs. segmentation approaches.
- Analyze model generalization to unseen tree species.
- Improve output quality using data augmentation and post-processing (e.g., NMS).

---

##  Motivation

Pith detection enables:

- Tree ring analysis and historical climate inference.
- Optimal wood cutting in sawmills.
- Quality grading for construction timber.

**Traditional methods** (calipers, edge detection, etc.) are subjective and inconsistent.

**Deep learning** offers automation, consistency, and improved generalization across species.

---

## Models Implemented

| Model             | Type            | Highlights |
|------------------|------------------|------------|
| Swin Transformer | Segmentation     | Highest accuracy & IoU. Hierarchical attention with fine segmentation precision. |
| YOLOv9            | Object Detection | Fastest inference. Bounding box-based detection. Best for real-time industrial use. |
| DeepLabV3         | Segmentation     | Good generalization using multi-scale features via ASPP. |
| U-Net             | Segmentation     | Lightweight. Strong for well-structured patterns. |
| Mask R-CNN        | Object Detection | High recall. Improved via Non-Maximum Suppression (NMS). Best when tuned properly. |

---

## 🔍 Key Findings

- **Swin Transformer** achieved the highest accuracy (0.94) and IoU (0.85), excelling in complex structures.
- **YOLOv9** was fastest, but its precision dropped with irregular pith boundaries.
- **DeepLabV3** was effective in handling multi-scale textures.
- **U-Net** was efficient and accurate on regular growth rings.
- **Mask R-CNN**, initially underperforming due to overlapping predictions, improved significantly when **NMS** was applied.

>  Mask R-CNN trained on a **smaller dataset (64 images)** outperformed a version trained on a larger dataset when tested on **oak tree images**, showing the importance of dataset quality.

---

## Technical Contributions

- Custom training loops for all models.
- Integrated augmentation (flips, rotations, color jittering, scaling).
- Manual tuning of hyperparameters and batch sizes.
- Post-processing via **Non-Maximum Suppression** for object detection refinement.
- Comparative evaluation across **582 labeled images** and an **11-image oak test set**.

---

## Evaluation Metrics

All models were evaluated using:

- **Accuracy** – Overall prediction correctness.
- **Precision** – How often predictions were correct.
- **Recall** – How many actual piths were found.
- **F1 Score** – Harmonic mean of precision and recall.
- **IoU (Intersection over Union)** – Quality of spatial overlap.

---

## Experimental Insight

The models were tested for generalization using a held-out oak dataset:

- **Mask R-CNN trained on 64 images** generalized better than its counterpart trained on 582 images.
- **Swin Transformer**, when combined with **NMS**, outperformed all others on the oak dataset, reaching **0.87 accuracy** and **0.75 IoU**.

---

## Model Behavior

- **Swin Transformer** showed slow convergence but the best final performance.
- **YOLOv9** converged rapidly but plateaued early (underfitting).
- **DeepLabV3** and **U-Net** had smooth loss curves and stable validation.
- **Mask R-CNN** suffered instability due to overlapping boxes until NMS was applied.

---
### Acknowledgments

>Tree Ring Lab, OSU – Oak image dataset
---
## Citation

If you use this repository or findings in your work, please cite:

```bibtex
@misc{pithdetection2024,
  title={Automatic Pith Detection in Tree Cross-Section Images Using Deep Learning},
  author={Liao, Tzu-I and Fakhry, Mahmoud and Varghese, Jibin Yesudas},
  year={2024},
  institution={Oregon State University}
}

