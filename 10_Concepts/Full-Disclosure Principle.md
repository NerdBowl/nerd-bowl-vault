---
tags:
  - game-theory
  - information-theory
  - economics/micro
aliases: []
status: good_enough
created: 2025-12-09 11:50
---
### Full-Disclosure Principle
The **Full-Disclosure Principle** suggests that in a market with [[Asymmetric Informatio|asymmetric information]], if a verifiable [[Signalling Theory|signal]] exists, agents will be compelled to reveal their private information to distinguish themselves from those with "worse" traits. This triggers an **unraveling** process where silence is interpreted as the worst possible news.
#### The Unraveling Logic
1. **Initial State:** Consumers view "silent" agents as having the average quality of the silent group.
2. **Incentive:** Agents with quality slightly _above_ this average have an incentive to disclose their status to separate themselves from the lower-quality pool.
3. **Iteration:** Once the above-average agents disclose, the average quality of the remaining silent pool drops. The new "best" of the silent pool now faces the same incentive to disclose .
4. **Equilibrium:** The process repeats until all agents (except arguably the very worst) are forced to disclose their true status.

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

