---
tags:
  - deep-learning
  - architecture
year: 2014
task: classification
---
![[Pasted image 20260704173559.png]]
![[Pasted image 20260705163717.png]]
**VGGNet** extends AlexNet with significantly increased depth. It was the last architecture built on the AlexNet-style paradigm (conv + pooling + FC head)

## Key Features

- Very deep architecture with **more than twice the parameters of AlexNet**
- Maintains the sequence: convolutions → subsampling → fully connected
- One of the first architectures to demonstrate that **network depth is a critical factor for performance**
- Uses only 3×3 convolutional filters stacked — small filters achieve the same receptive field as larger ones with fewer parameters and more non-linearities

## Limitation

The exponential growth in parameters (due to the large FC layers) makes VGGNet expensive to store and run.