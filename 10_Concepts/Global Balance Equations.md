---
tags:
aliases: []
status: not_started
created: 2025-12-13 00:08
---
### Global Balance Equations
_The set of linear algebraic equations that determine the limiting distribution of a continuous-time Markov chain by equating the rate of flow out of a state to the rate of flow into that state._

For a continuous-time Markov chain with limiting probabilities $P_j$, transition rates $q_{kj}$, and total departure rates $v_j$, the global balance equations are:
$$v_j P_j = \sum_{k \neq j} q_{kj} P_k$$
_Where:_
- $v_j P_j$: **Rate Out.** The rate at which the process leaves state $j$ weighted by the probability of being in state $j$.
- $\sum_{k \neq j} q_{kj} P_k$: **Rate In.** The sum of rates entering state $j$ from all other states $k$, weighted by the probability of being in those states $k$.
- **Normalization:** These equations must be solved subject to the constraint $\sum_j P_j = 1$.
#### Properties & Intuition
- **Derivation:** These are derived from the Kolmogorov Forward Equations by setting the time derivative $P'_{ij}(t)$ to 0 (as $t \to \infty$, the probabilities stabilize).
- **Physical Interpretation:** In the long run, the number of transitions _into_ a specific state $j$ must equal the number of transitions _out of_ state $j$. If "Rate In" > "Rate Out", probability mass would accumulate in $j$ indefinitely, violating the steady-state assumption.
- **Cut Equations:** For birth-death processes, global balance simplifies to "local balance" or "detailed balance" across cuts between states $n$ and $n+1$: $\lambda_n P_n = \mu_{n+1} P_{n+1}$.

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

