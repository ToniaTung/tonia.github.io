---
title: "Parasitic Wasp Detection & Gender Classification"
excerpt: >
  Deep learning pipeline (YOLOv7 + ResNet18) for insect detection and sex classification.
header:
  image: /images/portfolio/insect/cover.png
  teaser: /images/portfolio/insect/cover.png
collection: portfolio
date: 2024-03-01
categories:
  - Deep Learning
  - Computer Vision
tags:
  - YOLOv7
  - ResNet
  - Insect Detection
  - Machine Learning
---

## Overview

This project focuses on **automatic detection and gender classification of parasitic wasps**
using a **two-stage deep learning pipeline** developed at  
**National Taiwan University, Lab of Machine Learning and Machine Vision**.

The work integrates object detection and fine-grained classification to support
efficient biological analysis and large-scale data processing.

---

## Methodology

### Stage 1 — Detection
- YOLOv7 used to detect individual wasps in high-resolution images
- Robust to cluttered backgrounds and varying lighting conditions

### Stage 2 — Classification
- ResNet18 used for **gender classification**
- Operates on cropped detections from YOLOv7
- Optimized for fast inference and high accuracy

---

## Results

- **98.9% mAP@0.5** for detection
- **95.2% classification accuracy**
- **91% reduction in processing time**
  - via semi-automated Jupyter-based workflow

---

## Visualization

![Detection pipeline](/images/portfolio/insect/pipeline.png)

---

## Dissemination

- **ASABE 2025**
  - Full paper + lightning talk
- Research exchange with **KU Leuven Lab**

---

## Tools & Stack

- Python
- PyTorch
- YOLOv7
- ResNet18
- Jupyter
- OpenCV
