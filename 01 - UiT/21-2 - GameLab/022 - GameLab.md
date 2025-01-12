---
tags:
  - gameLab
  - subject
---
## Milestones
```dataview
LIST FROM #gameLab WHERE contains(tags, "milestone") SORT Due
```
## Exams

```dataview
LIST FROM #gameLab WHERE contains(tags, "exam") SORT Due
```

## Lectures
```dataview
LIST
FROM #gameLab
WHERE contains(tags, "lecture")
SORT Due
```


###### Links
[[High-level concept]]/[[Design]]/[[Prototype]]/[[Alpha]]/[[Beta]]
[[Oral Exam]]
[[Lecture]]