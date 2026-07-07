---
tags:
  - deep-learning
  - architecture
year: 2013
task: classification
aliases:
  - ILSVRC 2013
  - Zeiler and Fergus Net
---
![[Pasted image 20260704173313.png]]
![[Pasted image 20260705161125.png]]
Similar structure to [[AlexNet]] (5 conv layers + 2 FC layers with 4096 units each) but with significant innovations aimed at **understanding what CNNs learn**.

## Key Features

- Use of **smaller kernels** in the first convolutional layers (11×11 → 7×7)
- Different number of channels (for visualisation purposes)
- Introduced **explicability of CNNs through deconvolutional networks**

## Deconvolutional Networks

To understand what happens inside a CNN, Zeiler & Fergus introduced **DeconvNets**: a probe that maps activations from any layer back to pixel space by reversing the convolution process (run in reverse, no learning needed).

**Process**:
1. Connect a DeconvNet to a chosen CNN layer
2. Pass input image through the CNN → get activations
3. Map activations back to pixel space via: **Unpooling → Rectification → Filtering**

> *Unpooling* uses **switch variables** to track the original positions of maxima (since max pooling is not invertible).

The result is a visualisation showing **which input patterns activated a given filter** — revealing what the network found discriminative.

### Additional Visualisation Techniques

- **Occlusion experiments**: occlude parts of the image at various positions and observe changes in feature activations / classifier confidence
- **Class Model Visualisation**: instead of adjusting weights, find the **image that maximises the score for a specific label**
- **Grad-CAM** uses gradients of the classification score w.r.t. the final convolutional feature map to **evidence which regions most influence the prediction**