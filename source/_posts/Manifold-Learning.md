---
title: Manifold Learning
date: 2019-03-18 16:24:56
tags: feature regularization
categories: Deep learning
---

## Manifold Leanring for Semi-supervised Learning
* the model trained with labeled samples and unlabeled samples
* introducing manifold learning to learn the geometry of marginal distribution >reference first paper[Manifold Regularization: A Geometric Framework for Learning from Labeled and Unlabeled Examples](http://www.jmlr.org/papers/volume7/belkin06a/belkin06a.pdf) 
  * explanation in Chinese(https://zhuanlan.zhihu.com/p/33006509)
  * aim: data-depend regularization to exploit geometry of the marginal distribution

### Manifold learning
* non-linear dimensionality reduction method to obtain intrinsic feature >reference PAMI

### Semi-supervised Learning with Manifold Learning
* reason: leveraging a few of training samples to train model always fail to reflect the dataset distribution, which means that the trained model only adapt to the supervised label without learning the intrinsic feature. Introducing manifold learning to combine labeled samples and unlabeled samples can exploit the geometr of marginal distribution.

### Semi-supervised Multi-task Learning with Manifold Learning


>reference [Semisupervised feature analysis by mining correlations among multiple tasks]{https://arxiv.org/pdf/1411.6232.pdf}
* aim: feature selection in semi-supervised MTL
* method: sparce coefficients learnt 
\begin{aligned}
p(x) & = \min\_{w_t} \sum\_(l=1}^t (loss(w\_l) + \alpha ||w\_l||\_{1,2} + \gamma ||w||\_{\*})
\end{aligned}

including $l_{1,2}$ norm and Laplacian norm:

\begin{aligned}
\gamma ||w|| = \min\_{w,b}\sum\_{l=1}{t}Tr(w^Tx\_lL\_lx\_l^Tw)
\end{aligned}


>reference [Semi-supervised multitask learning]{http://papers.nips.cc/paper/3198-semi-supervised-multitask-learning.pdf}

>reference [Semi-supervised multi-task learning with task regularizations]{http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.194.1854&rep=rep1&type=pdf}

>reference [Semi-supervised multitask learning for scene recognition]{https://www.researchgate.net/profile/Lichao_Mou/publication/268880603_Semi-Supervised_Multitask_Learning_for_Scene_Recognition/links/567a67f608ae7fea2e9a08f1.pdf}

