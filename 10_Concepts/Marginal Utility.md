---
tags:
  - economics/micro
  - utility-functions
  - topic/optimization
aliases: []
status: good_enough
created: 2025-12-08 14:06
---
### Marginal Utility
Marginal Utility (MU) is the rate of change in total [[Utility Theory|utility]] resulting from a small change in the consumption of one good, holding the consumption of all other goods constant. 
Mathematically, for a utility function $U(X, Y)$:
$$
MU_X = \frac{\partial U}{\partial X}, \quad MU_Y = \frac{\partial U}{\partial Y}
$$
Essentially, gradients:
![[Gradients#Gradient]]

#### Relationship to MRS
The [[Marginal Rate of Substitution]] can be derived directly from marginal utility using the total differential utility function. Along any indifference curve, total utility is constant ($dU=0$):\
$$
dU = \frac{\partial U}{\partial X}dX + \frac{\partial U}{\partial Y}dY = 0
$$
$$
MU_X dX + MU_Y dY = 0
$$

Rearranging terms to find the slope $-dY/dX$:
$$
\left| \frac{dY}{dX} \right| = \frac{MU_X}{MU_Y}
$$
Thus, the MRS is the ratio of marginal utilities:
$$
MRS_{XY} = \frac{MU_X}{MU_Y}
$$




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

