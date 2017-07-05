---
title: tensorflow 学习笔记
date: 2017-07-02 22:31:10
tags: 标签
categories: Machine learning

---

# Learning tensorflow step by step with the org guide and sources from website

<!--more-->
## Part 1 install

#### Bosed on linux 14.04 python 2.7
### With GPU
1. virtualenv
    1. sudo apt-get install python-pip python-dev python-virtualenv
    2. go to create a work space
    3. virtualenv --system-site-packages targetDirectory
    4. source ~/tensorflow/bin/activate
    5. (tensorflow)$ pip install --upgrade tensorflow      # for Python 2.7
    6. (tensorflow)$ pip install --upgrade tensorflow-gpu  # for Python 2.7 and GPU
    7. (tensorflow)$ deactivate  # quit virtualenv
    8. rm -r targetDirectory #uninstall 
2. native pip
    1. sudo apt-get install python-pip python-dev
    2. pip install tensorflow 
    3. pip install tensorflow-gpu
    4. sudo pip uninstall tensorflow
3. Anaconda
    1. download Anaconda
    2. conda create -n tensorflow
    3. source activate tensorflow
    4. (tensorflow)$ pip install --ignore-installed --upgrade tfBinaryURL

### With CPU ONLY
1.  sudo apt-get install python-pip python-dev
2. sudo pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.2.1-cp27-none-linux_x86_64.whl

### Test by python program
#### >>> python

```
import tensorflow as tf
hello=tf.constant('hello,tensorflow!')
sess = tf.Session()
print sess.run(hello)
```
#### >>> hello,tensorflow!

## Part 2 Tutorial for beginners

### MNIST (dataset http://yann.lecun.com/exdb/mnist/)
Consists of images of handwritten digits and labels attach to it
If you want to get data from this set 
you should add two lines of codes into your file

```
from tensorflow.examples.tutorials.mnist import input_data
mnist = input_data.read_data_sets("MNIST_data/", one_hot=True)
```
1. Data include( Inorder to learned from separate data)
    1. mnist.train
    2. mnist.test
    3. mnist.validation

images --> "x" mnist.train.images -->array [55000,784] 784=28*28

labels --> "y" mnist.train.labels -->[0,9] array 
one-hot:3[0,0,0,1,0,0,0,0,0]==> [55000,10]

entry in the tensor ranges [0,1]

### Softmax Regression
A list of values between 0 and 1 that add up to 1