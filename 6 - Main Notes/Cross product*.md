
Tags: [[Calculus Bibliography]] [[Math]]
# Cross product
to find the cross product of two vectors, say $\lt a, b, c \gt$ cross $\lt u, v, w \gt$ you would start by forming a matrix where the first row is set to i, j, k, the second row is the first vector and the third row is the second vector.

$$ \begin{bmatrix}
i & j & k \\
a & b & c \\
u & v & w \\
\end{bmatrix} $$
you then find the determinant of this matrix using the formula for cofactor expansion
$$ i\begin{bmatrix}
b & c \\
v & w \\
\end{bmatrix} - j\begin{bmatrix}
a & c \\
u & w \\
\end{bmatrix}+k \begin{bmatrix}
a & b \\
u & v \\
\end{bmatrix} $$

# References
- [[Vector Definition]]
- [[Matrix Definition]]
- [[Determinants with Cofactor expansion]]