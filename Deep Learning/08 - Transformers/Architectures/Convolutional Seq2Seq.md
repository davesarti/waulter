---
tags:
  - deep-learning
  - architecture
year: 2017
task: machine-translation
---
![[Pasted image 20260707114643.png|458]]
![[Pasted image 20260707121706.png|460]]
## From RNN to CNN

In the original architecture of [[07.3 - RNN Encoder-Decoder and Attention|RNN with Attention]], the encoder consists of a bidirectional LSTM. In this work it is replaced with a [[Temporal Convolutional Network (TCN)|Temporal Convolutional Network (TCN)]], which produces latent representations used for attention computation. In addition, the decoder was also transformed into a CNN-based architecture. In both cases, encoder and decoder, **Gated Linear Units (GLU)** and **residual connections** are used.

## Encoder-Decoder

- **Encoder**: stack of convolutional layers over the source embeddings, gated by GLUs, that produces a set of key/value representations used by the attention mechanism.
- **Decoder**: a CNN-based architecture (also using GLUs and residual connections) that attends over the encoder representations to generate the target sequence.

The CNN-based decoder improves training efficiency by exploiting **parallel computation** capabilities.

## Gated Linear Units (GLU)

Each convolutional block uses a **Gated Linear Unit (GLU)** as its non-linearity, instead of the ReLU/tanh typically used in CNNs:

$$v([A\ B]) = A \otimes \sigma(B)$$

Where:

- $A$ and $B$ are two halves of the output of a linear convolution (the convolution outputs twice the desired number of channels, then splits them into $A$ and $B$).
- $\sigma(B)$ acts as a **gate**, controlling which parts of $A$ are allowed to pass through.
- $\otimes$ is element-wise multiplication.

## Convolutional Blocks

Each convolutional block consists of:

1. A 1D convolution layer,
2. followed by a GLU activation,
3. optionally followed by a residual connection.

## Positional Embeddings

Since CNNs process all positions in parallel and have no inherent notion of sequence order (unlike RNNs), **positional embeddings** are added element-wise to the token embeddings. These help the network know *where* in the sequence each token is, which is crucial for language modeling and translation.

## Decoder and Causal Convolutions

The decoder is **fully convolutional**, like the encoder: stacked 1D convolutional blocks with GLUs and residual connections. However, during decoding:

- Each output token is predicted using only the *previous* outputs — this requires **causal convolutions**, where the convolution's receptive field only extends to past positions.
- Convolutions in the decoder have an **asymmetric, triangular structure** (achieved via padding) that prevents the model from "peeking" at future tokens.
- The decoder still uses (soft) attention over the encoder's outputs to guide generation at every layer.

Because generation only depends on already-produced tokens and the encoder representations (not on a recurrent hidden state), training can be **highly parallelized** across time steps — unlike RNNs, which are inherently sequential.

## Attention Mechanism

The attention is **soft attention**, in the same spirit as Bahdanau/Luong attention in RNN [[07.3 - RNN Encoder-Decoder and Attention|Encoder-Decoder]] models: a weighted sum of encoder outputs, based on the decoder's internal representation at each step.

For decoder layer $l$, the attention $a^l_{ij}$ between decoder state $i$ and source element $j$ is a softmax over the dot-product between the decoder state summary $d^l_i$ and each output $z^u_j$ of the last encoder block $u$:

$$a^l_{ij} = \frac{\exp(d^l_i \cdot z^u_j)}{\sum_{t=1}^m \exp(d^l_i \cdot z^u_t)}$$

The conditional input $c^l_i$ fed to the current decoder layer is then a weighted sum of both the encoder outputs **and** the input element embeddings $e_j$ (i.e. the *context stack* mentioned above):

$$c^l_i = \sum_{j=1}^m a^l_{ij} (z^u_j + e_j)$$

