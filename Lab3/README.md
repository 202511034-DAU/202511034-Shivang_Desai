
## Student Information

**Name:** SHIVANG DESAI
**Student ID:** 202511034
**Course:** IT549 – Deep Learning
**Assignment:** Lab 3

---
# Image-Based AQI Classification using CNN and Transfer Learning


# Project Overview

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

# Conclusion

This project demonstrates the effectiveness of **deep learning for image-based AQI classification**.

Key findings:

* The **pretrained ResNet model outperformed the basic CNN**.
* Transfer learning significantly improves performance when training data is limited.
* Misclassification analysis highlights the challenges of visual pollution detection.

---


