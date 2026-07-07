---
tags:
  - deep-learning
  - loss-function
chapter: 1
---
**Task**: Regression — predicting a continuous output $y \in \mathbb{R}$.

### Formula

$$\mathcal{L}_{\text{MSE}}(\theta) = \frac{1}{N} \sum_{i=1}^{N} \left( y_i - \hat{y}_i \right)^2$$

Quadratic penalty makes it **sensitive to outliers**