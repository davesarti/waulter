---
tags:
  - deep-learning
  - activation-function
chapter: 1
---
![[Pasted image 20260701192632.png|364]]

**Use**: Hidden layers where zero-centered activations are desirable; similar to [[Sigmoid]] but with a wider output range.

### Formula

$$\tanh z = \frac{e^z - e^{-z}}{e^z + e^{-z}}$$

### Pros

- **Differentiable and continuous**, compatible with gradient-based optimization.
- Output range $[-1, 1]$ ensures activations are **zero-centered**, which can improve the model's ability to learn from data distributions compared to [[Sigmoid]].

### Cons

- Like [[Sigmoid]], **tends to saturate** throughout much of its domain — gradients become very small for large $|z|$, hindering backpropagation and potentially causing slower convergence.
