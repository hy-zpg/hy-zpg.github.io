---
title: Heterogeneous Multitask
date: 2019-02-26 15:46:30
tags: multitask
categories: Deep learning
---


# Large-scale Heterogeneous Learning in Big Data Analytics
> reference slide [Large-scale Heterogeneous Learning in Big Data Analytics](http://cci.drexel.edu/bigdata/bigdata2014/MTL_BigData_14.pdf)

* multi-task learning
'Multitask learning is an inductive transfer mechanism for improving generalization performance [Caruana, Machine Learning’97]'
* multi-label learning:
* multi-view learning:

## Heterogeneous outputs related to each other with the same set of inputs
> reference-1 [Heterogeneous Multitask Learning with Joint Sparsity Constraints](http://www.cs.cmu.edu/~sssykim/papers/yang_kim_xing_nips09.pdf)
  
  1. probelm: dealing with homogeneous tasks, such as purely regression (continue) or classification (discrete) task, from a common set of high-dimensional feature space. 
  2. method: modeling the joint sparsity as L1/L∞ or L1/L2 norm of the model parameters, achieving joint sparse feature selection.
  3. datasets: discovering genetic markers that influence multiple correlated traits jointly, datasets with different clinical traits including continuous and discrete labels.

## Heterogeneous inputs from multiple domains
> reference-2 [Heterogeneous Multitask Metric Learning
Across Multiple Domains](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8058002&tag=1) [Exploiting High-Order Information in Heterogeneous Multi-Task Feature Learning](https://www.semanticscholar.org/paper/Exploiting-High-Order-Information-in-Heterogeneous-Luo-Tao/1bf6d4b31fa26aa9e0c2b759e6bee9ec718dcae7)

* 'Multitask metric learning (MTML), which can be regarded as a special case of transfer metric learning (TML) by performing transfer across all related domains.'
* 'Heterogeneous transfer learning approaches can be adopted to remedy this drawback by deriving a metric from the learned transformation across different domains'
  1. probelm: inputs from heterogeneous domain can be solved by deriving a metric from the learned transformation from two domains, but pratical aims is to deal with multiple domain by learning the metric from all domains.
  2. method: metrics -> transformation -> subspace -> maximize high-order ovariance among the predictive structures of these domains, because high-order statistics (correlation information), which can only be exploited by simultaneously examining all domains, thus obtaining more reliable feature transformations and metrics.
  3. datasets: Document Categorization, Scene Classification and Image Annotation

## Heterogeneous features for different task
> reference-3 [Semantic Feature Learning for Heterogeneous
Multitask Classification via Non-Negative
Matrix Factorization](http://www.intsci.ac.cn/users/fzzhuang/papers/TOC2017.pdf)
  
  1. problem: different tasks have heterogenous feature in real world.
  2. method: leveraging a non-negative matrix factorization-based multitask method (MTNMF) to learn a common semantic feature space underlying different heterogeneous feature spaces of each task. it is similar to reference-1, feature selection vs feature factorization.
  3. datasets: 20Newsgroups&ImageNet (image and document), Email Spam Detection (15 persons), Sentiment Classification (books;  dvd; electronics; kitchen)

