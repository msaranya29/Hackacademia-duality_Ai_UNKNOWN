# YOLOv8 Space Station Object Detection

This repository contains a custom-trained YOLOv8 model for detecting critical safety equipment inside a simulated space station environment. It uses synthetic data and provides scripts for training, validating, and predicting with YOLOv8.

---

## Project Overview

- Detect objects: Toolbox, Oxygen Tank, Fire Extinguisher
- Dataset formatted for YOLO with images and labels
- Performance metrics: mAP@0.5, precision, recall, confusion matrix
- Scripts for training (train.py), prediction (predict.py), and validation

---

## Setup Instructions

### Prerequisites

- Python 3.8+
- Conda environment recommended
- GPU optional; CPU supported

### Installation

1. Clone the repo:

git clone https://github.com/yourusername/yolov8-space-station-detection.git

cd yolov8-space-station-detection


2. Create and activate Conda env:

conda create -n yolov8-env python=3.10 -y

conda activate yolov8-env



3. Install dependencies:

pip install -r requirements.txt

pip install ultralytics



---

## Dataset Structure and Configuration

Organize dataset as:

data/

train/

images/

labels/

val/

images/

labels/

test/

images/

labels/




yolo_params.yaml sample content:

train: data/train/images
val: data/val/images
test: data/test/images

nc: 3
names: ['Toolbox', 'Oxygen Tank', 'Fire Extinguisher']



---

## Training

Run training with:

python train.py --epochs 20 --batch 16 --img 640 --weights yolov8s.pt --device cpu



Checkpoints saved inside runs/train/.

---

## Validation

Use Python API:

from ultralytics import YOLO

model = YOLO('runs/train/exp/weights/best.pt')

metrics = model.val(data='yolo_params.yaml', split='val')

print(metrics)



Or CLI:


yolo val model=runs/train/exp/weights/best.pt data=yolo_params.yaml split=val




---

## Prediction

Run inference on test images:


python predict.py --weights runs/train/exp/weights/best.pt --source data/test/images --img 640 --conf 0.25 --device cpu





Outputs saved in predictions/images and predictions/labels.

---

## File Structure

├── train.py

├── predict.py

├── yolo_params.yaml

├── requirements.txt

├── runs/

├── predictions/

└── README.md



---


## Contact

For questions contact [Saranya] at [m.saranya.work@gmail.com]
