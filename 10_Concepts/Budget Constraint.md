---
tags:
  - topic/economics
  - topic/micro
  - topic/constraint
aliases: []
status: good_enough
created: 2025-12-08 12:47
---
### Budget Constraint
The Budget Constraint (or budget line) defines the set of all bundles of goods a consumer ca purchase for given values of income and prices. It represents the boundary of the consumer's opportunity set. 

This concept is part of the [[Rational Choice Theory]].

For two goods $X$ and $Y$, the budget constraint is satisfied when total expenditure  [[Feasible Set#Inequality Constraint|is less than or equals]] total income:
$$
P_{x}X+P_{y}Y\leq M
$$
presented as a line:
$$
Y=\frac{M}{P_{y}}-\frac{P_{x}}{P_{y}}X
$$

Anything under the line is part of the [[Feasible Set]], anything above that line is infeasible and beyond the consumer's reach. 

The slope can be seen as the [[Opportunity Cost]] of an additional unit of $X$, it indicates the number of units of $Y$ that must be sacrificed to purchase one additional unit of $X$. 

#### Non-Linear Budget Constraints
Budget constraints are not always linear. They can become non-linear due to pricing structures or policy constraints:
- **Quantity Discounts:** Occurs when the price per unit changes after a certain quantity -> The opportunity cost falls as consumption increases.
- **In-Kind Transfers:** Government Transfers restricted to specific goods create a horizontal segment in the budget. 

#### Non-Binary Budget Constraints
To analyze choices between $N$ goods, where $N>2$, economist view the choices as between a specific good $X$ and an "amalgam of other goods", called the **Composite Good** $Y$. 
The price of the composite good is defined as 1 unit of currency. 
Thus $Y$ represent the total amount of income left over to spend on other goods after buying $X$. The slope becomes simply $-P_{x}$.


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

