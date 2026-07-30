---
tags:
  - deep-learning
  - chapter
chapter: 4
---
## Sections

- [[04.1 - Model Capacity and Generalization]]
- [[04.2 - Parameter Norm Penalties]]
- [[04.3 - Data Augmentation]]
- [[04.4 - Injecting Noise]]
- [[04.5 - Early Stopping]]
- [[04.6 - Multi-Task Learning]]
- [[04.7 - Parameters Sharing]]
- [[04.8 - Model Ensembles]]
- [[04.9 - Dropout]]

---

## Formulas

### Parameter Norm Penalties

The **[[03.1 - Types of Gradient Descent#Empirical Loss|empirical loss]]** $\hat{L}(\mathbf{W})$ (the average per-example loss over the training set) is augmented with a penalty term $\Omega(\mathbf{W})$ that discourages large weights, giving the general regularized loss:

$$\tilde{L}(\mathbf{W}) = \hat{L}(\mathbf{W}) + \lambda\,\Omega(\mathbf{W})$$

| Method | Penalty $\Omega(\mathbf{W})$ | Effect on weights |
|---|---|---|
| **L2** (Ridge) | $\dfrac{1}{2}\displaystyle\sum_l \|\mathbf{w}_l\|^2$ | Small, non-zero |
| **L1** (Lasso) | $\displaystyle\sum_l \lvert\mathbf{w}_l\rvert$ | Sparse (many → 0) |

### Noise Injection

| Location | Noise model | Downstream effect |
|---|---|---|
| Input $x_i$ | $x_i + \mathcal{N}(0,\,\sigma_i^2)$ | $y_j + \mathcal{N}(0,\,w_i^2\sigma_i^2)$ → equivalent to L2 |
| Weights | $w + \mathcal{N}(0,\,\sigma^2)$ | Smoother learned function |
| Labels | Soft / smoothed targets | Prevents overconfident predictions |

--- 

## Summary

![[Pasted image 20260703191606.png]]