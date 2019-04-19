---
title: Semi-supervised Heteroneous Multitask Learning Baselines
date: 2019-02-28 15:23:11
tags: multitask
categories: Deep learning
---

## high-related

>reference [Learning without Forgetting](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8107520)
* distilled knowledge



>reference [An All-In-One Convolutional Neural Network for Face Analysis](https://arxiv.org/pdf/1611.00851.pdf)
* naive joint


>reference [From Facial Expression Recognition to Interpersonal Relation Prediction
Zhanpeng](https://arxiv.org/pdf/1609.06426.pdf)
* pseudo label



>reference NLP [Multi-task Learning of Pairwise Sequence Classification Tasks Over Disparate Label Spaces](https://arxiv.org/pdf/1802.09913.pdf)
'we should be able to not only model their relationship, but also to directly estimate the corresponding label of the target task based on auxiliary predictions.'
* probelm: jointly using unlabelled data and auxiliary, annotated datasets; domain gap; missing labels
* method: training the Label Transfer Network, minimise the squared error between the model predictions and the pseudo label
* baseline: yes (how to calculate loss funtion [squared error] based on pseudo label)


>reference [Seeing through the Human Reporting Bias: Visual Classifiers from Noisy Human-Centric Labels Ishan](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Misra_Seeing_Through_the_CVPR_2016_paper.pdf)
* confidence score
* same apply scene
* refer to paper writting



>reference non-DL [Semi-supervised Feature Analysis by Mining Correlations among Multiple Tasks](http://de.arxiv.org/pdf/1411.6232)
* problem: 'Since the objective function is non-smooth and difficult to solve, we propose an iterative algorithm with fast convergence.' 'These previous works, however, independently select features for each task, which fails to consider correlations among multiple related tasks.' 'Despite of their good performances, these classical algorithms are all implemented only with labeled training data.'
* method: 'ignoring the correlations among different features ->apply the sparse coefficients to the feature vectors -> proposing multiple feature selection'
* baseline: undetermined (hard to complete)


> [Pseudo-task Augmentation: From Deep Multitask Learning to Intratask Sharing—and Back](https://arxiv.org/pdf/1803.04062.pdf)
* related work conclude papers of joint training of models for multiple tasks.
  * 'how learned structure is shared across tasks':
     1. supervise different tasks at different depths of the shared structure []()
     2. duplicate the shared structure into columns and define mechanisms for sharing information across columns [Multitask Learning with Low-Level Auxiliary Tasks for Encoder-Decoder Based Speech Recognition
](https://arxiv.org/pdf/1704.01631.pdf), using intermediate representations as auxiliary supervision for low-level task recognition to improve final task performance.
* baseline: no( pose-emotion both are high-level task, not similar to keypoint detection)





## pseudo method related
 >reference CVPR 2018[Pseudo Mask Augmented Object Detection](http://openaccess.thecvf.com/content_cvpr_2018/papers/Zhao_Pseudo_Mask_Augmented_CVPR_2018_paper.pdf)
 'proposing an effective learning approach that progressively improves the quality pseudo from a coarse initialization,the detection network parameters Θ and pseudo masks Mpseudo are alternatively optimized following a EM-like way'
 * probelm: object detection without mask annotation
 * method: pseudo mask (alternatively,initialization,pseudo mask with refinement algorithm[graphical model, because the pixel charaterization])
 * baseline: yes(uing graphical model with learned information as input to refine pseudo label)

>reference [Learning from Noisy Labels with Distillation](https://arxiv.org/pdf/1703.02391.pdf)
* interpolation between noisy label and distilled knowledge
* baseline: yes

 >reference [Clustered Multi-Task Learning Via Alternating Structure Optimization
](http://papers.nips.cc/paper/4292-clustered-multi-task-learning-via-alternating-structure-optimization.pdf)
* 'ASO which aims to identify a shared low-dimensional predictive structure for all tasks','based on the standard assump- tion that each task can learn equally well from any other task','the clustering view of ASO has not been explored before'
* hard to understand, pure theories.

