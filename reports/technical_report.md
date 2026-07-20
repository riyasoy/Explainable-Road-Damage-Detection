# Road Damage Detection using YOLOv8 Nano: Towards Explainable Infrastructure Monitoring

## Technical Report

**Author:** Riya Soy

**Project Type:** Mini Research Project

**Date:** July 2026

**Keywords:** Computer Vision, Object Detection, YOLOv8, Explainable AI, Grad-CAM, Road Damage Detection, Intelligent Transportation Systems

## Abstract

Road damage detection is an important application of computer vision for intelligent transportation systems, enabling faster and more consistent infrastructure inspection than traditional manual surveys. However, conventional object detection models often operate as black-box systems, making it difficult to understand the reasoning behind their predictions.

This project investigates a deep learning approach for automated road damage detection using the YOLOv8 Nano object detection model. A custom dataset containing three road damage categories—cracks, potholes, and manholes—was used to train and evaluate the detector. The trained model achieved a precision of 0.497, recall of 0.475, mAP@0.50 of 0.442, and mAP@0.50:0.95 of 0.193 after 30 training epochs. Among the evaluated classes, potholes achieved the strongest detection performance, while cracks and manholes remained more challenging because of their greater visual variability and class imbalance.

In addition to object detection, this project proposes the integration of Gradient-weighted Class Activation Mapping (Grad-CAM) to improve model interpretability by highlighting the image regions that influence detection decisions. Although Grad-CAM has not yet been integrated into the current implementation, this work establishes a foundation for combining efficient object detection with explainable artificial intelligence techniques for intelligent infrastructure monitoring.

# 1. Introduction

Road transportation networks are critical components of modern infrastructure, supporting economic activity, public safety, and daily mobility. Over time, road surfaces deteriorate because of traffic loads, environmental conditions, and aging materials, leading to defects such as cracks, potholes, and damaged manholes. If these defects are not detected and repaired in a timely manner, they can increase maintenance costs, reduce driving comfort, damage vehicles, and contribute to road accidents.

Traditional road inspection methods primarily rely on manual surveys performed by trained personnel. Although manual inspection can provide accurate assessments, it is labor-intensive, time-consuming, expensive, and subject to human variability. As transportation networks continue to expand, there is an increasing need for automated inspection systems capable of detecting road damage efficiently and consistently.

Recent advances in deep learning, particularly convolutional neural networks (CNNs) and object detection models such as the YOLO (You Only Look Once) family, have significantly improved the ability of computer vision systems to detect objects in real time. Among these models, YOLOv8 offers an effective balance between detection accuracy and computational efficiency, making it suitable for applications requiring near real-time performance.

Despite these advances, most object detection systems provide only prediction outputs without explaining how those predictions are generated. This lack of transparency can reduce user confidence, particularly in safety-critical applications involving public infrastructure. Explainable Artificial Intelligence (XAI) techniques such as Gradient-weighted Class Activation Mapping (Grad-CAM) address this limitation by highlighting the image regions that most strongly influence a model's predictions.

The objective of this project is to develop an explainable road damage detection framework using YOLOv8 Nano and Grad-CAM. The study evaluates the performance of a lightweight object detection model trained on a custom road damage dataset and investigates how explainability techniques can improve transparency and trust in automated infrastructure monitoring systems.

## 2. Related Work

Automated road damage detection has become an active research area within intelligent transportation systems due to its potential to reduce the cost and time associated with manual road inspections. Recent advances in deep learning-based object detection, particularly the YOLO family of models, have significantly improved the accuracy and efficiency of pavement defect detection (Guo & Zhang, 2022; Sami et al., 2023).

Guo and Zhang (2022) proposed an improved YOLOv5-based approach for road damage detection, demonstrating enhanced localization performance for multiple pavement defects. Subsequent studies further refined YOLO architectures by introducing lightweight network modifications, attention mechanisms, and feature fusion techniques to improve detection accuracy while maintaining real-time inference capability (Miao et al., 2023; Lightweight Model for Pavement Defect Detection Based on Improved YOLOv7, 2023; RDD-YOLO, 2024).

