---
tags:
  - deep-learning
  - algorithm
chapter: 3
---
SGD with Momentum addresses two failure modes of plain [[Stochastic Gradient Descent|SGD]]:
- **Flat regions** → updates are tiny, progress is very slow.
- **Steep regions** → updates fluctuate wildly.

The solution is to introduce a **velocity** variable $\mathbf{v}$, which accumulates an exponentially decaying moving average of past gradients. It acts as an inertia term: the optimizer builds up speed in consistent directions and dampens oscillations in others.

### Algorithm

**Require:** Learning rate $\eta$, momentum parameter $\alpha$, initial parameters $\mathbf{w}$, initial velocity $\mathbf{v}$

1. **while** stopping criteria not met **do**
2. $\quad$ Sample a random training example $(\mathbf{x}^{(i)}, y^{(i)})$
3. $\quad$ Compute gradient: $\hat{\mathbf{g}} \leftarrow \nabla_\mathbf{w} L(f(\mathbf{x}^{(i)}, \mathbf{w}), y^{(i)})$
4. $\quad$ Update velocity: $\mathbf{v} \leftarrow \alpha\mathbf{v} - \eta\hat{\mathbf{g}}$
5. $\quad$ Update parameters: $\mathbf{w} \leftarrow \mathbf{w} + \mathbf{v}$
6. **end while**

### Properties

| | |
|---|---|
| **Addresses** | Flat regions (slow progress) + steep regions (oscillations) |
| **Key parameter** | $\alpha$ — controls how much past velocity is retained |
| **Convergence** | Faster than plain SGD |
| **Risk** | Can overshoot near the minimum due to inertia |

### Role of $\alpha$

$\alpha$ controls **how much of the previous velocity is retained**. If $\alpha > \eta$, the update is dominated by accumulated past gradients → stronger inertia, better at avoiding local minima and navigating flat regions.

### Trade-off

Momentum can **overshoot** the minimum due to the inertia effect. However, it reaches the minimum much **faster than plain SGD**, making it a strong default choice.

> See [[SGD with Nesterov Momentum|Nesterov Momentum]] for a corrected variant that looks ahead before computing the gradient.
