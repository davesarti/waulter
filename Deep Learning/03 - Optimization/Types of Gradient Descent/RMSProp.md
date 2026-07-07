---
tags:
  - deep-learning
  - algorithm
chapter: 3
---
[[Adagrad]] accumulates squared gradients forever, causing the learning rate to shrink to near-zero — especially problematic in non-convex settings. RMSProp fixes this by replacing the full history with an **exponentially decaying running average** of past squared gradients (similar to the momentum idea: $\alpha v - \epsilon \hat{g}$), also called a *Running Average*.

### Algorithm

**Require:** Learning rate $\eta$, decay rate $\rho$, initial parameters $\mathbf{w}$, small constant $\delta$

1. Initialize running average: $\mathbf{r} \leftarrow \mathbf{0}$
2. **while** stopping criteria not met **do**
3. $\quad$ Sample a random training example $(\mathbf{x}^{(i)}, y^{(i)})$
4. $\quad$ Compute gradient: $\hat{\mathbf{g}} \leftarrow \nabla_\mathbf{w} L(f(\mathbf{x}^{(i)}, \mathbf{w}), y^{(i)})$
5. $\quad$ Update running average: $\mathbf{r} \leftarrow \rho\mathbf{r} + (1 - \rho)\,\hat{\mathbf{g}} \odot \hat{\mathbf{g}}$
6. $\quad$ Update parameters: $\mathbf{w} \leftarrow \mathbf{w} - \dfrac{\eta}{\delta + \sqrt{\mathbf{r}}} \odot \hat{\mathbf{g}}$
7. **end while**

### Key Difference from Adagrad

| | Adagrad | RMSProp |
|---|---|---|
| **History** | Full sum of squared gradients | Exponentially decaying average |
| **Learning rate** | Monotonically decreasing | Can increase if gradients shrink |
| **Non-convex** | Problematic | Handles well |

By discounting older gradients via $\rho$, past history contributes less over time — preventing the learning rate from collapsing.

> There is also a variant that incorporates the [[SGD with Nesterov Momentum|Nesterov Momentum]] term, known as **RMSProp with Nesterov Momentum**.
