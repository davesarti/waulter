---
tags:
  - deep-learning
  - architecture
year: 2017
task: instance-segmentation
---
![[Pasted image 20260704192447.png]]

**Mask R-CNN** extends [[Faster R-CNN]] for [[05.6 - Instance Segmentation|instance segmentation]]: it adds a third output branch to the network that predicts a binary segmentation mask for each detected object, on top of the existing classification and bounding box regression heads.

## Key Features

- **RoI Align**: an improved version of RoI Pooling that uses **bilinear interpolation** ensuring more precise alignment of feature maps with the original image regions, significantly improving mask quality
- **Pixel-level segmentation**: assigns a label to each pixel of the image based on the object instance it belongs to
- **FCN (Fully Convolutional Network) branch**: added on top of the selected features to produce accurate, detailed segmentation masks
- Jointly trained for: classification + bounding box regression + mask prediction
