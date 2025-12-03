---
tags:
aliases: []
status: not_started
created: 2025-12-03 13:50
---
# Momentum Methods in [[10_Concepts/Line Search methods|Line Search]]

### Momentum Methods
To mitigate zigzagging and improve convergence speed, momentum methods recycle information from previous iterations. 
#### Polyak's Heavy-ball Method
This method adds a "momentum" term based on the previous step.
$$
y_{k} = x_{k} + \beta_{k}(x_{k}-x_{k-1})
$$
$$
x_{k+1} = y_{k} - \alpha_{k}\nabla f(x_{k})
$$
This takes into account the amount of movement the previous step had, and in which direction, scaled using $\beta$. If the current slope tells us to rapidly turn around, it will do more slowly as the old velocity is still going in the other direction. 

#### Nesterov's Accelerated Gradient Descent (NAG)
Just like Polyak's method, this adds the momentum or 'old velocity' of the previous step.
$$
y_{k} = x_{k} + \beta_{k}(x_{k}-x_{k-1})
$$
$$
x_{k+1} = y_{k} - \alpha_{k}\nabla f(y_{k})
$$
A crucial difference is in the calculation of $x_{k+1}$. Instead of calculating the gradient of $f(x_{k})$, $f(y_{k})$ is used. Thus, it calculates and uses the gradient at that future position where it would end up by solely taking the momentum. 
In places where it is rapidly falling down a hill, where at the bottom the global minimum is located, and right after that another (smaller) hill, it does not add the momentum downwards and the gradient downwards together, making it overshoot. For the NAG, it first applies the momentum, and then sees "OH! It was about to overshoot on this smaller hill, let's turn back!" and applies the new gradient back towards the global minimum. 

---

# Related
```dataviewjs
// Get the tags of the current file
const currentTags = dv.current().file.tags;

// List pages from "10_Concepts"
dv.list(dv.pages('"10_Concepts"')
    .where(p => 
        // 1. Exclude the current file
        p.file.name != dv.current().file.name &&
        // 2. Check if ANY tag in the candidate page exists in currentTags
        p.file.tags.some(t => currentTags.includes(t))
    )
    .limit(10)
    .file.link
)
```

### Direct Links to this document
```dataview
TABLE file.folder AS "Context"
FROM [[#]]
WHERE file.folder != "10_Concepts"
SORT file.folder ASC
```

