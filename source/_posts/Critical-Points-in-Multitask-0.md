---
title: Critical Points in Multitask Learning
date: 2019-02-28 11:16:26
tags: multitask
categories: Deep learning
---

## Several tips for heterogeneous multitask learning
* core problem - heterogeneity structrues in tasks[age and gender], source[documents and images], feature[generated from model for classification or regression tasks], samples[one labeled with age while another annotated with gender]

1. network with suitabel initialization and learning rate
2. construct feature relationship in network, offering trainable parameters, refer to [cross-stitch network]
3. feature selection, sparsity and factorization, which means that the specific branch layers to ontain task-specific fearures in a common feature space.

## Research directions
* feature relationship from the level of network.
* feature processing from the level fo feature space, such as selection, sparsity and facorization.
