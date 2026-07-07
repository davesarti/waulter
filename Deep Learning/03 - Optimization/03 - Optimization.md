---
tags:
  - deep-learning
  - chapter
chapter: 3
---
## Sections

- [[03.1 - Types of Gradient Descent]]
- [[03.2 - Normalization]]

---

## Formulas

### Weight Update Rules

| Algorithm | Update Rule |
|---|---|
| BGD / SGD | $\mathbf{w} \leftarrow \mathbf{w} - \eta\,\hat{\mathbf{g}}$ |
| Momentum | $\mathbf{v} \leftarrow \alpha\mathbf{v} - \eta\hat{\mathbf{g}}$, then $\mathbf{w} \leftarrow \mathbf{w} + \mathbf{v}$ |
| Nesterov | $\tilde{\mathbf{w}} \leftarrow \mathbf{w} + \alpha\mathbf{v}$, then same as Momentum |
| Adagrad | $\mathbf{w} \leftarrow \mathbf{w} - \dfrac{\eta}{\delta + \sqrt{\mathbf{r}}} \odot \hat{\mathbf{g}}$, $\mathbf{r} \leftarrow \mathbf{r} + \hat{\mathbf{g}} \odot \hat{\mathbf{g}}$ |
| RMSProp | $\mathbf{r} \leftarrow \rho\mathbf{r} + (1-\rho)\hat{\mathbf{g}} \odot \hat{\mathbf{g}}$, same update as Adagrad |
| Adam | $\mathbf{w} \leftarrow \mathbf{w} - \eta\dfrac{\hat{\mathbf{s}}}{\delta + \sqrt{\hat{\mathbf{r}}}}$ |

### Normalization

General form shared by all methods:

$$\hat{x} = \frac{x - \mu_S}{\sqrt{\sigma_S^2 + \epsilon}}, \qquad \text{Output} = \gamma\hat{x} + \beta$$

| Method | $\mu_S$, $\sigma_S$ computed over |
|---|---|
| **BN** | Batch $N$ per channel: $\dfrac{1}{m}\sum_j H_{:,j}$ |
| **LN** | $C,H,W$ per example: $\dfrac{1}{C \cdot H \cdot W}\sum_{c,h,w} x_{c,h,w}$ |
| **IN** | $H,W$ per channel per example: $\dfrac{1}{H \cdot W}\sum_{h,w} x_{n,c,h,w}$ |
| **GN** | $\frac{C}{G},H,W$ per group per example: $\dfrac{1}{(C/G) \cdot H \cdot W}\sum_{c \in g,\,h,w} x_{n,c,h,w}$ |
