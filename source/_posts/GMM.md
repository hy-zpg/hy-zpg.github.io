---
title: MMD and Density
date: 2019-01-15 10:31:01
tags: pseudo labels
categories: Theory
---


## Relation between MMD and density for pseudo data selection

combination of MMD and density: my understanding is that we can obtain MMD, density, prior weights from GMM, when GMM can be calculated from ground-trurh label of 

* MMD: first-order information

* Density: second-order information, the larger variance, the sparser, the small variance, the denser 

### GMM

* Gaussian Mixed Model: A Gaussian mixture model is a probabilistic model that assumes all the data points are generated from a mixture of a finite number of Gaussian distributions with unknown parameters. One can think of mixture models as generalizing k-means clustering to incorporate information about the covariance structure of the data as well as the centers of the latent Gaussians.


* Differentce between k-means and GMM: k-means notes that each point is assigned to different clusters, while GMM can calculate the probabiliy of each point belong to each clusters.

* Import parameters of GMM: K Gaussion models, also K clusters, $\pi$, $\mu$, $\Sigma$
\begin{aligned}
p(x) & = \sum\_{k=1}^K p(k)p(x|k) = \sum\_{k=1}^K \pi\_k \mathcal{N}(x|\mu\_k, \Sigma\_k)
\end{aligned}

