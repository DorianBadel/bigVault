---
tags:
  - advancedDatabases
  - book
---
```dataview
TABLE WITHOUT ID chapter as Chapter, file.link as File, (end - start) as Duration, type as Type, read as Read
FROM "01 - UiT/21-1 - Advanced Database Systems/Reading/Principles of Distributed Database Systems"
FLATTEN choice(type = "chapter", "🏳️","🏴") AS type
FLATTEN choice(read, "🪻", "") AS read
SORT chapter
```

[[Database Integration]], [[Multi-database Systems]], [[NewSQL]], [[NoSQL]], [[Polystores]]



