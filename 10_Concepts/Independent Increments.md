---
tags:
  - probability-theory/stochastic-processes
aliases:
  - Memoryless Incerements
status: good_enough
created: 2025-12-12 14:44
---
### Independent Increments
**Independent Increments** is a property of a stochastic process wherein the evolution of the process during one time interval is statistically independent of its evolution during any other non-overlapping time interval.

Formally, a counting process $\{N(t), t \ge 0\}$ has independent increments if, for any sequence of times $t_0 < t_1 < \dots < t_n$, the random variables representing the increments are mutually independent:
$$(N(t_1) - N(t_0)) \perp (N(t_2) - N(t_1)) \perp \dots \perp (N(t_n) - N(t_{n-1})) $$

_Where:_
- $\perp$: Denotes statistical independence.
- $N(t_k) - N(t_{k-1})$: The number of events occurring in the interval $(t_{k-1}, t_k]$.

#### Properties & Intuition
- **Predictive Limitation:** Knowledge of how many events occurred in the past (e.g., between time 0 and $s$) provides no information about how many events will occur in the future (e.g., between $s$ and $t$).
- **Markovian Nature:** This property implies a "fresh start" at any point $t$; the process's future behavior depends only on the interval length, not the history.
- **Intuition:** If you flip a fair coin, the result of the next flip is independent of the previous streak. Similarly, in a process with independent increments, a surge of arrivals in the last hour does not influence the probability of arrivals in the next hour.


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

