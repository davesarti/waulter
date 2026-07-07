---
tags:
  - deep-learning
  - algorithm
chapter: 3
---
Adam combines the ideas of [[SGD with Momentum|Momentum]] and [[RMSProp]] and adds a crucial innovation: **bias correction** for both the first and second moment estimates. This correction is necessary because both moments are initialised at zero and need time to "warm up" — without it, early updates are systematically biased towards zero.

### Algorithm

**Require:** Learning rate $\eta$, decay rates $\rho_1, \rho_2$, small constant $\delta$, initial parameters $\mathbf{w}$

1. Initialize first and second moments: $\mathbf{s} \leftarrow \mathbf{0}$, $\mathbf{r} \leftarrow \mathbf{0}$
2. Initialize time step: $t \leftarrow 0$
3. **while** stopping criteria not met **do**
4. $\quad$ Sample a random training example $(\mathbf{x}^{(i)}, y^{(i)})$
5. $\quad$ Compute gradient: $\hat{\mathbf{g}} \leftarrow \nabla_\mathbf{w} L(f(\mathbf{x}^{(i)}, \mathbf{w}), y^{(i)})$
6. $\quad$ Increment time step: $t \leftarrow t + 1$
7. $\quad$ Update biased first moment (Momentum): $\mathbf{s} \leftarrow \rho_1 \mathbf{s} + (1 - \rho_1)\hat{\mathbf{g}}$
8. $\quad$ Update biased second moment (RMSProp): $\mathbf{r} \leftarrow \rho_2 \mathbf{r} + (1 - \rho_2)\,\hat{\mathbf{g}} \odot \hat{\mathbf{g}}$
9. $\quad$ Correct bias in first moment: $\hat{\mathbf{s}} \leftarrow \dfrac{\mathbf{s}}{1 - \rho_1^t}$
10. $\quad$ Correct bias in second moment: $\hat{\mathbf{r}} \leftarrow \dfrac{\mathbf{r}}{1 - \rho_2^t}$
11. $\quad$ Update parameters: $\mathbf{w} \leftarrow \mathbf{w} - \eta\,\dfrac{\hat{\mathbf{s}}}{\delta + \sqrt{\hat{\mathbf{r}}}}$
12. **end while**

### What Adam Combines

| Concept | Source | Role in Adam |
|---|---|---|
| Stochastic sampling | [[Stochastic Gradient Descent\|SGD]] | Gradient estimated on one example per step |
| Momentum | [[SGD with Momentum\|SGD + Momentum]] | $\mathbf{s}$: exponential average of gradients (first moment) |
| Adaptive learning rate | [[RMSProp]] | $\mathbf{r}$: exponential average of squared gradients (second moment) |
| Bias correction | Adam (novel) | $\hat{\mathbf{s}}, \hat{\mathbf{r}}$: corrects the zero-initialisation bias |

### Bias Correction Intuition

At early steps, $\rho_1^t$ and $\rho_2^t$ are close to 1, so $1 - \rho_1^t$ and $1 - \rho_2^t$ are small. Dividing by them **amplifies** the moment estimates to compensate for the fact that they haven't fully "warmed up" yet. As $t$ grows, the correction becomes negligible and the moments reflect the true running averages.
