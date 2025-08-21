

[[ServiceNow]]

A transform map is a set of field maps that define the relationships between the [[Import Sets|Import Set]] and the fields in the target table

Coalescing a field, or multiple fields, means the field will be used as a unique key during imports. If a match is found using the coalesce fields the existing record will be updated with the information being imported, and if no match is found then it will be inserted into the table.