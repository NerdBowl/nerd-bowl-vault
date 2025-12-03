---
tags:
  - topic/optimization
aliases: []
status: good_enough
created: 2025-12-03 15:31
---
# Interior Point Method in Constrained Optimization

### Interior Point Method
Unlike the Simplex Method (which moves along boundaries) or the Ellipsoid method (which often stays outside), IPMs approach the optimum through the strictly feasible interior of the set. This is the modern standard for many convex problems. 
- Barrier Functions:
    1. IPMs replace hard constraints with a "barrier function" $\Phi(x)$ added to the objective.
    2. Properties of $\Phi(x)$:
    3. Domain is the interior of the feasible set $X$.
    4. $\nabla^2 \Phi(x) > 0$ (strictly convex).
    5. $\Phi(x) \to \infty$ as $x$ approaches the boundary of $X$
- **Common Barriers:**
    - **Logarithmic Barrier (Polyhedra):** $\Phi(x) = - \sum \log(b_i - a_i^\top x)$
    - **Logarithmic Determinant (PSD Matrices):** $\Phi(X) = - \log(\det X)$
- The Central Path:
    - We minimize the unconstrained penalized objective:
$$x(\mu) = \text{argmin}_x \{ f(x) + \mu \Phi(x) \}$$
    - Here, $\mu > 0$ is the barrier parameter. The set of minimizers $\{ x(\mu) : \mu > 0 \}$ forms a trajectory called the Central Path. As $\mu \to 0$, $x(\mu)$ converges to the constrained optimal solution.


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

