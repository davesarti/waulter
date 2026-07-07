---
tags:
  - deep-learning
  - architecture
year: 2023
task: interactive-image-editing
---
![[Pasted image 20260707214330.png]]

DragGAN allows interactive image editing via drag-and-drop. The user defines pairs of control points and target points, and the model drags the corresponding image regions accordingly, via:

1. **Motion Supervision**: guides control points toward their target points.
2. **Point Tracking**: continuously updates control-point positions as the image changes.

DragGAN shows that, despite newer generative paradigms (diffusion models), [[09.1 - Generative Adversarial Networks (GANs)|GANs]] keep offering practical, interactive editing capabilities.