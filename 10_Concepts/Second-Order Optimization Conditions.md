---
tags:
  - topic/optimization
  - topic/calculus
aliases: [Second-Order Conditions, SOC]
status: good_enough
created: 2025-11-20 18:46
---

# Second-Order Optimization Conditions

## Summary
When a function is **not** known to be convex, we rely on local information at a stationary point $x^*$ (where $\nabla f(x^*) = 0$) to determine if it is a minimizer, maximizer, or saddle point.

* **Necessary Condition:** If $x^*$ is a local minimizer, then the Hessian must be **Positive Semi-Definite** ($\nabla^2 f(x^*) \succeq 0$).
    * *Warning:* This is necessary but not sufficient (e.g., $f(x)=x^3$ at $x=0$).
* **Sufficient Condition:** If $x^*$ is a stationary point and the Hessian is **Positive Definite** ($\nabla^2 f(x^*) \succ 0$), then $x^*$ is a **strict local minimizer**.

## Details
### The Necessary Condition
If $x^*$ is a local minimizer, the function must "curve up" (or be flat) in all directions.
$$\nabla f(x^*) = 0 \quad \text{AND} \quad \nabla^2 f(x^*) \succeq 0$$

### The Sufficient Condition
If the curvature is strictly positive in all directions, the point is a local valley.
$$\nabla f(x^*) = 0 \quad \text{AND} \quad \nabla^2 f(x^*) \succ 0$$

### Indefinite Case (Saddle Point)
If $\nabla^2 f(x^*)$ has both positive and negative eigenvalues (Indefinite), then $x^*$ is a **saddle point** (min in one direction, max in another).

### Relation to Convexity
These conditions differ from the [[Convexity#Second-Order Condition (Hessian)|Second-Order Condition for Convexity]] in their **scope**:
- **Convexity** requires the Hessian to be PSD for **all** $x$ (Global property).
- **Optimization Conditions** only evaluate the Hessian at the stationary point $x^*$ (Local property).

> **Note:** If a function is convex, the Second-Order Necessary Condition ($\nabla^2 f(x^*) \succeq 0$) is automatically satisfied at any stationary point.

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

