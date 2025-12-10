---
tags:
aliases: []
status: not_started
created: 2025-12-07 11:50
---
### Dominant Strategy
A Dominant strategy is a strategy that yields a higher payoff for a player regardless of the strategy chosen by the opposing player. 

For a player $i$, a strategy $s_{dom}$ is dominant if:
$$
\pi_i(s_{dom}, s_{-i}) > \pi_i(s', s_{-i})
$$
for all alternative strategies $s'$ and all possible opposing strategy profiles $s_{-i}$.

If a player possesses a  dominant strategy, their behaviour is easy to predict as they have no incentive to deviate. 
If all players have a dominant strategy, than the intersection of these strategies is the equilibrium.
The outcome resulting from all players playing their dominant strategies is not guaranteed to be [[Pareto Optimality|pareto efficient]]. 

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

