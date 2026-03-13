
## Student Information

**Name:** SHIVANG DESAI

**Student ID:** 202511034

**Course:** IT549 – Deep Learning

**Assignment:** Lab 3

---
# Image-Based AQI Classification using CNN and Transfer Learning


# Lab Overview

This project implements an **image-based Air Quality Index (AQI) classification system** using deep learning techniques. The objective is to predict the **AQI_Class** of a location using environmental images.

Two models were implemented and compared:

1. **Basic Convolutional Neural Network (CNN)** trained from scratch
2. **Pretrained CNN using Transfer Learning (ResNet50)**

The project demonstrates a complete deep learning pipeline including:

* Data preprocessing
* Model training
* Model evaluation
* Performance comparison
* Misclassification analysis

---

# Dataset

The dataset consists of:

* **data.csv** – contains image file names and pollution-related information
* **sampled_images/** – image dataset

Only the following columns were used:

| Column    | Purpose                     |
| --------- | --------------------------- |
| Filename  | Input image                 |
| AQI_Class | Target classification label |

Other pollution measurements were not used for training.

---

# Data Preprocessing

The following preprocessing steps were performed:

* Images resized to **224 × 224**
* Pixel normalization using ImageNet statistics
* Label encoding for AQI classes
* Dataset split into:

| Split      | Percentage |
| ---------- | ---------- |
| Training   | 70%        |
| Validation | 15%        |
| Test       | 15%        |

---

# Model 1: Basic CNN

A Convolutional Neural Network was implemented from scratch.

### Architecture

Conv → ReLU → MaxPool
Conv → ReLU → MaxPool
Conv → ReLU → MaxPool
Fully Connected Layer
Dropout
Output Layer

### Training Settings

| Parameter     | Value            |
| ------------- | ---------------- |
| Epochs        | 5                |
| Optimizer     | Adam             |
| Loss Function | CrossEntropyLoss |
| Batch Size    | 32               |

---

# Model 2: Pretrained CNN (Transfer Learning)

A **ResNet50 pretrained on ImageNet** was used.

### Transfer Learning Strategy

* First **10 layers were frozen**
* Final classification layer replaced to match AQI classes
* Remaining layers fine-tuned

### Training Settings

| Parameter     | Value            |
| ------------- | ---------------- |
| Epochs        | 5                |
| Optimizer     | Adam             |
| Loss Function | CrossEntropyLoss |

---

# Model Evaluation

Both models were evaluated on the **test dataset** using:

* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix

### Performance Comparison

| Model             | Accuracy | Precision | Recall   | F1 Score |
| ----------------- | -------- | --------- | -------- | -------- |
| Basic CNN         | 0.815555 | 0.822432  | 0.815555 | 0.814150 |
| Pretrained ResNet | 0.801111 | 0.811128  | 0.801111 | 0.800259 |

The pretrained model generally performs better due to its ability to leverage **features learned from large-scale datasets like ImageNet**.
But here Basic CNN performed better.
The Basic CNN achieved slightly better performance than the pretrained ResNet model across all evaluation metrics. The CNN obtained an accuracy of 81.56%, whereas the pretrained ResNet achieved 80.11%.

The precision, recall, and F1-score values also show a similar pattern, with the CNN consistently performing slightly better. This indicates that the CNN model was able to learn discriminative features for AQI classification effectively from the dataset.

Possible Reasons for CNN Performing Better

Although pretrained models often outperform models trained from scratch, in this case the Basic CNN performed better. Possible reasons include:

Dataset characteristics
The dataset may contain features that are relatively simple for a custom CNN to learn, making transfer learning less advantageous.

Limited fine-tuning of the pretrained model
Only a small portion of the pretrained network was trained (with the first layers frozen), which may have limited its ability to adapt fully to the AQI classification task.

Small training duration
Both models were trained for only 5 epochs, which may not be sufficient for the pretrained model to properly adjust its weights to the dataset.

Domain difference from ImageNet
ResNet was originally trained on ImageNet objects, while this dataset focuses on environmental scenes related to air quality. Because of this domain difference, the pretrained features may not perfectly match the task.
Also i have only trained for 5 epoch and have freezed 10 layers in ResNET . This may also add to lower performance.
---

# Training Curves

Training and validation curves were plotted for:

* Loss vs Epoch
* Accuracy vs Epoch

These curves help visualize:

* Model convergence
* Overfitting or underfitting behavior

---

# Misclassification Analysis

Several misclassified images from the test dataset were analyzed.

Each image was visualized with:

* Predicted AQI class
* Actual AQI class

### Possible Reasons for Misclassification

1. Visual similarity between AQI classes
2. Variations in lighting and environmental conditions
3. Limited dataset size for some categories
4. Presence of background objects
5. Variations in image quality

---



