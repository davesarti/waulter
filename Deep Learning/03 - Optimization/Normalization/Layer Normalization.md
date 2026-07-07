---
tags:
  - deep-learning
  - normalization
chapter: 3
---

![[Pasted image 20260703180105.png|364]]

Layer Normalization normalizes **each example independently**, computing statistics across all its features ($C \times H \times W$). It does not depend on batch statistics and is completely unaffected by the other samples in the batch, making it suitable for any batch size.

### Normalization

For a single example $x$ with features spanning $C \times H \times W$:

$$\mu_x = \frac{1}{C \cdot H \cdot W} \sum_{c,h,w} x_{c,h,w}$$

$$\sigma_x = \sqrt{\delta + \frac{1}{C \cdot H \cdot W} \sum_{c,h,w} (x_{c,h,w} - \mu_x)^2}$$

$$\hat{x} = \frac{x - \mu_x}{\sigma_x}, \qquad \text{Output} = \gamma\hat{x} + \beta$$

### Properties

| | |
|---|---|
| **Normalizes over** | All features $(C, H, W)$ per example — ignores batch |
| **Batch-size dependent** | No — works with batch size 1 |
| **Learnable parameters** | $\gamma$ (scale), $\beta$ (bias) per feature |
| **Typical use** | Transformers, RNNs |
