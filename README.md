<h1 align="center">🚀 Conveyor Belt Defect Detection using YOLOv8</h1>

<p align="center">
Synthetic Dataset Generation and Automated Industrial Defect Detection
</p>

---

## 📌 Overview

This project generates a synthetic dataset of industrial components placed on a conveyor belt and trains a YOLOv8 model to detect manufacturing defects.

The system simulates real-world factory inspection scenarios by generating realistic images of:

- Washers
- Bolts
- Plastic Caps

along with common defects such as:

- Scratches
- Missing Features
- Wrong Colors
- Wrong Orientations

The generated images are automatically annotated in YOLO format and used to train a YOLOv8 object detection model.

---

## ✨ Features

### Synthetic Dataset Generation

- Realistic conveyor belt backgrounds
- Multiple industrial part types
- Automatic YOLO label generation
- Random object placement
- Collision-free object positioning

### Defect Simulation

- Scratch defects
- Missing features
- Wrong colors
- Wrong orientations

### Data Augmentation

- Brightness variation
- Contrast variation
- Gaussian blur
- Salt-and-pepper noise

### YOLOv8 Training Pipeline

- Automatic train/validation/test split
- YOLO configuration generation
- YOLOv8 model training
- Model evaluation and metrics reporting

---

## 🏷 Dataset Classes

| Class ID | Class Name |
|-----------|------------|
| 0 | good |
| 1 | scratch |
| 2 | missing_feature |
| 3 | wrong_color |
| 4 | wrong_orientation |

---

## 📂 Project Structure

```text
project/
│
├── GENERATOR.py
├── augment_data.py
├── trainedmodel.py
│
├── dataset/
│   ├── images/
│   │   ├── train/
│   │   ├── val/
│   │   └── test/
│   │
│   ├── labels/
│   │   ├── train/
│   │   ├── val/
│   │   └── test/
│   │
│   └── data.yaml
│
└── runs/
    └── detect/
```

---

## ⚙️ Installation

### Clone Repository

```bash
git clone https://github.com/yourusername/conveyor-defect-detection.git
cd conveyor-defect-detection
```

### Install Dependencies

```bash
pip install opencv-python
pip install numpy
pip install pillow
pip install tqdm
pip install matplotlib
pip install ultralytics
```

Or:

```bash
pip install -r requirements.txt
```

---

## 🏭 Dataset Generation

Generate synthetic images and YOLO annotations:

```bash
python GENERATOR.py
```

Default settings:

```python
TOTAL_IMAGES = 1200
IMG_W = 640
IMG_H = 640
PARTS_PER_IMG = (1, 4)
```

Generated dataset:

```text
dataset/
├── images/
├── labels/
└── data.yaml
```

---

## 🖼 Sample Generated Images

The generator creates realistic conveyor belt scenes with random industrial parts and defects.

Examples include:

- Good parts
- Scratched parts
- Missing features
- Wrong colors
- Incorrect orientations
example:
<img width="735" height="706" alt="image" src="https://github.com/user-attachments/assets/2715ef99-0e53-4866-9ed7-2bdbb17ac250" />

---

## 🔄 Data Augmentation

Run:

```bash
python augment_data.py
```

Applied augmentations:

- Brightness adjustment
- Contrast adjustment
- Gaussian blur
- Salt-and-pepper noise

These augmentations improve model robustness under varying industrial conditions.

---

## 🤖 YOLOv8 Training

Train the detector:

```python
from ultralytics import YOLO

model = YOLO("yolov8n.pt")

results = model.train(
    data="dataset/data.yaml",
    epochs=20,
    imgsz=640,
    batch=16
)
```

---

## 📊 Model Evaluation

Evaluate trained weights:

```python
from ultralytics import YOLO

model = YOLO("best.pt")

metrics = model.val(
    data="dataset/data.yaml",
    split="test",
    conf=0.25,
    iou=0.45
)
```

Metrics reported:

- mAP@0.5
- mAP@0.5:0.95
- Precision
- Recall

---

## 📋 YOLO Annotation Format

Example label:

```text
1 0.452 0.623 0.101 0.091
```

Format:

```text
class_id x_center y_center width height
```

All coordinates are normalized between 0 and 1.

---

## 📈 Training Outputs

After training, YOLOv8 generates:

```text
runs/
└── detect/
    └── train/
        ├── weights/
        │   ├── best.pt
        │   └── last.pt
        ├── results.png
        ├── confusion_matrix.png
        ├── PR_curve.png
        └── F1_curve.png
```

---

## 🎯 Applications

- Manufacturing Quality Inspection
- Industrial Automation
- Smart Factory Systems
- Conveyor Belt Monitoring
- Automated Defect Detection
- Predictive Maintenance

---

## 🔮 Future Improvements

- Real-world factory image fine-tuning
- Additional defect categories
- YOLOv8s / YOLOv8m / YOLOv8l training
- RTSP camera integration
- Real-time defect monitoring
- NVIDIA Jetson deployment
- Edge AI inference

---

## 🛠 Technologies Used

- Python
- OpenCV
- NumPy
- Matplotlib
- YOLOv8
- Ultralytics

---

## 👨‍💻 Author

**Noor Tandon**

Computer Vision Project focused on synthetic data generation and industrial defect detection using YOLOv8.

---

## ⭐ Acknowledgements

- Ultralytics YOLOv8
- OpenCV
- NumPy Community
- Google Colab

If you found this project useful, consider giving it a ⭐ on GitHub.
