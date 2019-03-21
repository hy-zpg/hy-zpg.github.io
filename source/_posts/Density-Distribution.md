---
title: Density & Distribution
date: 2019-02-21 15:46:01
tags: pesudo labels
categories: Theory
---

## Purity based density & distribution distance based GMM 

### Purity based density
>reference：ECCV 2018 [CurriculumNet: Weakly Supervised Learning from Large-Scale Web Images](http://openaccess.thecvf.com/content_ECCV_2018/papers/Sheng_Guo_CurriculumNet_Learning_from_ECCV_2018_paper.pdf)

>original reference： Science 2004 [Clustering by fast search and find of density peaks](http://sites.psu.edu/mcnl/files/2017/03/9-2dhti48.pdf)


#### Creativity
* leveraging data distribution density in feature space to evaluate the complexity of the data
ours -- evaluating the purity of pseudo label data by data density in feature space
* noisy data can be regared as regularied method to improve the model generalization
ours -- pesudo labels can improve the model generalization 

#### Technical detail
Density based clustering algorithm
* generating features
* calculating Euclidean distance D_ij
* calculating local density of each image
* calculating distance of each image: maximun local distance is regarded as cluster centre, image with smaller distance between its distance and cluster centre represents that its label have high confidence 


### Distribution distance based GMM 
#### Clustring based GMM
##### GMM with EM
*  original definition
\begin{aligned}
p(x) & = \sum_{k=1}^K p(k)p(x|k) = \sum_{k=1}^K \pi_k \mathcal{N}(x|\mu_k, \Sigma_k)
\end{aligned}
\pi_k  represent the possibility of sample belong to kth category

* new definition for coding
\begin{aligned}
\sum_{k} z_k = 1
\end{aligned}

##### Related code
* [sklearn.mixture.GaussianMixture](https://scikit-learn.org/stable/modules/generated/sklearn.mixture.GaussianMixture.html)

#### Data distribution distance EMD
> reference： [ Large Scale Fine-Grained Categorization and Domain-Specific Transfer Learning](http://openaccess.thecvf.com/content_cvpr_2018/papers/Cui_Large_Scale_Fine-Grained_CVPR_2018_paper.pdf)
> original reference： [The Earth Mover's Distance as a Metric for Image Retrieval](http://robotics.stanford.edu/~rubner/papers/rubnerIjcv00.pdf)

*  EDM definition: Signature matching can be naturally cast as a transportation problem by de fining one signature as the supplier and the other as the consumer, and by setting the cost for a supplier-consumer pair to equal the ground distance between an element in the fi rst signature and an element in the second

*  EMD data signature:
\begin{aligned}
s= (feature,weights)
\end{aligned}

* related code
* [general EMD](https://github.com/chalmersgit/EMD) [expaination](http://homepages.inf.ed.ac.uk/rbf/CVonline/LOCAL_COPIES/RUBNER/emd.htm)
* [pyemd-1D data](https://pypi.org/project/pyemd/)
* [scipy.atats.wasserstein_distance](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.wasserstein_distance.html)



 
 






