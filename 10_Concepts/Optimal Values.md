---
tags:
  - topic/calculus
  - topic/optimization
aliases:
  - maximum
  - minimum
  - infinum
  - extremas
  - extremes
status: good_enough
created: 2025-11-20 11:02
---
## Optimal Values
### Minimum
The *minimum* $\min_{x\in X}f(\mathbf{x})$
- is the smallest $k\in \mathbb{R}$ such that there exists a $\mathbf{x}^*\in X$ for which $f(\mathbf{x}^*)=k$;
- exists if and only if there exists a [[Mathematical Optimization#Global Minimizer|global minimizer]]

### Infinum
The *infinum* $\inf_{x\in X}f(\mathbf{x})$
- is the largest $k\in \mathbb{R} \cup \{ -\infty, +\infty \}$ such that there  $f(\mathbf{x}) \ge k$ for all $\mathbf{x}\in X$;
- always exists;
- Is the theoretical lower bound of the function $f$. A linear function with $a\not=0$ will have a an infinum of $-\infty$, while a minimum does not exist.

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

