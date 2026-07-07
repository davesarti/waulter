---
tags:
  - deep-learning
  - architecture
year: 2014
task: object-detection
---
![[Pasted image 20260704185132.png]]

**R-CNN** was the **first CNN-based approach for object detection**. Conceptually: Selective Search + AlexNet applied to each proposed region.

## Pipeline

1. Input image
2. **Selective Search** → ~2,000 region proposals per image
3. Each region is **warped** to a fixed size and passed through **AlexNet individually**
4. AlexNet extracts features → a classifier determines the class of each region

## Key Features

- Uses **proposed regions** to identify candidate object locations
- Applies a CNN to **extract features and classify objects within each region**
- Demonstrated significantly better performance than shallow models

## Limitations

- **Multi-stage pipeline** — training and inference are fragmented across separate steps
- **Selective Search is fixed** — does not adapt to the network or data
- Images must be resized before passing through the network
- **Very slow**: requires ~2,000 forward passes per image during testing; training and testing are both extremely time-consuming