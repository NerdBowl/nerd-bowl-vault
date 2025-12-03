---
tags:
  - topic/optimization
aliases: []
status: good_enough
created: 2025-12-03 15:49
---
# Lagrangian Function

## Summary
The **Lagrangian Function** (or simply "The Lagrangian") is a helper function used in **Constrained Optimization** to combine the objective function and constraints into a single, unconstrained equation. It serves as the foundation for finding optimal solutions via the **[[KKT Conditions]]** and for establishing **[[Duality (optimization)]]**.

## Details

### Definition
For a primal minimization problem with objective $f(x)$, equality constraints $i \in \mathcal{E}$, and inequality constraints $i \in \mathcal{I}$, the Lagrangian $\mathcal{L}(x, \lambda)$ is defined as:

$$
\mathcal{L}(x, \lambda) = f(x) - \sum_{i \in \mathcal{E} \cup \mathcal{I}} \lambda_i c_i(x)
$$

Where:
* $f(x)$ is the objective function.
* $c_i(x)$ are the constraint functions.
* $\lambda_i$ are the **[[Lagrange Multipliers]]**.

### Role in Optimization
Finding the minimizer of the constrained problem is mathematically related to finding the **stationary point** of the Lagrangian.

##### **First-Order Condition (Stationarity):**
A necessary condition for optimality is that the gradient of the Lagrangian with respect to $x$ is zero:
$$
\nabla_x \mathcal{L}(x^*, \lambda^*) = \nabla f(x^*) - \sum \lambda_i^* \nabla c_i(x^*) = 0
$$

##### **Second-Order Condition (Hessian):**
To verify if a stationary point is a minimizer (especially in non-convex problems), we examine the **Lagrangian Hessian**:
$$
\nabla^2 \mathcal{L}(x^*, \lambda^*) = \nabla^2 f(x^*) - \sum \lambda_i^* \nabla^2 c_i(x^*)
$$
* **Necessary:** For a local minimizer, $\nabla^2 \mathcal{L}$ must be Positive Semi-Definite (PSD) on the tangent subspace of active constraints.
* **Sufficient:** If $\nabla^2 \mathcal{L}$ is Positive Definite (PD) on that subspace, $x^*$ is a strict local minimizer.

### Connection to Duality
The Lagrangian allows us to define the **Dual Function** $q(\lambda)$, which provides a lower bound on the primal problem:
$$
q(\lambda) = \inf_x \mathcal{L}(x, \lambda)
$$

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

