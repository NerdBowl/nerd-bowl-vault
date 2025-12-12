---
tags:
  - probability-theory/stochastic-processes
  - probability-theory/markov-chains
aliases:
  - Asymptotic Distribution
  - Long-Run behavior
  - Limiting Probabilities
status: good_enough
created: 2025-12-12 11:32
---
### Limiting Distribution (DTMC)
The **limiting distribution** of a discrete-time Markov chain $\{X_n, n \ge 0\}$ characterizes the state of the process as $n \to \infty$, independent of the initial state. For a Markov chain with state space $\mathcal{S}$ and transition probability matrix $\mathbf{P}$, the limiting probability $\pi_j$ for state $j$ is defined as the limit of the $n$-step transition probability $P_{ij}^n$ as the number of steps approaches infinity.

If the limit exists and is independent of the starting state $i$, we define the vector $\boldsymbol{\pi} = (\pi_j)_{j \in \mathcal{S}}$ where:
$$\pi_j = \lim_{n \to \infty} P_{ij}^n = \lim_{n \to \infty} \mathbb{P}(X_n = j | X_0 = i) $$
_Where:_
- $P_{ij}^n$: The probability of transitioning from state $i$ to state $j$ in exactly $n$ steps.
- $\pi_j$: The long-run probability of the chain being in state $j$.

For the limiting distribution to exist and be unique (independent of $X_0$), the Markov chain generally must satisfy specific structural properties, typically being **irreducible** and **ergodic** (aperiodic and positive recurrent).

#### Properties & Intuition
- **Ergodicity Condition:** A limiting distribution exists and is unique if the Markov chain is irreducible (all states communicate), aperiodic (no fixed cycle length), and positive recurrent (expected return time is finite). Such chains are called _ergodic_.
- **Independence of Initial State:** If the limiting distribution exists for an ergodic chain, the system eventually "forgets" its starting position. The probability of being in state $j$ after a long time is simply $\pi_j$, regardless of where it started.
- **Relationship to Stationary Distribution:** For an irreducible ergodic chain, the limiting distribution is identical to the stationary distribution. It is the unique solution to the steady-state equations.
- **Intuition:** Imagine a particle moving randomly between nodes in a network. After infinite steps, the "Limiting Distribution" describes the proportion of time the particle spends in each node. If the system is ergodic, this proportion stabilizes and becomes predictable.

### Limiting Distribution (CTMC)
_The long-run probabilistic behavior of a continuous-time Markov chain, representing the proportion of time the process spends in each state as $t \to \infty$, independent of the starting state._

If the limit exists and is independent of the initial state $i$, the limiting probability $P_j$ is defined as:
$$P_j = \lim_{t \to \infty} P_{ij}(t)$$
_Where:_
- $P_{ij}(t)$: The probability of being in state $j$ at time $t$ given start at $i$.
- $P_j$: The long-run proportion of time the process is in state $j$12.
#### Properties & Intuition
- **Existence Conditions:** The limiting probabilities exist and are non-zero if the Markov chain is:
    1. **Irreducible:** All states communicate (possible to get from any state to any other).
    2. **Positive Recurrent:** Starting in any state, the mean time to return to that state is finite13.
- **Relation to Derivatives:** As $t \to \infty$, the probability $P_{ij}(t)$ stabilizes, implying that its derivative with respect to time, $P'_{ij}(t)$, approaches 0. This allows the Kolmogorov Forward Equations to be converted into algebraic equations (Balance Equations).
- **Interpretation:** $P_j$ is the probability that an observer arriving at a random large time $t$ will find the system in state $j$.

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

