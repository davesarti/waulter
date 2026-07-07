---
tags:
  - deep-learning
  - normalization
chapter: 3
---
![[Pasted image 20260703175834.png|364]]

Batch Normalization is a method for reconfiguring the parameters of a deep network that can be **applied to the input layer as well as to any hidden layer**. The key idea is to standardize the inputs of each layer by subtracting the batch mean and dividing by the batch standard deviation, computed per feature across all examples in the mini-batch.

### Normalization

Let $\mathbf{H}$ represent the outputs of a layer, with $\mu$ and $\sigma$ computed across the $m$ examples in the batch for each feature:

$$\mu = \frac{1}{m} \sum_j \mathbf{H}_{:,j}$$

$$\sigma = \sqrt{\delta + \frac{1}{m} \sum_j (\mathbf{H} - \mu)_j^2}$$

The normalized output is:

$$\mathbf{H}' = \frac{\mathbf{H} - \mu}{\sigma}$$

To preserve the expressive power of the network, two learnable parameters are introduced — a **scaling factor** $\gamma$ and a **bias** $\beta$:

$$\text{Output} = \gamma \mathbf{H}' + \beta$$

> During **testing**, running averages of $\mu$ and $\sigma$ collected during training are used instead of live batch statistics.

### Properties

| | |
|---|---|
| **Normalizes over** | Batch dimension $N$ — across all examples, per channel |
| **Batch-size dependent** | Yes — unstable with very small batches |
| **Learnable parameters** | $\gamma$ (scale), $\beta$ (bias) per feature |
| **Typical use** | CNNs, applied between conv/linear layer and activation |
| **Addresses** | Internal covariate shift |
