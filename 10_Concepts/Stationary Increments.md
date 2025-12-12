---
tags:
  - probability-theory/stochastic-processes
aliases:
  - Time Homogeneity
  - Stationarity of Increments
status: good_enough
created: 2025-12-12 14:46
---
### Stationary Increments
**Stationary Increments** is a property of a stochastic process where the probability distribution of the number of events occurring in any time interval depends **only** on the length of that interval, not on when the interval begins.

Formally, a counting process $\{N(t), t \ge 0\}$ has stationary increments if, for all $s \ge 0$ and $t > 0$, the random variable $N(t + s) - N(s)$ has the same distribution as $N(t) - N(0)$.
$$P(N(t_2) - N(t_1) = n) = P(N(t_2 - t_1) = n) $$
_Where:_
- $t_2 - t_1$: The length of the time interval.
- $n$: The number of events.

#### Properties & Intuition
- **Time Invariance:** The physical mechanisms driving the process do not change over time. The rate of event occurrence is constant.
- **Distributional Equality:** The number of events in the interval $[10, 15]$ has the exact same probability distribution as the number of events in $[0, 5]$.
- **Intuition:** A process with stationary increments has no "rush hours," "seasonal trends," or "downtimes." The likelihood of an event is uniform across the timeline.

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

