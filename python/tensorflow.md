# TensorFlow Usage Guide

TensorFlow is a powerful open-source library for developing and training deep learning and machine learning models. In this guide, we will explain key concepts and basic usage of TensorFlow to help you get started.

## Installation and Version Check

To install TensorFlow, use the following command:

```bash
pip install tensorflow
```

```python
import tensorflow as tf

print(tf.__version__)
```
## tensorflow basics
```python
import tensorflow as tf

# Define constants
a = tf.constant(5)
b = tf.constant(3)

# Define operations
sum = tf.add(a, b)

# Start a session
with tf.Session() as sess:
    result = sess.run(sum)
    print("Sum:", result)