Recent research has also focused on comparing successive generations of YOLO models and evaluating their suitability for practical deployment in intelligent transportation systems. These studies consistently report that lightweight object detectors provide an effective balance between computational efficiency and detection performance, making them attractive candidates for edge deployment and real-time infrastructure monitoring (Optimizing YOLO Architectures, 2024; Towards Real-world Deployment of Deep Learning Solutions for Road Damage Detection, 2024).

Although modern object detection models achieve promising detection accuracy, they generally operate as black-box systems, providing limited insight into the reasoning behind their predictions. This limitation has motivated growing interest in Explainable Artificial Intelligence (XAI). Gradient-weighted Class Activation Mapping (Grad-CAM) has emerged as one of the most widely adopted explainability techniques for visualizing the image regions that influence deep learning predictions. Recent studies have demonstrated that Grad-CAM can be successfully applied to object detection models, including YOLO-based detectors, to improve model transparency and facilitate error analysis (Kirchknopf et al., 2022; Cheng et al., 2025).

Motivated by these developments, this project proposes the integration of Grad-CAM-based explainability into a lightweight YOLOv8 Nano road damage detection framework. While the current work primarily focuses on developing and evaluating the detection model, future work will integrate Grad-CAM into the inference pipeline to provide interpretable visual explanations of model predictions.

## 3. Dataset

The experiments in this project were conducted using a road damage dataset containing three object categories:

- Crack
- Manhole
- Pothole

The dataset consists of a total of 2,009 annotated images divided into training, validation, and testing subsets.

**Table 1. Dataset Statistics**

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

The final validation metrics obtained from the trained model are summarized in **Table 2**.

**Table 2. Overall Validation Performance**

| Metric | Value |
|---------|------:|
| Precision | 0.497 |
| Recall | 0.475 |
| mAP@0.50 | 0.442 |
| mAP@0.50:0.95 | 0.193 |

These results demonstrate that the lightweight YOLOv8 Nano model was able to learn meaningful representations of road damage despite its limited model capacity and a relatively short training schedule of 30 epochs.

---

### Figure 1. Training Performance

![Training Results](figures/results.png)

*Training metrics over 30 epochs showing the convergence behavior of the YOLOv8 Nano model.*

### 6.2 Class-wise Performance
Performance varied across the three road damage categories.

| Class | mAP@0.50 |
|--------|---------:|
| Crack | 0.360 |
| Manhole | 0.309 |
| Pothole | 0.658 |

Among all classes, potholes achieved the highest detection accuracy. Their larger size and more distinctive visual appearance likely contributed to improved recognition performance. In contrast, cracks and manholes proved more challenging because they often exhibit irregular shapes, varying illumination conditions, and visual similarities to surrounding road surfaces.

---

### Figure 2. Precision–Recall Curve

![Precision–Recall Curve](figures/BoxPR_curve.png)

*Precision–Recall curve illustrating the trade-off between precision and recall across confidence thresholds.*

### 6.3 Training Behaviour

The training process showed gradual improvements in localization and classification performance over successive epochs. Precision–Recall curves, F1-score curves, and confusion matrices indicate that the detector learned meaningful representations of road damage while still exhibiting confusion between visually similar classes.
The training visualizations provide additional insight into the detector's learning behaviour, illustrating the evolution of precision, recall, and class-wise confusion throughout the training process.

---

### Figure 3. Confusion Matrix

![Confusion Matrix](figures/confusion_matrix.png)

*Confusion matrix showing class-wise prediction performance on the validation dataset.*

### 6.4 Prediction Examples

Qualitative evaluation of the trained model demonstrated successful detection of multiple road damage categories across different road scenes. Representative prediction examples have been included in the repository, covering successful detections of cracks, potholes, and manholes, as well as challenging failure cases. Including both successful and unsuccessful predictions provides a more comprehensive assessment of the detector's strengths and current limitations.

