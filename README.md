# Iris-Pupil-CV-Model

A deep learning project for **iris and pupil ellipse parameter prediction** from eye images.  
This model, named **EyeNet**, is designed for biomedical imaging applications such as ophthalmology diagnostics and biometric verification.

---

## Features
- **Multitask CNN architecture** for simultaneous iris and pupil prediction
- **Ellipse parameter regression** (center coordinates, major/minor axes, and orientation)
- **Preprocessing pipeline** with coordinate scaling to match resized images
- **Data augmentation** to improve model generalization
- **Evaluation metrics** including MAE, MSE, and R²

---

## Repository Structure
Iris-Pupil-CV-Model/
├── training_set/ # Training images and labels
├── testing_set/ # Test images and labels
├── Additional Submission Details/ # Supplemental project info
├── EyeNetModel.ipynb # Jupyter notebook with model training & evaluation
├── evaluation_metrics.csv # Model performance metrics
├── README.md # Project documentation
└── .gitignore # Ignore system files

# EyeNet: Iris-Pupil Ellipse Prediction with Deep Learning

**EyeNet** is a multitask deep learning model built with PyTorch that predicts geometric parameters of pupil and iris ellipses from eye images. It is designed for biomedical imaging and biometric analysis, offering accurate center, axis, and orientation predictions.

---

## Dataset

Images and corresponding label `.csv` files are stored in:
- `training_set/images/` & `training_set/groundtruth/`
- `testing_set/images/` & `testing_set/groundtruth/`

Each label file contains 10 ellipse parameters:
- **Pupil:** `x`, `y`, `rx`, `ry`, `theta`
- **Iris:**  `x`, `y`, `rx`, `ry`, `theta`

---

## Model Architecture

- **Shared CNN encoder:** VGG-style blocks with batch normalization and pooling
- **Global average pooling:** for fixed-size feature vectors
- **Two regression heads:** one each for pupil and iris
- **Loss Function:** SmoothL1 (Huber) for robustness to outliers
- **Optimizer:** AdamW with learning rate decay and early stopping

---

## Evaluation Metrics

| Metric                         | Value (%) |
|-------------------------------|-----------|
| Mean % Pupil Diameter Y Error | 24.79     |
| Mean % Iris Diameter Y Error  | 8.93      |
| Mean Pupil IoU                | 63.44     |
| Mean Iris IoU                 | 84.41     |

---

## Visualization

- Green: True pupil center
- Red: Predicted pupil center
- Cyan: True iris center
- Magenta: Predicted iris center

---

## Outputs

- Training loss curve
- Learning rate schedule
- Per-task loss tracking
- Evaluation metric histograms
- Saved model: `best_eye_model_full.pth`
- Evaluation CSV: `evaluation_metrics.csv`

---

## Run Training

```bash
# Inside EyeNetModel.ipynb
# or script-based version:
python train_eyenet.py
