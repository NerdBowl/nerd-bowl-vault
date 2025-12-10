---
tags:
  - game-theory
aliases:
  - sequential game
status: good_enough
created: 2025-12-06 21:21
---
### Extensive Form Games
An **Extensive Form Game** (or **Sequential Game**) is a game theoretic model in which players choose actions over time, rather than simultaneously. This structure captures the dynamic nature of strategic interaction, where a player can condition their current strategy on the observed prior actions of other players.

**Key Characteristics:**
- **Temporal Sequence:** Players move in turns (e.g., Player A moves, then Player B moves).
- **Full Knowledge:** Subsequent players are able to choose their strategy with full knowledge of the previous player's choice.
- **Strategic Complexity:** Unlike simultaneous games where a strategy is a single action, a strategy in a sequential game must specify an action for _every_ possible contingency (every decision node where the player might be called to act).

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

