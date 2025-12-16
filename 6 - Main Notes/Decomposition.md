Status:

Tags: [[Databases]]
# Decomposition

Often times the only way to prevent duplication of information or to achieve a certain [[Normalization|form]] is to break down a table into two individual tables. Ideally we also usually want to achieve **lossless decomposition** which means decomposing in such a way that we can re-join the tables without losing any data. Another way of expressing this is that we should design schema so that we can use natural joins without loss.

Typically to achieve lossless decomposition we take a schema R = (<u>A</u>, <u>B</u>, C, D) and we can take the keys from that original schema, $R_1$ = (<u>A</u>, <u>B</u>, C) $R_2$ = R = (<u>A</u>, <u>B</u>, D) since the keys by definition must be unique and therefore can satisfy the natural join.

# References:
[[Normalization]]