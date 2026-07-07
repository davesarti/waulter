---
tags:
  - deep-learning
  - loss-function
chapter: 1
---
**Task**: Binary classification — predicting $y \in \{0, 1\}$.

### Formula

$$\mathcal{L}_{\text{BCE}}(\theta) = - \left[ y \log \hat{y} + (1 - y) \log(1 - \hat{y}) \right]$$

where $\hat{y}_i = \sigma(z_i) \in (0, 1)$ is the predicted probability that $y_i = 1$. The loss is computed on a single sample.

### Probabilistic Derivation

BCE arises from **MLE under a Bernoulli assumption**. The model outputs:

$$p(y = 1 \mid x, \theta) = \hat{y}, \qquad p(y = 0 \mid x, \theta) = 1 - \hat{y}$$

Taking the negative log-likelihood over $N$ samples yields the BCE formula above. This is the same derivation as [[01.1 - From Logistic Regression to FNNs#MLE for Logistic Regression|logistic regression]].