---
tags:
  - deep-learning
  - architecture
year: 2015
task: classification
aliases:
  - Residual Network
  - DenseNet
  - SENet
---
![[Pasted image 20260704180116.png]]
![[Pasted image 20260705172128.png]]
**ResNet** addressed a surprising problem: simply making networks deeper does not always improve performance — at some depth, **performance degrades** (not just due to overfitting, but even on training data). ResNet solved this with **residual (skip) connections**.

## Key Features

- **Identity layers / skip connections**: allow the model to learn to bypass certain layers when they are not needed
- Uses **many small 3×3 kernels** → reduces parameters (2M) and improves computational efficiency
- Skip connections make the **loss landscape much more uniform** → easier to optimise
- ResNet can be seen as an **implicit ensemble of shallower networks**: unrolling a residual block reveals multiple paths through the network

---

## DenseNet

An evolution of ResNet where **each layer is directly connected to all other layers** in the block (not just the previous one).

**Advantages:**
- **Feature reuse**: each layer receives input from all previous layers → efficient reuse of information
- **Parameter reduction**: less need to learn features from scratch → better overall efficiency

## SENet (Squeeze-and-Excitation Network)

Improves ResNet by adding **SE blocks** that **adaptively recalibrate features based on channel importance**
**Mechanism:**
1. *Squeeze*: global average pooling → single value per channel
2. *Excitation*: sigmoid-activated FC layers → weight per channel
3. *Recalibration*: multiply feature maps by learned weights

**Advantages:**
- **Feature recalibration**: focuses on the most relevant channels
- **Performance improvement**: improved accuracy while reducing the number of parameters needed
