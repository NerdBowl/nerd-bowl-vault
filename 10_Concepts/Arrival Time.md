---
tags:
  - probability-theory/stochastic-processes
aliases:
  - Waiting Time
  - Event Time
status: good_enough
created: 2025-12-12 17:05
---
### Arrival Time
The **Arrival Time** (or Waiting Time) $S_n$ represents the absolute time at which the $n$-th event in a Poisson process occurs. It is defined as the sum of the first $n$ interarrival times.

**Definition:**
$$S_n = \sum_{i=1}^{n} T_i$$

_Where:_
- $S_n$: The time of the $n$-th event ($S_0 = 0$).
- $T_i$: The $i$-th interarrival time (i.i.d. Exponential($\lambda$)).

*Distribution:*
The random variable $S_n$ follows a Gamma Distribution with parameters $n$ (shape) and $\lambda$ (rate).
$$f_{S_n}(t) = \frac{\lambda e^{-\lambda t}(\lambda t)^{n-1}}{(n-1)!}, \quad t \ge 0$$

The expectation is $E[S_n] = \frac{n}{\lambda}$.

#### Properties & Intuition
- Duality with Counting Process: There is a fundamental equivalence between the arrival times and the counting process:
$$N(t) \ge n \iff S_n \le t$$
    This states that having at least $n$ events by time $t$ is logically equivalent to the $n$-th event occurring at or before time $t$.
- **Sum of Exponentials:** The Gamma distribution arises naturally as the sum of i.i.d. exponential variables.    
- **Intuition:** While $T_n$ tells you how long you wait _between_ buses, $S_n$ tells you the specific time the $n$-th bus arrives on the schedule (relative to $t=0$).


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

