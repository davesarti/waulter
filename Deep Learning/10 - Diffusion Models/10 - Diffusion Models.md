---
tags:
  - deep-learning
  - chapter
chapter: 10
---
## Sections

- [[10.1 - Diffusion Model]]
- [[10.2 - Generative Trilemma]]
- [[10.3 - Stochastic Equation and Denoising Score Matching]]
- [[10.4 - DIffusion Model Architecture and Text Conditioning]]
- [[10.5 - Stable Diffusion]]

---

## Formulas

### Forward Process (Diffusion)

$$x_t = \sqrt{\bar{\alpha}_t} \cdot x_0 + \sqrt{1 - \bar{\alpha}_t} \cdot \epsilon, \quad \epsilon \sim \mathcal{N}(0, I)$$

| Symbol | Meaning |
|---|---|
| $x_0$ | Original clean data sample |
| $x_t$ | Noised sample at timestep $t$ |
| $\bar{\alpha}_t = \prod_{s=1}^{t}(1 - \beta_s)$ | Cumulative product of noise schedule |
| $\beta_t$ | Variance added at step $t$ |

### Reverse Process (Denoising) Loss

$$\mathcal{L} = \mathbb{E}_{x_0, t, \epsilon} \left[ \| \epsilon - \epsilon_\theta(x_t, t) \|_2^2 \right]$$

| Symbol | Meaning |
|---|---|
| $\epsilon_\theta(x_t, t)$ | Neural network predicting noise at step $t$ |
| $\epsilon$ | True noise added in forward process |

### Score Function

$$s(x) = \nabla_x \log p(x)$$

| Symbol | Meaning |
|---|---|
| $s(x)$ | Score (gradient of log-probability) |
| $p(x)$ | Probability density of $x$ |

