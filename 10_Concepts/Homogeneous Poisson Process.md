---
tags:
  - probability-theory/stochastic-processes
aliases:
  - HPP
  - Poisson Counting Process
  - Poisson Distribution
status: good_enough
created: 2025-12-11 10:25
---
### Homogeneous Poisson Process
A **Homogeneous Poisson Process** is a continuous-time stochastic process $\{N(t), t \geq 0\}$ representing a counting process where events occur continuously and independently at a constant average rate. It is the fundamental model for random arrivals in systems where the timing of the next event is independent of previous events.

*Definition 1 (Constructive/Incremental):*
A counting process $\{N(t), t \ge 0\}$ is a Poisson process with rate $\lambda > 0$ if:
1. $N(0) = 0$.
2. The process has **independent increments** (counts in disjoint intervals are independent).
3. The number of events in any interval of length $t$ is Poisson distributed with mean $\lambda t$.
$$P(N(t+s) - N(s) = n) = e^{-\lambda t} \frac{(\lambda t)^n}{n!}, \quad n=0,1,\dots$$

_Where:_
- $N(t)$: The total number of events that have occurred up to time $t$.
- $\lambda$: The constant intensity or rate parameter (expected events per unit time).
- $s, t$: Non-negative time parameters.

*Definition 2 (Infinitesimal/Local):*
Alternatively defined by behavior over a small interval $h \to 0$:
1. $N(0) = 0$.
2. Stationary and independent increments.
3. $P(N(h) = 1) = \lambda h + o(h)$.
4. $P(N(h) \ge 2) = o(h)$.

_Where:_
- $o(h)$: Little-o notation, representing a function $g(h)$ such that $\lim_{h \to 0} \frac{g(h)}{h} = 0$. This implies that simultaneous events are impossible in continuous time.

#### Properties & Intuition
- **Stationary Increments:** The probability distribution of the number of events depends only on the length of the time interval, not on _when_ the interval starts.
- **Memorylessness:** The future evolution of the process depends only on the current state, not the past.
- **Rare Events:** It naturally models phenomena where events are rare individually but occur at a predictable rate in aggregate (The Law of Rare Events).
- **Intuition:** Imagine throwing darts at a timeline randomly. If the timeline is long enough and the darts are thrown independently with a constant probability density, the count of darts in any section follows a Poisson process.

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

