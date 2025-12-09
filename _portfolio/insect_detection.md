---
title: "Automated Counting and Gender Identification of Parasitoid Wasps"
excerpt: "A two-stage deep learning framework using YOLOv7 and ResNet18 for high-accuracy parasitoid wasp counting and sex identification.<br/><img src='/images/projects/insect-detection/cover.png'>"
collection: portfolio
permalink: /projects/insect-detection/
date: 2025-07-13
venue: "ASABE Annual International Meeting"
paperurl: "https://doi.org/10.13031/aim.202500146"
pdfurl: /files/publications/insect-paper.pdf
---

## Introduction

Parasitoid wasps play a crucial role in sustainable agriculture by naturally controlling pest populations. In mass-rearing and quality control processes, **accurate counting and gender identification** are essential, as only female wasps possess parasitism capability.

However, parasitoid wasps are extremely small (≈1 mm), and gender differentiation relies on subtle morphological traits, making manual microscopic inspection labor-intensive and impractical at scale.

To address this challenge, this project proposes a **fully automated two-stage deep learning framework** for counting and sex identification of *Trissolcus* sp. parasitoid wasps. By combining **object detection** and **fine-grained gender classification**, the system significantly reduces manual effort while achieving high accuracy and robustness under dense and overlapping conditions.

---

## Method Overview

The proposed system consists of two stages:

1. Wasp detection and counting  
2. Gender classification  

High-resolution images are first processed to localize individual wasps efficiently, followed by fine-grained gender classification on cropped regions.

---

## Stage I: Wasp Detection and Counting (YOLOv7)

High-resolution scanner images (3981 × 3981 px) are downsampled to **1120 × 1120 px** for efficient detection.

A **YOLOv7** detector is trained to localize individual wasps. The total count is obtained by summing the predicted bounding boxes.

### Training Details
- Optimizer: SGD  
- Learning rate: 0.001  
- Momentum: 0.937  
- Weight decay: 0.0005  
- Epochs: 100  
- Batch size: 4  

This stage achieved **mAP@0.5 = 99.4%**.

---

## Stage II: Gender Classification (ResNet18)

Detected bounding boxes are mapped back to the original images and cropped without resizing. Crops are center-padded to **640 × 640 px** to preserve morphological details.

The classifier predicts:
- Female
- Male
- Unrecognizable

---

## Dataset

### Image Acquisition
- Species: *Trissolcus* sp.
- Imaging device: Flatbed scanner (6400 dpi)
- Total annotated images: 150
- Train/test split: 4:1

### Classification Dataset

| Class | Samples |
|------|--------|
| Female | 2,927 |
| Male | 1,166 |
| Unrecognizable | 584 |
| **Total** | **4,677** |

Annotations were performed by entomology experts using LabelImg.

---

## Experimental Results

### Detection Performance (YOLOv7)
- Precision: 99.9%
- Recall: 98.7%
- F1-score: 99.3%
- mAP@0.5: **99.4%**

### Gender Classification Performance (ResNet18)
- Overall accuracy: **96.74%**
- Mean average precision: **95.86%**

#### Per-Class Performance

| Class | Precision | Recall | F1-score |
|------|----------|--------|---------|
| Female | 99.3% | 95.8% | 97.5% |
| Male | 96.5% | 98.9% | 97.7% |
| Unrecognizable | 91.8% | 92.6% | 92.2% |

---

## Robustness Evaluation

### Dense & Overlapping Wasps
- Detection mAP: 99.7%
- Classification accuracy: 92.89%

### Cross-Species Validation (*Trissolcus mitsukurii*)
- Detection mAP: 99.8%
- Classification accuracy: 92.23%

These results demonstrate strong **generalization across species and imaging conditions**.

---

## Conclusion and Future Work

This project presents a **scalable and highly accurate automated pipeline** for parasitoid wasp counting and gender identification.

Future work includes:
- Expanding datasets across species  
- Improving robustness under extreme occlusion  
- Integrating advanced synthetic data generation  
- Real-world deployment for agricultural monitoring  
