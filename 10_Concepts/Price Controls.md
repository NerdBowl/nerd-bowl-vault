---
tags:
  - topic/micro
  - topic/economics
aliases: []
status: good_enough
created: 2025-12-06 11:11
---
### Price Controls
Price controls are government-mandated legal restrictions on the price at which a good or service can be sold. They are typically implemented to maintain prices above or below the equilibrium level, often motivated by concern for the well-being of the poor. 

#### Price Ceiling
A **Price Ceiling** is a maximum allowable price, set by law, above which a good cannot be sold. To be binding (effective), it must be set _below_ the market equilibrium price.
- **Variable:** $R_c$ (Example: Rent Control Level).
- **Condition:** $R_c < P^*$, where $P^*$ is the equilibrium price.
##### Properties & Dynamics
1. **Excess Demand (Shortage):** At $R_c$, the quantity demanded ($Q^d$) exceeds the quantity supplied ($Q^s$). $Q^d > Q^s$.
2. **Non-Price Rationing:** Because price cannot ration the scarce supply, alternative mechanisms emerge:
    - First-come, first-served.
    - Discrimination/Favoritism (renting to friends/family)
    - Illegal side payments (black markets)
3. **Quality Deterioration:** With excess demand ($Q^d > Q^s$), sellers have little incentive to maintain quality. Maintenance costs are cut, leading to degradation of the stock (e.g., peeling paint, broken thermostats)28.
4. **Misallocation of Stock:** Individuals with low valuation may occupy units (e.g., a single person in a large apartment) because the low price reduces the incentive to downsize, while those with high valuation are excluded 29.

#### Price Floor
A **Price Floor** (or Price Support) is a minimum allowable price, set by law, below which a good cannot be sold. To be binding, it must be set _above_ the market equilibrium price.
- **Variable:** $P_s$ (Price Support Level).
- **Condition:** $P_s > P^*$, where $P^*$ is the equilibrium price.
##### Properties & Dynamics
1. **Excess Supply (Surplus):** At $P_s$, the quantity supplied ($Q^s$) exceeds the quantity demanded ($Q^d$). $Q^s > Q^d$.
2. **Government Purchase Requirement:** To maintain the price at $P_s$, the government must become an active buyer, purchasing the surplus ($Q^s - Q^d$).
3. **Resource Waste:**
    - Valuable inputs (labor, capital, fertilizer) are used to produce output that consumers do not want at that price.
    - The surplus often decays in storage or is destroyed.
4. **Regressive Distribution:** Price supports often benefit large corporate owners (who produce the most volume) rather than the intended small family farms.

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

