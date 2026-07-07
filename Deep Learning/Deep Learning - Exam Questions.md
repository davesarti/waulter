---
tags:
  - deep-learning
  - exam-prep
---

Prep questions collected ahead of the exam. Duplicates from the raw list have been merged; grouped by topic. No answers included on purpose.

Related: [[Deep Learning]]

## Optimization

- [ ] What is momentum? Write down the formula and explain what $\alpha$ and $\epsilon$ are.
- [ ] Difference between momentum and gradient descent
- [ ] Vanilla gradient descent — draw the figure
- [ ] Adagrad — difference between Adam and Adagrad
- [ ] Adam optimization algorithm — besides the concept, know all hyperparameters and what they are for
- [ ] For a given network (e.g. discussed in class), which optimization algorithm does it use, and why?

## Regularization

- [ ] Weight decay — formula and explanation
- [ ] L1 regularization
- [ ] L2 regularization
- [ ] Regularization — general formula and explanation
- [ ] Empirical loss — formula and explanation

## Activation Functions

- [ ] Activation functions and their diagrams — explain all the ones studied

## Normalization

- [ ] Difference between batch normalization and layer normalization — write down the formulas and how $\sigma$ is computed
- [ ] Instance normalization

## Convolutional Neural Networks

- [ ] Softmax unit
- [ ] Convolutional layers — what are the parameters? Which hyperparameters do you need to set when implementing one?
- [ ] Inception / GoogLeNet architecture — draw it
- [ ] ResNet — draw it
- [ ] RCNN, Fast RCNN and Faster RCNN — explanation, plus a brief explanation of Mask RCNN
- [ ] How do CNNs work (convolution formula)? What have we seen about CNNs in the context of sequence models?
- [ ] How do you design a network for semantic segmentation?

## Recurrent Neural Networks / Sequence Models

- [ ] LSTM — what is the structure?
- [ ] Draw the LSTM structure and explain how it captures the same concept as the residual connections in ResNet
- [ ] Difference between vanilla RNN and GRU
- [ ] Why and when do we use sigmoid vs. tanh in LSTM, GRU and vanilla RNN?
- [ ] RNN samples — give an example
- [ ] PixelRNN

## Autoencoders

- [ ] Difference between autoencoders and variational autoencoders, in terms of latent space

## Generative Adversarial Networks

- [ ] Training a GAN — explain and write down the (loss) formula
- [ ] Overfitting in GANs
- [ ] Conditional GAN — draw the figure
- [ ] CycleGAN
- [ ] GAN label information
- [ ] Why are GANs called "adversarial"?
- [ ] How do we measure a GAN? How do we produce a good-quality GAN?
- [ ] What are the Inception Score and the Fréchet Inception Distance (FID)?

## Transformers / Attention

- [ ] Attention model for image captioning — local vs. global attention, and how to implement them
- [ ] Transformer encoder structure and self-attention, explained in detail from input through the computation of self-attention to the output. How can you use a transformer for classifying images?
