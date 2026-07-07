---
tags:
  - deep-learning
  - chapter
chapter: 5
---
## Sections

- [[05.1 - Convolutions]]
- [[05.2 - Inside a CNN]]
- [[05.3 - CNN Architectures]]
- [[05.4 - Regularisation Techniques for CNNs]]
- [[05.5 - Object Detection]]
- [[05.6 - Instance Segmentation]]

---

## Formulas

### Convolution

$$S(i,j) = \sum_m \sum_n I(m,n)\, K(i-m,\, j-n)$$

### Output Size

$$\text{Output} = \frac{N - K + 2P}{S} + 1$$

| Symbol | Meaning |
|---|---|
| $N$ | Input size |
| $K$ | Kernel size |
| $P$ | Padding |
| $S$ | Stride |

--- 

## Architectures

### LeNet (1998)
![[Pasted image 20260704171450.png]]
![[Pasted image 20260705153850.png]]

### AlexNet (2012)
![[Pasted image 20260704171842.png]]
![[Pasted image 20260705155530.png]]

### Zeiler & Fergus Net (2013)
![[Pasted image 20260704173313.png]]
![[Pasted image 20260705161125.png]]

### VGGNet (2014)
![[Pasted image 20260704173559.png]]
![[Pasted image 20260705163717.png]]

### GoogleNet (2014)
![[Pasted image 20260704174720.png]]
![[Pasted image 20260705170351.png]]

### ResNet (2015)
![[Pasted image 20260704180116.png]]
![[Pasted image 20260705172128.png]]

### R-CNN (2014)
![[Pasted image 20260704185132.png]]

### Fast R-CNN (2015)
![[Pasted image 20260704185410.png]]
![[Pasted image 20260705180433.png]]

### Faster R-CNN (2015)
![[Pasted image 20260704185719.png]]
![[Pasted image 20260705180642.png]]

### YOLO (2016)
![[Pasted image 20260704190739.png|500]]

### Mask R-CNN (2017)
![[Pasted image 20260704192447.png]]
