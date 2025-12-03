---
tags:
  - topic/optimization
aliases: []
status: good_enough
created: 2025-12-03 15:28
---
# Cutting Plane Method In [[Mathematical Optimization|Constrained Optimization]]

### Cutting Plane Method
This method iteratively refines the feasible region by adding linear constraints that remove infeasible areas without excluding the optimal solution. 

#### Theoretical Basis
For a convex differentiable function $f$, the first-order condition implies the function always lies above its tangent plane. Similarly, for a convex constraint function $-c(x)$ feasible points satisfy linear inequalities derived from the gradient. 

#### Algorithm
The method approximates the problem by ignoring difficult non-linear constraints initially, solving a simpler linear problem, and then adding constraints if the solution violates the original constraints. 

###### Steps
1. Initialize $k\leftarrow 0$
2. While the current solution is infeasible do:
	1. Find an optimal solution $x_{k}$ to the current simpler problem
	2. If a non-linear constraint is violated
		1. Add the linear cut constraint: $c(x_k) + \nabla c(x_k)^\top (x - x_k) \ge 0$.
3. $k \leftarrow k+1$

#### Handling Convex Objectives
The basic algorithm handles non-linear constraints, but if the objective function $f(x)$ is convex and non-linear, we cannot solve it directly with a linear solver. The "trick" is to transform the problem by introducing a new variable $t$.
- Rewrite $\min f(x)$ as $\min t$ subject to the constraint $t - f(x) \ge 0$
- This effectively turns the non-linear objective into a non-linear constraint. The algorithm then minimizes the linear objective $t$ and adds linear cuts to approximate the constraint $t \ge f(x)$ whenever it is violated.

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

