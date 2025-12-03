---
tags:
  - topic/line-search
  - topic/optimization
aliases: []
status: not_started
created: 2025-12-03 13:56
---
# Optimal Step Lengths in [[Line Search Methods]]
## Optimal Step Length
Most of the time, step lengths are fixed or decaying. However, the most effective methods find the optimal step length $\alpha$ that minimizes the function along the search direction. This is a 1D optimization problem: 
$$
\min_{\alpha>0}\phi(\alpha) \quad \text{where} \quad \phi(\alpha)=f(x_{k}+\alpha p_{k})
$$
### The bisection method
This method finds a [[Gradients#Stationary Points|stationary point]] of $\phi(\alpha)$ by iteratively narrowing down an interval $[L,U]$ that contains the minimum. 
Prerequisites:
- $p$ must be a descent direction, implying $\phi'(0)<0$
- We must identify an interval $[L, U]$ such that the slope at $L$ is negative ($\phi'(L) < 0$) and the slope at $U$ is positive ($\phi'(U) > 0$). This guarantees a local minimizer exists between them.

**Algorithm** (Similar to Binary Search)
- **Initialize:** Interval $[L, U]$ and tolerance $\delta > 0$.
- **While** $(U - L) > \delta$:
    - Calculate midpoint: $M = \frac{1}{2}(L + U)$.
    - Calculate the derivative (slope) at the midpoint: $\phi'(M) = \nabla f(x_k + M p_k)^\top p_k$.
    - Case 1: If $\phi'(M) < 0$, the function is still sloping down. The minimum is to the right of $M$. Update: $L \leftarrow M$
    - Case 2: If $\phi'(M) > 0$, the function is sloping up. The minimum is to the left of $M$. Update:  $U \leftarrow M$
    - Case 3: If $\phi'(M) = 0$, $M$ is the stationary point. Update:  $L \leftarrow M, \quad U \leftarrow M$
- **Return:** $\frac{1}{2}(L + U)$ as the approximate optimal step length.


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

