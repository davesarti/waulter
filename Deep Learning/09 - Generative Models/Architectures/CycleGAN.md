---
tags:
  - deep-learning
  - architecture
year: 2017
task: image-to-image-translation
---
**CycleGAN** translates images between two domains **without paired data** (e.g., photographs ↔ Monet-style paintings).

![[Pasted image 20260707212801.png|466]]

CycleGAN is built from three components:
- **Translator**: converts an image from one domain (e.g., photos) to another (e.g., Monet paintings).
- **Discriminator**: determines whether an image belongs to the target domain, and verifies that translating it back to the source domain still resembles the original.
- **Generator**: transforms the translated image back to the original domain, preserving fidelity.

The model works in both directions (domain X → Y and Y → X), sharing parameters between the two directions and reversing roles. Training adds a **Cycle-Consistency Loss** (similar to L1) on top of the classical [[09.1 - Generative Adversarial Networks (GANs)|GAN]] loss, ensuring that an image translated and then translated back stays close to the original.