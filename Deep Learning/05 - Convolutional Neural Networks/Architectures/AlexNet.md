---
tags:
  - deep-learning
  - architecture
year: 2012
task: classification
---
![[Pasted image 20260704171842.png]]
![[Pasted image 20260705155530.png]]
**AlexNet** marked the beginning of the **deep learning revolution** and was the first modern CNN architecture. It won the ImageNet Challenge (ILSVRC 2012) by a large margin.

## Key Features

- Similar structure to [[LeNet]] but with a **larger model** (60M parameters) and more data (ImageNet)
- Kernel size smaller in later layers than in early
- Input: 224×224 — higher resolution than LeNet → 7 hidden layers needed
- **First GPU implementation** of a neural network (split across 2 GPUs in parallel)
- First use of **[[ReLU]]** instead of [[Tanh]] as activation function — same performance in less time
- Introduced **[[04.9 - Dropout|dropout]]** for regularisation

## Universal Feature Extractor

Features learned by AlexNet (4096-dimensional representations) can be **reused across different computer vision tasks without retraining** — making it a universal feature extractor.