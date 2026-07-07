---
tags:
  - deep-learning
  - chapter
chapter: 7
---

## Sections

- **7.1** [[07.1 - Captioning Models and Attention|Captioning Models and Attention]]
- **7.2** [[07.2 - Seq2Seq|Seq2Seq]]
- **7.3** [[07.3 - RNN Encoder-Decoder and Attention|RNN Encoder-Decoder and Attention]]
- **7.4** [[07.5 - GNMT|GNMT (Google Neural Machine Translation)]]

---

## Formulas

### Show and Tell

$$I \to \text{LSTM}_{t=-1} \qquad h_t = \text{LSTM}(W_e S_t,\, h_{t-1})$$

| Symbol | Meaning |
|---|---|
| $I$ | CNN feature vector (image) |
| $S_t$ | One-hot word vector at time $t$ |
| $W_e S_t$ | Word embedding |

### Show, Attend and Tell

$$z_t = \sum_i \alpha_{i,t}\, a_i$$

| Symbol | Meaning |
|---|---|
| $a_i$ | CNN feature vector for spatial region $i$ |
| $\alpha_{i,t}$ | Attention weight over region $i$ at time $t$ |
| $z_t$ | Context vector (soft attention) |

### Seq2Seq / RNN Encoder-Decoder

$$h_t = f(x_t,\, h_{t-1}) \qquad c = q(h_1, \dots, h_T)$$

$$p(\mathbf{y}) = \prod_{t=1}^{T'} p\!\left(y_t \mid y_1, \dots, y_{t-1},\, c\right)$$

| Symbol | Meaning |
|---|---|
| $c$ | Fixed-size context vector |
| $s_t$ | Decoder hidden state at time $t$ |

### RNN with Global Attention

$$e_{t,j} = a(s_{t-1},\, h_j) \qquad \alpha_{t,j} = \frac{\exp(e_{t,j})}{\sum_{k=1}^{T} \exp(e_{t,k})} \qquad c_t = \sum_{j=1}^{T} \alpha_{t,j}\, h_j$$

$$\tilde{s}_t = \tanh\!\left(W_c[c_t;\, s_t]\right), \qquad p(y_t \mid y_{<t}, x) = \operatorname{softmax}(W_s\, \tilde{s}_t)$$

| Symbol | Meaning |
|---|---|
| $h_j$ | Encoder annotation at position $j$ |
| $a$ | Feedforward alignment model |
| $\tilde{s}_t$ | Attentional decoder state |

### RNN with Local Attention

$$p_t = L_s \cdot \sigma\!\left(v_p^\top \tanh(W_p\, s_{t-1})\right)$$

$$\alpha_{tj} = \operatorname{softmax}(h_j^\top W_a s_{t-1})\cdot\exp\!\left(-\frac{(j - p_t)^2}{2\sigma^2}\right)$$

$$c_t = \sum_{j} \alpha_{tj}\, h_j$$

| Symbol | Meaning |
|---|---|
| $p_t$ | Predicted centre position |
| $L_s$ | Source sequence length |
| $D$ | Half-window size ($\sigma = D/2$) |

### GNMT — Residual Connections

$$x^{i+1}_t = \text{LSTM}^i(x^i_t) + x^i_t \qquad (i \geq 3)$$

---

## Architectures

### Show and Tell

![[Pasted image 20260706152555.png]]
![[Pasted image 20260706154003.png]]

### Show, Attend and Tell

![[Pasted image 20260706155157.png]]
![[Pasted image 20260706160508.png]]

### Seq2Seq

![[Pasted image 20260706161400.png]]

### RNN Encoder-Decoder

![[Pasted image 20260706165429.png]]

### RNN with Global Attention

![[Pasted image 20260706171008.png]]

### RNN with Local Attention

![[Pasted image 20260706175240.png]]

### GNMT

![[Pasted image 20260707095137.png]]
