---
tags:
  - game-theory
aliases: []
status: good_enough
created: 2025-12-07 11:44
---
### Payoff Matrix
A payoff matrix is a tabular representation of a [[Normal Form Games|Normal Form Game]] that summarizes the payoffs for every possible combination of strategies between two players. 

The structure is as follows:
- **Rows**: Represent the strategies/actions available to player 1 (Row Player)
- **Columns**: Represent the strategies available to Player 2 (Column Player)
- **Cells**: Contain the payoffs for both players resulting from the intersection of a specific row strategy and a specific column strategy. 

To determine the best response for the row player given a column's player action, you can pick the action that gives the most payoff for the row player in that column.

This matrix can be used to easily find a [[Nash Equilibrium]], and a [[Dominant Strategy]].


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

