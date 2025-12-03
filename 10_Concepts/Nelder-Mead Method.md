---
tags:
  - topic/line-search
  - topic/optimization
aliases: []
status: good_enough
created: 2025-12-03 14:03
---
# Nelder-Mead Method

### Nelder-Mead Simplex Method
This method is a 'direct search' method that does not approximate gradients but rather evolves a geometric shape to find the minimum. 

#### The Simplex
A simplex is a generalization of a triangle to $n$-dimensions. It consists of $n+1$ vertices.
- In 2D: A triangle (3 points).
- In 3D: A tetrahedron (4 points).

#### [The Algorithm](https://www.youtube.com/watch?v=j2gcuRVbwR0)
The method iteratively improves the worst point in the simplex.
**Preparation:**
1. Initialize $n+1$ vertices.
2. **Order** them such that $f(x_1) \le f(x_2) \le \dots \le f(x_{n+1})$.
    - $x_1$: Best point.
    - $x_{n+1}$: Worst pointt
3. Compute the **Centroid** $\bar{x}$ of the _best_ $n$ points (excluding the worst)
**Iteration Steps** The algorithm attempts to replace the worst point $x_{n+1}$ using the following logic:
4. **Reflection ($r$):**
    - Reflect the worst point through the centroid: $r = \bar{x} + (\bar{x} - x_{n+1})$.
    - _Intuition:_ If the worst point is high up a hill, the minimum is likely on the opposite side of the average.
    - _Decision:_ If $f(x_1) \le f(r) < f(x_n)$, accept $r$.
5. **Expansion ($e$):**
    - If the Reflection $r$ is the new **best** point ($f(r) < f(x_1)$), we have found a very good direction. Go further.
    - Compute $e = \bar{x} + 2(\bar{x} - x_{n+1})$.
    - _Decision:_ Accept the best between $r$ and $e$.
6. **Contraction ($c$):**
    - If the Reflection $r$ is typically bad (worse than the second-worst point $x_n$), we overshot or are in a valley. We need to step back.
    - _Outside Contraction:_ If $f(r) < f(x_{n+1})$, compute average between centroid and reflection.
    - _Inside Contraction:_ If $f(r) \ge f(x_{n+1})$, compute average between centroid and worst point.
    - _Decision:_ If the contraction point is better than the point it is based on, accept it.
7. **Shrink:**
    - If all else fails (Reflection and Contraction did not improve the worst point), the simplex is likely too large around a minimum.
    - **Action:** Shrink the entire simplex towards the best point $x_1$. Replace all $x_j$ with $\frac{1}{2}(x_j + x_1)$.
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

