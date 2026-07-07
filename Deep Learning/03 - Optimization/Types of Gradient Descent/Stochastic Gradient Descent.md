---
tags:
  - deep-learning
  - algorithm
chapter: 3
---
SGD computes the gradient and applies a parameter update for **each individual training example** rather than averaging over the whole dataset.

### Algorithm

**Require:** Learning rate $\eta$, initial parameters $\mathbf{w}$

1. **while** stopping criteria not met **do**
2. $\quad$ Sample a random training example $(\mathbf{x}^{(i)}, y^{(i)})$
3. $\quad$ Compute gradient: $\hat{\mathbf{g}} \leftarrow \nabla_\mathbf{w} L(f(\mathbf{x}^{(i)}, \mathbf{w}), y^{(i)})$
4. $\quad$ Update parameters: $\mathbf{w} \leftarrow \mathbf{w} - \eta\hat{\mathbf{g}}$
5. **end while**

### Properties

| | |
|---|---|
| **Gradient estimate** | Single example — high variance |
| **Convergence** | Noisy, can fluctuate around the minimum |
| **Cost** | Low per step — very fast iterations |
| **Best for** | Large datasets, frequent parameter updates |

### Comparison with BGD

SGD requires **less computational resources** than [[Batch Gradient Descent|BGD]], but is **more susceptible to fluctuations** due to the variability introduced by individual training examples.
