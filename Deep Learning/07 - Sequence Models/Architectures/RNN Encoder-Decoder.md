---
tags:
  - deep-learning
  - architecture
year: 2014
task: sequence-to-sequence
---

**RNN Encoder-Decoder** is a general framework that maps a variable-length input sequence $\mathbf{x} = (x_1, \dots, x_T)$ to a variable-length output sequence $\mathbf{y} = (y_1, \dots, y_{T'})$.

![[Pasted image 20260706165429.png]]

## Architecture

### Encoder

Reads the input sequence one token at a time and updates its hidden state:
$$h_t = f(x_t,\, h_{t-1})$$
After processing all $T$ tokens, the final hidden state produces the **context vector**:
$$c = q(h_1, \dots, h_T) \qquad \text{(typically } c = h_T\text{)}$$

### Decoder

Conditioned on $c$, generates the output sequence autoregressively:
$$p(\mathbf{y}) = \prod_{t=1}^{T'} p\!\left(y_t \mid y_1, \dots, y_{t-1},\, c\right)$$
Each conditional is modelled by an RNN whose hidden state $s_t$ depends on $s_{t-1}$, $y_{t-1}$, and $c$.

## Limitation

> [!warning] Fixed-Vector Bottleneck
> The entire input sequence must be compressed into a **single fixed-size vector** $c$. Performance degrades sharply on **long sequences**, since $c$ cannot retain all relevant information — this is the central motivation for the attention mechanism.
