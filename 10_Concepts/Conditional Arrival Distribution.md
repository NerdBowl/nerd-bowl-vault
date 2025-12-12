---
tags:
  - probability-theory/stochastic-processes
aliases:
  - Arrival Times Conditioning
  - Order Statistics Property of Poisson Processes
  - Uniform Property of Poisson Arrivals
status: good_enough
created: 2025-12-12 21:46
---
### Conditional Arrival Distribution
For a Homogeneous Poisson Process (HPP) with rate $\lambda$, if it is known that $n$ events have occurred in the interval $[0, t]$, the joint distribution of the arrival times $S_1, S_2, \dots, S_n$ is identical to the distribution of the **order statistics** of $n$ independent random variables uniformly distributed on the interval $(0, t)$.

Unlike the interarrival times $X_i$ (which are i.i.d. Exponential) or the arrival times $S_n$ (which are Gamma distributed unconditionally), the _conditional_ arrival times lose their dependence on the rate $\lambda$ and depend only on the interval length $t$ and the count $n$.
$$f_{S_1, \dots, S_n | N(t)=n}(s_1, \dots, s_n) = \frac{n!}{t^n}, \quad 0 < s_1 < s_2 < \dots < s_n < t$$

_Where:_
- $N(t)$: The counting process representing the number of events in $[0, t]$.
- $S_i$: The time of the $i$-th event ($S_i = \sum_{j=1}^i X_j$).
- $n!$: The number of permutations of $n$ distinct items.
- $t^n$: The volume of the hypercube formed by $n$ independent uniform variables on $(0, t)$.    

#### Properties & Intuition
- **Unordered Independence:** While the actual arrival times $S_1, \dots, S_n$ are dependent (since $S_i < S_{i+1}$), the set of arrival times considered as an _unordered_ set acts exactly like a set of $n$ i.i.d. Uniform$(0, t)$ random variables.
- Simplification of Expectations: For any symmetric function $g$ (where the order of arguments does not matter), the expectation over the arrival times can be computed using independent uniform variables $U_i$:
$$E\left[ \sum_{i=1}^n g(S_i) \mid N(t)=n \right] = E\left[ \sum_{i=1}^n g(U_i) \right] = n E[g(U)]$$
- **Intuition:** Because the Poisson process has **stationary** and **independent increments**, the probability of an event occurring in any small sub-interval $dt$ within $[0, t]$ is proportional only to the length of $dt$. Since the rate $\lambda$ is constant, no specific time within the interval is "favored" over any other. Therefore, given that an event occurred, its location is uniformly distributed.

### Conditional Arrival Times for non-homogeneous PP
If the Poisson process is **non-homogeneous** with intensity function $\lambda(t)$, the conditional arrival times are still independent and identically distributed, but they are no longer uniform. Instead, they have the common density function:
$$f(s) = \frac{\lambda(s)}{m(t)}, \quad 0 < s < t$$
_Where:_
- $m(t) = \int_0^t \lambda(y) dy$: The mean value function (expected number of events by time $t$).
- The uniformity of the HPP is a special case where $\lambda(s) = \lambda$, resulting in $f(s) = \lambda / (\lambda t) = 1/t$.

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

