
Linear Systems
- A Linear system is a set of two or more linear equations that share the same variables. The solution to a linear system is a set of values for these variables that makes all equations in the system true at the same time. 
- A Linear system can only have zero, one, or infinitely many solutions.
- Two linear systems with the same solution set are called equivalent systems.
- The augmented matrix rewrites a linear system as follows:   $$\left\{\begin{array}{l}x_1+5x_2+3x_3=1\\2x_1+x_2+15x_3=8\\-x_1+x_2+3x_3=1\end{array}\right.\quad\Longrightarrow\quad\left[\begin{array}{ccc|c}1&5&3&1\\2&1&15&8\\-1&1&3&1\end{array}\right]$$
- Elementary row operations are the operations that can be performed on an augmented matrix to produce an equivalent system.
	1. One row is replaced by the sum of itself and a multiple of another row.
	2. Two rows are interchanged
	3. One row is multiplied by a nonzero constant.
- A system is called:
	- consistent if it has at least one solution
	- inconsistent if it has no solution at all
- Note: If a system is inconsistent then the row reduction algorithm will produce at least one row of the form $\left[ \begin{array}{cccc|c} 0 & 0 & \cdots & 0 & c \end{array} \right]$ with $c \neq 0$.
- A matrix is in echelon form if it has the following three properties:
	1. All nonzero rows are above any row of all zeros.
	2. Each leading entry (pivot) is in a column to the right of the leading entry in the previous row.
	3. All entries below a leading entry are zero.
- A matrix is in reduced echelon form if it has the following three properties:
	1. It is in echelon form.
	2. The pivot of each nonzero row is 1.
	3. Each leading 1 is the only nonzero entry in its column.
- A variable of a linear system is called a:
	- Basic variable if its column contains a pivot position.
	- Free variable it is column does not contain a pivot position.
- Solving a system of linear equations:
	1. Row reduce the augmented matrix to echelon form.
	2. Determine whether or not the system is consistent.
	3. In case of consistency, find the solution(s) by:
		- Backward substitution, or;
		- further row reduction to reduced echelon form.

Vector-Matrix
- The product of a matrix $A$ with $n$ columns and a vector $\mathbf{x}$ with $n$ entries is defined by: $$A\mathbf{x} = \begin{bmatrix} \mathbf{a}_1 &\dots & \mathbf{a}_n \end{bmatrix} \begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix} = x_1\mathbf{a}_1 + \dots + x_n\mathbf{a}_n$$
- If $A$ is an $m \times n$ matrix, $\mathbf{u}$ and $\mathbf{v}$ are vectors in $\mathbb{R}^n$ and $c$ is a scalar, then:
	- $A(\mathbf{u} + \mathbf{v}) = A\mathbf{u} + A\mathbf{v}$
	- $A(c\mathbf{u}) = c(A\mathbf{u})$
- A transformation $T : \mathbb{R}^n \to \mathbb{R}^m$ is called a **linear transformation** if:
	- $T(\mathbf{u} + \mathbf{v}) = T(\mathbf{u}) + T(\mathbf{v})$ for all vectors $\mathbf{u}, \mathbf{v}$ in $\mathbb{R}^n$;
	- $T(c\mathbf{u}) = cT(\mathbf{u})$ for all scalars $c$ in $\mathbb{R}$ and vectors $\mathbf{u}$ in $\mathbb{R}^n$.
- Let $T : \mathbb{R}^n \to \mathbb{R}^m$ be a linear transformation. Then there is a unique $m \times n$ matrix $A$ such that $T(\mathbf{x}) = A\mathbf{x}.$ $A$ is called the standard matrix of $T$.

Linear combination, Span, Linear independence
 - Given vectors $\mathbf{v}_1, \mathbf{v}_2, \ldots, \mathbf{v}_p$ in $\mathbb{R}^n$ and given scalars $c_1, c_2, \ldots, c_p$, the vector $\mathbf{y}$ defined by $\mathbf{y} = c_1\mathbf{v}_1 + \ldots + c_p\mathbf{v}_p$ is called a **linear combination** of $\mathbf{v}_1, \ldots, \mathbf{v}_p$ with weights $c_1, \ldots, c_p$.
	-  $\mathbf{y}$ is a linear combination of $\mathbf{v}_1, \ldots, \mathbf{v}_p$ if and only if there exists a solution to the linear system with augmented matrix $\left[ \begin{array}{cccc|c} \mathbf{v}_1 & \mathbf{v}_2 & \ldots & \mathbf{v}_p & \mathbf{y} \end{array} \right]$ .
- Given a set of vectors $\mathbf{v}_1, \mathbf{v}_2, \ldots, \mathbf{v}_p$ in $\mathbb{R}^n$. The **span** is the set of all linear combinations of $\mathbf{v}_1, \ldots, \mathbf{v}_p$, denoted by $\text{Span}\{\mathbf{v}_1, \mathbf{v}_2, \ldots, \mathbf{v}_p\}$.
- A set of vectors is **linearly independent** if the only solution to $x_1\mathbf{v}_1 + \cdots + x_p\mathbf{v}_p = \mathbf{0}$, is the trivial solution ($x_1 = 0, \ldots, x_p = 0$). If another solution exists, the set if linearly dependent.





Matrices
- Matrix transformation
- Matrix scalar multiplication:
- Matrix addition:
- Matrix multiplication:
- Powers of a Matrix:
- Transpose of a Matrix:


- 

