---
title: Overview of Generative Models
date: 2019-04-09 18:31:46
tags: overview
categories: Generative Model
---
<!-- <img src="https://www.yanhong.me/images/gm.jpg" width="50%" height="50%"> -->
<!-- <img src="⁨hy-zpg.github.io⁩/source⁩/imgs⁩/gm.jpg" class="full-image" width="180" height="180" title="hello"> -->
<!-- ![avatar](http://baidu.com/pic/doge.png)-->
## Taxonomy of Generative models
!['taxonomy of generative models'](/imgs/gm.jpg)

### PixelsRNN and PixelsCNN

* this method belongs to ___explicit density model___.

* Using ___chain rule___ to decompose likelihood of an image x into product of 1-d distributions:

\begin{aligned}
 p\_{\theta}(x)=\prod\_{i=1}^{n} p\_{\theta}\left(x\_{i} | x\_{1}, \ldots, x\_{i-1}\right)
\end{aligned}


where $x_i$ represents pixel, $p(x)$ denoets the likelihood of image $x$

* it's important to define ___ordering___ of those pixels

* complex distribution over pixels can be sloved by neural networks

* pros: ___explicitly___ compute likelihood $p(x)$.

* cons: sequential generation is slow.

#### PixelsRNN
* generating image pixels from corner, and then using RNN(LSTM) to model dependency on previous pixels.

* drawback is that the process of sequential generation if slow.

#### PixelsCNN
* generating image pixels from corner, and then using CNN to cover context region.

* generation proceed sequentially is still slow.

### Variational Autoenconders

* this method defines ___intractable density function___ with latent $z$:

\begin{aligned}
p\_{\theta}(x)=\int p\_{\theta}(z) p\_{\theta}(x | z) d z
\end{aligned}

#### Autoencoders
* mapping image $x$ to features $z$ with deep neural networks, $z$ is regarded to capture meaningful factors of variation in data.
* to learn feature $z$ by reconstruction error: $x$ -> $z$ -> $\hat_{x}$ with encoder and decoder.

#### Variational Autoenconders for generation problem
* Assuming training data $x(i)$ representation $z$ is generated from latent representation $z$. Specifically, first sampling $z$ from true prior $p\_{\theta}(z)$, then sampling $x$ from true conditional $p\_{\theta}(x|z^(i))$

* the aim is to estimate the true parameter $\theta$ by maximuming likelihood of training data:

\begin{equation}
p\_{\theta}(x)=\int p\_{\theta}(z) p\_{\theta}(x | z) d z
\end{equation}

where $p\_{\theta}(z)$ is gaussion prior, and $p\_{\theta}(x | z) $ is decoder.

* intractable optimization problem, because it's impossible to compute $p(x | z)$ for every $z$ which means the integral operation is fail in this condition. 

* posterior density $p\_{\theta}(z | x)=p\_{\theta}(x | z) p\_{\theta}(z) / p\_{\theta}(x)$ is also intractable, since $p\_{\theta}(x)$ is intractable data likelihood. 