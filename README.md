# Radar Object Classification

Deep-learning-based classification of radar targets using cropped Range-Doppler maps and additional radar features.
## Project Context

This work was developed as part of the **VIDETEC-2** research project
("Increased Traffic Safety via Intelligent Detection Technologies").

VIDETEC-2 investigated intelligent infrastructure-based sensing technologies
for improving traffic safety at urban intersections. The project focused on
the detection, localization, classification, and movement prediction of road
users, with particular emphasis on vulnerable road users such as pedestrians
and cyclists. The project combined infrastructure-mounted micro-Doppler radar
sensors with Communication, Localization and Surveillance (CLS) technologies
to collect traffic data from real-world intersection scenarios.

This repository contains a machine-learning pipeline developed using radar
measurements collected within the VIDETEC-2 project. The work focuses on
radar-based road-user classification using range-Doppler maps together with
additional radar-derived features such as range, speed, azimuth, and
range-compensated signal strength.

The radar data used in this work were collected using stationary radar
sensors installed as part of the VIDETEC-2 measurement infrastructure. The
resulting dataset contains measurements of different road-user classes,
including pedestrians, cyclists, cars, scooters, and trucks.

The project was a collaboration involving IMST GmbH, DLR, CGF AG, TU Munich,
and Dortmund University of Applied Sciences and Arts (FH Dortmund). The
VIDETEC-2 project ran from January 2023 to December 2025.

For more information about the project and the publicly available datasets,
see the [official VIDETEC-2 project website](https://www.videtec-projekt.de/)

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

The original radar measurements are  included in this repository and they originate from an internal measurement campaign (Videtec2 Project).

The notebook expects the corresponding radar `.pkl` files to be available locally.

Expected files:

```text
radar_east_ip51.pkl
radar_west_ip52.pkl
radar_videtec_ip53.pkl
```

Place the files in the project directory or update the data path in the notebook.

## Running the Notebook

Create the Conda environment from the included `environment.yml`:

```bash
conda env create -f environment.yml
conda activate radar
```

Then open:

```text
radar_object_classification.ipynb
```

and run the notebook from top to bottom.

## Model Export

The trained PyTorch model can be exported to ONNX for deployment and inference using ONNX Runtime.


