---
tags:
  - game-theory
  - topic/optimization
  - biology/evolution
aliases: []
status: good_enough
created: 2025-12-09 13:57
---
### Frequency-Dependent Selection
Frequency-Dependent Selection is an evolutionary process where the fitness (payoff) of a phenotype (or strategy) is a function of its relative frequency within the population.

#### Mathematical Stability Condition
A population reaches equilibrium when the average payoffs for all surviving strategies are equal.
$$P_{TypeA} = P_{TypeB}$$
Where:
- $P_i$ represents the average payoff (fitness) for type $i$.
    
**Dynamics:**
- **Growth Rule:** Strategies with higher relative payoffs reproduce at a higher rate, increasing their share of the population.
- **Equilibrium:** If the payoff of Strategy A decreases as Strategy A becomes more common, the population will stabilize at a specific mix of strategies.
- **Individual vs. Group Payoffs:** Evolution selects for traits based on individual payoffs, often resulting in equilibria where the population as a whole is worse off than if everyone adopted a cooperative strategy.


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

