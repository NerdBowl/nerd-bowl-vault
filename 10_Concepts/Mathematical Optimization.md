---
tags:
  - topic/optimization
aliases:
  - optimization
status: good_enough
created: 2025-11-20 11:02
---
# Mathematical Optimization

## Definition
Mathematical optimization problems are problems of the form 
$$
\min_{{\mathbf{x}\in X}}f(\mathbf{x)}
$$
where $f:X\rightarrow \mathbb{R}$ is a function, and $X \subseteq \mathbb{R}^n$ is a set. 
- If $X=\mathbb{R}^n$, we call the problem *unconstrained*
- If $X\not=\mathbb{R}^n$, we call the problem *constrained*
In particular if $X$ is a polyhedron and $f$ is linear, the optimization problem is *linear*.

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

