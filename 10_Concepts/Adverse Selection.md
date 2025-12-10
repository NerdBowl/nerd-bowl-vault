---
tags:
  - game-theory
  - economics/micro
aliases: []
status: good_enough
created: 2025-12-09 10:55
---
### Adverse Selection
Adverse Selection is a market process occurring **pre-contractually** in which "undesirable" members of a population (from the perspective of the uninformed party) are more likely to participate in a voluntary exchange than "desirable members". This occurs because the [[Asymmetric Information|uninformed]] party offers a price based on the average quality of the pool, which is attractive only to low-quality agents. 

**Mechanisms**
- Market unraveling:
	- If quality cannot be observed, the market price reflects the weighted average of all goods. 
	- Owners of high-quality goods value them above the average market price and withdraw from the marker. 
	- The withdrawal of high-quality goods lowers the average quality, lowering price further, causing more withdrawals. 
- Inefficiency: Trades that would be mutually beneficial fail to occur due to the information gap. 

#### The Market for Lemons
George Akerlof's model demonstrates that the mere fact a good is offered for sale acts as a signal of lower quality. In extreme cases, this drives "good" goods entirely out of the market, leaving only 'lemons'. 

#### Statistical Discrimination
The practice of judging an individual based on the average characteristics of their group, because gathering individual information is too costly. 
[[Insurance Market|Insurers]] charge rates based on group risk to approximate individual risk. Abandoning this leads to adverse selection, where low-risk individuals leave the pool, forcing premiums up for high-risk individuals. 




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

