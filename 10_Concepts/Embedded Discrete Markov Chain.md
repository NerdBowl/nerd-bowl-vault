---
tags:
  - probability-theory/stochastic-processes
aliases:
  - Jump Chain
  - Discrete Skeleton
status: good_enough
created: 2025-12-12 23:22
---
### Embedded Discrete Markov Chain
The **Embedded Discrete Markov Chain** (or embedded chain) is a discrete-time stochastic process $\{X_n, n=0, 1, ...\}$ derived from a continuous-time process by observing the sequence of distinct states visited, ignoring the duration of time spent in each state. It captures the structural routing of the system.

The one-step transition probability $P_{ij}$ represents the conditional probability that, given the process is leaving state $i$, it will next enter state $j$:
$$P_{ij} = \frac{q_{ij}}{v_i} = \frac{q_{ij}}{\sum_{k \neq i} q_{ik}}, \quad \text{for } i \neq j$$

_Where:_
- $P_{ij}$: Transition probability of the embedded discrete chain.
- $q_{ij}$: Instantaneous transition rate from $i$ to $j$ in the continuous chain.
- $v_i$: Total departure rate from state $i$.
- Assumption: $P_{ii} = 0$ (The embedded chain considers only transitions to _distinct_ states).
#### Properties & Intuition
- **Structure vs. Time:** The Embedded Chain decouples the _logic_ of state changes (where do we go next?) from the _timing_ of state changes (how long do we wait?).
- **Ergodicity:** If the continuous chain is ergodic, the embedded chain allows the calculation of limiting probabilities $\pi_i$ for the discrete sequence of states, which relates to the continuous limiting probabilities $P_i$ via weighting by mean sojourn times.
- **Conditional Independence:** Given the current state $i$, the next state $j$ is determined purely by the relative weights of the transition rates $q_{ij}$, independent of the time spent in $i$.


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

