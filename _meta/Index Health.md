
## Orphans not in Index
```dataview
LIST
FROM "3 - Main Notes"
WHERE !any(file.outlinks, (l) => contains(l.path, "Indexes"))
SORT file.mtime DESC
```


