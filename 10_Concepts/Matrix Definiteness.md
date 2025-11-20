---
tags:
  - topic/linear-algebra
aliases: [Positive Definite, PSD, Negative Definite, Indefinite Matrix]
status: good_enough
created: 2025-11-20 17:52
---
# Matrix Definiteness

## Summary
**Matrix Definiteness** classifies symmetric matrices based on the sign of the quadratic energy they generate. It is the matrix equivalent of checking if a number is positive, negative, or zero.

For a symmetric matrix $A$ and any non-zero vector $x$:
* **Positive Definite (PD):** The quantity $x^T A x$ is strictly positive ($>0$).
* **Positive Semi-Definite (PSD):** The quantity $x^T A x$ is non-negative ($\geq 0$).

**Intuition:**
* If $A$ is Positive Definite, it acts like a "positive number."
* In Optimization (Hessian): It means the surface curves **up** (like a bowl).
* In Probability (Covariance): It means variance cannot be negative.

## Details

### Classification via Quadratic Form
The scalar value $x^T A x$ determines the definiteness.

| Type                       | Quadratic Form ($x^T A x$)   | Eigenvalues ($\lambda$) | Geometric Shape        |
| :------------------------- | :--------------------------- | :---------------------- | :--------------------- |
| **Positive Definite**      | $> 0$                        | All $\lambda_i > 0$     | Bowl (Valley)          |
| **Positive Semi-Definite** | $\geq 0$                     | All $\lambda_i \geq 0$  | Valley with flat floor |
| **Negative Definite**      | $< 0$                        | All $\lambda_i < 0$     | Hill (Peak)            |
| **Negative Semi-Definite** | $\leq 0$                     | All $\lambda_i \leq 0$  | Ridge with flat roof   |
| **Indefinite**             | Mixed (some $>0$, some $<0$) | Mixed signs             | Saddle Point           |
|                            |                              |                         |                        |

### Eigenvalue Test
A symmetric matrix can be diagonalized. The definiteness is determined entirely by the signs of its **Eigenvalues**.
* $A$ is PD $\iff$ all eigenvalues are positive.
* $A$ is Indefinite $\iff$ at least one positive and one negative eigenvalue exist.

### Sylvester's Criterion (Determinant Test)
For a matrix to be **Positive Definite**, all its leading principal minors (determinants of upper-left sub-matrices) must be positive.
* Upper-left $1 \times 1$ determinant $> 0$
* Upper-left $2 \times 2$ determinant $> 0$
* ...
* Full determinant $> 0$

### Common Applications
* **Hessian Matrix:** Determines local minima (PD) vs maxima (ND).
* **Covariance Matrix:** A covariance matrix $\Sigma$ is always symmetric and **PSD**. It is PD if there is no perfect multicollinearity between variables.
* **Cholesky Decomposition:** A numerical method (essentially square-rooting a matrix) that requires the matrix to be PD.

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

