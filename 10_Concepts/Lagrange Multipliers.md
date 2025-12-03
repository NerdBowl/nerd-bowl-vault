---
tags:
  - topic/optimization
  - topic/economics
aliases:
  - Dual Variables
  - Shadow Prices
status: good_enough
created: 2025-11-20 18:02
---
# Lagrange Multipliers
## Summary
**Lagrange Multipliers** (denoted $\lambda$) are the scalar variables introduced in the **[[10_Concepts/Lagrangian Function]]** to enforce constraints. Geometrically, they represent the scaling factor required to align the gradient of the objective function with the gradient of the [[10_Concepts/Feasible Set#Constraints|constraints]]. Economically, they measure the **sensitivity** of the optimal value to changes in the constraints (often called "Shadow Prices").

## Details

### Geometric Intuition
At an optimal point $x^*$, the gradient of the objective function $\nabla f$ must be parallel to the gradient of the active constraint $\nabla c$. The Lagrange multiplier is the scaling factor $\lambda$ that satisfies:
$$
\nabla f(x) = \lambda \nabla c(x)
$$
* If $\lambda = 0$, the constraint is **Inactive** (it does not restrict the solution).
* If $\lambda \neq 0$, the constraint is **Active**.

### Sensitivity Analysis (Shadow Prices)
Lagrange multipliers have a practical interpretation as the rate of change of the optimal objective value as constraints are relaxed.

If we relax a constraint $c_j(x) = 0$ to $c_j(x) = \epsilon$, the improvement in the objective function $f(x)$ is approximately:
$$
f(x^*(\epsilon)) - f(x^*) \approx \lambda_j^* \epsilon
$$
In other words, $\lambda_j^*$ tells you how much the "cost" decreases if the constraint is loosened by 1 unit.

### Role in KKT Conditions
In the context of the **[[KKT Conditions]]**, multipliers must satisfy specific feasibility rules:
1.  **Dual Feasibility:** For inequality constraints ($c_i(x) \ge 0$), the multiplier must be non-negative ($\lambda_i \ge 0$) to ensure the gradient points "inward" toward the feasible region.
2.  **Complementary Slackness:** $\lambda_i c_i(x) = 0$. This ensures that either the constraint is active ($c_i=0$) or the multiplier is zero.

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

