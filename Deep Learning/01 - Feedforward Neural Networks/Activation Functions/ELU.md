---
tags:
  - deep-learning
  - activation-function
chapter: 1
---
![[Pasted image 20260701210924.png|364]]

**Use**: Alternative to [[ReLU]] and [[Leaky ReLU]] — retains the advantages of ReLU while avoiding neuron death, at a small computational cost.

### Formula

$$\text{ELU}(z) = \begin{cases} \alpha \cdot (\exp(z) - 1) & \text{if } z < 0 \\[4pt] z & \text{if } z \geq 0 \end{cases}$$

where $\alpha > 0$ controls the saturation value for negative inputs.

### Pros

- Retains all advantages of [[ReLU]] for $z \geq 0$.
- Avoids the **dying neuron** problem: negative inputs yield a smooth, non-zero output rather than hard zero.
- Produces outputs that are **closer to zero-centered** compared to plain [[ReLU]].

### Cons

- Requires **exponentiation** for negative inputs, slightly increasing computational cost compared to [[ReLU]].