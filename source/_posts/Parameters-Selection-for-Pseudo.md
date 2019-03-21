---
title: Parameters-Selection-for-Pseudo
date: 2019-02-27 15:52:24
tags: pesudo labels
categories: Deep learning
---

## temperature in distilled knowledge
> reference-1 [Distilling the Knowledge in a Neural Network](https://arxiv.org/pdf/1503.02531.pdf)
 
aim: distilling the knowledge in an ensemble of models into a single model
temperature: the higher the temperature T, the softer the probability distribution over classes. 'For the distillation we tried temperatures of [1, 2, 5, 10] and used a relative weight of 0.5 on the cross-entropy for the hard targets, where bold font indicates the best value'

> reference-2 from reference-1 [Learning without Forgetting](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8107520)

aim: useing only new task data to train the network while preserving the original capabilities
temperature: T=2, grid search method

## density threshold in local feature density
## distribution distance is transfered into weights