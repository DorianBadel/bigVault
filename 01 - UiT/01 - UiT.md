## [[022 - GameLab]]
```dataview
TABLE WITHOUT ID file.link as Milestone, Due, Completed
FROM #gameLab
WHERE contains(tags, "milestone") OR contains(tags, "exam")
FLATTEN choice(Completed, "✨","") AS Completed
SORT Due
```

## [[021 - Advanced Database Systems]]
```dataviewjs
// Initialize counters and titles
let totalReadPages = 0;
let totalPages = 0;
let results = [];

// Specify the parent folder
let parentFolder = "01 - UiT/21-1 - Advanced Database Systems/Reading";

// Get all files in the parent folder
let files = dv.pages(`"${parentFolder}"`)
    .filter(page => page.file.path.split('/').length === parentFolder.split('/').length + 1)
    .map(page => ({
        path: page.file.path.replace(/\.md$/, ''), // Remove the .md extension
        title: page.file.name.replace(/\.md$/, '') // Remove the .md extension for the title
    }));

// Function to determine color based on percentage
function getColor(percentage) {
    if (percentage <= 10) return "#FFFFFF";
    if (percentage <= 23) return "#52EEA3";
    if (percentage <= 36) return "#51E1E9";
    if (percentage <= 49) return "#54B6F8";
    if (percentage <= 62) return "#437CF3";
    if (percentage <= 75) return "#9446F8";
    if (percentage <= 88) return "#E3365E";
    return "#E22C3C";
}

// Iterate over each specified file
for (let file of files) {
    let fileReadPages = 0;
    let fileTotalPages = 0;

    for (let page of dv.pages(`"${file.path}"`)) {
        if (page.end && page.start) {
            let pageCount = page.end - page.start;
            fileTotalPages += pageCount;
            if (page.read) {
                fileReadPages += pageCount;
            }
        }
    }

    // Calculate completion percentage for each file
    let fileCompletion = fileTotalPages > 0 ? (fileReadPages / fileTotalPages * 100).toFixed(2) : 0;

    // Determine color for the completion percentage
    let color = getColor(fileCompletion);

    // Add result for each file with colored completion
    results.push([
        dv.fileLink(file.path),
        `<span style="color: ${color};">${fileCompletion}%</span>`
    ]);

    // Accumulate totals
    totalReadPages += fileReadPages;
    totalPages += fileTotalPages;
}

// Display the result
dv.table(["Title", "Completion"], results);
```

```dataview
TABLE WITHOUT ID file.link as "Advanced Databases", Tags
FROM #advancedDatabases
WHERE !contains(tags, "subject")
FLATTEN choice(contains(tags, "lecture"), "🎓", "📕") as Tags 
SORT tags
```

## [[020 - Advanced Distributed Systems]]
```dataview
TABLE WITHOUT ID file.link as "Advanced Distributed", Due, Completed
FROM #advancedDistributed
SORT Due
```