## 7. Discussion

The results demonstrate that YOLOv8 Nano can effectively detect road damage while maintaining a lightweight architecture suitable for real-time applications. Although the overall detection performance is moderate, the model successfully learned meaningful visual representations from the training dataset within only 30 epochs.

Among the three road damage categories, potholes achieved the highest overall mAP@0.50 score (0.658), indicating stronger average detection performance than cracks and manholes. However, qualitative analysis of prediction examples revealed that potholes were still frequently confused with manholes or partially detected as cracks in challenging scenes. Water-filled potholes, overlapping defects, and variations in road texture sometimes caused the detector to assign incorrect class labels despite successfully localizing the damaged region. These observations suggest that although potholes were the best-performing class overall, significant classification errors remain, highlighting opportunities for further improvement through additional training data, longer training schedules, and model refinement.

These observations highlight the importance of evaluating both quantitative performance metrics and qualitative prediction examples when assessing object detection systems for real-world infrastructure monitoring.

The analysis of representative prediction images revealed both successful detections and failure cases. Successful predictions indicate that the model learned useful spatial features for identifying road damage. However, several failure cases demonstrate that complex backgrounds, lighting variations, partial occlusions, and subtle surface defects continue to challenge the detector.

An important objective of this project extends beyond achieving high detection accuracy. The planned integration of Gradient-weighted Class Activation Mapping (Grad-CAM) aims to improve the interpretability of the model by highlighting image regions that contribute most strongly to each prediction. Such explainability is particularly valuable for intelligent transportation systems, where engineers and decision-makers benefit from understanding not only what the model predicts but also why those predictions are made.

Overall, the findings suggest that lightweight object detection models such as YOLOv8 Nano provide a practical foundation for automated road inspection. With additional data, longer training, and explainability analysis, the system has the potential to support more reliable infrastructure monitoring applications.

## 8. Limitations

Although the proposed approach demonstrates the feasibility of lightweight road damage detection using YOLOv8 Nano, several limitations remain.

The model was trained for only 30 epochs, which may not have been sufficient for complete convergence. Furthermore, only the YOLOv8 Nano variant was evaluated in this study; comparisons with larger YOLOv8 models were beyond the scope of the current project. In addition, the lightweight YOLOv8 Nano architecture prioritizes computational efficiency over maximum detection accuracy, resulting in reduced performance for visually complex classes.

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

1. Guo, G., & Zhang, Z. (2022). *Road damage detection algorithm for improved YOLOv5*. Scientific Reports.

2. Sami, A. A., Sakib, S., Deb, K., & Sarker, I. H. (2023). *Improved YOLOv5-based real-time road pavement damage detection in road infrastructure management*. Algorithms.

3. Miao, R., Xianfeng, Z., Xiao, C., Bo, Z., & Ziyuan, F. (2023). *YOLOv5s-M: A deep learning network model for road pavement damage detection from urban street-view imagery*. International Journal of Applied Earth Observation and Geoinformation.

4. *Lightweight Model for Pavement Defect Detection Based on Improved YOLOv7*. (2023).

5. *RDD-YOLO: Road Damage Detection Algorithm Based on Improved YOLOv8*. (2024). Applied Sciences.

6. *Optimizing YOLO Architectures for Optimal Road Damage Detection and Classification: A Comparative Study from YOLOv7 to YOLOv10*. (2024). IEEE BigData.

7. *Towards Real-world Deployment of Deep Learning Solutions for Road Damage Detection*. (2024). IEEE BigData.

8. Kirchknopf, A., Slijepcevic, D., Wunderlich, I., Breiter, M., Traxler, J., & Zeppelzauer, M. (2022). *Explaining YOLO: Leveraging Grad-CAM to Explain Object Detections*.

9. Cheng, Z., Wu, Y., Li, Y., Cai, L., & Ihnaini, B. (2025). *A Comprehensive Review of Explainable Artificial Intelligence (XAI) in Computer Vision*. Sensors.
