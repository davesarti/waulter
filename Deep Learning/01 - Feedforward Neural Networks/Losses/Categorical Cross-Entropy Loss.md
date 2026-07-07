---
tags:
  - deep-learning
  - loss-function
chapter: 1
---
**Task**: Multi-class classification

### Formula

With one-hot encoded targets $\mathbf{y}_i \in \{0,1\}^N$:

$$\mathcal{L}_{\text{CCE}}(\theta) = -\sum_{i=1}^{N}  y_{i} \log \hat{y}_{i}$$


where $y_i$ is the true probability of class i and $\hat{y_i}$ is the predicted probability of class i