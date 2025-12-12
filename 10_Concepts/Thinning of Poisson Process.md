---
tags:
  - probability-theory/stochastic-processes
aliases:
  - Decomposed Poisson Process
  - Splitting of Poisson Processes
  - Bernoulli Thinning
status: good_enough
created: 2025-12-12 22:01
---
### Thinning of Poisson Process
**Thinning** (or decomposition) is the process of subdividing a single Poisson process into multiple independent Poisson processes based on probabilistic classification. Consider a parent Poisson process $\{N(t), t \ge 0\}$ with rate $\lambda$. If each event occurring in $N(t)$ is independently classified as Type $i$ with probability $p_i$ (where $\sum p_i = 1$), the resulting counting processes $\{N_i(t), t \ge 0\}$ are independent Poisson processes.
$$N_i(t) \sim \text{Poisson}(\lambda p_i t) $$

_Where:_
- $\lambda$: The rate of the original (parent) process.
- $p_i$: The probability of an event being classified as Type $i$.
- $N_i(t)$: The counting process for events of Type $i$.

The independence of the resulting processes $\{N_i(t)\}$ is a non-trivial and fundamental result; despite originating from the same source, the number of Type I events in an interval provides no information about the number of Type II events in that same interval.

#### Properties & Intuition
- **Independence:** The derived processes $N_1(t)$ and $N_2(t)$ are statistically independent. Proof involves showing the joint probability factors into the product of marginal probabilities: $P(N_1(t)=k, N_2(t)=m) = P(N_1(t)=k)P(N_2(t)=m)$.
- **Rate Scaling:** The intensity of each decomposed process is simply the original rate scaled by the classification probability ($\lambda_i = \lambda \cdot p_i$).
- **Intuition:** If a random flow of events is randomly split, the resulting sub-flows remain random (Poisson) and do not influence each other. This is effectively the inverse operation of Superposition.
### Non-Homogeneous Thinning
This is a sub-part where the classification probability depends on time, $p(t)$. If events from a homogeneous Poisson process with rate $\lambda$ are counted with time-dependent probability $p(t)$, the resulting process of counted events is a **Non-homogeneous Poisson Process** with intensity function $\lambda(t) = \lambda p(t)$.


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

