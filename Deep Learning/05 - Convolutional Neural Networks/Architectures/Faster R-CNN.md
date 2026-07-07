---
tags:
  - deep-learning
  - architecture
year: 2015
task: object-detection
---
![[Pasted image 20260704185719.png]]
![[Pasted image 20260705180642.png]]
**Faster R-CNN** eliminates Selective Search entirely by replacing it with a learned **Region Proposal Network (RPN)** that runs on the same convolutional feature map as the detector — making region proposals essentially free.

## Key Features

- **Region Proposal Network (RPN)**: a small network that slides over the feature map and predicts region proposals directly — the network *learns* to propose regions
- **RoI Pooling**: proposed regions are reshaped and passed to the classification + regression head (same as Fast R-CNN)
- **End-to-end architecture**: the entire model (backbone + RPN + head) is trained in a single step
