---
tags:
  - deep-learning
  - chapter
chapter: 6
---
## Sections

- [[06.1 - Handling Variable-Length Sequences]]
- [[06.2 - Vanilla RNN]]
- [[06.3 - Long Short-Term Memory (LSTM)]]
- [[06.4 - Gated Recurrent Unit (GRU)]]

---

## Formulas

### Vanilla RNN

$$h_t = \tanh(W_x x_t + W_h h_{t-1})$$

$$y_t = \text{softmax}(W_y h_t + b_y)$$

| Symbol | Meaning |
|---|---|
| $x_t$ | Input at time $t$ |
| $h_t$ | Hidden state at time $t$ |
| $W_x$ | Weights for current input |
| $W_h$ | Weights for previous hidden state |
| $W_y$ | Weights for output |

### BPTT

$$\frac{\partial e}{\partial W_h} = \sum_{t=1}^{T} \frac{\partial e_t}{\partial W_h}$$

$$\frac{\partial e}{\partial W_h} \propto \sum_{t} \left( \frac{\partial e}{\partial h_t} \cdot \prod_{k=1}^{t} \frac{\partial h_k}{\partial h_{k-1}} \right)$$

### LSTM

$$\begin{pmatrix} i_t \\ f_t \\ o_t \\ g_t \end{pmatrix} = \begin{pmatrix} \sigma \\ \sigma \\ \sigma \\ \tanh \end{pmatrix} W \begin{pmatrix} x_t \\ h_{t-1} \end{pmatrix}$$

$$c_t = f_t \odot c_{t-1} + i_t \odot g_t$$

$$h_t = o_t \odot \tanh(c_t)$$

| Symbol | Meaning |
|---|---|
| $i_t$ | Input gate |
| $f_t$ | Forget gate |
| $o_t$ | Output gate |
| $c_t$ | Memory cell |
| $g_t$ | Input modulation |

### GRU

$$r_t = \sigma\!\left(W_r \begin{pmatrix} x_t \\ h_{t-1} \end{pmatrix} + b_t\right)$$

$$z_t = \sigma\!\left(W_z \begin{pmatrix} x_t \\ h_{t-1} \end{pmatrix} + b_z\right)$$

$$h'_t = \tanh W\!\begin{pmatrix} x_t \\ r_t \odot h_{t-1} \end{pmatrix}$$

$$h_t = (1 - z_t) \odot h_{t-1} + z_t \odot h'_t$$

| Symbol | Meaning |
|---|---|
| $r_t$ | Reset gate |
| $z_t$ | Update gate |
| $h'_t$ | Candidate hidden state |

---

## Architectures

### Vanilla RNN

![[Pasted image 20260705183701.png]]

### LSTM

![[Pasted image 20260705185223.png]]

### GRU

![[Pasted image 20260705185650.png]]
