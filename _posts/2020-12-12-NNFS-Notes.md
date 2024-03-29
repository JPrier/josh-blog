---
toc: true
layout: post
description: Notes from NNFS
categories: [Studying]
title: Notes From NNFS
---

Wanting to relearn the ML basics from my university degree I started going through the course [Neural Networks From Scratch](https://nnfs.io/).

This post contains my notes and learnings from the course.


## The Basics of a Layer

A layer of a neural network contains 1 or more *neurons*, these neurons will take a vector (or matrix with batches) as input and have a vector of weights to multiply by each of the inputs and a bias to add to the input*weights.

```python

input = [1, 2]
weights = [1,2]
bias = 1

# output of a single neuron
output = inputs*weights + bias
```

This is easily scaled up to multiple neurons with matrices

```python
import numpy as np

inputs = [1.0, 2.0, 3.0, 2.5]
weights = [[0.2, 0.8, -0.5, 1],
           [0.5, -0.91, 0.26, -0.5],
           [-0.26, -0.27, 0.17, 0.87]]
biases = [2.0, 3.0, 0.5]

layer_outputs = np.dot(weights, inputs) + biases
```

> Tip: numpy `shape` has an out to in order s.t. in `shape(x,y)` x is the size of the outmost dimension and y is the size of the most inner dimension

Each layer is essentially the dot product the weights and the previous layer's output (input data for the first layer)

## Batches

In the previous examples we take a vector as an input `input = [1,2]`. This vector is a single object in our dataset, this can be an image of a dog, the values a house sold, (x,y) values of a point, or anything else. Each value is a feature of the object, a feature describes some aspect of the object. In the case of points on a 2d graph the features for the objects would be the x and y coordinates of each point so our input in this case would be [x, y].

We do not want to pass a single object as input for each pass of the neural network, this would be slow and would take forever for large datasets. Instead of passing single objects we can pass multiple objects at once in what is called a **batch**.

A batch will contain 2 or more vectors, typically we have batch sizes of 16-64 with 32 being common.
Too small of a batch size will cause the neural network to underfit, this is due to the model not getting enough information in each pass causing it to make too large of a change to the parameters on each pass. 
Too large of a batch size will cause the neural network to overfit, this is due to it fitting to too much of the sample data at once which will cause the test accuracy to be much lower.


## Activation Functions

### The Basics

The activation function is a tool to adjust how and when a neuron of the network should activate. A network will typically use a different activation function between the output and hidden layers.

We use the activation function with the calculation of the weights, inputs, and bias per neuron
```python
output = Activaiton(weights*input + bias)
```

### Step Function
A simple activation function is the step function

```python
x = weights*inputs + bias
if x > 0
  y = 1
else 
  y = 0
```
The step function is a binary on or off for a neuron, 1 or 0 depending on the value of the calculation

### Linear Activation Function

### Sigmoid Function

### ReLU
