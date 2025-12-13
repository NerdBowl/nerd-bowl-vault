---
tags:
  - probability-theory/stochastic-processes
aliases:
  - Merged Poisson Process
  - Sum of Poisson Processes
  - Pooling of Poisson Processes
status: good_enough
created: 2025-12-12 21:53
---
### Superposition of Poisson Processes
The **Superposition of Poisson Processes** states that the summation of $k$ independent Poisson processes yields a single, aggregate Poisson process. Let $\{N_1(t), t \ge 0\}, \dots, \{N_k(t), t \ge 0\}$ be $k$ independent Poisson processes with respective rate parameters $\lambda_1, \dots, \lambda_k$.

The merged process $\{N(t), t \ge 0\}$, defined by the sum of the counting variables, is a Poisson process with a rate equal to the sum of the individual rates.
$$N(t) = \sum_{i=1}^{k} N_i(t) \sim \text{Poisson}\left(t \sum_{i=1}^{k} \lambda_i\right) $$
_Where:_
- $N(t)$: The total count of events occurring by time $t$ in the merged process.
- $\lambda_i$: The constant intensity (rate) of the $i$-th component process.
- $\Lambda = \sum \lambda_i$: The aggregate rate of the superimposed process.

#### Properties & Intuition
- **Closure under Addition:** The sum of independent Poisson random variables is itself Poisson distributed. Since independent Poisson processes possess stationary and independent increments, their sum retains these properties, satisfying the definition of a Poisson process.
- **Interarrival Distribution:** The time until the next event in the merged process, $T_{min}$, is equivalent to the minimum of the times to the next event for each constituent process. Since individual interarrival times are Exponentially distributed ($T_i \sim \text{Exp}(\lambda_i)$), and the minimum of independent exponentials is Exponential with the sum of the rates, the merged interarrival times follow $\text{Exp}(\Lambda)$.
- **Intuition:** If independent event streams occur randomly at constant average rates, observing them collectively results in a stream where events occur at a rate equal to the combined total of the individual rates.
### Type Probability in Merged Processes
This sub-part defines the probability that an observed event in the superimposed process originated from a specific constituent process $i$. Due to the memoryless property of the exponential distribution, this probability is constant and independent of time.
$$P(\text{Next event is of Type } i) = \frac{\lambda_i}{\sum_{j=1}^{k} \lambda_j} $$

_Where:_
- $\lambda_i$: Rate of the specific process $i$.
- $\sum \lambda_j$: Total rate of the merged process.

This property implies that the sequence of event types in a superimposed process constitutes a sequence of independent and identically distributed (i.i.d.) discrete random variables.


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

