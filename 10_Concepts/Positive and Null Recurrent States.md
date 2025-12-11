---
tags:
  - probability-theory/stochastic-processes
aliases:
  - Positive Recurrent
  - Positive Recurrent State
  - Null Recurrent
  - Null Recurrent State
  - Positive Recurrence
  - Null Recurrence
  - Mean Recurrence Time
  - Expected Return Time
status: good_enough
created: 2025-12-11 19:58
---
### Positive and Null Recurrent States
This is a sub-classification of a [[Recurrent and Transient States|Recurrent State]], based on the expected time of return.
If state $i$ is recurrent (probability of return $f_i = 1$), we define $N_i$ as the number of transitions until the process returns to state $i$, and $m_i$ as the expected value of $N_i$:
$$m_i = E[N_i | X_0 = i]$$
- **Positive Recurrent:** State $i$ is positive recurrent if $m_i < \infty$.
- **Null Recurrent:** State $i$ is null recurrent if $m_i = \infty$.

#### Properties & Intuition
- **Class Property:** Positive recurrence and null recurrence are class properties.
- **Finite Chains:** An irreducible finite-state Markov chain must be positive recurrent. Null recurrence typically arises in infinite state spaces (e.g., random walks).
- Relationship to Limiting Probabilities ($\pi_j$):
    For an irreducible, aperiodic chain, the long-run proportion of time spent in state $j$ is the inverse of the mean return time:
$$ \pi_j = \frac{1}{m_j}$$
    - If $j$ is **positive recurrent**, then $\pi_j > 0$.
    - If $j$ is **null recurrent**, then $\pi_j = 0$ (the process returns, but so infrequently that the long-run proportion of time spent there is zero).

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

