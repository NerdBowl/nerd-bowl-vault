---
tags:
  - probability-theory/stochastic-processes
aliases:
  - Holding Time
  - State Occupancy Time
status: good_enough
created: 2025-12-12 23:16
---
### Sojourn Time
**Sojourn Time** (or holding time) is the random variable $T_i$ representing the continuous duration a stochastic process remains in state $i$ before making a transition to a different state. Due to the Markov property required of the parent process, the sojourn time must be memoryless.

*Distribution Formula:*
In a stationary Continuous-Time Markov Chain, the sojourn time $T_i$ follows an Exponential Distribution:
$$f_{T_i}(t) = v_i e^{-v_i t}, \quad t \ge 0$$
_Where:_
- $v_i$: The transition rate (parameter) of state $i$. It represents the rate at which the process leaves state $i$.
- $v_i = \sum_{j \neq i} q_{ij}$ (sum of instantaneous rates to all other states).
#### Properties & Intuition
- **Memoryless Property:** The probability that the process leaves state $i$ in the next $\Delta t$ seconds is constant, regardless of how long it has already been in state $i$. If a variable is not exponential, the process cannot be Markovian.
- **Rate of Transition ($v_i$):** The mean sojourn time is $E[T_i] = 1/v_i$. A high $v_i$ implies the state is unstable and the system leaves it quickly; a low $v_i$ implies the system "lingers" in state $i$.
- **Independence:** The sojourn time $T_i$ and the next state visited $X_{n+1}$ are independent random variables.


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

