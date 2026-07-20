# Technical Report

## Explainable Road Damage Detection using YOLOv8 and Grad-CAM
**Author:** Riya Soy

**Project Type:** Mini Research Project

**Keywords:** Computer Vision, Object Detection, YOLOv8, Explainable AI, Grad-CAM, Road Damage Detection, Intelligent Transportation Systems

## Abstract

Road damage detection is an important application of computer vision for intelligent transportation systems, enabling faster and more consistent infrastructure inspection than traditional manual surveys. However, conventional object detection models often operate as black-box systems, making it difficult to understand the reasoning behind their predictions.

This project investigates an explainable deep learning approach for automated road damage detection using the YOLOv8 Nano object detection model. A custom dataset containing three road damage categories—cracks, potholes, and manholes—was used to train and evaluate the detector. The trained model achieved a precision of 0.497, recall of 0.475, mAP@0.50 of 0.442, and mAP@0.50:0.95 of 0.193 after 30 training epochs. Among the evaluated classes, potholes achieved the strongest detection performance, while cracks and manholes remained more challenging because of their greater visual variability and class imbalance.

Beyond object detection, this project aims to improve model interpretability by integrating Gradient-weighted Class Activation Mapping (Grad-CAM), allowing visual inspection of the image regions influencing the model's predictions. Although the Grad-CAM implementation is planned as ongoing work, the project establishes a foundation for combining accurate object detection with explainable artificial intelligence techniques for intelligent infrastructure monitoring.

# 1. Introduction

Road transportation networks are critical components of modern infrastructure, supporting economic activity, public safety, and daily mobility. Over time, road surfaces deteriorate because of traffic loads, environmental conditions, and aging materials, leading to defects such as cracks, potholes, and damaged manholes. If these defects are not detected and repaired in a timely manner, they can increase maintenance costs, reduce driving comfort, damage vehicles, and contribute to road accidents.

Traditional road inspection methods primarily rely on manual surveys performed by trained personnel. Although manual inspection can provide accurate assessments, it is labor-intensive, time-consuming, expensive, and subject to human variability. As transportation networks continue to expand, there is an increasing need for automated inspection systems capable of detecting road damage efficiently and consistently.

Recent advances in deep learning, particularly convolutional neural networks (CNNs) and object detection models such as the YOLO (You Only Look Once) family, have significantly improved the ability of computer vision systems to detect objects in real time. Among these models, YOLOv8 offers an effective balance between detection accuracy and computational efficiency, making it suitable for applications requiring near real-time performance.

Despite these advances, most object detection systems provide only prediction outputs without explaining how those predictions are generated. This lack of transparency can reduce user confidence, particularly in safety-critical applications involving public infrastructure. Explainable Artificial Intelligence (XAI) techniques such as Gradient-weighted Class Activation Mapping (Grad-CAM) address this limitation by highlighting the image regions that most strongly influence a model's predictions.

The objective of this project is to develop an explainable road damage detection framework using YOLOv8 Nano and Grad-CAM. The study evaluates the performance of a lightweight object detection model trained on a custom road damage dataset and investigates how explainability techniques can improve transparency and trust in automated infrastructure monitoring systems.

## 2. Related Work

Recent advances in deep learning have significantly improved the performance of automated road damage detection systems. Object detection architectures based on the YOLO (You Only Look Once) family have become widely adopted because they provide an effective balance between detection accuracy and inference speed, making them suitable for real-time infrastructure monitoring applications.

Several publicly available road damage datasets have accelerated research in this domain by enabling the development and comparison of deep learning models under standardized evaluation settings. These datasets typically include multiple categories of road defects such as cracks, potholes, and surface deterioration captured under varying environmental conditions.

Although modern object detectors achieve high detection performance, most operate as black-box models, providing little insight into the reasoning behind their predictions. This limitation has encouraged growing interest in Explainable Artificial Intelligence (XAI) techniques, including Gradient-weighted Class Activation Mapping (Grad-CAM), which can highlight image regions influencing model decisions.

In the next revision of this report, this section will be expanded with recent peer-reviewed literature discussing YOLO-based road damage detection methods, explainability techniques, and intelligent transportation applications.

## 3. Dataset

The experiments in this project were conducted using a road damage dataset containing three object categories:

- Crack
- Manhole
- Pothole

