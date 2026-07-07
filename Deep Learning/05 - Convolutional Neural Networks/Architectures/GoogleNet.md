---
tags:
  - deep-learning
  - architecture
year: 2014
task: classification
aliases:
  - Inception
  - InceptionNet
---
![[Pasted image 20260704174720.png]]
![[Pasted image 20260705170351.png]]
**GoogleNet** represented a paradigm shift: the focus moved from simply making networks wider/deeper to **drastically reducing the number of parameters while increasing depth**. A 22-layer CNN with only **4 million parameters**.

## Key Features

- **No fully connected layers** → dramatically reduces model complexity and overfitting risk
- **Inception modules**: parallel convolutional branches with different kernel sizes (1×1, 3×3, 5×5) that are concatenated → captures features at multiple scales simultaneously
- **1×1 convolutions** to reduce the number of channels before expensive convolutions → improves computational efficiency
- **Intermediate supervision**: auxiliary classifiers at intermediate layers to fight vanishing gradients (deeper networks are more prone to this)
- **[[Batch Normalization]]** introduced: stabilises and speeds up training; allows achieving similar performance in fewer steps