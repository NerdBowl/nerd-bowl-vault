---
tags:
  - topic/optimization
  - topic/line-search
aliases: []
status: good_enough
created: 2025-12-03 13:54
---
# Newton's Methods in [[Line Search Methods]]

## Newton's Method
Gradient Descent finds the tangent plane at the current location, and takes a step in that direction (downwards). This is First-order optimization. 
Newton's method is an example of second-order optimization. Instead of fitting a linear function (the tangent) to the current location, it fits a quadratic function (bowl shaped) to the current location by looking at the surrounding curvature of the function. Then it can jump down to the minimum of this quadratic function. If the objective function is truly quadratic, then this method finds the minimum in exactly one step. 

**The Quadratic Model** We minimize the model function $m_{k}(p)$, which is the second-order Taylor-Expansion of $f$ around $x_{k}$:
$$
m_{k}(p) \approx f(x_{k})+\nabla f(x_{k})^T p+\frac{1}{2} p^T \nabla^2 f(x_{k})p
$$
Here, $\nabla^2 f(x_k)$ is the Hessian matrix (the matrix of second partial derivatives).

**The Algorithm** To find the search direction $p_{k}$, we minimize $m_{k}(p)$ by setting its derivative to zero. This leads to the linear system $\nabla^2 f(x_k) p_k = - \nabla f(x_k)$.
1. Choose starting point $x_{0}\in \mathbb{R}^n$. Set $k=0$.
2. While not converged:
	1. Compute Hessian and Gradient
	2. Solve for search direction $p_k = -[\nabla^2 f(x_k)]^{-1} \nabla f(x_k)$
	3. Update position: $x_{k+1} \leftarrow x_{k}+p_{k}$ (in practice: $x_{k+1} \leftarrow x_{k}+\alpha_{k}p_{k}$, with step length $\alpha_{k}$)
	4. $k\leftarrow k+1$

Issues with this method are:
- Computation: Computing and inverting the Hessian is computationally expensive ($O(n^3)$ ([[10_Concepts/Complexity|Big-Oh]]))
- [[10_Concepts/Convexity|Non-Convexity]]: If the Hessian is not positive definite, the direction $p_{k}$ might not be a descent direction (it could point toward a saddle point or maximum)

### Quasi-Newton Methods (BFGS)
Quasi-Newton methods aim to gain the cheap computation of gradient descent, while also having fast divergence. These methods essentially combine the two by approximating the Hessian Matrix (or its inverse) as it moves through the optimization landscape. Using the information of the gradient, and change in position, the curvature can be learned.

**The Secant Equation**Let $B_k$ be the approximation of the Hessian at step $k$. It must satisfy the Secant Equation based on Taylor's theorem:
$$B_k [x_k - x_{k-1}] = \nabla f(x_k) - \nabla f(x_{k-1})$$
**Notation**
- Displacement: $s_{k-1} = x_k - x_{k-1}$
- Change in Gradient: $y_{k-1} = \nabla f(x_k) - \nabla f(x_{k-1})$

#### The BFGS Update
The Broyden-Fletcher-Goldfarb-Shanno (BFGS) algorithm is the most popular Quasi-Newton method. It updates the _inverse_ Hessian approximation, denoted as $B_k^{-1}$ (sometimes denoted $H_k$), directly.

The update formula to generate $B_k^{-1}$ from $B_{k-1}^{-1}$ is:
$$B_k^{-1} = \left(I - \frac{s_{k-1}y_{k-1}^\top}{y_{k-1}^\top s_{k-1}}\right) B_{k-1}^{-1} \left(I - \frac{y_{k-1}s_{k-1}^\top}{y_{k-1}^\top s_{k-1}}\right) + \frac{s_{k-1}s_{k-1}^\top}{y_{k-1}^\top s_{k-1}}$$
**The Algorithm**
1. **Initialize:** $x_0 \in \mathbb{R}^n$ and an initial inverse Hessian approximation $B_0^{-1}$ (usually the Identity matrix $I$).
2. **While not converged:**
    - Compute search direction: $p_k = -B_k^{-1} \nabla f(x_k)$
    - Perform line search to find step length $\alpha_k$ and update: $x_{k+1} = x_k + \alpha_k p_k$
    - Compute differences: $s_k = x_{k+1} - x_k$ and $y_k = \nabla f(x_{k+1}) - \nabla f(x_k)$
    - Update the inverse Hessian approximation $B_{k+1}^{-1}$ using the BFGS formula above.
    - $k \leftarrow k+1$.

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

