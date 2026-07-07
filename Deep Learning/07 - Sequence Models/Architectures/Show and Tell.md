---
tags:
  - deep-learning
  - architecture
year: 2014
task: image-captioning
---
**Show and Tell**  combines [[GoogleNet]]] and [[06.3 - Long Short-Term Memory (LSTM)|LSTM]] to generate captions for images.

![[Pasted image 20260706152555.png]]
![[Pasted image 20260706154003.png]]
## Pipeline

1. **Feature extraction**: GoogleNet processes the image and produces a feature vector $I$
2. **Initialisation**: $I$ is inserted into the LSTM sequence at time $t = -1$, only once
3. **Word sequence**: starting at $t = 0$, word vectors are fed in one at a time. Each word is represented as a one-hot vector $S_t$ with dimensions equal to the vocabulary size
4. **Embedding**: each word vector $S_t$ is transformed through an embedding layer: $W_e S_t$
5. **LSTM step**: the embedded word and the previous hidden state produce a new hidden state and the probability $p_t$ of the next word
6. **Output**: the word with the highest probability $\log p_t(S_{t+1})$ is chosen as the output for that timestep
7. **Termination**: the process repeats until the special end-of-sentence token $S_N$ is produced or a maximum sequence length is reached

> The quality of the generated caption depends strongly on CNN performance — making fine-tuning of the CNN crucial.

During training, the words that are fed in the model are the ground truth, regardless to the model predictions

## Inference Methods

### Sampling

The first word is extracted according to probability $p_1$. Its embedding is then fed as input and the next word is extracted with probability $p_2$ (which depends on the previous prediction). This continues until the EOS token or maximum length is reached.

### Beam Search

At each step, the model keeps the **$k$ best sentences up to time $t$** as candidates to generate sentences of length $t + 1$, retaining only the $k$ best at each step. This explores more word combinations than sampling, improving caption quality.