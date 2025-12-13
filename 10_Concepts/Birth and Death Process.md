---
tags:
aliases: []
status: not_started
created: 2025-12-13 00:44
---
### Birth and Death Process
A **Birth and Death Process** is a continuous-time Markov chain (CTMC) defined on the state space of non-negative integers $\{0, 1, 2, \dots\}$, characterized by the restriction that state transitions can only occur between neighboring states. Specifically, if the system is in state $n$, it can only transition to state $n+1$ (a "birth") or state $n-1$ (a "death").

#### Fundamental Parameters and Dynamics
The process is governed by two sets of exponential rates dependent on the current state $n$:
- **Birth Rate ($\lambda_n$):** The rate at which the process transitions from state $n$ to $n+1$.
    - The time until the next birth is exponentially distributed with mean $1/\lambda_n$.
- **Death Rate ($\mu_n$):** The rate at which the process transitions from state $n$ to $n-1$.
    - The time until the next death is exponentially distributed with mean $1/\mu_n$.
    - Boundary condition: $\mu_0 = 0$ (cannot drop below state 0).

**Total Exit Rate ($v_n$):**
The total rate at which the process leaves state $n$ is the sum of the birth and death rates. The time spent in state $n$ (sojourn time) before any transition occurs follows an exponential distribution with rate $v_n$.
$$v_n = \lambda_n + \mu_n$$
_Where:_
- $v_n$: The instantaneous transition rate out of state $n$.

**Transition Probabilities ($P_{ij}$):**
When the process leaves state $n$, the probability of the next state being $n+1$ or $n-1$ is determined by the relative magnitude of the rates:
$$P_{n, n+1} = \frac{\lambda_n}{\lambda_n + \mu_n}, \quad P_{n, n-1} = \frac{\mu_n}{\lambda_n + \mu_n}$$
_Note:_ $P_{0,1} = 1$ because $\mu_0 = 0$.
#### Limiting Probabilities (Long-Run Behavior)
For an ergodic birth and death process, the limiting probability $P_n$ (the long-run proportion of time spent in state $n$) is determined by equating the rate of entering and leaving each state (Balance Equations).

**Balance Equation (Level Crossing):**
In the long run, the rate of transitions from $n$ to $n+1$ must equal the rate of transitions from $n+1$ to $n$:
$$\lambda_n P_n = \mu_{n+1} P_{n+1}$$

**Limiting Probability Formula:**
Solving the recursion yields the closed-form solution for any state $n \ge 1$:
$$P_n = \frac{\lambda_0 \lambda_1 \cdots \lambda_{n-1}}{\mu_1 \mu_2 \cdots \mu_n} P_0$$
The probability of being in state 0 ($P_0$) is found via the normalization condition $\sum_{n=0}^{\infty} P_n = 1$:
$$P_0 = \frac{1}{1 + \sum_{n=1}^{\infty} \frac{\lambda_0 \lambda_1 \cdots \lambda_{n-1}}{\mu_1 \mu_2 \cdots \mu_n}}$$

**Condition for Existence:**
Limiting probabilities exist if and only if the denominator is finite:
$$\sum_{n=1}^{\infty} \frac{\lambda_0 \lambda_1 \cdots \lambda_{n-1}}{\mu_1 \mu_2 \cdots \mu_n} < \infty$$

#### Properties & Intuition
- **Time Reversibility:** All ergodic birth and death processes are **time reversible**. Intuitively, if a movie of the process were played backward, the transitions would still look like valid births and deaths with rates consistent with the stationary distribution.
- **Nearest-Neighbor Interaction:** The memoryless property of the exponential distribution combined with the restriction to unit steps simplifies the analysis of complex systems (like queues) into recursive relationships.
- **State Dependence:** Unlike simple random walks, the rates $\lambda$ and $\mu$ can vary with $n$, allowing the model to capture dynamics like "the more people in the system, the faster they leave" (e.g., infinite server queues).
### Pure Birth Process
A **Pure Birth Process** is a specific instance of a BDP where the death rates $\mu_n = 0$ for all $n$. The process never decreases in state.
- **Poisson Process:** A pure birth process where $\lambda_n = \lambda$ (constant rate) for all $n$.
- **Yule Process:** A pure birth process where $\lambda_n = n\lambda$ (linear birth rate). This models a population where each individual reproduces independently at rate $\lambda$.    


---

# Related
```dataviewjs
await dv.view("99_System/Scripts/tag_tables", dv.current());
```

### Direct Links to this document
```dataview
TABLE file.folder AS "Context"
FROM [[#]]
WHERE file.folder != "10_Concepts"
SORT file.folder ASC
```

