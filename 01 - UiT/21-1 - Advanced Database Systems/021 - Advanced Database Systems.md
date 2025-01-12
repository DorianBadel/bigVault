---
tags:
  - advancedDatabases
  - subject
---
## Reading
```dataview
LIST
FROM #advancedDatabases
WHERE !contains(type, "chapter") AND !contains(tags, "lecture") AND !contains(tags, "subject")
```

## Other
```dataview
TABLE week as Week
FROM "01 - UiT/21-1 - Advanced Database Systems/Lectures"
SORT lecture
```


###### Links
[[Database system Concepts]]/[[Next Generation Databases]]/[[Principles of Distributed Database Systems]]

[[01 - UiT/21-1 - Advanced Database Systems/Lectures/Lectures|Lectures]]