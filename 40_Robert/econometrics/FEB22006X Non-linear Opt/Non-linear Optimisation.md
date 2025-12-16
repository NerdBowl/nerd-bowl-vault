
- Mathematical Optimization Problems are problems of the form $\min_{\mathbf{x}\in X}f(\mathbf{x})$ where $f : X \to \mathbb{R}$ is a function and $X \subseteq \mathbb{R}^n$ is a set.
	- If $X = \mathbb{R}^n$ then we call the problem unconstrained, if $X \neq \mathbb{R}^n$, we call the problem constrained. 
	- If $X$ is a polyhedron and $f$ is linear, the optimization problem is linear.
	- We focus on continuous optimization problems, where $X$ is usually countable.


- Optimization algorithms: to find the minimum of a function.
	- Gradient Descent
	- Newton's method
	- Quasi-Newton methods (BFGS)
- Line search: We often compute a direction, and we need how far to move in that direction.
- Wolfe conditions: define "good enough" for the step size for a line search.
	- Sufficient Decrease: the new function value must lie **below** a linear line drawn with a slightly flatter slope than the tangent at $x_k$. $$f(x_k + \alpha_k p_k) \le f(x_k) + c_1 \alpha_k \nabla f(x_k)^T p_k$$
	- Curvature condition: We want the slope (gradient) at the new point to be **flatter** (less negative) than the slope at the starting point. $$\nabla f(x_k + \alpha_k p_k)^T p_k \ge c_2 \nabla f(x_k)^T p_k$$
	- For some $0 < c_1 < c_2 < 1$.
- Taylor’s theorem: ?
- Coordinate Descent: Line search along coordinate directions.
- Golden Section Search: Finds step length without gradients by successively narrowing the range of values inside which the minimum is known to exist. Uses golden ratio.
- Nelder-Mead Simplex Method: The algorithm evaluates the function at the vertices of the simplex. Based on these values, it attempts to move the simplex "downhill" away from the worst point.
- Cauchy-Schwarz inequality: $$|\mathbf{u} \cdot \mathbf{v}| \le \|\mathbf{u}\| \|\mathbf{v}\|$$

- KKT conditions: ?
- Frobenius Norm: square root of the sum of the squares of the elements of a matrix.
	- Denoted $||A||_F$
	- Analogous to the euclidean L2 norm.
- Lipschitz continuous: A function is continuous, and the absolute value of the slope is limited by some real value. 
- Wolfe Conditions: ?
- Positive definite: ?
- 