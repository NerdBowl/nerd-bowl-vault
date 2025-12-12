---
tags:
  - probability-theory/stochastic-processes
aliases:
  - Infinitesimal Generator
  - Infinitesimal Generator Matrix
  - Rate Matrix
  - Transition Rate Matrix
  - Generator Matrix
status: good_enough
created: 2025-12-12 23:32
---
### Q-Matrix
The **Q-Matrix** (denoted $Q$) is the fundamental operator describing the evolution of a **Continuous-Time Markov Chain (CTMC)**. It is defined as the derivative of the transition probability matrix $P(t)$ at time $t=0$. It encapsulates the **instantaneous transition rates** between states, determining both the holding times in states and the probabilities of jumping to specific next states.

Mathematically, the Q-Matrix is defined by the limit:
$$Q = \lim_{h \to 0^+} \frac{P(h) - I}{h} = P'(0)$$
_Where:_
- $P(h)$: The transition probability matrix over a small time interval $h$.
- $I$: The identity matrix.
- $Q$: The matrix with entries $q_{ij}$.

#### Instantaneous Transition Rates & Infinitesimal Definitions
The elements of $Q$, denoted as $q_{ij}$, are derived from the infinitesimal behavior of the process over a time interval $h \to 0$.

**Off-Diagonal Entries ($i \neq j$):**
The instantaneous transition rate $q_{ij}$ represents the rate of flow from state $i$ to state $j$.
$$q_{ij} = \lim_{h \to 0} \frac{P_{ij}(h)}{h}, \quad \text{for } i \neq j $$
_Where:_
- $P_{ij}(h) = P(X(t+h) = j \mid X(t) = i)$.
- Interpretation: For small $h$, the probability of moving from $i$ to $j$ is approximately $q_{ij}h + o(h)$.

**Diagonal Entries ($i = j$) and Total Departure Rate ($v_i$):**
The diagonal entry $q_{ii}$ is the negative of the total departure rate leaving state $i$, denoted as $v_i$.
$$v_i = \lim_{h \to 0} \frac{1 - P_{ii}(h)}{h} = \sum_{j \neq i} q_{ij} $$
$$q_{ii} = -v_i $$
_Where:_
- $v_i$: The parameter of the exponential distribution governing the **holding time** (sojourn time) in state $i$.
- $P_{ii}(h)$: The probability of remaining in state $i$ for time $h$.
- Interpretation: For small $h$, the probability of _leaving_ state $i$ is approximately $v_i h + o(h)$.
    
#### Properties & Intuition
- Row Sum Property: The rows of a Q-matrix sum to zero. Since probability is conserved (must go somewhere or stay), the rate of leaving ($v_i$) must equal the sum of rates to specific destinations.
$$\sum_{j} q_{ij} = 0 \implies q_{ii} = -\sum_{j \neq i} q_{ij}$$
- **Kolmogorov Equations:** The Q-matrix relates the static probabilities to their time evolution via differential equations:
    - **Backward Equation:** $P'(t) = Q P(t)$
    - **Forward Equation:** $P'(t) = P(t) Q$
- **Competing Exponentials Intuition:** When the process enters state $i$, it initiates independent "alarm clocks" for every possible destination $j$, each ringing after an exponentially distributed time with rate $q_{ij}$. The process moves to the state whose clock rings first.
    - The time until _any_ clock rings is exponential with rate $v_i = \sum q_{ij}$.
    - The probability that the jump is specifically to state $j$ is $P_{ij} = q_{ij} / v_i$.
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

