---
tags:
  - deep-learning
  - architecture
year: 2018
task: sequence-modeling
---
**Temporal Convolutional Network (TCN)**, also called **Convolutional Sequence Model**, was the first architecture to apply a CNN to sequence processing.

![[Pasted image 20260707104614.png]]

The network is obtained tacking many residual blocks, each with exponentially increasing dilation (d=1,2,4,8,...d = 1, 2, 4, 8, ... d=1,2,4,8,...), making the network's receptive field grow exponentially with depth, so it can capture long-range dependencies in sequences.

TCNs are distinguished by two main features:

- **Sequence Length Preservation**: the architecture can take a sequence of any length and map the input to an output sequence of the same length.
- **Causality in Convolutions**: the convolutions used are causal, ensuring that there is no leakage of information from the future into the past -> future information is masked

## Sequence Length Preservation

To achieve this, TCNs use a **1D fully convolutional network (FCN)** architecture, where each hidden layer has the same length as the input layer. **Length padding** (kernel size − 1) is added to preserve the length of subsequent layers.

## Causality: Dilated Causal Convolution

To maintain causality, TCNs employ **dilated causal convolution** to ensure that each output depends only on past inputs, respecting the causality constraint and avoiding any "loss" of future information into past predictions.

## Other Ingredients

- **ReLU** activation function
- **Dropout** as a regularization technique
- **Weight normalization block**: normalizes the vector of weights, accelerating convergence without introducing dependencies between examples in a minibatch
- **Residual connections** are also used to enhance the learning process.
