---
tags:
  - deep-learning
  - loss-function
chapter: 1
---
**Task**: Regression — predicting a continuous output $y \in \mathbb{R}$.

### Formula

$$\mathcal{L}_{\text{MAE}}(\theta) = \frac{1}{N} \sum_{i=1}^{N} \left| y_i - \hat{y}_i \right|$$

**Robust to outliers** — linear penalty vs. quadratic in MSE

> [!warning] Non-smooth gradient
> MAE's gradient is constant ($\pm 1$) regardless of the error magnitude — it never "slows down" near the solution. This can cause instability close to the optimum and makes it harder to use with standard gradient descent.
