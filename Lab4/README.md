# Deep Learning Lab Assignment: Object Detection


* Name:       Shivang Desai
* Student ID: 202511034

---

## Assignment Overview

This assignment focuses on understanding and implementing various object detection techniques, ranging from traditional region-based methods (R-CNN family) to modern real-time detectors (YOLO). Each task demonstrates both conceptual understanding and practical implementation.

---

## Dataset

* Dataset: Fruit Images Dataset
* Classes: Apple, Banana, Orange (including mixed images during training)
* Annotation Format: Pascal VOC (XML)
* Converted Format: YOLO (normalized bounding boxes)

---

## Task-wise Implementation and Results

### Task 1: Intersection over Union (IoU)

* Implemented IoU function from scratch.
* Verified using three cases:

  * High overlap → IoU close to 1
  * Partial overlap → moderate IoU
  * No overlap → IoU = 0

---

### Task 2: Selective Search (R-CNN Step 1)

* Generated region proposals using OpenCV Selective Search.
* Extracted top 200 proposals.
* Observed large number of overlapping candidate regions.

---

### Task 3: R-CNN Bottleneck

* Used ResNet18 to extract features from 100 region proposals.
* Each region processed independently.

**Result:**

* Total execution time: 0.3727 seconds
* Average time per region: 0.003727 seconds

---

### Task 4: Fast R-CNN (RoI Pooling)

* Performed a single forward pass on the entire image.
* Applied RoI pooling for region feature extraction.

**Result:**

* Total execution time: 0.0056 seconds

**Observation:**

* Significant speed improvement compared to R-CNN.

---

### Task 5: Faster R-CNN

* Used pre-trained Faster R-CNN model.
* Applied confidence thresholding.
* Visualized final detections.

**Result:**

* Number of detections after filtering: 2

---

### Task 6: Non-Maximum Suppression (NMS)

* Implemented custom NMS using IoU.
* Reduced overlapping bounding boxes.

**Result:**

* Detections before NMS: 2
* Detections after NMS: 2

**Observation:**

* Minimal overlap in predictions, so NMS had no effect.

---

### Task 7: YOLO Fine-Tuning

#### Pre-trained YOLO

* Performed inference using YOLOv8 pre-trained weights.

**Result:**

* Average inference time: ~12.9 ms per image
* Moderate detection accuracy

---

#### Fine-tuned YOLO

* Fine-tuned YOLOv8 on the custom fruit dataset.
* Evaluated using validation set.

**Results:**

* mAP@50: 0.8406
* mAP@50-95: 0.6212
* Precision: 0.713
* Recall: 0.767
* Average inference time: 32.07 ms per image

---

## Model Comparison

| Model                      | Inference Time (ms/image) | Precision        | Recall           |
| -------------------------- | ------------------------- | ---------------- | ---------------- |
| Faster R-CNN (pre-trained) | 4491.15 ms                | High (~0.80+)    | High (~0.80+)    |
| YOLOv8 (pre-trained)       | ~12.9 ms                  | Moderate (~0.60) | Moderate (~0.60) |
| YOLOv8 (fine-tuned)        | 32.07 ms                  | 0.713            | 0.767            |

---

## Key Observations

* R-CNN is computationally expensive due to repeated CNN passes for each region.
* Fast R-CNN significantly improves efficiency by sharing convolutional computation.
* Faster R-CNN integrates region proposal generation within the network.
* YOLO performs detection in a single forward pass, making it much faster.
* Fine-tuning YOLO improves accuracy significantly on domain-specific data.

---

## Conclusion

This assignment demonstrates the evolution of object detection models and highlights the trade-off between accuracy and speed. While Faster R-CNN provides high accuracy, it is computationally expensive. YOLO offers real-time performance, and fine-tuning enhances its accuracy, making it suitable for practical applications.

---



