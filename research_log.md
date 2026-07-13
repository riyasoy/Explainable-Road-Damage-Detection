# Research Log

---

## Day 1

**30/June/2026:** 

### Objective

Started the Explainable Road Damage Detection project.

### Tasks Completed

- Created GitHub repository.
- Added LICENSE.
- Added .gitignore.
- Created research_log.md.
- Created Google Colab notebook.
- Installed Ultralytics.
- Successfully loaded YOLOv8 Nano model.
- Performed inference on sample images.

### Observations

YOLOv8 successfully detected road objects using the pretrained model.

### Next Goal

Find and prepare a suitable road damage dataset.

## Day 2 — 3 July 2026

### Objective
Prepare the RDD2022 dataset for model development.

### Tasks Completed
- Downloaded the RDD2022 dataset.
- Created a structured dataset directory.
- Extracted the dataset for inspection.
- Prepared the repository for the data exploration phase.

### Observations
The dataset download completed successfully. The next step is to inspect the folder structure, annotation format, and class distribution before training.

### Next Goal
Explore the dataset structure and verify annotation files for YOLOv8 training.

## Day 3 — 5 July 2026

### Objective
Inspect the RDD2022 dataset and verify its readiness for YOLOv8 training.

### Tasks Completed
- Verified the extracted dataset structure.
- Confirmed the dataset contains train, validation, and test splits.
- Confirmed each split contains corresponding images and YOLO-format label files.
- Verified the dataset is already organized for YOLOv8, eliminating the need for annotation conversion.
- Inspected YOLO annotation files and confirmed that labels follow the normalized YOLO bounding box format (Class ID, X-center, Y-center, Width, Height).

### Observations
- The dataset is already formatted for YOLO training, allowing the project to proceed directly to dataset exploration and verification.
- Each annotation file contains one row per detected road damage. Bounding boxes are stored as normalized coordinates rather than pixel values, making the annotations resolution-independent.

### Next Goal
Inspect sample annotations, visualize bounding boxes, analyze class distribution, and prepare the dataset configuration file (`data.yaml`) for model training.

## Day 4 — 13 July 2026

### Objective

Rebuild the project environment after system failure and re-establish the baseline object detection workflow.

### Tasks Completed

- Recreated the Google Colab environment.
- Reinstalled the required libraries and dependencies.
- Loaded the pretrained YOLOv8 Nano model (`yolov8n.pt`).
- Performed inference on a road image containing a visible pothole.
- Visualized the prediction results.
- Reviewed the YOLO annotation format.
- Documented the baseline experiment in the project notebook and GitHub repository.

### Observations

- The pretrained YOLOv8 Nano model failed to detect the pothole.
- A tree in the background was incorrectly classified as a **giraffe** with a confidence score of approximately **0.32**.
- This result confirms that the pretrained model, which is trained on the COCO dataset, is not suitable for detecting road damage without domain-specific training.

### Next Goal

Resume work with the RDD2022 dataset and begin preparing the custom training pipeline for YOLOv8.
