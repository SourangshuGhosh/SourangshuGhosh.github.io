---
layout: default
title: Loss Function
---

## Definition

A **loss function** is a mapping
\[
\mathcal{L} : \mathcal{Y} \times \mathcal{Y} \to \mathbb{R}
\]
that assigns a real-valued penalty to the discrepancy between a *predicted output*
\[
\hat{y} = f_\theta(x)
\]
and a *target output* \( y \).

In the context of learning, the loss function induces an ordering on hypotheses by
quantifying how well a parametric function \( f_\theta \) approximates the desired
input–output relation.

---

## Role in Learning Theory

Learning is typically formulated as a **variational problem**:
\[
\min_{\theta \in \Theta} \; \mathbb{E}_{(x,y)\sim \mathcal{D}}
\big[ \mathcal{L}(f_\theta(x), y) \big],
\]
where:
- \( \mathcal{D} \) is an unknown data-generating distribution,
- \( \Theta \) is the parameter space,
- \( f_\theta \) is a hypothesis from a function class \( \mathcal{F} \).

The loss function therefore serves as:
1. the **objective functional** to be minimized,
2. the **interface** between data and optimization,
3. the **implicit definition of task success**.

---

## Empirical Risk Minimization

Since \( \mathcal{D} \) is unknown, the expected risk is approximated by the
**empirical risk**:
\[
\mathcal{R}_n(\theta)
= \frac{1}{n}\sum_{i=1}^n \mathcal{L}(f_\theta(x_i), y_i),
\]
leading to the **empirical risk minimization (ERM)** problem:
\[
\min_{\theta} \; \mathcal{R}_n(\theta).
\]

The choice of loss function directly affects:
- statistical consistency,
- optimization landscape,
- generalization behavior.

---

## Common Classes of Loss Functions

### Squared Error Loss

\[
\mathcal{L}_{\text{MSE}}(\hat{y}, y)
= \|\hat{y} - y\|^2
\]

Properties:
- smooth and differentiable,
- convex in \( \hat{y} \),
- strongly penalizes large errors.

Often interpreted as arising from **Gaussian noise assumptions**.

---

### Absolute Error Loss

\[
\mathcal{L}_{\text{MAE}}(\hat{y}, y)
= \|\hat{y} - y\|
\]

Properties:
- convex but non-differentiable at zero,
- robust to outliers,
- induces median estimators.

---

### Cross-Entropy Loss

For classification with probabilistic outputs:
\[
\mathcal{L}_{\text{CE}}(p, q)
= -\sum_{k} q_k \log p_k
\]

Interpretation:
- negative log-likelihood,
- measures divergence between distributions,
- tightly linked to information theory.

---

### 0–1 Loss (Idealized)

\[
\mathcal{L}_{0\text{–}1}(\hat{y}, y)
=
\begin{cases}
0 & \text{if } \hat{y} = y, \\
1 & \text{otherwise}.
\end{cases}
\]

This loss is:
- discontinuous,
- non-convex,
- computationally intractable for optimization.

Most practical losses are **surrogates** for this ideal objective.

---

## Mathematical Properties

### Non-negativity

\[
\mathcal{L}(\hat{y}, y) \ge 0
\quad \forall (\hat{y}, y).
\]

Ensures meaningful minimization.

---

### Differentiability

Gradient-based optimization requires:
\[
\nabla_\theta \mathcal{L}(f_\theta(x), y)
\]
to exist almost everywhere.

This requirement excludes many theoretically natural losses.

---

### Convexity

A loss function is convex in \( \hat{y} \) if:
\[
\mathcal{L}(\lambda \hat{y}_1 + (1-\lambda)\hat{y}_2, y)
\le
\lambda \mathcal{L}(\hat{y}_1, y)
+ (1-\lambda)\mathcal{L}(\hat{y}_2, y).
\]

In deep learning:
- losses may be convex in outputs,
- but are **almost never convex in parameters**.

---

### Lipschitz Continuity

A loss is Lipschitz continuous if:
\[
|\mathcal{L}(\hat{y}_1,y)-\mathcal{L}(\hat{y}_2,y)|
\le L\|\hat{y}_1-\hat{y}_2\|.
\]

This property plays a central role in:
- generalization bounds,
- stability analysis,
- robustness guarantees.

---

## Loss Landscape and Optimization

The **loss landscape**
\[
\theta \mapsto \mathcal{R}_n(\theta)
\]
inherits its geometry from:
- the loss function,
- the hypothesis class,
- data distribution.

Key phenomena:
- flat vs sharp minima,
- saddle points,
- plateaus.

The loss function strongly influences:
- gradient magnitudes,
- curvature,
- numerical stability.

---

## Statistical Interpretation

Many losses correspond to **negative log-likelihoods**:
\[
\mathcal{L}(\hat{y}, y)
= -\log p(y \mid \hat{y}).
\]

Thus, minimizing empirical risk corresponds to **maximum likelihood estimation**
under implicit noise assumptions.

The loss function therefore encodes:
- noise model,
- error tolerance,
- inductive bias.

---

## Limitations and Pathologies

### Misalignment with Task Metrics

Optimizing a surrogate loss may not optimize the true task objective
(e.g., accuracy, F1-score).

---

### Sensitivity to Outliers

Losses with unbounded gradients (e.g., squared loss) can be dominated by rare samples.

---

### Implicit Bias

Even with zero training loss, different losses can lead to different solutions
due to:
- geometry of descent,
- interaction with regularization,
- optimization dynamics.

---

## Related Concepts

- [Neural Network](/concepts/neural-network/)
- [Empirical Risk Minimization](/concepts/empirical-risk-minimization/)
- [Gradient Descent](/concepts/gradient-descent/)
- [Backpropagation](/concepts/backpropagation/)
- [Generalization](/concepts/generalization/)
- [Optimization Landscape](/concepts/optimization-landscape/)

---

## Conceptual Summary

The loss function is **not a technical detail**.
It is the **formal definition of learning success**, simultaneously shaping:

- statistical behavior,
- optimization dynamics,
- inductive bias,
- and generalization.

Choosing a loss function is therefore a **modeling decision**, not merely an
implementation choice.
