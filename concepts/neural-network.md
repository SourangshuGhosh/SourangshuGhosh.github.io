---
layout: default
title: Neural Network
---

## Definition

A **neural network** is a parametric function  
$$
f_\theta : \mathbb{R}^n \to \mathbb{R}^m
$$
defined as a composition of affine maps and nonlinear activation functions.

---

## Mathematical Formulation

A feedforward neural network with $L$ layers is given by:
$$
f(x) = W_L \sigma(W_{L-1} \sigma( \cdots \sigma(W_1 x + b_1)) + b_{L-1}) + b_L
$$

---

## Key Properties

- Universal approximation (under assumptions)
- Non-convex parameter space
- High expressive capacity

---

## Limitations

- Poor extrapolation
- Optimization instability
- Sensitivity to initialization

---

## Related Concepts

- [Loss Function](/concepts/loss-function/)
- [Backpropagation](/concepts/backpropagation/)
- [Gradient Descent](/concepts/gradient-descent/)