The dataset consists of a total of 2,009 annotated images divided into training, validation, and testing subsets.

| Dataset Split | Number of Images |
|---------------|-----------------:|
| Training | 1406 |
| Validation | 301 |
| Testing | 302 |
| **Total** | **2009** |

The dataset contains images captured under diverse road conditions, illumination levels, and viewing perspectives. Such variability increases the difficulty of the detection task while improving the model's ability to generalize to unseen road scenes.

## 4. Methodology

The overall workflow of this project consists of dataset preparation, model training, performance evaluation, and explainability analysis. The objective is to develop a lightweight object detection system capable of accurately identifying common types of road damage while providing interpretable predictions.

### 4.1 Data Preparation

The dataset was divided into training, validation, and testing subsets. Each image contains bounding box annotations corresponding to one of three road damage categories: crack, manhole, and pothole. The dataset configuration was provided to the YOLOv8 training framework through a YAML configuration file.

### 4.2 Model Selection

YOLOv8 Nano (YOLOv8n) was selected as the baseline object detection model because of its lightweight architecture, fast inference speed, and suitability for real-time applications. Although larger YOLO models generally provide higher detection accuracy, the Nano variant offers an effective balance between computational efficiency and performance.

### 4.3 Model Training

The model was trained for 30 epochs using the Ultralytics YOLOv8 framework on a Tesla T4 GPU in Google Colab. During training, the model optimized its weights using annotated road damage images while monitoring validation performance after each epoch.

### 4.4 Performance Evaluation

Model performance was evaluated using commonly adopted object detection metrics including Precision, Recall, mean Average Precision at IoU threshold 0.50 (mAP@0.50), and mean Average Precision across IoU thresholds from 0.50 to 0.95 (mAP@0.50:0.95). Confusion matrices and precision–recall curves were also analyzed to understand class-wise performance.

### 4.5 Explainability

To improve model transparency, Grad-CAM has been selected as the explainability technique for this project. Grad-CAM produces heatmaps highlighting the image regions that contribute most strongly to the model's predictions. The implementation of Grad-CAM is planned as the next stage of this work and will be integrated into the inference pipeline.

## 5. Experimental Setup

The experiments were conducted using the Ultralytics implementation of YOLOv8 within the Google Colab environment. Model training was performed using an NVIDIA Tesla T4 GPU, enabling efficient optimization of the lightweight YOLOv8 Nano architecture.

The detector was trained for 30 epochs using images resized to 640 × 640 pixels. The dataset was divided into predefined training, validation, and testing subsets consisting of 1,406, 301, and 302 images, respectively. The default optimization strategy provided by the Ultralytics framework was used throughout training.

Model performance was monitored using validation metrics generated after each training epoch. Precision, Recall, mAP@0.50, and mAP@0.50:0.95 were selected as the primary evaluation metrics because they are widely adopted for benchmarking object detection models. In addition, confusion matrices, precision–recall curves, and F1-score curves were analyzed to better understand class-wise performance and model behavior.

## 6. Results

The trained YOLOv8 Nano model successfully learned to detect three categories of road damage: cracks, manholes, and potholes. Performance was evaluated using the validation dataset after 30 training epochs.

### 6.1 Overall Detection Performance

The final validation metrics obtained from the trained model are summarized in Table 2.

| Metric | Value |
|---------|------:|
| Precision | 0.497 |
| Recall | 0.475 |
| mAP@0.50 | 0.442 |
| mAP@0.50:0.95 | 0.193 |

These results indicate that the model achieved moderate detection performance despite using the lightweight YOLOv8 Nano architecture and a relatively short training schedule.

### 6.2 Class-wise Performance

Performance varied across the three road damage categories.

| Class | mAP@0.50 |
|--------|---------:|
| Crack | 0.360 |
| Manhole | 0.309 |
| Pothole | 0.658 |

Among all classes, potholes achieved the highest detection accuracy. Their larger size and more distinctive visual appearance likely contributed to improved recognition performance. In contrast, cracks and manholes proved more challenging because they often exhibit irregular shapes, varying illumination conditions, and visual similarities to surrounding road surfaces.

### 6.3 Training Behaviour

The training process showed gradual improvements in localization and classification performance over successive epochs. Precision–Recall curves, F1-score curves, and confusion matrices indicate that the detector learned meaningful representations of road damage while still exhibiting confusion between visually similar classes.

