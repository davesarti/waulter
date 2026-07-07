---
tags:
  - deep-learning
  - chapter
chapter: 1
---
## Sections

- [[01.1 - From Logistic Regression to FNNs]]
- [[01.2 - FNN architecture]]
- [[01.3 - Loss Functions]]
- [[01.4 - Unit Types]]
- [[01.5 - Activation Functions]]

---

## Architecture

![[img_ffn_arch.png]]

---

## Formulas

### Layer Computation

| Name | Formula |
|---|---|
| Layer composition | $f(\mathbf{x}) = f^{(L)}(\cdots f^{(1)}(\mathbf{x})\cdots)$ |
| Linear unit | $\hat{y} = W^T h + b$ |
| Gradient descent update | $\theta \leftarrow \theta - \eta\,\nabla_\theta \mathcal{L}(\theta)$ |

### Maximum Likelihood Estimation

| Name                | Formula                                                                     |
| ------------------- | --------------------------------------------------------------------------- |
| Likelihood          | $L(\theta) = \displaystyle\prod_{i=1}^{N} p(x_i \mid \theta)$               |
| Log-likelihood      | $\ell(\theta) = \displaystyle\sum_{i=1}^{N} \log p(x_i \mid \theta)$        |
| MLE estimate        | $\hat{\theta}_{\text{MLE}} = \arg\max_{\theta}\;\ell(\theta)$               |
| Logistic regression | $p(y=1 \mid x, \theta) = \sigma(\theta^T x) = \dfrac{1}{1+e^{-\theta^T x}}$ |

### Activation Functions

| Name           | Formula                                                                                                        |
| -------------- | -------------------------------------------------------------------------------------------------------------- |
| Sigmoid     | $\sigma(z) = \dfrac{1}{1+e^{-z}}$                                                                              |
| Tanh        | $\tanh z = \dfrac{e^z - e^{-z}}{e^z + e^{-z}}$                                                                 |
| ReLU        | $\text{ReLU}(z) = \max(0, z)$                                                                                  |
| Leaky ReLU  | $\text{LeakyReLU}(z) = \max(\alpha \cdot z,\;z)$                                                               |
| ELU         | $\text{ELU}(z) = \begin{cases} \alpha(e^z - 1) & z < 0 \\ z & z \geq 0 \end{cases}$                           |
| GELU        | $\text{GELU}(x) = x \cdot \dfrac{1}{2}\!\left[1 + \operatorname{erf}\!\left(\dfrac{x}{\sqrt{2}}\right)\right]$ |
| Softmax     | $\text{Softmax}(z_i) = \dfrac{e^{z_i}}{\sum_j e^{z_j}}$                                                        |

### Loss Functions

| Name | Task | Formula |
|---|---|---|
| BCE | Binary classification | $\mathcal{L}_{\text{BCE}} = -\bigl[y_i \log \hat{y}_i + (1-y_i)\log(1-\hat{y}_i)\bigr]$ |
| CCE | Multi-class classification | $\mathcal{L}_{\text{CCE}} = -\displaystyle\sum_{i=1}^{N} y_i \log \hat{y}_i$ |
| MSE | Regression | $\mathcal{L}_{\text{MSE}} = \dfrac{1}{N}\displaystyle\sum_{i=1}^{N}(y_i - \hat{y}_i)^2$ |
| MAE | Regression | $\mathcal{L}_{\text{MAE}} = \dfrac{1}{N}\displaystyle\sum_{i=1}^{N}\lvert y_i - \hat{y}_i \rvert$ |
| Huber | Regression | $\mathcal{L}_{\delta} = \dfrac{1}{N}\displaystyle\sum_{i=1}^{N}\begin{cases}\frac{1}{2}(y_i-\hat{y}_i)^2 & \lvert y_i-\hat{y}_i\rvert \leq \delta \\ \delta\!\left(\lvert y_i-\hat{y}_i\rvert - \frac{\delta}{2}\right) & \text{otherwise}\end{cases}$ |
