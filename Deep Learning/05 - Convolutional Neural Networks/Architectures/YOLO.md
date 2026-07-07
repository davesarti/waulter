---
tags:
  - deep-learning
  - architecture
year: 2016
task: object-detection
---
![[Pasted image 20260704190739.png|500]]

**YOLO** is an innovative approach to object detection that stands out for its **speed and efficiency**. Unlike region-proposal approaches (R-CNN family), YOLO frames detection as a **direct regression problem** on a grid.

## Key Features

- **Single convolutional network**: one forward pass predicts all bounding boxes and class probabilities simultaneously — much faster than two-stage detectors
- **Grid-based approach**: the image is divided into an S×S grid; each cell predicts bounding boxes and class probabilities for objects whose centre falls in that cell
- **Direct regression**: no separate region proposal step — bounding boxes and class scores are predicted end-to-end
- **Multi-part loss:** the loss directly corresponds to different aspects of detection performance
$$\mathcal{L} = \mathcal{L}_{\text{localization}} + \mathcal{L}_{\text{confidence}} + \mathcal{L}_{\text{classification}}$$
## Bounding Box Selection

For each predicted bounding box, YOLO outputs:
- A **class probability** map
- **Offset values** for the bounding box coordinates
- Boxes with class probability above a threshold are selected as final detections

## Limitations

- You must **choose the right number of grid splits** (S×S)
- Struggles with **small or overlapping objects** (each cell predicts a fixed number of boxes)

## Trade-off

YOLO is significantly faster than Faster R-CNN but may sacrifice some accuracy, especially on small objects. Later versions (YOLOv2, v3, ...) addressed these limitations.