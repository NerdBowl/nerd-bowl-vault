---
tags:
  - topic/optimization
  - topic/setTheory
  - topic/constraint
aliases: []
status: good_enough
created: 2025-12-03 14:07
---
# Feasible Set

## Constraints
A **constraint** is a logical predicate or condition defined on a set of variables $x \in \mathbb{R}^n$ that restricts the domain of valid values.
Formally, a system of constraints defines a subset $\mathcal{F} \subseteq \mathbb{R}^n$, known as the **Feasible Set** (or Feasible Region).
The set $\mathcal{F}$ is defined as:
$$\mathcal{F} = \{ x \in \mathbb{R}^n \mid c_i(x) = 0, \ \forall i \in \mathcal{E} \quad \text{and} \quad c_j(x) \ge 0, \ \forall j \in \mathcal{I} \}$$
Where:
- $c(x)$ are the constraint functions mapping $\mathbb{R}^n \to \mathbb{R}$.
- $\mathcal{E}$ is the index set for **Equality Constraints**.
- $\mathcal{I}$ is the index set for **Inequality Constraints**.
If $\mathcal{F}$ is empty ($\mathcal{F} = \emptyset$), the system is **inconsistent** (or infeasible).

### Equality Constraints
$$c(x) = 0$$
- **Definition:** A restriction that forces the variables to satisfy an exact equation.
- **Geometry:** In $n$-dimensions, a single equality constraint typically reduces the solution space to an $(n-1)$-dimensional surface (a "manifold").
    - In 2D, this is a curve (line, circle, etc.).
    - In 3D, this is a surface (plane, sphere, etc.).
### Inequality Constraint
$$c(x) \ge 0$$
- **Definition:** A restriction that bounds the variables to a specific range or side of a boundary.
- **Geometry:** In $n$-dimensions, a single inequality constraint defines a **region** or **volume** (a "half-space" or interior of a shape).

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

