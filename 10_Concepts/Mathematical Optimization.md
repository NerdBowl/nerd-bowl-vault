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

## Constrained Optimization
### Problem Definition
We focus on minimizing a function subject to specific restrictions.

We aim to find the [[Optimal Values#Infinum|infinum]] of $f(x)$ subject to the two types of constraints:
$$\begin{aligned} \min & \quad f(x) \\ \text{subject to} & \quad c_i(x) = 0, \quad \forall i \in \mathcal{E} \quad \text{(Equality constraints)} \\ & \quad c_i(x) \geq 0, \quad \forall i \in \mathcal{I} \quad \text{(Inequality constraints)} \end{aligned}$$
In constrained optimization, a [[Minimizers#Global Minimizer|global minimizer]] is formally referred to as an **optimal solution**, and a local minimizer is a **locally optimal solution**.

### Necessary Conditions
To find a minimizer, we analyze the relationship between the gradient of the objective function $\nabla f$ and the gradients of the constraints $\nabla c_i$.

#### Equality Constraints ($c_i(x)=0$)
If we are at a feasible point $x$, we can only move in directions $s$ that keep us on the constraint curve (tangent directions).
- **Feasible Direction:** To stay feasible (to first order), the movement $s$ must satisfy $\nabla c_i(x)^T s = 0$.
- **Descent Direction:** To decrease the function value, the movement $s$ must satisfy $\nabla f(x)^T s < 0$.
- **Optimality:** If there is no direction $s$ that is both feasible and a descent direction, then $\nabla f(x)$ must be parallel to the constraint gradient $\nabla c_i(x)$. This implies $\nabla f(x) = \lambda \nabla c_i(x)$ for some scalar $\lambda$.

#### Inequality Constraints ($c_i(x) \geq 0$)
Inequality constraints add complexity because they can be either **active** (limiting the solution) or **inactive**.
- **Inactive Case ($c_i(x) > 0$):** The constraint is not currently restricting the solution. Locally, the problem behaves as if it were unconstrained. Thus, $\nabla f(x) = 0$ .
- **Active Case ($c_i(x) = 0$):** The point is on the boundary. We cannot move "out" of the feasible region.
    - For $x$ to be a minimizer, the gradient $\nabla f$ must point "inward" toward the forbidden region (otherwise, we could move into the feasible region and decrease $f$).
    - Mathematically, $\nabla f(x) = \lambda_i \nabla c_i(x)$ where **$\lambda_i \geq 0$**.
#### Complementarity
To handle both active and inactive cases simultaneously, we introduce the complementarity condition:
$$\lambda_i c_i(x) = 0$$
This ensures that either the constraint is active ($c_i(x)=0$) or the multiplier is zero ($\lambda_i=0$) .


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

