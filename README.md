# Radar Object Classification

Deep-learning-based classification of radar targets using cropped Range-Doppler maps and additional radar features.

## Overview

This project investigates radar-based object classification using:

* Range-Doppler (RD) maps
* Range-compensated radar magnitude
* Doppler/speed
* Range
* Azimuth

A convolutional neural network (CNN) is used to extract features from the Range-Doppler maps. The extracted representation is combined with numerical radar features for final object classification.

## Object Classes

| Label | Class      |
| ----: | ---------- |
|     2 | Pedestrian |
|     3 | Cyclist    |
|     4 | Car        |
|     5 | Truck      |
|    12 | Scooter    |

## Pipeline

```text
Radar measurements
       ↓
Range-Doppler maps
       ↓
Data preprocessing
       ↓
Range compensation
       ↓
Feature normalization
       ↓
CNN feature extraction
       ↓
Feature fusion
       ↓
Object classification
       ↓
Evaluation
```

## Models

The notebook contains implementations using:

* PyTorch
* TensorFlow/Keras

The PyTorch model uses a CNN branch for the Range-Doppler map and combines the learned representation with RCS, speed, range, and azimuth.

## Evaluation

The classification models are evaluated using:

* Validation accuracy
* Training/validation loss
* Confusion matrix
* ROC curves
* AUC
* Permutation-based feature importance

## Dataset

The original radar measurements are not included in this repository because they originate from an internal measurement campaign.

The notebook expects the corresponding radar `.pkl` files to be available locally.

Expected files:

```text
radar_east_ip51.pkl
radar_west_ip52.pkl
radar_videtec_ip53.pkl
```

Place the files in the project directory or update the data path in the notebook.

## Running the Notebook

Create a Python environment and install the required packages:

```bash
pip install -r requirements.txt
```

Then open:

```text
radar_object_classification.ipynb
```

and run the notebook from top to bottom.

## Model Export

The trained PyTorch model can be exported to ONNX for deployment and inference using ONNX Runtime.

## Notes

For a rigorous evaluation, the recommended approach is to split data by measurement run rather than randomly splitting individual radar detections. This reduces the possibility of measurements from the same run appearing in both training and validation sets.
