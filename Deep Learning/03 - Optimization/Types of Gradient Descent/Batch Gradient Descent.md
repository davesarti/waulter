---
tags:
  - deep-learning
  - algorithm
chapter: 3
---


Batch Gradient Descent is one of the most widely used methods for parameter optimisation in neural networks. At every iteration it computes the gradient using the **entire training dataset** before taking a single update step.

### Algorithm

**Require:** Learning rate $\eta$, initial parameters $\mathbf{w}$

1. **while** stopping criteria not met **do**
2. $\quad$ Compute gradient over all $N$ training examples $\{(\mathbf{x}^{(1)}, y^{(1)}), \ldots, (\mathbf{x}^{(N)}, y^{(N)})\}$:
$$\hat{\mathbf{g}} \leftarrow \frac{1}{N} \nabla_\mathbf{w} \sum_{i=1}^{N} L(f(\mathbf{x}^{(i)}, \mathbf{w}), y^{(i)})$$
3. $\quad$ Update parameters: $\mathbf{w} \leftarrow \mathbf{w} - \eta\hat{\mathbf{g}}$
4. **end while**

### Properties

|                       |                                                |
| --------------------- | ---------------------------------------------- |
| **Gradient estimate** | Full dataset average — low variance            |
| **Convergence**       | Stable and accurate                            |
| **Cost**              | High — requires a full pass over data per step |
| **Parallelism**       | Limited by dataset size                        |

> $\eta$ is the **learning rate**: it controls the step size taken when updating parameters.
