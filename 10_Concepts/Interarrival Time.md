---
tags:
  - probability-theory/stochastic-processes
aliases:
  - Inter-arrival Time
  - Sojourn Time
  - Holding Time
status: good_enough
created: 2025-12-12 17:03
---
### Interarrival Time
The **Interarrival Time** sequence $\{T_n, n \ge 1\}$ of a Homogeneous Poisson Process represents the elapsed time between consecutive events.

*Theorem:*
If $\{N(t), t \ge 0\}$ is a Poisson process with rate $\lambda$, then the sequence of interarrival times $T_1, T_2, \dots$ consists of independent and identically distributed (i.i.d.) random variables following an Exponential Distribution with parameter $\lambda$.
$$f_{T}(t) = \lambda e^{-\lambda t}, \quad t \ge 0$$
$$P(T_n \le t) = 1 - e^{-\lambda t}$$
_Where:_
- $T_1$: Time of the first event.
- $T_n$: Time elapsed between the $(n-1)$-th event and the $n$-th event ($S_n - S_{n-1}$).
- $\lambda$: The rate parameter of the underlying Poisson process.

#### Properties & Intuition
- **Memorylessness:** $P(T > s + t | T > s) = P(T > t)$. The probability of waiting an additional $t$ seconds is independent of how long one has already waited.
- **Relationship to Counts:** The event $T_1 > t$ (no arrival in the first $t$ units) is equivalent to the event $N(t) = 0$.
- **Intuition:** Because the Poisson process has independent and stationary increments, the "clock" essentially resets after every event. The process is probabilistically identical at any moment $t$ to its state at $t=0$, meaning the wait for the _next_ event always follows the same distribution.


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

