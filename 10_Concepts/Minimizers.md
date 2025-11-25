---
tags:
  - topic/optimization
  - topic/calculus
aliases:
  - minimization
  - optimization
status: good_enough
created: <% tp.file.creation_date() %>
---
## Minimizers
### Global Minimizer
Let $X\subseteq \mathbb{R}^n$, and let $f:X\rightarrow\mathbb{R}$ be a function. A point $\mathbf{x}^* \in X$ is a *global minimizer* of $f$ over $X$ such that 
$$
f(\mathbf{x}^*)\le f(\mathbf{x}) \quad \forall \mathbf{x}\in X
$$

### Local Minimizer
Let $X\subseteq \mathbb{R}^n$, and let $f:X\rightarrow\mathbb{R}$ be a functioin. A point $\mathbf{x}^* \in X$ is a *local minimizer* of $f$ over $X$ if there exists an $\epsilon>0$ such that 
$$
f(\mathbf{x}^*)\le f(\mathbf{x}) \quad \forall \mathbf{x}\in X \text{ with } ||\mathbf{x}-\mathbf{x}^*|| < \epsilon 
$$

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

