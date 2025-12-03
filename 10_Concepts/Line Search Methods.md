---
tags:
  - topic/optimization
  - topic/line-search
aliases: []
status: good_enough
created: 2025-12-03 13:34
---
# Line Search Methods

## Summary
Line search is a strategy for iterative optimization that finds a minimum by moving along a chosen direction. The general update rule is:
$$
x_{k+1} \leftarrow x_{k} + \alpha_{k}p_{k}
$$
where $x_k$ is the current position, $p_k$ is the **search direction**, and $\alpha_k$ is the **step length** (a scalar determining how far to move).

When stationary points cannot be determined analytically, numerical line search algorithms are used to approximate them. 
## Details
Line search is a strategy for iterative optimization that finds a minimum by moving along a chosen direction. The general update rule is:
$$
x_{k+1} \leftarrow x_{k} + \alpha_{k}p_{k}
$$
where $x_k$ is the current position, $p_k$ is the **search direction**, and $\alpha_k$ is the **step length** (a scalar determining how far to move).
### Descent Direction
For the function value to decrease ($f(x_{k+1}) < f(x_k)$), the search direction $p$ must be a **descent direction**. This requires that the angle between the direction and the gradient is obtuse:
$$
\nabla f(x)^T p < 0
$$


### Step Length ($\alpha$)
The step length $\alpha_k$ can be chosen in two ways:
1.  **Exact Line Search:** Finding the $\alpha$ that minimizes $f(x_k + \alpha p_k)$ exactly (e.g., using the [[Bisection Method]]).
2.  **Inexact Line Search:** Choosing an $\alpha$ that provides "sufficient decrease" without solving the full minimization sub-problem.
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

