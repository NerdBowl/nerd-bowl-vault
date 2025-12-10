---
tags:
  - decision-theory
  - economics/micro
  - utility-functions
aliases: []
status: good_enough
created: 2025-12-09 16:18
---
### Prospect Theory
Prospect Theory is a descriptive model of decision-making under uncertainty. It servers as an alternative to the [[Utility Theory#Expected Utility Theory|Expected Utility Theory]], positing that individuals evaluate outcomes as changes from a reference point (gains and losses) rather than as final states of wealth. 

#### Key Components
1. **Reference Dependence:** Utility is derived from gains and losses relative to a neutral reference point.
2. **Asymmetric Value Function:** The subjective value of losses is greater than the subjective value of equivalent gains.
3. **Probability Weighting:** Objective probabilities are transformed into subjective decision weights. 

#### Properties
Prospect Theory claims no normative significance. It describes how people actually behave, not how they should behave. 

**[[RIsk Attitudes]]**
1. Risk Averse: high probability gains, and low probability losses
2. Risk seeking: high probability losses, and low probability gains

#### Value Function
The Value Function, denoted as $V(\Delta x)$, replaces the [[Utility Theory|utility function]] $U(W)$ in Prospect Theory. It is defined over **changes in wealth** relative to a reference point, rather than total wealth levels. 

The function is characterized by the following properties for a change outcome $x$:
1. **Reference Point:** $V(0) = 0$.
2. **Concavity in Gains ($x > 0$):** $V''(x) < 0$. This implies diminishing marginal sensitivity to gains (Risk Aversion).
3. **Convexity in Losses ($x < 0$):** $V''(x) > 0$. This implies diminishing marginal sensitivity to losses (Risk Seeking)
4. **Loss Aversion ($x = y$):** $|V(-y)| > V(y)$. The function is steeper in the negative domain than in the positive domain.

The asymmetric steepness explains why people may reject a bet with a positive expected value. The difference between 10 and 20 euros feels larger than the difference between 1000 and 1010 euros. 

#### Probability Weighting
**Probability Weighting** is the modification of objective probabilities $p$ into subjective decision weights $\pi(p)$ or $w(p)$. In Prospect Theory, agents do not weight outcomes by their raw probability (as in Expected Utility Theory) but by a transformed weight that overemphasizes certain ranges of likelihood.

**Properties & Dynamics**
- **Certainty Effect:** People underweight high probabilities relative to certainty. The psychological distance between 99% and 100% is perceived as much larger than the distance between 10% and 11%.
- **Possibility Effect:** People overweight small, non-zero probabilities. A 0.00001% chance is treated as a "possibility" significantly greater than 0%.
- **Allais Paradox:** A violation of the Expected Utility independence axiom where people prefer a sure gain over a gamble with higher expected value, but switch preferences when both probabilities are scaled down.





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

