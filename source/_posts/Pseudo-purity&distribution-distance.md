---
title: Pseudo Purity and Dataset Distribution Distance
date: 2019-02-17 18:07:47
tags: pesudo labels
categories: Theory
---

## Purity and distribution distance based density 
### Data density

>reference  ECCV 2018 [ CurriculumNet: Weakly Supervised Learning from Large-Scale Web Images](http://openaccess.thecvf.com/content_ECCV_2018/papers/Sheng_Guo_CurriculumNet_Learning_from_ECCV_2018_paper.pdf)

#### creativity
1. leveraging data distribution density in feature space to evaluate the complexity of the data
    ours -- evaluating the purity of pseudo label data by data density in feature space
2. noisy data can be regared as regularied method to improve the model generalization
    ours -- pesudo labels can improve the model generalization 
    
#### technical detail
1. density based clustering algorithm
     * generating features
     * calculating Euclidean distance D_ij
       * calculating local density of each image
       * calculating distance of each image: maximun local distance is regarded as cluster centre, image with smaller distance between its distance and cluster centre represents that its label have high confidence 

### Data distribution distance EMD
> reference IJCV 2000 [The Earth Mover's Distance as a Metric for Image Retrieval](http://robotics.stanford.edu/~rubner/papers/rubnerIjcv00.pdf)

#### definition
1. EDM: Signature matching can be naturally cast as a transportation problem by de fining one signature as the supplier and the other as the consumer, and by setting the cost for a supplier-consumer pair to equal the ground distance between an element in the fi rst signature and an element in the second
2. signature: 
\begin{aligned}
s= (feature,weights)
\end{aligned}



## Purity and distribution distance based gmm

### GMM with EM
*  original definition
\begin{aligned}
p(x) & = \sum\_{k=1}^K p(k)p(x|k) = \sum\_{k=1}^K \pi\_k \mathcal{N}(x|\mu\_k, \Sigma\_k)
\end{aligned}

$\pi\_k$  represent the possibility of sample belong to kth category

* new definition for coding
\begin{aligned}
 \sum\_{k} z_k = 1
\end{aligned}



