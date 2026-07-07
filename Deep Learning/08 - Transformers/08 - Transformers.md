---
tags:
  - deep-learning
  - chapter
chapter: 8
---
## Sections

- **8.1** [[08.1 - CNNs in sequence models|CNNs in sequence models]]
- **8.2** [[08.2 - Transformer|Attention is All You Need]]
- **8.3** [[08.3 - Vision Transformer (ViT)|Vision Transformer (ViT)]]
- **8.4** [[08.4 - Swin Transformer|Swin Transformer]]

---

## Formulas

### Convolutional Seq2Seq — GLU

$$v([A\ B]) = A \otimes \sigma(B)$$

| Symbol | Meaning |
|---|---|
| $A, B$ | Two halves of a linear convolution's output |
| $\sigma(B)$ | Gate controlling which parts of $A$ pass through |

### Convolutional Seq2Seq — Attention

$$a^l_{ij} = \frac{\exp(d^l_i \cdot z^u_j)}{\sum_{t=1}^m \exp(d^l_i \cdot z^u_t)} \qquad c^l_i = \sum_{j=1}^m a^l_{ij} (z^u_j + e_j)$$

| Symbol | Meaning |
|---|---|
| $d^l_i$ | Decoder state summary at layer $l$, position $i$ |
| $z^u_j$ | Encoder output of the last block $u$, position $j$ |
| $c^l_i$ | Conditional input fed to decoder layer $l$ |

### Self-Attention

$$\text{Attention}(Q, K, V) = \text{softmax}\!\left(\frac{QK^T}{\sqrt{d_k}}\right) V$$

| Symbol | Meaning |
|---|---|
| $Q$ | Query — the current word being processed |
| $K$ | Key — the potentially relevant words |
| $V$ | Value — the content of the relevant words |
| $d_k$ | Dimension of the keys (scaling factor) |

### DeiT — Soft Distillation

$$\mathcal{L}_{\text{global}} = (1-\lambda)\,\mathcal{L}_{\text{CE}}(\psi(Z_s), y) + \lambda \tau^2\, \text{KL}\big(\psi(Z_s/\tau), \psi(Z_t/\tau)\big)$$

| Symbol | Meaning |
|---|---|
| $\tau$ | Temperature factor (softens probabilities) |
| $\lambda$ | Weighting between CE and KL terms |

### DeiT — Hard Distillation

$$\mathcal{L}_{\text{global}}^{\text{hardDistill}} = \frac{1}{2}\,\mathcal{L}_{\text{CE}}(\psi(Z_s), y) + \frac{1}{2}\,\mathcal{L}_{\text{CE}}(\psi(Z_s), y_t)$$

| Symbol | Meaning |
|---|---|
| $y_t$ | Teacher's predicted (hard) label |

---

## Architectures

### Temporal Convolutional Network (TCN)

![[Pasted image 20260707104614.png]]

### Convolutional Seq2Seq

![[Pasted image 20260707114643.png|458]]
![[Pasted image 20260707121706.png|460]]

### Transformer

![[Pasted image 20260707153616.png]]

### Vision Transformer (ViT)

![[Pasted image 20260707172410.png]]

### Swin Transformer

![[Pasted image 20260707171428.png]]

