---
tags:
  - topic/analysis
  - topic/optimization
  - topic/theorems
aliases: [Extreme Value Theorem]
status: good_enough
created: 2025-11-20 18:51
---
# Weierstrass Theorem

## Summary
The **Weierstrass Theorem** (also known as the Extreme Value Theorem) provides the theoretical guarantee that a problem actually has a solution. It states that a **continuous function** defined on a **compact (closed and bounded) set** attains a global minimum and a global maximum.

## Details
### The Theorem
Let $X \subset \mathbb{R}^n$ be a **compact** non-empty set, and let $f: X \to \mathbb{R}$ be a continuous function. Then $f$ has a global minimizer.

### Key Definitions
To apply this, the set $X$ must satisfy two conditions:
1.  **Bounded:** There exists a number $M > 0$ such that the magnitude of every point in the set is limited ($||x|| \le M$ for all $x \in X$).
2.  **Closed:** The set contains all its boundary points (e.g., $[a, b]$ is closed, $(a, b)$ is not).

### Application in Unconstrained Optimization
In unconstrained problems ($X = \mathbb{R}^n$), the domain is **not** bounded, so Weierstrass does not apply directly.

**The "Compactness Trick":**
If the function grows to infinity as we move away from the origin ($f(x) \to \infty$ as $||x|| \to \infty$), we can artificially restrict the search to a large box $[-M, M]$.
1.  Pick a large $M$ such that the minimum must lie inside the box.
2.  The box $[-M, M]$ is compact.
3.  Therefore, a global minimum exists inside the box.
4.  Since it's inside the box (not on the edge), it must be one of our stationary points.

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

