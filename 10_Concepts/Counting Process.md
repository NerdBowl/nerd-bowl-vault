---
tags:
  - probability-theory/stochastic-processes
aliases:
  - Event Counter
  - Cumulative Process
status: good_enough
created: 2025-12-12 14:39
---
### Counting Process
A stochastic process $\{N(t), t \ge 0\}$ is defined as a **Counting Process** if $N(t)$ represents the total number of "events" that have occurred by time $t$. It serves as a mathematical framework for modeling sequential occurrences over continuous time.

A process must satisfy four specific axioms to be classified as a Counting Process:
1. **Non-negativity:** $N(t) \ge 0$.
2. **Integer-valued:** $N(t) \in \{0, 1, 2, \dots\}$.
3. **Non-decreasing:** If $s < t$, then $N(s) \le N(t)$.
4. **Interval Relation:** For $s < t$, the quantity $N(t) - N(s)$ equals the number of events occurring in the interval $(s, t]$.
#### Properties & Intuition
- **Cumulative Nature:** By definition, the value of the process can never decrease; it is a cumulative step function.
- **Discrete State, Continuous Time:** While the index $t$ is continuous ($t \in [0, \infty)$), the state space is discrete (non-negative integers)2222.
- **Intuition:** Think of a mechanical clicker used to count people entering a venue. The value on the clicker at any specific time $t$ corresponds to $N(t)$. It can stay the same or jump up by integers, but it can never go down.


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

