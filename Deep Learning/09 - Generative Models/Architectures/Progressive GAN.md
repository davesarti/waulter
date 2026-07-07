---
tags:
  - deep-learning
  - architecture
year: 2017
task: high-resolution-image-generation
aliases:
  - ProGAN
  - PGGAN
---
![[Pasted image 20260707213219.png]]

**Progressive GANs** introduce the concept of **progressive growth**: the Generator and Discriminator start at a small resolution (e.g., $4\times4$) and new layer blocks are added gradually as training stabilizes, up to very high resolutions (e.g., $1024\times1024$).

At each stage, both networks reuse the parameters learned in previous, lower-resolution stages. This lets the model learn coarse structure first and refine details later, improving final image quality.