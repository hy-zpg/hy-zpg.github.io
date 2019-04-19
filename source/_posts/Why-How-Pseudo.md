---
title: Why and How to Use Pseudo
date: 2019-02-22 10:53:37
tags: pesudo labels
categories: Theory
---


* Pseudo labels in multi-task learning
* Pseudo data selection with density and distribution distance

## Pseudo labels
The reason why need to apply pseudo data into model training 
* >reference [CurriculumNet: Weakly Supervised Learning from Large-Scale Web Images](http://openaccess.thecvf.com/content_ECCV_2018/papers/Sheng_Guo_CurriculumNet_Learning_from_ECCV_2018_paper.pdf), demonstrating that training a CNN from scratch using both clean and noisy data is better than just using the clean one, on the condition that the amount of pseudo data is limited.
* >reference [From Facial Expression Recognition to Interpersonal Relation Prediction Zhanpeng](https://arxiv.org/pdf/1609.06426.pdf), stating explaination that pseudo data can bridge the gap between heterogeneous data.
* >reference [Seeing through the Human Reporting Bias: Visual Classifiers from Noisy Human-Centric Labels](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Misra_Seeing_Through_the_CVPR_2016_paper.pdf), 'what's the all attributs of images' versus 'what's the labeled attributes', labeling missing attributes. The novalty may be regarded as a baseline (waiting to understand the detail).
* data imbalance in joint training strategy, such as 20k~ pose dataset AFLW and 90k~ emotion dataset ExpW.


## Pseudo data selection
Because much noisy data can effect the model performance and even disturb the model training process, leading to poor model performance, pseudo data selection can control the ratio of pseudo data in the whole datasets.

### Density
* reason: because clusters are easily detected by the local density of data points, in the pseudo data belong to same categoty have similar feature. Appling a density based clustering algorithm that measures the complexity of psuedo data using data distribution density in. each category.
* implementation detail: measuring the purity of data with pseudo label based on its distribution density in a feature space, and rank the purity to generate pseudo weights, pseudo data with higher density is assigned larger weights, while smaller weights are assigned to low-density pseudo data.

### Distribution distance
* reason: 
 * 'transfer learning is one important method in machine learning, it can relax the condition of the independent identical distribution in train dataset and test dataset, so that knowledge can be transfered from source domain to target domain','its main application includes domain adaptation and multi-domain tranferation'.
 * instance-based domain adaption: calculating the distance between source domain data and target domain data, then adjusting the weights of target domain instance so that the target data can be matched with source domain data. In detail, the smaller distance, the higher similarity.
* implementation detail: 
   1. GMM
     * reason:
     * implementation: generating Gaussian Mixture models (GMM) based on A1 (data with pseuodo label) and B (data with ground truth) in each categoty. Assuming GMM has K Gaussian models, we obtain G(A1_1), ..., G(A1_K), G(B1_1), ..., G(B1_K); 
   2. EMD
     * reason: >reference [Large Scale Fine-Grained Categorization and Domain-Specific Transfer Learning](http://openaccess.thecvf.com/content_cvpr_2018/papers/Cui_Large_Scale_Fine-Grained_CVPR_2018_paper.pdf),  which takes domain scale into account by adding a scale factor. In this paper, transfer learning can be viewed as moving a set of images from the source domain S to the target domain T. The work needed to be done by moving an image to another can be defined as their feature Euaullean distance, so the distance between two domains can be defined as the least amount of total work needed. This definition of domain similarity can be calculated by the Earth Mover’s Distance (EMD). 
       * original EMD equation

	     \begin{aligned}
		 \sum\_{i=1}^{m}\sum\_{j=1}^{n}f\_{i,j}=\min \{\sum\_{i=1}^{m}w\_{pi},\quad \sum\_{j=1}^{n}w\_{qj}\}
		 \end{aligned}

		 \begin{aligned}
		 EMD(P,Q)={\frac {\sum\_{i=1}^{m}\sum\_{j=1}^{n}f\_{i,j}d\_{i,j}}{\sum\_{i=1}^{m}\sum\_{j=1}^{n}f\_{i,j}}}
	     \end{aligned}

		 \begin{aligned}
		 P=\{(p\_{1},w\_{p1}),(p\_{2},w\_{p2}),...,(p\_{m},w\_{pm})\}
		 \end{aligned}

		 \begin{aligned}
		 Q=\{(q\_{1},w\_{q1}),(q\_{2},w\_{q2}),...,(q\_{n},w\_{qn})\}
		 \end{aligned}

	   * reference paper EMD application
		 g(s_{i}) from the mean value of image features in category i from source domain
		 g(t_{i}) from the mean value of image features in category i from target domain
		 \begin{aligned}
		 \sum\_{i=1}^{m}\sum\_{j=1}^{n}f\_{i,j}=\min \{\sum\_{i=1}^{m}w\_{pi},\quad \sum\_{j=1}^{n}w\_{qj}\}
		 \end{aligned}

		 \begin{aligned}
		 EMD(P,Q)={\frac {\sum\_{i=1}^{m}\sum\_{j=1}^{n}f\_{i,j}d\_{i,j}}{\sum\_{i=1}^{m}\sum\_{j=1}^{n}f\_{i,j}}}
	     \end{aligned}

		 \begin{aligned}
		 S=\{(s\_{1},w\_{s1}),(s\_{2},w\_{s2}),...,(s\_{m},w\_{sm})\}
		 \end{aligned}

		 \begin{aligned}
		 T=\{(t\_{1},w\_{t1}),(t\_{2},w\_{t2}),...,(t\_{n},w\_{tn})\}
		 \end{aligned}

		 \begin{aligned}
		 D=[d\_{i,j}] = || g(s\_{i}) − g(t\_{j})|| 
		 \end{aligned}

		 \begin{aligned}
		 sim(S, T) = e−γd(S,T )
		 \end{aligned}

	   * EMD application for pseudo data selection
	   	 $g(p)$ represents mean value of image features in specific cluster from the same category in source domain
	   	 $g(g\_{i})$ is mean value of image features in cluster i from the same category in target domain
	     \begin{aligned}
		 \sum\_{i=1}^{m}\sum\_{j=1}^{n}f\_{i,j}=\min \{\sum\_{i=1}^{m}w\_{pi},\quad \sum\_{j=1}^{n}w\_{qj}\}
		 \end{aligned}

		 \begin{aligned}
		 EMD(P,Q)={\frac {\sum\_{i=1}^{m}\sum\_{j=1}^{n}f\_{i,j}d\_{i,j}}{\sum\_{i=1}^{m}\sum\_{j=1}^{n}f\_{i,j}}}
	     \end{aligned}

		 \begin{aligned}
		 P=\{(p\_{1},w\_{p1}),(p\_{2},w\_{p2}),...,(p\_{m},w\_{pm})\}
		 \end{aligned}

		 \begin{aligned}
		 G=\{(g\_{1},w\_{g1}),(g\_{2},w\_{g2}),...,(g\_{n},w\_{gn})\}
		 \end{aligned}

		 \begin{aligned}
		 D=[d\_{i,j}] = || g(p\_{i}) − g(g\_{j})|| 
		 \end{aligned}

		 \begin{aligned}
		 sim(S, T) = e−γd(S,T )
		 \end{aligned}
     * implementation: calculating the distance between $G(A\_1^i)$ and the whole cluster in G(B1). As for distance calculation with EMD method, we obtain $P={G(A\_1^i)\_{mean},G(A\_1^i)\_{probs}}$ and $Q={[G(B\_1^i)\_{mean}, ..., G(B\_1^K)\_{mean}],[G(B\_1^i)\_{probs}, ..., G(B\_1^K)\_{probs}]}$, so we can calculate distance vector $D=(emd\_1,emd\_k)$, which is used for obtaining distribution weights $weights\_g$.
