---
tags:
  - deep-learning
  - architecture
year: 2015
task: machine-translation
---

**RNN with Global Attention** extends [[RNN Encoder-Decoder]] by replacing the single fixed context vector with a **step-specific context vector** $c_t$, computed as a weighted sum over *all* encoder hidden states.

![[Pasted image 20260706171008.png]]

## Attention Mechanism

At decoder step $t$, each encoder state $h_j$ is scored against the previous decoder state $s_{t-1}$ via a small feedforward **alignment model** $a$:
$$e_{t,j} = a(s_{t-1},\, h_j)$$
Scores are normalised with softmax to obtain **attention weights**:
$$\alpha_{t,j} = \frac{\exp(e_{t,j})}{\sum_{k=1}^{T} \exp(e_{t,k})}$$
The context vector is the weighted sum of all encoder annotations:
$$c_t = \sum_{j=1}^{T} \alpha_{t,j}\, h_j$$

$c_t$ together with the current decoder state $s_t$ produce the attentional state $\tilde{s}_t$, which drives the output:
$$\tilde{s}_t = \tanh\!\left(W_c[c_t;\, s_t]\right), \qquad p(y_t \mid y_{<t}, x) = \operatorname{softmax}(W_s\, \tilde{s}_t)$$

The matrix $\alpha_{tj}$ provides an interpretable **source↔target alignment**.

> [!success] Key Advantage
> No fixed-size bottleneck — the model can attend to different parts of the input at each step, handling long sequences effectively.
