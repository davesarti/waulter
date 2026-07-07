---
tags:
  - deep-learning
  - algorithm
chapter: 3
---
Mini-Batch Gradient Descent is a compromise between [[Batch Gradient Descent|BGD]] and [[Stochastic Gradient Descent|SGD]]. Instead of using the full dataset or a single example, it applies updates using a **fixed-size subset** of the training data at each iteration, called a *mini-batch*. Algorithm is identical to BGD but limited in sample number.

### Properties

| | |
|---|---|
| **Gradient estimate** | Batch average — moderate variance |
| **Convergence** | More stable than SGD, faster than BGD |
| **Cost** | Independent of total dataset size $N$ |
| **Parallelism** | Naturally suited for GPUs |

### Advantages

- Computation time **does not depend on the total dataset size** $N$ → suitable even for very large datasets.
- Allows **parallel processing**, making it ideal for GPU implementations.
- Provides a good balance between the stability of BGD and the efficiency of SGD.

### Remaining Problem

Along flat directions of the loss surface, gradient steps are small (slow progress). Along steep directions, steps can be large and jittery. This asymmetry motivates the introduction of **[[SGD with Momentum|momentum]]**.
