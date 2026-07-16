# Explainable Road Damage Detection using YOLOv8 and Grad-CAM

> A Computer Vision project demonstrating explainable AI for intelligent transportation systems using YOLOv8 object detection and Grad-CAM visualization.

---

# Project Overview

Road damage detection plays an important role in intelligent transportation systems, autonomous driving, and smart city infrastructure. Manual road inspection is expensive, time-consuming, and often inconsistent.

This project develops an explainable deep learning pipeline capable of detecting multiple categories of road damage while providing visual explanations of the model's decision-making process using Explainable AI (XAI).

Unlike traditional object detection projects that only produce bounding boxes, this work investigates **why** the neural network predicts a particular road defect by integrating **Grad-CAM**.

---

# Objectives

- Detect road damage automatically using YOLOv8
- Train a custom detector on a road damage dataset
- Evaluate detection performance using standard object detection metrics
- Interpret model predictions using Grad-CAM
- Demonstrate how Explainable AI improves trust in computer vision systems

---

# Dataset

Dataset:

**Road Damage Dataset: Potholes, Cracks and Manholes**

Classes:

- Crack
- Manhole
- Pothole

Dataset Statistics

| Split | Images |
|--------|-------:|
| Train | 1406 |
| Validation | 301 |
| Test | 302 |
| **Total** | **2009** |

---

# Model

Model:

YOLOv8 Nano (`yolov8n`)

Reasons for selecting YOLOv8 Nano:

- Fast inference
- Lightweight architecture
- Suitable for real-time applications
- Excellent baseline for edge deployment
- Easy integration with Explainable AI techniques

---

# Methodology

The workflow followed in this project:

```
Road Damage Dataset
        │
        ▼
Dataset Preparation
        │
        ▼
Train / Validation / Test Split
        │
        ▼
YOLOv8 Training
        │
        ▼
Performance Evaluation
        │
        ▼
Road Damage Detection
        │
        ▼
Grad-CAM Visualization
        │
        ▼
Model Interpretation
```

---

# Baseline Experiment

Before training the custom detector, the pretrained YOLOv8 Nano model was tested on a road image.

### Observation

The pretrained COCO model failed to detect potholes because road damage classes are not included in the COCO dataset.

Instead, it incorrectly classified a background tree as a giraffe.

This demonstrates why domain-specific training is necessary.

---

# Training Configuration

| Parameter | Value |
|-----------|------:|
| Model | YOLOv8 Nano |
| Epochs | 30 |
| Image Size | 640 × 640 |
| Batch Size | 16 |
| Optimizer | Auto |
| Device | Tesla T4 GPU |

---

# Results

Validation Results

| Metric | Score |
|---------|------:|
| Precision | **0.497** |
| Recall | **0.475** |
| mAP@0.5 | **0.442** |
| mAP@0.5:0.95 | **0.193** |

Per-Class Performance

| Class | mAP@0.5 |
|--------|---------:|
| Crack | 0.360 |
| Manhole | 0.309 |
| Pothole | 0.658 |

The detector achieved the strongest performance on pothole detection while crack and manhole detection remain challenging because of greater visual variability.

---

# Explainable AI using Grad-CAM

Most object detection systems only provide predictions.

Grad-CAM allows us to visualize **which image regions influenced the model's decision**.

Benefits:

- Improves model transparency
- Increases user trust
- Helps identify false detections
- Useful for model debugging
- Supports responsible AI development

---

# Repository Structure

```
Explainable-Road-Damage-Detection/

├── notebooks/
│   └── RoadDamageDetection.ipynb
│
├── images/
│   ├── original_road.jpg
│   ├── baseline_prediction.jpg
│   ├── confusion_matrix.png
│   ├── results.png
│   └── gradcam_example.png
│
├── results/
│   ├── weights/
│   ├── predictions/
│   └── evaluation/
│
├── README.md
├── LICENSE
└── .gitignore
```

---

# Future Improvements

- Train larger YOLOv8 models
- Hyperparameter optimization
- Data augmentation
- Additional road damage categories
- Real-time video inference
- Edge deployment on embedded devices
- Comparative analysis with Faster R-CNN and YOLO11

---

# Technologies Used

- Python
- PyTorch
- Ultralytics YOLOv8
- OpenCV
- NumPy
- Matplotlib
- Google Colab
- Grad-CAM

---

# Applications

- Smart Cities
- Intelligent Transportation Systems
- Autonomous Vehicles
- Infrastructure Monitoring
- Road Maintenance
- AI-assisted Inspection Systems

---

# Author

**Riya Soy**

Mechatronics Engineer

Research Interests

- Computer Vision
- Explainable AI
- Intelligent Infrastructure
- Edge AI
- AI for Public Systems

---

# Acknowledgements

- Ultralytics YOLOv8
- Road Damage Dataset authors
- PyTorch
- OpenCV
