---
title: Cross-stitch-network
date: 2019-02-27 14:03:23
tags: multitask
categories: Deep learning
---

## cross-stitch-network
> reference CVPR 2016[Cross-stitch Networks for Multi-task Learning](https://arxiv.org/pdf/1604.03539.pdf) [tensorflow-code](https://github.com/helloyide/Cross-stitch-Networks-for-Multi-task-Learning/blob/master/gender_age_multi_task_learning.py)

* problem: existing multi-task approaches rely on enumerating multiple net- work architectures specific to the tasks at hand, that do not generalize.
* method: proposing a new sharing unit: “cross-stitch” unit. These units combine the activations from multiple networks.


## self-defined cross-stitch layer in keras with tensorflow as backbone
``` bash
class Cross_stitch(Layer):
	# basic parameter setting
    def __init__(self,input_shape_1,input_shape_2, **kwargs):
        super(Cross_stitch, self).__init__(**kwargs)
        self.input_shape_1 = input_shape_1
        self.input_shape_2 = input_shape_2
    # apply trainable parameters in network, similar to convolutional layer 
    # shape is important, you must to calculate specific size based on the shape of input and output
    # in cross-stitch network: [xa,xb]*[papameter]=[xa',xb'], the detail refer to the paper
    def build(self, input_shape):
        shape = self.input_shape_1 + self.input_shape_2
        self.cross_stitch = self.add_weight(
            shape=(shape,shape),
            initializer=tf.initializers.identity(),
            name='cross_stitch')
        self.built = True
    # conduct implement of the detailed algorithm calculation
    # inputs represent the output of upper layer, such as x=Dense(parameter)(inputs)
    def call(self,inputs):
        inputss = tf.concat((inputs[0], inputs[1]), axis=1)
        output = tf.matmul(inputss, self.cross_stitch)
        output1 = tf.reshape(output[:,:self.input_shape_1],shape=[-1,self.input_shape_1])
        output2 = tf.reshape(output[:,self.input_shape_2:],shape=[-1,self.input_shape_2])
        return [output1, output2]
    def get_config(self):
        config = {'input_shape_1': self.input_shape_1,'input_shape_2': self.input_shape_2}
        base_config = super(Cross_stitch, self).get_config()
        return dict(list(base_config.items()) + list(config.items()))
```