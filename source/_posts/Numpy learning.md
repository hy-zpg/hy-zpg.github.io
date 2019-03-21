---
title: Numpy learning
date: 2019-01-14 22:25:55
tags: numpy
categories: Codes
---

One-hot labels preprocessing

* Weighting samples with confidence score
``` bash
index = np.ragmax(predicted_result,axis=1)
arg = np_utils.to_categorical(index,classes)
weighted_one_hot=predicted_result*arg
```

* Selection && weighting samples with confidence score
``` bash
weighted_selected_one_hot=np.where(predicted_result>k,predicted_result,0)
```

* Extending vector into matrix
``` bash
xx = [np.full(classes,value) for value in x]
```


