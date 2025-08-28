# OralVis AI Research Intern Task: Tooth Numbering Detection

This repository contains the complete solution for the AI Research Intern computer vision task. The primary goal was to train a YOLOv8 model to detect and classify teeth in panoramic dental X-rays according to the FDI numbering system.

## Project Overview

The project involved the following key steps:

1.  **Data Preparation**: The provided dataset of ~500 images was analyzed and split into training (80%), validation (10%), and test (10%) sets.
2.  **Configuration**: A `dental_data.yaml` file was created to define the dataset paths and map the 32 class IDs to their corresponding FDI tooth names.
3.  **Model Training**: A pretrained YOLOv8s model was fine-tuned on the custom dental dataset for 100 epochs.
4.  **Evaluation**: The trained model was evaluated on the unseen test set to measure its performance using standard object detection metrics.

## Environment Setup

To set up the environment and install the required packages, create a virtual environment and run the following command:

```bash
pip install -r requirements.txt
```

A `requirements.txt` file should be created containing the necessary libraries, primarily:

```
ultralytics
torch
torchvision
pyyaml
opencv-python
matplotlib
```

## How to Run

The model was trained and evaluated within the provided Google Colab notebook (`[Your_Notebook_Name].ipynb`).

### Training

The training process uses the configuration specified in `dental_data.yaml` and can be initiated by running the cells in the notebook or using the following command in the terminal:

```bash
yolo train data=dental_data.yaml model=yolov8s.pt epochs=100 imgsz=640 batch=16 name=dental_detection_final
```

### Evaluation

To evaluate the best trained model on the test set, use the following command:

```bash
yolo val model=runs/detect/dental_detection_final/weights/best.pt data=dental_data.yaml split=test
