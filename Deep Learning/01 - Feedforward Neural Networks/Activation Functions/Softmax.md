---
tags:
  - deep-learning
  - activation-function
chapter: 1
---
![[Pasted image 20260702105035.png|364]]

### Formula

$$\text{Softmax}(z_i) = \frac{e^{z_i}}{\sum_j e^{z_j}}$$

where $z_i$ is the non-normalized score (logit) for class $i$, and $\sum_j e^{z_j}$ is the sum of the exponents of all logits.

### Properties

- **Produces valid probabilities** — outputs are non-negative and sum to 1.
- **Naturally handles multiclass problems** — provides a full probability distribution over all classes.
- **Differentiable and smooth** — suitable for gradient-based optimization like backpropagation.
- **Emphasizes largest scores** — amplifies logit differences, highlighting the most likely class.
- **Compatible with cross-entropy loss** — leads to stable, efficient training.
- **Interpretable output** — values directly represent predicted class probabilities.

### Log Softmax

Log Softmax is a variant used to **improve numerical stability** when computing probabilities:

$$\log \text{Softmax}(z_i) = z_i - \log\!\left(\sum_j e^{z_j}\right)$$
