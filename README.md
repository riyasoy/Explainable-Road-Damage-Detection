# Explainable Road Damage Detection using YOLOv8 and Grad-CAM

## Overview

This project investigates automated road damage detection using the YOLOv8 object detection framework together with Explainable AI (XAI) techniques, specifically Grad-CAM.

The objective is to develop an interpretable computer vision system capable of detecting different types of road damage while providing visual explanations of the model's predictions. The project follows a research-oriented workflow including dataset analysis, model training, explainability, performance evaluation, and result visualization.

## Baseline Experiment

Before training a custom model, the pretrained **YOLOv8 Nano** model (`yolov8n.pt`) was evaluated on a road image containing a visible pothole.

### Input Image

![Original Road Image](images/original_road.jpg)

### Prediction Result

![Baseline Prediction](images/baseline_prediction.jpg)

### Observations

- The pretrained model failed to detect the pothole.
- A tree in the background was incorrectly classified as a **giraffe** with a confidence score of approximately **0.32**.
- No road damage was detected.

### Discussion

The pretrained YOLOv8 Nano model is trained on the COCO dataset, which contains 80 everyday object classes such as people, vehicles, and animals. However, it does not include road damage categories such as potholes or cracks.

As a result, the model was unable to recognize the pothole and instead produced a false positive.

### Conclusion

This baseline experiment demonstrates the limitations of a generic object detection model for road damage detection and motivates the need to train YOLOv8 on a dedicated Road Damage Dataset (RDD2022).

| Experiment      | Model                  | Result                                                               |
| --------------- | ---------------------- | -------------------------------------------------------------------- |
| Baseline        | Pretrained YOLOv8 Nano | ❌ Missed pothole; false positive (tree → giraffe, confidence ≈ 0.32) |
| Custom Training | YOLOv8 + RDD2022       | ⏳ In Progress                                                        |
| Explainability  | YOLOv8 + Grad-CAM      | ⏳ Planned                                                            |


**Current Status:** 🚧 In Progress
