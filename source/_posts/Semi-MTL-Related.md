---
title: Semi-MTL Related
date: 2019-03-09 14:59:07
tags: multitask
categories: Deep learning
---

## MTL

### Learning Methods
* Supervised
* Semi-supervised

### Scenarios
* Homogeneous
* Heterogeneous
  * Heterogeneous Tasks (Document & Images & Audio)
  * Hterogeneous Datsets (Each dataset with a set of labels)

### Improvement Ideas
* Network Structure
* Feature Selection

### Application
* CV
* NLP


ALL MTL is the combination of above mentioned.
Our method is semi-supervised MTL with heterogeneous datasets, comparison including supervised or semi-supervised MTL with heterogeneous dataset.



>reference [Semi-supervised Feature Analysis by Mining Correlations among Multiple Tasks](https://arxiv.org/pdf/1411.6232.pdf)

* semi-supervised, heterogeneou datasets, feature selection.
* scenario: CV, dataset A for tasks A[labeled and unlabeled], dataset B for tasks B[labeled and unlabeled]
* method: manifold learning, mining feature correlation by sparse coefficients.
* No

> reference [Deep Cross Residual Learning for Multitask Visual Recognition](https://arxiv.org/pdf/1604.01335.pdf)

* supervised, heterogeneou datasets, network structure.
* scenario: CV, dataset A for tasks A[labeled], dataset B for tasks B[labeled]
* method: enables intuitive learning across multiple related tasks using cross-connections called cross-residuals
* Yes? Netowrk realization?



> reference [A Framework for Learning Predictive Structures from Multiple Tasks and Unlabeled Data](http://www.jmlr.org/papers/volume6/ando05a/ando05a.pdf)

* semi-supervised, heterogeneou datasets, network structure.
* scenario: 
* method: 
* No

>reference [Multi-task Learning of Pairwise Sequence Classification Tasks Over Disparate Label Spaces](https://arxiv.org/pdf/1802.09913.pdf)

* supervised, heterogeneou datasets, network structure.
* scenario: text classification, dataset A for tasks A[labeled], dataset B for tasks B[labeled]
* method: combining multi-task learning and semi- supervised learning by inducing a joint embed- ding space between disparate label spaces and learning transfer functions between label embeddings. LTN can be used to label unlabelled and auxiliary task data by utilising the ‘distilling knowledge’ contained in auxiliary model predictions. not only model their relationship, but also to directly estimate the cor- responding label of the target task based on auxil- iary predictions
* Yes: embedding, prediction, output, temperature=1, embedding can be realized with cross-stich network



>reference [Neural Network for Heterogeneous Annotations](http://www.aclweb.org/anthology/D16-1070)

* supervised, heterogeneou datasets, multi-view & stacking setting
* scenario: NLP, dataset A for tasks A[labeled], dataset B for tasks B[labeled]
* method: multi-view, stacking, neurual network
* Yes: not understand



