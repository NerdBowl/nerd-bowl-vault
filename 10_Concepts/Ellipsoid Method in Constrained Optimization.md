---
tags:
  - topic/optimization
aliases: []
status: good_enough
created: 2025-12-03 15:30
---
# Ellipsoid Method in Constrained Optimization

### Ellipsoid Method
This algorithm maintains an ellipsoid that is guaranteed to contain the optimal solution. In each step, it cuts the ellipsoid in half, and finds a new smaller ellipsoid containing the remaining feasible half. 

#### Algorithm
1. Start with an ellipsoid $E(z, B)$ that is guaranteed to contain the optimal solution
2. Check the centroid $z$.
	1. If $z$ is feasible: use the gradient of the objective $\nabla f(z)$ to cut off the half-space where the objective is higher (useless regions)
	2. If $z$ is infeasible: Use the gradient of the constraint $\nabla c_i(z)$ to cut off the half space that violates the constraint
3. Construct the smallest new ellipsoid $E(z_+, B_+)$ containing the valid intersection

**Update rule** for a cut defined by vector $a$:
$$z_+ = z + \frac{1}{(n+1)\sqrt{a^\top B a}} Ba$$
$$B_+ = \frac{n^2}{n^2 - 1} \left( B - \frac{2}{(n+1)a^\top B a} B a a^\top B \right)$$

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

