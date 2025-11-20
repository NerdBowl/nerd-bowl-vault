---
tags:
  - topic/calculus
  - topic/optimization
aliases: []
status: good_enough
created: 2025-11-20 14:57
---
## Gradient
Let $f : \mathbb{R}^n \to \mathbb{R}$ be partially differentiable at some point $\mathbf{x}^* \in \mathbb{R}^n$. Then, the $\textbf{gradient}$ of $f$ at $\mathbf{x}^*$ is

$$
\nabla f(\mathbf{x}^*) := \begin{bmatrix} 
\frac{\partial f(\mathbf{x}^*)}{\partial x_1} \\ 
\vdots \\ 
\frac{\partial f(\mathbf{x}^*)}{\partial x_n} 
\end{bmatrix}
$$

## Stationary Points
Any point $\mathbf{x}^*$ where $\nabla f(\mathbf{x}^*)=0$ is called stationary.

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

