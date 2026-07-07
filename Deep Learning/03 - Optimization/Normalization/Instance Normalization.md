---
tags:
  - deep-learning
  - normalization
chapter: 3
---
![[Pasted image 20260703180501.png|364]]

Instance Normalization normalizes each **channel of each example independently**, using only the spatial dimensions $H \times W$ to compute statistics. It is the most fine-grained of the sample-based methods — each channel of each image is treated as an isolated unit, completely ignoring both the rest of the batch and the other channels.

### Normalization

For example $n$ and channel $c$:

$$\mu_{n,c} = \frac{1}{H \cdot W} \sum_{h,w} x_{n,c,h,w}$$

$$\sigma_{n,c} = \sqrt{\delta + \frac{1}{H \cdot W} \sum_{h,w} (x_{n,c,h,w} - \mu_{n,c})^2}$$

$$\hat{x}_{n,c} = \frac{x_{n,c} - \mu_{n,c}}{\sigma_{n,c}}, \qquad \text{Output} = \gamma\hat{x} + \beta$$

### Properties

| | |
|---|---|
| **Normalizes over** | Spatial dimensions $(H, W)$ per channel per example |
| **Batch-size dependent** | No |
| **Learnable parameters** | $\gamma$ (scale), $\beta$ (bias) per channel |
| **Typical use** | Style transfer, image generation |
