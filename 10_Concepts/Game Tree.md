---
tags:
  - game-theory
aliases: []
status: good_enough
created: 2025-12-08 11:36
---
### Game Tree
A Game Tree is a graphical representation of an [[Extensive Form Games|Extensive Form Game]]. It maps the flow of decisions, the sequence of players, and the final outcomes. 

**Components**
- **Root Node:** The starting point of the game where the first player makes a decision. 
- **Decision Nodes:** Points in the tree where a specific player must choose an action.
- **Branches:** Lines connecting nodes, representing the specific actions or strategies available to a player at that node. 
- **Terminal Nodes:** The game has concluded.
- **Payoffs:** Associated with every Terminal Node is a set of payoffs for each player, representing utility or value derived from that specific path through the tree. 


#### Backward Induction
Backward induction is the primary solution technique for finding the equilibrium in [[Extensive Form Games]]. It operates on the principle of anticipating rational behavior at future decision points to determine optimal behavior at current decision points. 
1. **Identify Terminal Decisions:** Begin by analyzing the last choice that has to be made in the game. 
2. **Optimize the Final Stage:** Determine the optimal action for the player at that final node by comparing the payoffs.
3. **Prune and Step Back:** Treat the optimal outcome of the final stage as a fixed certainty. Move backward to the immediately preceding decision node. 
4. **Optimize the Preceding Stage:** The preceding player, anticipating the final player's rational response, chooses the action that maximizes their own payoff given that response. 
5. **Iterate:** Continue this process until the initial root node is reached.

Backward Induction reveals a specific type of equilibrium called [[10_Concepts/Sub-game Perfect Nash Equilibrium|Sub-game Perfect Nash Equilibrium]].
This strategy does assume that players are rational, and that the rationality is common knowledge. 


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

