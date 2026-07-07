---
tags:
  - deep-learning
  - architecture
year: 2015
task: object-detection
---
![[Pasted image 20260704185410.png]]
![[Pasted image 20260705180433.png]]
**Fast R-CNN** is an improved version of R-CNN that directly addresses its efficiency bottleneck: instead of running the CNN separately for each region proposal, it runs the CNN **once on the entire image**.

## Key Features

- **Single forward pass**: the CNN (backbone, e.g. VGG) is applied once to the whole image, producing a **shared convolutional feature map**
- **RoI Pooling layer**: for each region proposal, a fixed-size feature vector is extracted from the shared feature map using RoI pooling — avoids redundant computation and makes warping unnecessary
- **End-to-end training**: classification and bounding box regression are trained jointly
