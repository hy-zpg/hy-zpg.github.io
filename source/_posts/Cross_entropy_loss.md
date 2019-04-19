---
title: Cross Entropy Loss
date: 2019-01-16 10:37:13
tags: tensorflow
categories: Deep learning
---

## Cross entropy loss calculation in different circumstances

* Cross_entropy_loss in tensorflow
``` bash
def softmax_cross_entropy_with_logits(
    _sentinel=None,  # pylint: disable=invalid-name
    labels=None,
    logits=None,
    dim=-1,
    name=None):
  _ensure_xent_args("softmax_cross_entropy_with_logits", _sentinel, labels,
                    logits)
  with ops.name_scope(name, "softmax_cross_entropy_with_logits_sg",
                      [logits, labels]) as name:
    labels = array_ops.stop_gradient(labels, name="labels_stop_gradient")
  return softmax_cross_entropy_with_logits_v2(
      labels=labels, logits=logits, dim=dim, name=name)
def softmax_cross_entropy_with_logits_v2(
    _sentinel=None,  # pylint: disable=invalid-name
    labels=None,
    logits=None,
    dim=-1,
    name=None):
  _ensure_xent_args("softmax_cross_entropy_with_logits", _sentinel, labels,
                    logits)
  with ops.name_scope(name, "softmax_cross_entropy_with_logits",
                      [logits, labels]) as name:
    logits = ops.convert_to_tensor(logits, name="logits")
    labels = ops.convert_to_tensor(labels, name="labels")
    convert_to_float32 = (
        logits.dtype == dtypes.float16 or logits.dtype == dtypes.bfloat16)
    precise_logits = math_ops.cast(
        logits, dtypes.float32) if convert_to_float32 else logits
    # labels and logits must be of the same type
    labels = math_ops.cast(labels, precise_logits.dtype)
    input_rank = array_ops.rank(precise_logits)
    shape = logits.get_shape()
    if dim is not -1:
      def _move_dim_to_end(tensor, dim_index, rank):
        return array_ops.transpose(
            tensor,
            array_ops.concat([
                math_ops.range(dim_index),
                math_ops.range(dim_index + 1, rank), [dim_index]
            ], 0))
      precise_logits = _move_dim_to_end(precise_logits, dim, input_rank)
      labels = _move_dim_to_end(labels, dim, input_rank)
    input_shape = array_ops.shape(precise_logits)
    precise_logits = _flatten_outer_dims(precise_logits)
    labels = _flatten_outer_dims(labels)
    cost, unused_backprop = gen_nn_ops.softmax_cross_entropy_with_logits(
        precise_logits, labels, name=name)
    output_shape = array_ops.slice(input_shape, [0],
                                   [math_ops.subtract(input_rank, 1)])
    cost = array_ops.reshape(cost, output_shape)
    if not context.executing_eagerly(
    ) and shape is not None and shape.dims is not None:
      shape = shape.as_list()
      del shape[dim]
      cost.set_shape(shape)
    if convert_to_float32:
      return math_ops.cast(cost, logits.dtype)
    else:
      return cost
```

* Cross_entropy_loss in Keras with backbone of tensorflow
``` bash
tf.nn.softmax_cross_entropy_with_logits(labels=target,logits=output)
```

## The reason why the value of loss become inf
* log(x) when x -> 0
* learning rate is too high
* some parameters of Nel appear inf
* input data appear inf
* the parameters of model no longer updated 


## Cross_entropy_loss with missing labels

* leveraging fixed zero array or ones array as ground truth and generating mask in loss function
``` bash
def mask_cross_entropy_loss(y_true,y_pred):
	mask=K.all(K.equal(y_true,0),axis=-1)
	mask=1-K.cast(mask,K.floatx())
	loss = K.categorical_crossentropy(y_true,y_pred)*mask
	return (K.sum(loss)/K.sum(mask)
``` 

* corresponding accuracy with mask
``` bash
def mask_cross_entropy_acc(y_true,y_pred):
	mask=K.all(K.equal(y_true,0),axis=-1)
	mask=1-K.cast(mask,K.floatx())
	acc = K.cast(K.equal(K.argmax(y_true,axis=-1),K.argmax(y_pred,axis=-1)),K.floatx()))*mask
	return (K.sum(acc)/K.sum(mask)
``` 
