---
tags:
  - deep-learning
  - chapter
chapter: 2
---
## Sections

- [[02.1 - The Gradient Descent Algorithm]]
- [[02.2 - Backpropagation introduction]]
- [[02.3 - Backpropagation Step by Step]]
- [[02.4 - Properties and Limitations of Backpropagation]]

---

## Formulas

### Forward Pass

| Name | Formula |
|---|---|
| Pre-activation | $z^{(l)} = w^{(l)}\, a^{(l-1)} + b^{(l)}$ |
| Activation | $a^{(l)} = \sigma\!\left(z^{(l)}\right)$ |
| Pre-activation (multi-neuron) | $z_j^{(l)} = \displaystyle\sum_i w_{ji}^{(l)}\, a_i^{(l-1)} + b_j^{(l)}$ |

### Gradient Descent

| Name            | Formula                                                                                                                                                                                        |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Weight update   | $w \leftarrow w - \eta\, \dfrac{\partial L}{\partial w}$                                                                                                                                       |
| Gradient vector | $\Delta_w L = \left[\dfrac{\partial L}{\partial w^{(1)}},\ \dfrac{\partial L}{\partial b^{(1)}},\ \ldots,\ \dfrac{\partial L}{\partial w^{(l)}},\ \dfrac{\partial L}{\partial b^{(l)}}\right]$ |
|                 |                                                                                                                                                                                                |

### Backpropagation — Chain Rule

| Name                             | Formula                                                                                                                                                                                                             |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Gradient w.r.t. weight           | $\dfrac{\partial L}{\partial w^{(l)}} = \dfrac{\partial z^{(l)}}{\partial w^{(l)}} \cdot \dfrac{\partial a^{(l)}}{\partial z^{(l)}} \cdot \dfrac{\partial L}{\partial a^{(l)}}$                                     |
| Gradient w.r.t. bias             | $\dfrac{\partial L}{\partial b^{(l)}} = \dfrac{\partial z^{(l)}}{\partial b^{(l)}} \cdot \dfrac{\partial a^{(l)}}{\partial z^{(l)}} \cdot \dfrac{\partial L}{\partial a^{(l)}}$                                     |
| Upstream gradient                | $\dfrac{\partial L}{\partial a^{(l-1)}} = \dfrac{\partial z^{(l)}}{\partial a^{(l-1)}} \cdot \dfrac{\partial a^{(l)}}{\partial z^{(l)}} \cdot \dfrac{\partial L}{\partial a^{(l)}}$                                 |
| Upstream gradient (multi-neuron) | $\dfrac{\partial L}{\partial a_i^{(l-1)}} = \displaystyle\sum_j \dfrac{\partial z_j^{(l)}}{\partial a_i^{(l-1)}} \cdot \dfrac{\partial a_j^{(l)}}{\partial z_j^{(l)}} \cdot \dfrac{\partial L}{\partial a_j^{(l)}}$ |
