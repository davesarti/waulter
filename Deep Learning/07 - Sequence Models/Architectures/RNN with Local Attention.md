---
tags:
  - deep-learning
  - architecture
year: 2015
task: machine-translation
---
**Local Attention** is a more computationally efficient alternative to [[RNN with Global Attention]].

![[Pasted image 20260706175240.png]]


## Local Attention Mechanism

Instead of attending over all source positions, the model selects a **centre position** $p_t$ and attends only within the window $[p_t - D,\; p_t + D]$.

The model learns to predict the center position:
$$p_t = L_s \cdot \sigma\!\left(v_p^\top \tanh(W_p\, s_{t-1})\right)$$
where $L_s$ is the source sequence length and $v_p$, $W_p$ are learnable parameters.

### Gaussian Focus

Attention weights are further sharpened with a **Gaussian** centred at $p_t$:
$$\alpha_{tj} = softmax(h_j^TW_as_{t-1})\cdot\exp\!\left(-\frac{(j - p_t)^2}{2\sigma^2}\right)$$

This down-weights positions far from the predicted centre while keeping the mechanism fully differentiable.

## Context Vector and Output

The context vector $c_t$ is the weighted sum over the window:
$$c_t = \sum_{j} \alpha_{tj}\, h_j$$

The decoder hidden state and $c_t$ are concatenated and passed through a layer to produce $\tilde{h}_t$, which is used for the final prediction:
$$\tilde{s}_t = \tanh\!\left(W_c[c_t;\, s_t]\right), \qquad p(y_t \mid y_{<t}, x) = \operatorname{softmax}(W_s\, \tilde{s}_t)$$
