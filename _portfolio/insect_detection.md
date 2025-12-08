---
title: "Automated Counting and Gender Identification of Parasitoid Wasps"
excerpt: "A two-stage deep learning framework using YOLOv7 and ResNet18 for high-accuracy parasitoid wasp counting and sex identification.<br/><img src='/images/projects/insect-detection/cover.png'>"
collection: portfolio
permalink: /projects/insect-detection/
date: 2025-07-13
venue: "ASABE Annual International Meeting"
paperurl: "https://doi.org/10.13031/aim.202500146"
---

## Introduction

Parasitoid wasps play a crucial role in sustainable agriculture by naturally controlling pest populations. In mass-rearing and quality control processes, **accurate counting and gender identification** are essential, as only female wasps possess parasitism capability. However, parasitoid wasps are extremely small (≈1 mm), and gender differentiation relies on subtle morphological traits, making manual microscopic inspection labor-intensive and impractical at scale.

To address this challenge, this project proposes a **fully automated two-stage deep learning framework** for counting and sex identification of *Trissolcus* sp. parasitoid wasps. By combining **object detection** and **fine-grained gender classification**, the system significantly reduces manual effort while achieving high accuracy and robustness under dense and overlapping conditions. :contentReference[oaicite:0]{index=0}

---

## Method Overview (Two-Stage Framework)

The proposed system consists of two integrated stages:

1. **Wasp Detection and Counting**
2. **Gender Classification**

High-resolution images are first processed to localize individual wasps efficiently, followed by a fine-grained classification stage operating on cropped high-resolution image patches.

---

## Stage I: Wasp Detection and Counting (YOLOv7)

High-resolution scanner images (3981 × 3981 px) are computationally expensive for direct detection. To improve efficiency, images are **downsampled to 1120 × 1120 px** before detection.

A **YOLOv7** object detector is trained to localize individual wasps, producing bounding boxes for each detected insect. The total wasp count is obtained directly by counting predicted bounding boxes.

### Training Details
- Optimizer: Stochastic Gradient Descent (SGD)
- Initial learning rate: 0.001  
- Momentum: 0.937  
- Weight decay: 0.0005  
- Epochs: 100  
- Batch size: 4  
- Data augmentation: mosaic, scaling, translation, hue/saturation/brightness adjustment

This stage achieved a **mean average precision (mAP) of 99.4%**, demonstrating reliable localization even under overlapping and cluttered conditions. :contentReference[oaicite:1]{index=1}

---

## Stage II: Gender Classification (ResNet18)

Bounding boxes predicted by YOLOv7 are mapped back to the **original high-resolution images**, and the corresponding wasp regions are cropped without resizing. Cropped regions are center-padded to **640 × 640 px** to preserve fine morphological details.

A **ResNet18** classifier is trained to classify each wasp into three categories:
- Female
- Male
- Unrecognizable

### Training Details
- Optimizer: AdamW  
- Learning rate: 3e-5  
- Weight decay: 0.02  
- Epochs: 100  
- Batch size: 32  
- Data augmentation: rotation (±15°), flips, color jitter  
- Class imbalance handled via class-weighted loss

---

## Dataset

### Image Acquisition
- Species: *Trissolcus* sp.
- Imaging device: Flatbed scanner (6400 dpi)
- Imaging area: 6 × 6 cm
- Samples per image: ~40–50 wasps
- Total annotated images: 150
- Train/test split: 4:1

### Classification Dataset
| Class | Samples |
|------|--------|
| Female | 2,927 |
| Male | 1,166 |
| Unrecognizable | 584 |
| **Total** | **4,677** |

Annotations were performed by entomology experts using LabelImg. :contentReference[oaicite:2]{index=2}

---

## Experimental Results

### Detection Performance (YOLOv7)
- Precision: 99.9%  
- Recall: 98.7%  
- F1-score: 99.3%  
- mAP@0.5: **99.4%**

### Gender Classification Performance (ResNet18)
- Overall accuracy: **96.74%**
- Mean average precision (mAP): **95.86%**

#### Per-Class Performance
| Class | Precision | Recall | F1-score |
|------|----------|-------|---------|
| Female | 99.3% | 95.8% | 97.5% |
| Male | 96.5% | 98.9% | 97.7% |
| Unrecognizable | 91.8% | 92.6% | 92.2% |

---

## Robustness Evaluation

### Dense & Overlapping Wasps
On a challenging dataset with **886 densely packed individuals**, the system maintained:
- Detection mAP: 99.7%
- Classification accuracy: 92.89%

### Cross-Species Validation
The trained model was evaluated on a related species (*Trissolcus mitsukurii*), achieving:
- Detection mAP: 99.8%
- Classification accuracy: 92.23%

These results demonstrate strong **generalization across species and imaging conditions**. :contentReference[oaicite:3]{index=3}

---

## Conclusion and Future Work

This project presents a **scalable and highly accurate automated pipeline** for parasitoid wasp counting and gender identification. The integration of YOLOv7 and ResNet18 enables reliable processing of high-resolution images while maintaining computational efficiency.

### Future Directions
- Expanding datasets across diverse environments and species
- Improving classification robustness under extreme occlusion
- Integrating advanced generative models for synthetic data enhancement
- Deploying the system for real-world agricultural monitoring workflows

---

## Reference

**Chiao-Jo Tung**, Yi-Hui Wu, Shih-Yang Lee, Yan-Fu Kuo.  
*Application of Deep Learning in Counting and Gender Identification of Parasitoid Wasps*,  
ASABE Annual International Meeting, 2025. :contentReference[oaicite:4]{index=4}
