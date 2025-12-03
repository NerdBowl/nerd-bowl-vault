---
tags:
  - topic/optimization
aliases: []
status: good_enough
created: 2025-12-03 15:55
---
### KKT Conditions
The KKT conditions act as the necessary "first derivative test" for constrained optimization.
**Theorem:** If $x^*$ is a local minimizer and a constraint qualification holds, there exist Lagrange multipliers $\lambda_i^*$ such that the following four conditions are met 1:
1. Stationarity: The gradient of the Lagrangian with respect to $x$ is zero.
$$\nabla_x \mathcal{L}(x^*, \lambda^*) = \nabla f(x^*) - \sum_{i \in \mathcal{E} \cup \mathcal{I}} \lambda_i^* \nabla c_i(x^*) = 0$$
(This is equivalently written in the slides as $\nabla f(x^) = \sum \lambda_i^* \nabla c_i(x^)$).
2. Primal Feasibility: The point must satisfy the original physical constraints.
$$c_i(x^*) = 0, \forall i \in \mathcal{E}; \quad c_i(x^*) \geq 0, \forall i \in \mathcal{I}$$

3. Dual Feasibility: The multipliers for inequality constraints must be non-negative (ensuring the gradient points "inward").
$$\lambda_i^* \geq 0, \quad \forall i \in \mathcal{I}$$
4. Complementary Slackness: A constraint is either active ($c_i=0$) or its multiplier is zero ($\lambda_i=0$).
$$\lambda_i^* c_i(x^*) = 0, \quad \forall i \in \mathcal{I}$$

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

