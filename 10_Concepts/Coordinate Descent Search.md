---
tags:
  - topic/line-search
  - topic/optimization
aliases: []
status: good_enough
created: 2025-12-03 13:58
---
# Coordinate Descent [[Line Search Methods|Search]]
### Coordinate Descent
Instead of calculating a specific descent direction $p_{k}$, using a gradient, this method cycles through the dimensions of the coordinates changing one value at a time to find the direction to move to find the minimum. 

Imagine standing on a hill, and instead of looking where downhill is, you feel by moving left and right, and then choosing the direction that minimized your height. Then you move forward and backwards and minimize your height again. 

**Algorithm**
- Initialize starting point
- Cycle through dimensions / directions
- For each dimensions / direction $p_{k}$, perform a line search to find the optimal step length
- Repeat until convergence

Cycling through dimensions can be done:
- $\texttt{cyclic}$: ($1 \dots n \quad \text{repeat}$);
- $\texttt{back-and-forth}$: ($1 \dots n \dots 1 \quad \text{repeat}$);
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

