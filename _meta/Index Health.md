
## 🚨 Orphans — in NO index (file these or they get duplicated)
```dataview
LIST
FROM "6 - Main Notes"
WHERE !any(file.outlinks, (l) => contains(l.path, "4 - Indexes"))
SORT file.mtime DESC
```

## 📭 No `Tags:` line at all
```dataview
LIST
FROM "6 - Main Notes"
WHERE !file.frontmatter AND length(filter(file.lists, (x) => false)) = 0
SORT file.ctime DESC
```





























[[meta notes]]
