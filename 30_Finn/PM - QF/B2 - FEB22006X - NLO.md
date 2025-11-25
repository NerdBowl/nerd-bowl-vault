# Non-Linear Optimization

# Course Information

### Study Goals

Operations research boils down to minimizing (or maximizing) some function over some set. For example, the set could consist of all possible solutions to a practical problem, and the function could represent the cost of a solution. Given these two, an operations research expert tries to find the cheapest solution that meets all requirements.

There are multiple courses in the Econometrics and Operations Research program where we minimize functions over sets. Linear Programming is about minimizing linear functions over polyhedra. Combinatorial Optimisation considers functions defined on countable sets. This course, in all modesty, covers everything else: not-necessarily-linear functions defined on uncountable sets.

There are three main aims in this course. Obviously, you will learn the theory of non-linear optimization. Moreover, you will develop your programming skills in Python. Finally, we will train formal reasoning by writing mathematical proofs.

To be more precise, by the end of the course, you should be able to:
- prove what the unconstrained minimum of a continuous function is (ifit can be found analytically);
- implement a line search algorithm to approximate the minimum of acontinuous function (if it cannot be found analytically);
- Explain what the different options for line search are;
- prove what the minimum is of a continuous function on an algebraic set;
- explain what types of algorithms are used in practice to solve continuous optimization problems;
- determine the Lagrangian dual of a continuous optimization problem;
- create logically valid theoretical proofs in the context of non-linear optimization;
- implement simple algorithms in Python.

### Assessment

The final grade is based on the following:
- Two assignments (count for 10% each); see Section 6.1.
- Written exam (counts for 80%); see Section 6.2.

The resit covers the same material as the exam, and also counts for 80%. There is no minimum grade for the exam or resit to get a valid grade. In general, partial results – such as assignment grades – of previous years are not valid in the current academic year.

# Week 1: Unconstrained Analysis

## 1. The Optimization Problem
We focus on **Unconstrained Optimization** where $X = \mathbb{R}^n$. The goal is to find the minimizer.

![[Mathematical Optimization#Definition]]

### Minima vs Infima
It is crucial to distinguish between the mathematical minimum and the infimum.

![[Optimal Values#Minimum]]

![[Optimal Values#Infinum]]

## 2. Finding Candidates (Stationary Points)
To find a minimizer, we first look for stationary points.

![[Gradients#Stationary Points]]
![[Fermat's Theorem (Optimization)#Fermat's Theorem]]

## 3. Proving Optimality via Convexity
If we can prove the function is convex, the search becomes much easier.

![[Convexity#Convex Functions]]

![[Convexity#Strict Convexity]]

> **Theorem:** If $f$ is convex, any stationary point is a **Global Minimizer**.

## 4. General Conditions for Local Minimizers
If the function is *not* convex, we rely on second-order conditions.

![[10_Concepts/Second-Order Optimization Conditions#Summary]]

**Example:**
For $f(x) = 3x^4 + 8x^3 - 18x^2$:
* $x=0$: Hessian is negative (local max).
* $x=1$: Hessian is positive (local min).
* $x=-3$: Hessian is positive (local min).

## 5. Existence of Global Minimizers
How do we know a solution exists at all?

![[10_Concepts/Weierstrass Theorem#Summary]]

## Roadmap: Finding the Global Minimizer
When faced with an unconstrained problem $\min_{x \in \mathbb{R}^n} f(x)$, follow this decision tree:

### Step 1: Find Stationary Points
Solve the gradient equation for $x$:
$$\nabla f(x) = 0$$
* *Outcome:* You get a set of candidate points $x^*_1, x^*_2, \dots$.

### Step 2: Check Convexity (The "Happy Path")
Check the Hessian matrix $\nabla^2 f(x)$ for all $x$.
* **Is $\nabla^2 f(x) \succeq 0$ (Positive Semi-Definite) everywhere?**
    * **YES:** $f$ is convex. All stationary points found in Step 1 are **Global Minimizers**. You are done.
    * **NO:** Proceed to Step 3.

### Step 3: Classify Local Candidates (The "Hard Path")
Since $f$ is not convex, we must check each candidate individually using **Second-Order Conditions**.
* Calculate the Hessian $\nabla^2 f(x^*)$ at each specific candidate point.
    * **If Indefinite:** Saddle point (ignore).
    * **If Negative Definite:** Local Maximum (ignore).
    * **If Positive Definite:** **Local Minimizer** Keep this candidate.

### Step 4: The Global Argument (Weierstrass)
You now have a list of Local Minimizers. To prove one is **Global**, you must rule out that the function dips to $-\infty$ somewhere far away.
* **Check Limits:** Does $\lim_{||x|| \to \infty} f(x) = \infty$?
    * **YES:** You can restrict the domain to a compact set (Box). By **Weierstrass**, a global minimum exists. It *must* be one of your local minimizers.
    * **Compare:** Evaluate $f(x)$ at all local minimizers. The one with the lowest value is the **Global Minimizer**.


