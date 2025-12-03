---
tags:
  - topic/optimization
aliases: []
status: good_enough
created: 2025-12-03 15:53
---
# Constraint Qualifications

### Constraint Qualification
The [[KKT conditions ]]are not automatically true for every minimizer. To rely on KKT, one of the following Constraint Qualifications must hold.

#### Slater's Condition (for convex problems)
**Problem Definition**
- Objective $f$ is convex
- Equality constraints are affine ($a_i^Tx + b_i = 0$).
- Inequality constraints are concave ($-c_{i}$ is convex).
**The Condition**
Slater's condition is satisfied if there exists a point $x^{*}$ such that:
- The equality constraints are satisfied: $c_{i}(x^{*})=0$ for all $i\in\mathcal{E}$.
- The inequality constraints are strictly satisfied: $c_{i}(x^{*})>0$ for all $i\in\mathcal{I}$.

**Implication**
If Slater's conditions holds for a convex problem, KKT conditions are necessary and sufficient for global optimality. 

#### Linear Independence Constraint Qualification (LICQ)
This is a more general condition for non-convex problems:
**Definition** LICQ holds at $x^*$ if the gradients of all **active** constraints $\{\nabla c_i(x^*) : i \in \mathcal{E} \text{ or } (i \in \mathcal{I} \text{ and } c_i(x^*)=0)\}$ are linearly independent .
**Implication** If LICQ holds at a local minimizer, the KKT conditions must hold.

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

