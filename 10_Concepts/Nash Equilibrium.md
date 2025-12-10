---
tags:
  - game-theory
aliases: []
status: good_enough
created: 2025-12-06 22:21
---
### Nash Equilibrium
A Nash Equilibrium is a combination of strategies such that each player is behaving optimally given the strategy choices of the other players. 
A strategy profile $(s_i^*, s_{-i}^*)$ is a Nash Equilibrium if:
$$
\pi_i(s_i^*, s_{-i}^*) \geq \pi_i(s_i, s_{-i}^*)
$$
for every feasible strategy $s_i$ available to player $i$.



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

