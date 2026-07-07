---
tags:
  - deep-learning
  - algorithm
chapter: 3
---
All previous methods use a **single global learning rate** $\eta$ for all parameters. This is problematic when features have different levels of importance: some parameters may need large updates, others very small ones.

Adagrad solves this by **adapting the learning rate per parameter**, scaling it by the square root of the sum of all historical squared gradients.

### Algorithm

**Require:** Learning rate $\eta$, initial parameters $\mathbf{w}$, small constant $\delta$ (avoids division by zero)

1. Initialize accumulated squared gradients: $\mathbf{r} \leftarrow \mathbf{0}$
2. **while** stopping criteria not met **do**
3. $\quad$ Sample a random training example $(\mathbf{x}^{(i)}, y^{(i)})$
4. $\quad$ Compute gradient: $\hat{\mathbf{g}} \leftarrow \nabla_\mathbf{w} L(f(\mathbf{x}^{(i)}, \mathbf{w}), y^{(i)})$
5. $\quad$ Accumulate: $\mathbf{r} \leftarrow \mathbf{r} + \hat{\mathbf{g}} \odot \hat{\mathbf{g}}$
6. $\quad$ Update parameters: $\mathbf{w} \leftarrow \mathbf{w} - \dfrac{\eta}{\delta + \sqrt{\mathbf{r}}} \odot \hat{\mathbf{g}}$
7. **end while**

> $\odot$ denotes element-wise multiplication.

### Properties

| | |
|---|---|
| **Adapts** | Learning rate individually per parameter |
| **Accumulator** | $\mathbf{r}$ — running sum of squared past gradients |
| **Advantage** | Larger updates for rare/important features |
| **Limitation** | Learning rate decreases monotonically → may stall |

### Intuition

- Parameters with **large past gradients** → $\mathbf{r}$ is large → effective learning rate is **reduced**.
- Parameters with **small past gradients** → $\mathbf{r}$ stays small → effective learning rate remains **high**.

This allows for more stable convergence when dimensions of the optimisation surface have very different curvatures.

### Limitation

$\mathbf{r}$ only ever grows — the learning rate **decreases monotonically** and can become vanishingly small before convergence. This is addressed by [[RMSProp]].
