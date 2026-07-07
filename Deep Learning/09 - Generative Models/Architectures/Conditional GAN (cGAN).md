---
tags:
  - deep-learning
  - architecture
year: 2014
task: conditional-image-generation
aliases:
  - cGAN
---
![[Pasted image 20260707212343.png|327]]

A **cGAN** links an input to its corresponding label, enabling supervised information to guide generation (e.g., a photo of a lion paired with the label "lion"). The optimization problem is unchanged, so standard [[09.1 - Generative Adversarial Networks (GANs)|GAN]] techniques still apply.

The Generator incorporates the label as an extension of the latent space (e.g., appending a one-hot label vector to $z$). The Discriminator also uses the label of real data, letting it focus on a specific class and improving its discriminative performance.