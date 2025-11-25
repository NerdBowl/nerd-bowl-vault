---
tags:
  - topic/optimization
  - topic/setTheory
aliases: [Convex Analysis, Concavity, Convex Optimization, Convex Function, Concave Function]
status: good_enough
created: 2025-11-20 17:18
---
# Convexity

## Summary
**Convexity** is a geometric property fundamental to optimization and quantitative finance because it guarantees that a local minimum is a global minimum.

* **Convex Set:** A region where a straight line segment connecting *any* two points inside the region remains entirely within the region (no "dents").
* **Convex Function:** A function where the line segment connecting any two points on the graph lies **above** the curve. Intuitively, the function "holds water" like a cup.
* **Concave Function:** The inverse of a convex function ($f$ is concave if $-f$ is convex). The connecting line lies **below** the curve. Intuitively, it "spills water" like a hill.
* **Strict Convexity:** A stronger form where the graph contains no "flat" segments. While a convex function guarantees a global minimum, a strictly convex function guarantees a unique global minimum.


## Details

### Convex Sets
Formally, a set $S \subseteq \mathbb{R}^n$ is **convex** if for any $x, y \in S$ and any $\lambda \in [0, 1]$:

$$
\lambda x + (1 - \lambda)y \in S
$$

This means the weighted average of any two points in the set is also in the set.
* *Note:* There is no standard definition for a "Concave Set." A set is generally either Convex or Non-Convex.

### Convex Functions
A function $f: S \to \mathbb{R}$ is **convex** if its domain $S$ is a convex set and for all $x, y \in S$ and $\lambda \in [0, 1]$:

$$
f(\lambda x + (1 - \lambda)y) \leq \lambda f(x) + (1 - \lambda)f(y)
$$

This is the definition of **[[10_Concepts/Jensen's Inequality|Jensen's Inequality]]**.

#### First-Order Condition (Gradient)
If $f$ is differentiable, it is convex if and only if the graph lies above its tangent hyperplane at all points:

$$
f(y) \geq f(x) + \nabla f(x)^T (y - x)
$$

#### Second-Order Condition ([[10_Concepts/Hessian Matrix|Hessian]])
If $f$ is twice differentiable, it is convex if and only if its Hessian matrix (the matrix of second derivatives) is **Positive Semi-Definite (PSD)** for all $x$ in the domain:

$$
\nabla^2 f(x) \succeq 0
$$

In 1D, this simply means the second derivative is non-negative ($f''(x) \geq 0$).

### Strict Convexity
A function is **strictly convex** if the inequality holds strictly ($<$) for distinct points.
* **Intuition:** The graph has no flat spots (no lines). It is "round" everywhere.
* **Definition:** For $x \neq y$ and $\lambda \in (0, 1)$:

$$
f(\lambda x + (1 - \lambda)y) < \lambda f(x) + (1 - \lambda)f(y)
$$

#### Second-Order Condition (Strict)
If $f$ is twice differentiable, strict convexity usually implies the Hessian is **Positive Definite (PD)** (denoted $\nabla^2 f(x) \succ 0$), meaning all eigenvalues are strictly positive.
* *Crucial Note:* $\nabla^2 f(x) \succ 0$ implies strict convexity, but strict convexity does not require $\nabla^2 f(x) \succ 0$ everywhere (e.g., $f(x)=x^4$ is strictly convex but $f''(0)=0$).

#### Why Strictness Matters
* **Convex:** Local Min = Global Min (but there might be infinite global minima, like a flat valley floor).
* **Strictly Convex:** Local Min = **Unique** Global Min.

### Concave Functions
A function $f$ is **concave** if $-f$ is convex.
* **Inequality:** $f(\lambda x + (1 - \lambda)y) \geq \lambda f(x) + (1 - \lambda)f(y)$
* **Second-Order:** The Hessian is Negative Semi-Definite ($\nabla^2 f(x) \preceq 0$).

---

# Related
```dataviewjs
// Get the tags of the current file
const currentTags = dv.current().file.tags;

// List pages from "10_Concepts"
dv.list(dv.pages('"10_Concepts"')
    .where(p => 
        // 1. Exclude the current file
        p.file.name != dv.current().file.name &&
        // 2. Check if ANY tag in the candidate page exists in currentTags
        p.file.tags.some(t => currentTags.includes(t))
    )
    .limit(10)
    .file.link
)
```

### Direct Links to this document
```dataview
TABLE file.folder AS "Context"
FROM [[#]]
WHERE file.folder != "10_Concepts"
SORT file.folder ASC
```

