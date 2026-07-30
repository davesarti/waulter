---
tags:
  - deep-learning
  - normalization
chapter: 3
---

## Group Normalization (GN)

Group Normalization is a more modern technique that sits between [[Layer Normalization]] and [[Instance Normalization]]. The $C$ channels are divided into $G$ groups of size $C/G$, and normalization statistics are computed independently within each group, per example — without any dependency on the batch.

This makes GN particularly useful when the dimensionality of the data is high and normalizing entire layers would be excessive, yet the batch size is too small for Batch Normalization to be stable.

### Normalization

For example $n$, group $g$ spanning channels $\{c : \lfloor cG/C \rfloor = g\}$:

$$\mu_{n,g} = \frac{1}{(C/G) \cdot H \cdot W} \sum_{c \in g,\,h,w} x_{n,c,h,w}$$

$$\sigma_{n,g} = \sqrt{\delta + \frac{1}{(C/G) \cdot H \cdot W} \sum_{c \in g,\,h,w} (x_{n,c,h,w} - \mu_{n,g})^2}$$

$$\hat{x}_{n,c} = \frac{x_{n,c} - \mu_{n,g(c)}}{\sigma_{n,g(c)}}, \qquad \text{Output} = \gamma\hat{x} + \beta$$

> **Special cases:** $G = 1$ recovers Layer Normalization; $G = C$ recovers Instance Normalization.

### Properties

| | |
|---|---|
| **Normalizes over** | $(C/G) \times H \times W$ per group per example |
| **Batch-size dependent** | No |
| **Learnable parameters** | $\gamma$ (scale), $\beta$ (bias) per channel |
| **Typical use** | Object detection, segmentation (small-batch scenarios) |
