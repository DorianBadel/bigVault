---
tags:
  - advancedDatabases
---

```dataview
TABLE WITHOUT ID chapter as Chapter, file.link as File, (end - start) as Duration, type as Type, read as Read
FROM "01 - UiT/21-2 - Advanced Database Systems/Reading/Database system Concepts"
FLATTEN choice(type = "chapter", "🏳️","🏴") AS type
FLATTEN choice(read, "🌾", "") AS read
SORT chapter
```
