---
tags:
  - topic/optimization
  - utility-functions
  - economics/micro
aliases: []
status: good_enough
created: 2025-12-08 14:17
---
### Corner Solution
A corner solution is a special solution to a [[Mathematical Optimization|maximization problem]] in which one of the arguments in the optimal solution is zero. 

### Corner Solution in Economics
A corner solution generally arises when the consumer's willingness to trade ([[Marginal Rate of Substitution]]) is consistently higher or lower than the market price ratio for all levels of consumption:
- Consumption of only Good X (Y=0):
$$
MRS > \frac{P_X}{P_Y} \quad \text{at } Y=0
$$
- Consumption of only Good Y (X=0):
$$
MRS < \frac{P_X}{P_Y} \quad \text{at } X=0
$$
The highest [[Indifference Curves|indifference curve]] attainable is not tangential to the [[Budget Constraint|budget line]].

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

