
[[Linear Algebra Bibliography]]

to solve a system of equations using matrices what you do is you take a system of linear equations, say:
$5x + 2y + 8z = 10$
$8x + 50y +10z = 86$
$0x + 10y + -10z = 10$
and then convert it into a matrix:
$$\begin{bmatrix}
5 & 2 & 8 & 10 \\
8 & 50 & 10 & 86 \\
0 & 10 & -10 & 10 \\
\end{bmatrix}$$
from here you would convert it into row echelon form mainly by using [[Scalar Multiplication]] on rows and adding multiples of a row to another row, which would look something like 
$$\begin{bmatrix}
1 & 2 & 8 & a \\
0 & 1 & 10 & b \\
0 & 0 & 1 & c \\
\end{bmatrix}$$
from here you can also do Gauss-Jordan elimination to get something that looks like this:
$$\begin{bmatrix}
1 & 0 & 0 & a \\
0 & 1 & 0 & b \\
0 & 0 & 1 & c \\
\end{bmatrix}$$
