---
tags:
  - deep-learning
  - loss-function
chapter: 1
---
**Task**: Regression — predicting a continuous output $y \in \mathbb{R}$.

### Formula

$$\mathcal{L}_{\delta}(\theta) = \frac{1}{N} \sum_{i=1}^{N} \begin{cases} \dfrac{1}{2}(y_i - \hat{y}_i)^2 & \text{if } |y_i - \hat{y}_i| \leq \delta \\[6pt] \delta\!\left(|y_i - \hat{y}_i| - \dfrac{1}{2}\delta\right) & \text{otherwise} \end{cases}$$

where $\delta$ is a **hyperparameter controlling the transition between the quadratic and linear regions** of the loss.

### Intuition

Huber Loss combines the best features of [[MSE Loss]] and [[Mean Absolute Error Loss]]:

- **Small errors** ($|y_i - \hat{y}_i| \leq \delta$): behaves like MSE.
- **Large errors**: behaves like MAE.

This avoids problems such as **overfitting** and the **steep slope of the MSE curve** for large residuals.
