# Explainable Road Damage Detection using YOLOv8 and Grad-CAM

## Overview

This project investigates automated road damage detection using the YOLOv8 object detection framework together with Explainable AI (XAI) techniques, specifically Grad-CAM.

The objective is to develop an interpretable computer vision system capable of detecting different types of road damage while providing visual explanations of the model's predictions. The project follows a research-oriented workflow including dataset analysis, model training, explainability, performance evaluation, and result visualization.

## Baseline Experiment

The pretrained YOLOv8 Nano model (`yolov8n.pt`) was tested on an image containing a pothole.

### Observations

- Failed to detect the pothole.
- Incorrectly classified a tree as a giraffe (confidence ≈ 0.32).
- Demonstrates that pretrained COCO models are not suitable for road damage detection without fine-tuning.

This baseline experiment motivates the use of a dedicated road damage dataset (RDD2022) for custom training.

| Experiment      | Model                  | Result                                                               |
| --------------- | ---------------------- | -------------------------------------------------------------------- |
| Baseline        | Pretrained YOLOv8 Nano | ❌ Missed pothole; false positive (tree → giraffe, confidence ≈ 0.32) |
| Custom Training | YOLOv8 + RDD2022       | ⏳ In Progress                                                        |
| Explainability  | YOLOv8 + Grad-CAM      | ⏳ Planned                                                            |


**Current Status:** 🚧 In Progress
