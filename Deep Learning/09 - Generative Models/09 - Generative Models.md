---
tags:
  - deep-learning
  - chapter
chapter: 9
---
## Sections

- [[09.1 - Generative Adversarial Networks (GANs)]]
- [[09.2 - DCGANs]]
- [[09.3 - Evaluation of GANs]]
- [[09.4 - Different GAN Losses]]
- [[09.5 - GANs Training Tricks]]
- [[09.6 - GANs Zoo]]
- [[09.7 - Autoencoders]]
- [[09.8 - Variational Autoencoders (VAEs)]]
- [[09.9 - VQ-VAEs]]
- [[09.10 - GAN and VAE Comparison]]

---

## Formulas

### GAN Objective

$$\min_{\theta_g} \max_{\theta_d} \; \mathbb{E}_{x \sim p_{data}} \big[\log(D_{\theta_d}(x))\big] + \mathbb{E}_{z \sim p_z}\big[\log(1 - D_{\theta_d}(G_{\theta_g}(z)))\big]$$

| Symbol | Meaning |
|---|---|
| $D_{\theta_d}(x)$ | Discriminator output for real data |
| $D_{\theta_d}(G_{\theta_g}(z))$ | Discriminator output for generated (fake) data |

### LSGAN Loss

$$\min_{\theta_d} \; \frac{1}{2}\mathbb{E}_{x \sim p_{data}}\big[(D_{\theta_d}(x) - 1)^2\big] + \frac{1}{2}\mathbb{E}_{z \sim p_z}\big[D_{\theta_d}(G_{\theta_g}(z))^2\big]$$
$$\min_{\theta_g} \; \frac{1}{2}\mathbb{E}_{z \sim p_z}\big[(D_{\theta_d}(G_{\theta_g}(z)) - 1)^2\big]$$

### VAE — Likelihood and ELBO

$$p_\theta(x) = \int p_\theta(z)\,p_\theta(x|z)\,dz$$

$$\log p_\theta(x) \ge \mathbb{E}_z[\log p_\theta(x|z)] - D_{KL}\big[q_\phi(z|x)\,\|\,p_\theta(z)\big]$$

| Symbol | Meaning |
|---|---|
| $\mathbb{E}_z[\log p_\theta(x\|z)]$ | Reconstruction term (Decoder) |
| $D_{KL}[q_\phi(z\|x)\,\|\,p_\theta(z)]$ | Regularization term (Encoder vs. Gaussian prior) |

### VAE — Reparameterization Trick

$$z = \mu(x) + \sigma(x) \cdot \epsilon, \qquad \epsilon \sim \mathcal{N}(0, I)$$

## Notes

