---
tags:
  - finance/insurance
  - quant-finance
  - statistics
aliases: []
status: good_enough
created: 2025-12-09 10:21
---
### Insurance Market
Insurance markets function as a mechanism for risk sharing where independent risks are pooled to reduce uncertainty for individual agents. 

**Risk Pooling**
Individuals contribute a small sure loss to a pool, which covers the large potential losses of the few who suffer bad outcomes. Pooling transforms inherent uncertainty for the individual into a stable, predictable loss for the group.

The [[Law of Large Numbers]] applies here.

**Independence & Constraints**
- Risks should be independent, otherwise pooling does not work. 
  A fire likely effects 1 or 2 houses at a time, while a flood affects a large portion of the pool. So for fires, everyone pays for the damage, for floods, everything is still paying for themselves effectively. 
- A solution for this correlation risk is to pool risks over larger areas, or the government can also subsidize. 

#### Economics of Insurance
- **Unfair Gamble:** Private insurance is always an "unfair gamble" in statistical terms because premiums must cover not just the expected loss but also administrative costs.
- **Reservation Price for Insurance:** A risk-averse individual is willing to buy this "unfair" gamble as long as the premium is less than their **[[Reservation Utility|reservation price]]**.
    - The reservation price is the amount that reduces the agent's wealth to the **Certainty Equivalent** of the uninsured risk.
    - _Surplus:_ Trade occurs because the reservation price of the risk-averse consumer is higher than the break-even premium of the insurer (Expected Loss + Admin Costs).


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

