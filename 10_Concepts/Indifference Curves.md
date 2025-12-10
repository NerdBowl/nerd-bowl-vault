---
tags:
  - economics/micro
  - decision-theory
  - consumer-theory
aliases: []
status: good_enough
created: 2025-12-08 13:42
---
### Indifference Curves
An **Indifference Curve** is a geometric representation of a consumer's preferences, defined as the set of all consumption bundles that yield the same level of satisfaction (utility) to the consumer. In a two-good space (e.g., Good X and Good Y), it is the locus of points $(x, y)$ such that $U(x, y) = \bar{U}$, where $\bar{U}$ is a constant utility level.

An **Indifference Map** allows for a complete description of consumer preferences by aggregating infinitely many indifference curves, each corresponding to a different level of satisfaction. Higher curves represent strictly preferred bundles.

#### Properties & Dynamics
The standard behavior of indifference curves is derived from the fundamental axioms of rational choice (Completeness, Transitivity, Monotonicity, and Convexity):
- **Ubiquitous (Completeness):** An indifference curve passes through every possible bundle in the consumption set. This is assured by the completeness property, which states a consumer can rank any two bundles.
- **Downward Sloping (Monotonicity):** Indifference curves have a negative slope. This is a direct consequence of the "More-is-Better" assumption; if a consumer gives up some amount of one good, they must be compensated with more of the other to remain equally satisfied.
- **Non-Intersecting (Transitivity):** Two indifference curves from the same map cannot cross. If they did, it would violate the property of transitivity and the more-is-better assumption (creating a logical contradiction where a bundle is both equivalent to and strictly preferred to another).
- **Convex to the Origin:** Curves bow inward toward the origin. This shape reflects a diminishing [[Marginal Rate of Substitution|marginal rate of substitution]], implying consumers prefer balanced mixtures of goods over extremes.

#### Special Preference Structures
While standard preferences are strictly convex, specific functional formas leas to unique indifference curve shapes:
- **Perfect Substitutes:** Linear indifference curves. MRS is constant everywhere. Optimization often leads to [[Corner Solutions|corner solutions]].
- **Perfect Complements (Leontief preferences):** L-shaped indifference curves. MRS is infinite on vertical segment, zero on the horizontal segment, and undefined at the vertex. Goods are consumed in fixed proportions. Additional units of one good without the other provice no extra utility. 
- **Satiation points (Bliss points):** Circular or closed-loop indifference curves centered around a specific bundle. A satiation point represents the ideal bundle. Moving away from this point in any directionreduces utility. Beyond this point, Monotonicity assumptions fail, and indifference curves may slope upward. 


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

