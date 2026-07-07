---
tags:
  - deep-learning
  - activation-function
chapter: 1
---
![[Pasted image 20260701211218.png|466]]

**Use**: State-of-the-art models (GPT-3, BERT) — combines the behaviour of [[ReLU]], Dropout, and Zoneout into a single smooth activation.

### Formula

$$\text{GELU}(x) = x P(X \leq x) = x\,\Phi(x) = x \cdot \frac{1}{2}\!\left[1 + \operatorname{erf}\!\left(\frac{x}{\sqrt{2}}\right)\right]$$

where $\Phi(x)$ is the CDF of the standard normal distribution.

> [!note] Swish is graphically very similar to GELU.

### Key idea

GELU integrates features of three regularization techniques:

- **Like [[ReLU]]**: acts as a smooth gating function — keeps positive inputs and smoothly suppresses negative ones, unlike the hard threshold of [[ReLU]].
- **Like Dropout**: scales activations between 0 and 1, functioning as a deterministic, input-dependent probabilistic gate.
- **Like Zoneout**: partially preserves activations, avoiding strict on/off behaviour.

### Pros

- **Smooth and non-monotonic**: differentiable everywhere, enabling stable gradient flow without the hard zero of [[ReLU]].
- **Input-dependent gating**: the stochastic interpretation means the network implicitly performs regularization during the forward pass.
- Empirically outperforms [[ReLU]] and [[ELU]] on large-scale models (Transformers, BERT, GPT).

### Cons

- More **computationally expensive** than [[ReLU]] due to the error function $\operatorname{erf}$.
- In practice often approximated as $x \cdot \sigma(1.702\, x)$ for speed.

### Related functions

- **Swish** — smooth non-monotonic function; has been shown to outperform [[ReLU]] on deeper models (e.g. ImageNet). Graphically very similar to [[GELU]].