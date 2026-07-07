---
tags:
  - deep-learning
  - activation-function
chapter: 1
---
![[Pasted image 20260701193301.png|364]]

**Use**: *Default choice* for hidden layers in most feedforward networks — fast and effective.

### Formula

$$\text{ReLU}(z) = \max(0, z)$$

### Pros

- Provides **wide and consistent gradients** when active: no saturation for positive inputs, which greatly accelerates gradient descent.
- The **non-positive clipping** acts as an implicit regularizer, accelerating convergence and enabling faster learning.
- Limitation in differentiability at $z = 0$ is negligible in practice (the one-sided derivative is returned).
- Good practice: **initialize biases with small positive values** to ensure units are initially active and gradients can propagate.

### Cons

- Outputs are **not centered on zero**, which can cause issues in some learning contexts.
- **Dying ReLU**: when most inputs are in the negative range, a ReLU neuron outputs 0 and receives no gradient — the weight stops updating entirely.
- **Sensitive to large learning rates**: if the learning rate is too high, weights can shift into the highly negative range, deactivating neurons permanently.
