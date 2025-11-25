---
tags:
  - topic/optimization
  - topic/calculus
aliases:
  - optimization
status: good_enough
created: 2025-11-20 14:45
---

# Fermat's Theorem (Optimization)

## Fermat's Theorem
Fermat's Theorem states that if a differentiable function $f$ has a local extremum ([[Optimal Values|minimum]] or maximum) at a point $x^*$, and $x^*$ is an **interior point** of the domain, then the [[Gradients|gradient]]) at that point must be zero:
$$\nabla f(x^*) = 0$$
This establishes that all interior extrema are [[Gradients#Stationary Points|stationary points]].

## Details
### Constraints vs. Unconstrained
The theorem **only** holds for unconstrained problems or interior solutions of constrained problems.
* **Interior:** $\nabla f = 0$ (Fermat applies).
* **Boundary:** $\nabla f \neq 0$ (Fermat fails; requires [[10_Concepts/Lagrange Multipliers|Lagrange Multipliers]]).

### Intuition
If the slope were not zero, you could move slightly in the direction of the slope to find a lower (or higher) value, implying the current point is not an extremum.

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

