---
tags:
  - advancedDatabases
  - book
---

```dataview
TABLE WITHOUT ID chapter as Chapter, file.link as File, (end - start) as Duration, type as Type, read as Read
FROM "01 - UiT/21-1 - Advanced Database Systems/Reading/Database system Concepts"
WHERE start
FLATTEN choice(type = "chapter", "🏳️","🏴") AS type
FLATTEN choice(read, "🌾", "") AS read
SORT chapter
```

[[Semi-structured Data]], [[Object Orientation]], [[Textual Data]], [[Big Data]], [[Data Analytics]], [[Database-System Architectures]], [[Parallel and Distributed Storage]], [[Overview]], [[Distributed Query Processing]]