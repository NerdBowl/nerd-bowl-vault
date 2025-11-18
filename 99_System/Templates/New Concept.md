---
tags:
  - topic/
aliases: []
status: not_started
created: <% tp.file.creation_date() %>
---

# <% tp.file.title %>

## Summary
<% tp.file.cursor() %>
## Details

---

## Related
- 

```dataview
TABLE file.folder AS "Context"
FROM [[#]]
WHERE file.folder != "10_Concepts"
SORT file.folder ASC
```

```dataview
LIST
FROM #topic/
WHERE file.tags = this.file.tags
AND file.name != this.file.name
LIMIT 10
```
