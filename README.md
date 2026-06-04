# Brain Tumor Detection and Classification using YOLOv26

## Overview

This project implements a **YOLOv11-based Brain Tumor Detection and Classification System** for MRI scans. The model is trained to detect and classify three major brain tumor types:

- Glioma
- Meningioma
- Pituitary Tumor

The system performs **object detection and localization**, providing both the tumor class and bounding box coordinates within MRI images.

---

## Features

✅ Automatic brain tumor detection from MRI scans  
✅ Tumor localization using bounding boxes  
✅ Multi-class classification

- Glioma
- Meningioma
- Pituitary

✅ Real-time inference capability  
✅ High detection accuracy using YOLOv11  
✅ Training and validation visualization support  
✅ Confusion matrix and F1-score analysis

---

## Dataset

The dataset consists of annotated brain MRI images containing:

| Class | Label ID |
|---------|---------|
| Glioma | 0 |
| Meningioma | 1 |
| Pituitary | 2 |

Each image is annotated in YOLO format:

```txt
<class_id> <x_center> <y_center> <width> <height>
```

### Dataset Structure

```text
dataset/
│
├── train/
│   ├── images/
│   └── labels/
│
├── valid/
│   ├── images/
│   └── labels/
│
└── data.yaml
```

---

## Model Architecture

This project uses **YOLOv11 Object Detection** architecture.

### Advantages

- Fast inference speed
- Accurate object localization
- Multi-class detection
- Lightweight deployment
- Suitable for real-time medical image analysis

---

## Training

### Installation

```bash
pip install ultralytics
```

### Train Model

```bash
yolo detect train \
    model=yolo11n.pt \
    data=data.yaml \
    epochs=100 \
    imgsz=640
```

---

## Validation

Run validation:

```bash
yolo detect val \
    model=runs/detect/train/weights/best.pt \
    data=data.yaml
```

---

## Results

### F1-Confidence Curve

The model achieves its best overall performance at approximately:

- **F1 Score:** 0.89
- **Confidence Threshold:** 0.44

Observations:

- Meningioma achieves the highest F1 performance.
- Pituitary shows strong detection accuracy.
- Glioma remains the most challenging class.

---

### Confusion Matrix Analysis

#### Glioma

- Correctly detected: 148
- Missed detections: 38
- Most challenging class due to shape and appearance variations.

#### Meningioma

- Correctly detected: 100
- Very few misclassifications.
- Highest class-wise accuracy.

#### Pituitary

- Correctly detected: 128
- Strong classification performance.

---

### Normalized Confusion Matrix

Class-wise recall:

| Class | Recall |
|---------|---------|
| Glioma | 79% |
| Meningioma | 95% |
| Pituitary | 93% |

---

## Sample Predictions

The model successfully identifies:

- Tumor location
- Tumor type
- Bounding box coordinates

Example predictions:

```text
Glioma
Confidence: 0.91

Meningioma
Confidence: 0.95

Pituitary
Confidence: 0.94
```

---

## Evaluation Metrics

| Metric | Value |
|----------|----------|
| Best F1 Score | 0.89 |
| Confidence Threshold | 0.44 |
| Glioma Recall | 79% |
| Meningioma Recall | 95% |
| Pituitary Recall | 93% |

---

## Inference

Run prediction on an MRI image:

```bash
yolo detect predict \
    model=best.pt \
    source=test_image.jpg
```

Output:

```text
runs/detect/predict/
```

Contains:

- Predicted images
- Bounding boxes
- Confidence scores

---

## Applications

- Computer-Aided Diagnosis (CAD)
- Clinical Decision Support Systems
- Medical Imaging Research
- Automated Tumor Screening
- Radiology Assistance

---

## Future Improvements

- Support for additional tumor types
- Tumor segmentation using YOLO-Seg
- Integration with Grad-CAM explainability
- Web deployment using Flask/FastAPI
- Real-time hospital workflow integration
- 3D MRI volume analysis

---

## Technologies Used

- Python
- YOLOv11
- Ultralytics
- OpenCV
- NumPy
- Matplotlib
---
- PyTorch

---
