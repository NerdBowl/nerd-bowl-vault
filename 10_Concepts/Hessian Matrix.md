---
tags:
  - topic/optimization
  - topic/linear-algebra
aliases: [Hessian, Second Derivative Matrix, Curvature Matrix]
status: good_enough
created: 2025-11-20 17:48
---

# Hessian Matrix

## Summary
The **Hessian Matrix** is a square matrix of second-order partial derivatives of a scalar-valued function. It describes the **local curvature** of a function of many variables.

While the **Gradient** vector points to the direction of steepest ascent (slope), the **Hessian** tells us how that slope is changing (curvature).

It is the multivariate equivalent of the second derivative $f''(x)$.

## Details

### Definition
For a function $f: \mathbb{R}^n \to \mathbb{R}$, the Hessian matrix $\mathbf{H}$ (or $\nabla^2 f$) is an $n \times n$ matrix where the element in the $i$-th row and $j$-th column is:

$$
\mathbf{H}_{ij} = \frac{\partial^2 f}{\partial x_i \partial x_j}
$$

### Symmetry (Schwarz's Theorem)
If the second partial derivatives are continuous, the order of differentiation does not matter ($\frac{\partial^2 f}{\partial x_i \partial x_j} = \frac{\partial^2 f}{\partial x_j \partial x_i}$).
* Therefore, the Hessian is a **Symmetric Matrix**.
* This implies it has real eigenvalues and orthogonal eigenvectors.

### The Second Derivative Test (Optimization)
At a critical point (where Gradient $\nabla f = 0$), the eigenvalues of the Hessian determine the nature of the point ([[10_Concepts/Matrix Definiteness]]):
* **Positive Definite ($\succ 0$):** All eigenvalues $> 0$. The point is a **Local Minimum** (Bowl shape).
* **Negative Definite ($\prec 0$):** All eigenvalues $< 0$. The point is a **Local Maximum** (Hill shape).
* **Indefinite:** Eigenvalues are mixed (some $+$, some $-$). The point is a **Saddle Point**.


### 4. Quadratic Approximation
The Taylor expansion of $f$ near a point $x$:
$$
f(x + \Delta x) \approx f(x) + \nabla f(x)^T \Delta x + \frac{1}{2} \Delta x^T \mathbf{H}(x) \Delta x
$$

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

