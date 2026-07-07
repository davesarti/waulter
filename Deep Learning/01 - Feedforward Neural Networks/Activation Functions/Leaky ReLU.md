---
tags:
  - deep-learning
  - activation-function
chapter: 1
---
![[Pasted image 20260701193852.png|364]]

**Use**: Drop-in replacement for [[ReLU]] when dying neurons are a concern — maintains a small gradient for negative inputs.

### Formula

**Generalized form:**

$$h(z, \alpha_i) = \max(0, z_i) + \alpha_i \min(0, z_i)$$

**Leaky ReLU** sets $\alpha_i$ to a small fixed constant (e.g. $0.01$):

$$\text{LeakyReLU}(z) = \max(\alpha \cdot z,\ z)$$

### Pros

- Solves the **dying ReLU** problem by ensuring a non-zero gradient even when $z < 0$.
- Preserves all advantages of [[ReLU]] for positive inputs.

### Cons

- Generalized ReLUs are **not universally better** than standard [[ReLU]] and may introduce additional computational complexity.
- The optimal value of $\alpha$ is problem-dependent.
