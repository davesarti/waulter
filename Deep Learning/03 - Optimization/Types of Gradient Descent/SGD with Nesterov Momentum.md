---
tags:
  - deep-learning
  - algorithm
chapter: 3
---
Nesterov Momentum is a refinement of [[SGD with Momentum]]. The key difference: instead of computing the gradient at the **current position** and then applying momentum, Nesterov first takes a step in the direction of the accumulated velocity, and *then* computes the gradient at that **lookahead position**.

### Algorithm

**Require:** Learning rate $\eta$, momentum parameter $\alpha$, initial parameters $\mathbf{w}$, initial velocity $\mathbf{v}$

1. **while** stopping criteria not met **do**
2. $\quad$ Compute lookahead position: $\tilde{\mathbf{w}} \leftarrow \mathbf{w} + \alpha\mathbf{v}$
3. $\quad$ Sample a random training example $(\mathbf{x}^{(i)}, y^{(i)})$
4. $\quad$ Compute gradient at lookahead: $\hat{\mathbf{g}} \leftarrow \nabla_{\tilde{\mathbf{w}}} L(f(\mathbf{x}^{(i)}, \tilde{\mathbf{w}}), y^{(i)})$
5. $\quad$ Update velocity: $\mathbf{v} \leftarrow \alpha\mathbf{v} - \eta\hat{\mathbf{g}}$
6. $\quad$ Update parameters: $\mathbf{w} \leftarrow \mathbf{w} + \mathbf{v}$
7. **end while**

### Key Difference from Standard Momentum

| | Standard Momentum | Nesterov Momentum |
|---|---|---|
| **Gradient evaluated at** | Current position $\mathbf{w}$ | Lookahead position $\tilde{\mathbf{w}} = \mathbf{w} + \alpha\mathbf{v}$ |
| **Correction timing** | After the momentum step | Within the same update step |

The gradient always points in the optimal direction. The momentum term may not. By evaluating the gradient at the lookahead point, **if momentum overshoots, the gradient can correct it in the same step** — rather than waiting for the next iteration.
