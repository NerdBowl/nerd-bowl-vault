---
tags:
  - topic/line-search
  - topic/optimization
aliases: []
status: good_enough
created: 2025-12-03 14:00
---
# The Golden Section Method in Search

### The Golden Section Method
The bisection method was used to find the optimal step size $\alpha$. Bisection  requires the derivative $\phi '(\alpha)$ to check if the slope is positive or negative. Without derivatives, we use the Golden Section Method.
- **Prerequisites:** The function $\phi(\alpha)$ must be unimodal on the interval $[L, U]$ (it has one unique minimum).
- **Intuition:** To narrow down the interval $[L, U]$ without derivatives, we need to evaluate the function at two internal points, $M$ and $T$. To ensure the interval shrinks by a constant efficient ratio every time regardless of which side holds the minimum, we place these points using the Golden Ratio $\varphi \approx 1.618$.
- **The Algorithm:**
    1. **Initialize:** Bounds $L < M < U$ such that the ratio of segments corresponds to the Golden Ratio (specifically $(M-L)/(U-M) \in \{ \varphi, 1/\varphi \}$).
    2. **Loop** while $(U - L) > \epsilon$:
        - Pick a test point $T$ in the larger sub-interval (between $L$ and $M$ or $M$ and $U$).
        - **Compare** $\phi(T)$ and $\phi(M)$:
            - If $\phi(T) < \phi(M)$: The minimum is in the new smaller region around $T$. $T$ becomes the new "middle" $M$, and the bounds are tightened.
            - If $\phi(T) \ge \phi(M)$: The minimum is likely around $M$. The bounds are tightened to exclude $T$.
    3. **Result:** The interval shrinks linearly by a factor of $1/\varphi \approx 0.618$ per iteration.

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

