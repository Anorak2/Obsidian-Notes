
[[Theory of Computing]]

The pumping lemma for CFL's is used to prove that a CFL is not [[Context Free Grammar|context free]]

If A is a context free language then A has a Pumping length "P" such that any string "S", where $|S| \geq P$ may be divided into 5 pieces $S = uvxyz$ such that the 
following **must** be true:
1. $uv^ixy^iz$ is in A for every $i \geq 0$
2. $|vx| > 0$ 
3. $|vxy| \leq P$ 