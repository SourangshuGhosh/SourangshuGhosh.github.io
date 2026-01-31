---
layout: default
title: Loss Function
---

## Definition

A **loss function** is a mapping
$$
\mathcal{L}: \mathbb{R}^m \times \mathbb{R}^m \to \mathbb{R}
$$
that quantifies the discrepancy between a model prediction and a target output.

---

## Role in Learning

Learning is posed as an optimization problem:
$$
\min_\theta \; \mathbb{E}_{(x,y)}[\mathcal{L}(f_\theta(x), y)]
$$

---

## Properties

- Non-negativity
- Differentiability (often assumed)
- Convexity (rare in deep models)

---

## Limitations

- Choice induces bias
- Poor alignment with task metrics
- Sensitivity to outliers

---

## Related Concepts

- [Neural Network](/concepts/neural-network/)
- [Gradient Descent](/concepts/gradient-descent/)
- [Empirical Risk Minimization](/concepts/empirical-risk-minimization/)
