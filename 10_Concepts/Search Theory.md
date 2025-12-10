---
tags:
  - search-theory
  - information-theory
  - economics/micro
aliases: []
status: good_enough
created: 2025-12-09 10:15
---
### Search Theory
Search theory analyzes the optimal strategy for gathering information when opportunities are distributed over a range and acquiring information is costly.

An agent should continue searching only if the **expected gain** from the next search exceeds the **cost** of that search.
- **Optimal Strategy:** Continue searching until a bundle is found that exceeds a specific threshold, known as the [[Reservation Utility|acceptance wage or reservation price]].

### Search Theory in Economics
**1. Job Search (Seeking High Wage):**
- **Assumptions:** Wages are uniformly distributed between $Low$ and $High$ (e.g., 100 and 200). Cost of search is $C$.
- **Probability of Improvement:** If current offer is $w^*$, probability of finding a better offer is $\frac{High - w^*}{Range}$.
- **Expected Value of Improvement:** If a better offer is found, its average value is $\frac{High + w^*}{2}$. The net gain is $\frac{High - w^*}{2}$.
- Expected Gain Equation:
$$EG(w^*) = \left(\frac{High - w^*}{Range}\right) \times \left(\frac{High - w^*}{2}\right) = \frac{(High - w^*)^2}{2 \cdot Range}$$
- Equilibrium Condition: Set $EG(w^*) = C$.
$$w^* = High - \sqrt{2 \cdot Range \cdot C}$$
**2. Product Search (Seeking Low Price):**
- **Assumptions:** Prices distributed uniformly on $(0, P)$. Cost of search is $C$.
- Acceptance Price Formula:
$$P^* = \sqrt{2PC}$$

#### Market implications
- **Law of One Price Violations:** In models with perfect information, identical products sell for the same price. Search theory explains why price dispersion persists: sellers can charge higher prices because it is costly for consumers to search for the absolute lowest price.
- **Technology:** The internet and price comparison sites reduce search costs, which theoretically reduces price dispersion .


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

