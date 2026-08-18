### Unfiled 
```dataview
LIST
FROM [[]]
WHERE !contains(this.file.outlinks, file.link) AND contains(file.folder, "Main Notes")
SORT file.name ASC
```
