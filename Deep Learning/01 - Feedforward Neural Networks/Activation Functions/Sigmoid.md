---
tags:
  - deep-learning
  - activation-function
chapter: 1
---
![[Pasted image 20260701190401.png|364|center|375]]

**Use**: Binary classification — output can be interpreted as a probability $\hat{y} \in (0, 1)$.
### Formula

$$\sigma(z) = \frac{1}{1 + e^{-z}}$$

### Pros

- Acts as a **squashing non-linearity**, compressing outputs into $[0, 1]$ — ideal when the model must produce probabilities.
- **Differentiable and smooth** over its entire domain, enabling stable integration with gradient-based optimization.

### Cons

- **Tends to saturate** in most of its domain: gradients approach zero for large $|z|$, obstructing effective backpropagation.
- **Sensitivity decreases** for both large and small inputs — the function is only strongly sensitive near zero.
