---
tags:
  - deep-learning
  - chapter
chapter: 0
---
## Sections

- [[00.1 - Basic Definitions (AI, ML, DL)]]
- [[00.2 - Artificial Neuron]]
- [[00.3 - Multilayer Perceptron]]
- [[00.4 - Supervised vs Unsupervised vs Reinforcement Learning]]
- [[00.5 - Discriminative vs Generative Models]]

## Formulas

---
### Perceptron (1958)

$$\hat{y} = h(\boldsymbol{\theta}^T \mathbf{x} + \theta_0)$$

**Training rule** — given $\mathcal{T} = \{(\mathbf{x}_i, y_i)\}$, $y_i \in \{0,1\}$, learning rate $0 < \eta < 1$:

$$\boldsymbol{\theta}^{t+1} = \boldsymbol{\theta}^t + \eta\,(\hat{y}_i - y_i)\,\mathbf{x}_i$$
$$\theta_0^{t+1} = \theta_0^t + \eta\,(\hat{y}_i - y_i)$$

No update when $\hat{y}_i = y_i$ (error term vanishes).


---
### Supervised Learning

Training set: $\mathcal{T} = \{(\mathbf{x}_1, y_1), \ldots, (\mathbf{x}_m, y_m)\}$

$$\text{Classification:} \quad f: \mathbb{R}^d \to \{1, 2, \ldots, k\}$$
$$\text{Regression:} \quad f: \mathbb{R}^d \to \mathbb{R}$$

### Unsupervised Learning

Training set (no labels): $\mathcal{T} = \{\mathbf{x}_1, \ldots, \mathbf{x}_m\}$

Dimensionality reduction: $\mathbf{x} \in \mathbb{R}^d \;\longmapsto\; \mathbb{R}^k, \quad k \ll d$

Density estimation: learn $p(\mathbf{x})$

---
### Generative Models

Discriminative models learn $p(y \mid \mathbf{x})$; generative models learn $p(\mathbf{x})$ or $p(\mathbf{x}, y)$.

Latent-space sampling:

$$\mathbf{z} \sim p(\mathbf{z}) \;\xrightarrow{\text{decode}}\; \mathbf{x} \sim \hat{p}(\mathbf{x})$$

Hierarchy: $\text{Unsupervised} \supset \text{Generative Models} \supset \text{Probabilistic Generative Models}$