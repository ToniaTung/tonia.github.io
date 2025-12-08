---
title: "Layout-to-Image Deep Learning for Voltage Contrast Analysis (YOLO-VC)"
excerpt: "Industry project contribution: layout-to-image conversion, SEM registration, and deep-learning data pipelines for voltage-contrast inference."
collection: portfolio
permalink: /projects/yolo-vc/
date: 2025-02-11
venue: "PDF Solutions Inc. (Industry Project)"
layout: single

---

## Project Context

This work was conducted during my time as a **Part-Time Research Assistant at PDF Solutions Inc.**  
The project focuses on **automating voltage contrast (VC) analysis** in semiconductor failure analysis using deep learning.

⚠️ **Note on authorship and scope**  
- This was an **internal industry project**
- I am **not a paper co-author**
- The content below reflects **only the components I personally designed and implemented**

---

## My Role and Contributions

Within the larger YOLO-VC project, I was responsible for the **data-processing and preprocessing infrastructure** that enabled deep-learning–based voltage contrast inference.

My contributions include:

- Python-based **layout-to-image conversion pipeline**
- **SEM image registration framework**
- Feature extraction and data preparation for downstream learning
- Supporting integration into the YOLO-VC training workflow

I did **not** design the full model architecture or publish the final study.

---

## Layout-to-Image Conversion Pipeline

I developed a **scalable Python pipeline** that converts semiconductor layouts into **image-based representations** suitable for deep learning models.

### Key Responsibilities
- Converted **GDS/OASIS layout files** into rectangular, grid-aligned image tensors
- Encoded layout information into **multi-channel images**, including:
  - Metal layers
  - Via layers
  - Geometry boundaries
- Indexed layout objects by **layer-wise geometry identifiers**
- Optimized data generation for **large full-chip layouts**

This pipeline enabled standardized input generation for machine-learning workflows.

---

## SEM Voltage Contrast Image Registration

To bridge physical measurement data and layout information, I implemented a **robust SEM image registration framework**.

### What I Implemented
- Python-based image alignment between:
  - SEM voltage contrast images
  - Corresponding layout coordinates
- Computation of:
  - Per-geometry gray-level statistics
  - Local voltage contrast descriptors
- Structured output for labeling and training preparation

This step ensured accurate spatial correspondence between layout geometry and measured contrast signals.

---

## Deep Learning Integration Support (YOLO-VC)

While the detection model itself was developed by the broader team, I supported the learning pipeline by:

- Preparing **model-ready datasets**
- Assisting with **input formatting and validation**
- Ensuring alignment between:
  - Layout-derived features
  - SEM-derived voltage contrast measurements

The infrastructure I built was directly used in training and evaluation workflows.

---

## Outcomes and Impact

My contributions enabled:

- Reliable data generation for **full-chip-scale inference**
- Accurate layout–SEM alignment for training supervision
- Significant reduction of manual preprocessing in voltage contrast analysis

These components supported the deployment of deep-learning inference within **industrial semiconductor analysis pipelines**.

---

## Skills and Tools Used

- Python
- Computer vision preprocessing
- Image registration
- Layout processing (GDS / OASIS)
- Data pipelines for deep learning
- Industry-scale dataset handling
