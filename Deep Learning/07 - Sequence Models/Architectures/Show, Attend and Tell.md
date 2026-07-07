---
tags:
  - deep-learning
  - architecture
year: 2015
task: image-captioning
---
**Show, Attend and Tell** extends [[Show and Tell]] by adding an **attention mechanism** that allows the model to focus on specific parts of the image while generating each caption word.

![[Pasted image 20260706155157.png]]

![[Pasted image 20260706160508.png]]
## Key Innovations

- **Feature Extractor**: a CNN extracts a set of feature vectors, each representing a different spatial part of the image — **spatial information is preserved**, unlike in Show and Tell
- **RNN with Attention**: the extracted feature maps are passed to **each cell** of the RNN during caption generation, not only at initialisation
- Each RNN cell produces both:
  - $p(y_t)$ — the **probability distribution** over the next word
  - $\alpha_t$ — an **attention map** indicating the relevant parts of the image for that word

## LSTM Cell Inputs

Each LSTM cell receives **three inputs** at every timestep:

| Input | Description |
|---|---|
| $h_{t-1}$ | Previous latent (hidden) state |
| $y_{t-1}$ | Previously predicted word |
| $z_t$ | Context vector — dot product of the CNN feature map and the previous attention map $\alpha_{t-1}$ |
