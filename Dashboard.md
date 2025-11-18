```dataview
TABLE status as "State", file.folder as "Location"
FROM #math OR #cs
WHERE status != "perfect"
SORT status ASC
```
