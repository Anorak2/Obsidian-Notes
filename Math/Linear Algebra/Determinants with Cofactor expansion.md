
[[Linear Algebra Bibliography]]

the long way to find the determinant of an $n*n$ matrix is by doing a summation of the [[Minors of a matrix|minor]] at position $a_{uv}$ times the [[Co-factors of a Matrix|co-factor]] at position $C_{uv}$
$$|A|=\sum_{j=1}^n a_{ij} = a_{i1}C_{i2}+...$$
this definition can be recursive down until you reach a [[Determinant of 2x2 Matrix|2x2 Matrix]] which is easy to find the determinant of. This approach is slow because it scales according to O(n!) 