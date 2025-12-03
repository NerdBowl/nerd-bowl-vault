---
tags:
  - topic/optimization
aliases: []
status: good_enough
created: 2025-12-03 15:33
---
# Duality (optimization)

## Duality Theory
Duality associates the original minimization problem (primal) with a maximization problem (Dual). This provides lower bounds and certification of optimality.
### Constructing the Dual
Given the Primal Problem (P):
$$\inf_x f(x) \quad \text{subject to} \quad c_i(x) = 0 \, \forall i \in \mathcal{E}, \quad c_i(x) \ge 0 \, \forall i \in \mathcal{I}$$
1. **Lagrangian Lower Bound:** For any valid Lagrange multipliers $\lambda$, the minimum of the Lagrangian is a lower bound on the primal:
$$q(\lambda) = \inf_x \left\{ f(x) - \sum_{i \in \mathcal{E} \cup \mathcal{I}} \lambda_i c_i(x) \right\}$$
2. **The Dual Problem:** The dual seeks the best (highest) lower bound
$$\sup_\lambda q(\lambda) \quad \text{subject to} \quad \lambda_i \ge 0 \, \forall i \in \mathcal{I}$$

Even if the primal is not convex, the Dual objective $q(\lambda)$ is always concave (and its domain convex), making the dual easier to solve in some cases. 

### Weak Duality
For any feasible $x$ in the Primal and any feasible $\lambda$ in the Dual:
$$f(x)\ge(g(\lambda))$$
This means the optimal value of the Dual is always less than or equal to the optimal value of the primal.

### Strong Duality
Strong duality holds when the optimal values coincide ($f(x^*) = q(\lambda^*)$). This requires specific conditions.

**Theorem**
If the Primal problem (P) is convex and satisfies Slater's Condition, then strong duality holds, and the Dual has an optimal solution.

### Connection to KKT
There is a direct links between KKT points and Duality:
1. If $(x^*,\lambda^*)$ is a KKT point of a convex primal problem, then $\lambda^*$ is an optimal solution to the Dual.
2. We can solve the Dual to find $\lambda^*$, then use it to reconstruct the optimal $x^*$.

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

