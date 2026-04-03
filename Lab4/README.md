Deep Learning Lab Assignment: Object Detection



* **Name:** Shivang Desai
* **Student ID:** 202511034

---

##  Assignment Overview

This lab explores the evolution of **object detection models**, starting from early region-based approaches to modern real-time detectors. The assignment involves both **conceptual understanding** and **practical implementation** of various models.

---

##  Dataset

* **Dataset Used:** Fruit Images Dataset
* **Classes:** Apple, Banana, Orange (and Mixed in extended setup)
* **Annotations:** Bounding boxes provided in VOC (XML) format
* **Preprocessing:** Converted annotations to YOLO format

---

##  Tasks Implemented

### Task 1: Intersection over Union (IoU)

* Implemented IoU from scratch
* Tested on multiple bounding box pairs

---

### Task 2: Selective Search (R-CNN Step 1)

* Generated region proposals using OpenCV
* Visualized top 200 bounding boxes

---

### Task 3: R-CNN Bottleneck

* Extracted features for 100 region proposals using ResNet18
* Measured execution time

---

### Task 4: Fast R-CNN (RoI Pooling)

* Performed single CNN pass
* Applied RoI pooling
* Compared speed with R-CNN

---

### Task 5: Faster R-CNN

* Used pre-trained Faster R-CNN model
* Applied confidence thresholding
* Visualized detections

---

### Task 6: Non-Maximum Suppression (NMS)

* Implemented custom NMS algorithm
* Reduced overlapping detections

---

### Task 7: YOLO Fine-Tuning

* Fine-tuned YOLOv8 on custom dataset
* Evaluated using mAP metrics
* Compared with pre-trained YOLO and Faster R-CNN

---

## Results Summary

| Model                      | Inference Time (ms/image) | Precision | Recall   |
| -------------------------- | ------------------------- | --------- | -------- |
| Faster R-CNN (pre-trained) | 4491.15 ms                | High      | High     |
| YOLOv8 (pre-trained)       | ~12.9 ms                  | Moderate  | Moderate |
| YOLOv8 (fine-tuned)        | 32.07 ms                  | 0.713     | 0.767    |

* **mAP@50 (YOLO fine-tuned):** 0.841
* **mAP@50-95:** 0.621

---

## Key Observations

* Faster R-CNN provides high accuracy but is computationally expensive.
* YOLO achieves real-time performance due to its single-stage architecture.
* Fine-tuning significantly improves YOLO’s detection accuracy on custom data.

---

## Conclusion

This assignment demonstrates the trade-off between **speed and accuracy** in object detection models. While Faster R-CNN offers strong performance, YOLO provides a practical solution for real-time applications. Fine-tuning further enhances YOLO’s effectiveness on domain-specific datasets.

---



## 📎 Notes

* Results may vary depending on hardware (CPU/GPU).

---