Training visualizations included in the GitHub repository further illustrate the learning dynamics of the model, including precision, recall, F1-score progression, and confusion matrix analysis.

### 6.4 Prediction Examples

Qualitative evaluation of the trained model demonstrated successful detection of multiple road damage categories across different road scenes. Representative prediction examples have been included in the repository, covering successful detections of cracks, potholes, and manholes, as well as challenging failure cases. Including both successful and unsuccessful predictions provides a more comprehensive assessment of the detector's strengths and current limitations.

## 7. Discussion

The results demonstrate that YOLOv8 Nano can effectively detect road damage while maintaining a lightweight architecture suitable for real-time applications. Although the overall detection performance is moderate, the model successfully learned meaningful visual representations from the training dataset within only 30 epochs.

Among the three road damage categories, potholes achieved the highest overall mAP@0.50 score (0.658), indicating stronger average detection performance than cracks and manholes. However, qualitative analysis of prediction examples revealed that potholes were still frequently confused with manholes or partially detected as cracks in challenging scenes. Water-filled potholes, overlapping defects, and variations in road texture sometimes caused the detector to assign incorrect class labels despite successfully localizing the damaged region. These observations suggest that although potholes were the best-performing class overall, significant classification errors remain, highlighting opportunities for further improvement through additional training data, longer training schedules, and model refinement.

The analysis of representative prediction images revealed both successful detections and failure cases. Successful predictions indicate that the model learned useful spatial features for identifying road damage. However, several failure cases demonstrate that complex backgrounds, lighting variations, partial occlusions, and subtle surface defects continue to challenge the detector.

An important objective of this project extends beyond achieving high detection accuracy. The planned integration of Gradient-weighted Class Activation Mapping (Grad-CAM) aims to improve the interpretability of the model by highlighting image regions that contribute most strongly to each prediction. Such explainability is particularly valuable for intelligent transportation systems, where engineers and decision-makers benefit from understanding not only what the model predicts but also why those predictions are made.

Overall, the findings suggest that lightweight object detection models such as YOLOv8 Nano provide a practical foundation for automated road inspection. With additional data, longer training, and explainability analysis, the system has the potential to support more reliable infrastructure monitoring applications.

## 8. Limitations

Although the proposed approach demonstrates the feasibility of lightweight road damage detection using YOLOv8 Nano, several limitations remain.

The model was trained for only 30 epochs, which may not have been sufficient for complete convergence. In addition, the lightweight YOLOv8 Nano architecture prioritizes computational efficiency over maximum detection accuracy, resulting in reduced performance for visually complex classes.

The dataset also presents challenges including varying lighting conditions, road textures, object scales, partial occlusions, and class imbalance. These factors contribute to missed detections and incorrect class predictions, particularly for cracks and manholes. Furthermore, explainability using Grad-CAM has not yet been fully integrated into the inference pipeline and therefore has not been quantitatively evaluated in this study.

These limitations provide opportunities for future improvements in both model performance and interpretability.

## 9. Future Work

Several extensions can further improve this project.

Future work will focus on integrating Grad-CAM to visualize the regions influencing model predictions and to better understand both successful detections and failure cases. Additional experiments using larger YOLOv8 variants, such as YOLOv8s and YOLOv8m, will be conducted to compare accuracy and computational efficiency.

Further improvements include increasing the number of training epochs, applying stronger data augmentation techniques, evaluating additional road damage datasets, and performing comparative experiments with other object detection architectures. In the longer term, the system could be extended for real-time road inspection using edge devices or intelligent transportation platforms.

## 10. Conclusion

This project presented a lightweight framework for automated road damage detection using the YOLOv8 Nano object detection model. The trained detector successfully identified three categories of road damage—cracks, potholes, and manholes—and achieved moderate detection performance on a custom road damage dataset.

Beyond model development, the project emphasizes the importance of explainability in computer vision applications. By incorporating Grad-CAM in future work, the system aims to provide greater transparency into the decision-making process of deep learning models used for infrastructure monitoring.

Overall, this study demonstrates that lightweight object detection models can serve as a practical foundation for intelligent road inspection systems while highlighting the importance of continued improvements in accuracy, robustness, and model interpretability.

## References

> References will be added after reviewing recent literature on road damage detection, YOLO-based object detection, and Explainable Artificial Intelligence (XAI).
