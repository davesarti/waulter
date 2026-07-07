---
tags:
  - deep-learning
  - architecture
year: 2018
task: image-generation
---
**StyleGAN** captures and manipulates style attributes (pose, hair type, smile shape, ...) and lets them be varied stochastically via random noise.

![[Pasted image 20260707213441.png]]
![[Pasted image 20260707221019.png|491]]

Key changes to the Generator:
- A **style vector**, derived from the latent representation through 8 fully connected layers.
- **Instance Normalization**, computing per-image mean ($\mu$) and standard deviation ($\sigma$) of pixel values. Normalizing with these statistics removes image-specific brightness/color variation without altering content structure — $\mu$ and $\sigma$ then encode stylistic aspects like texture and color. Applied at different layers to control different aspects of style, then reintegrated at the final generation stage for precise stylistic control.

### Adaptive Instance Normalization (AdaIN)

$$\text{AdaIN}(x, y) = \sigma(y)\left(\frac{x - \mu(x)}{\sigma(x)}\right) + \mu(y)$$

Use the variance and mean of the **content image** to normalize the image itself. Then take the mean and variance from the **style image** and apply them to the (normalized) content image.

This allows style control at different levels of the network:
- Shallow layers control coarse features (pose, face shape)
- Intermediate layers affect style elements (hairstyle, eyes)
- Deeper layers influence fine details (texture, wrinkles)

### Noise Injection
- At each layer, uncorrelated Gaussian noise is added to the feature maps through learned scaling factors.
- This adds stochastic variation and allows control over fine-grained details (e.g., hair texture, skin pores).

### Mixing Regularization
- During training, StyleGAN introduces mixing regularization: randomly uses two latent codes at different layers of the generator for some training samples.
- This encourages the network to decouple features across layers and promotes better disentanglement of styles.

### Upsampling: Bilinear Instead of Transposed Convolution
- Traditional GANs used **transposed convolutions** (deconvolutions), which often introduced checkerboard artifacts.
- StyleGAN replaces these with **bilinear interpolation**, resulting in smoother and more stable images.