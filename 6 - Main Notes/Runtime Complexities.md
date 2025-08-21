Status:

Tags: [[Data Structures]] [[Algorithms]] [[3 - Tags/Optimization|Optimization]]
# Runtime Complexities
**Data Structures**

|                                                   | Key Type    | Get(x)      | add(x)      |
| ------------------------------------------------- | ----------- | ----------- | ----------- |
| [[Binary Search Trees\|Bushy BST]]                | Comparable  | $O(\log n)$ | $O(\log n)$ |
| [[Hash Tables\|RSC Hash Table]]                   | Hashable    | $O(1)^*$    | $O(1)^*$    |
| [[Arrays\|Data Indexed Array]]                     | Chars/ASCII | $O(1)$      | $O(1)$      |
| [[Tries]](BST, Hash Table, data indexed char map) | Strings     | $O(1)$      | $O(1)$      |
**Graph Algorithms**

| Problem        | Algorithm                                                          | Runtime (if E > V) | Notes                             |
| -------------- | ------------------------------------------------------------------ | ------------------ | --------------------------------- |
| Shortest Paths | [[Graphs Shortest Path Problem - Dijkstra's\|Dijkstra's]]          | O(E log V)         | Fails for negative weighted edges |
| MST            | [[Graphs Spanning Tree and Min Spanning Tree\|Prim's]]             | O(E log V)         | Analogous to Dijkstra's           |
| MST            | [[Graphs - Kruskal's Algorithm\|Kruskal's]]                        | O(E log E)         | Uses WQUPC*                       |
| MST            | [[Graphs - Kruskal's Algorithm\|Kruskal's]], with pre-sorted edges |                    | Uses WQUPC*                       |
Note: weighted quick union path compression
**Sorting Algorithms**

|                                   | Space            | Worst Case                | Best Case          | Runtime                       | Notes                                                                                                                         | Stable |
| --------------------------------- | ---------------- | ------------------------- | ------------------ | ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ------ |
| [[Selection Sort]]                | $\Theta(1)$      |                           |                    | $\Theta(n^2)$                 | a stable selection sort does exist but no by default                                                                          | Can be |
| [[Heap Sort]]                     | $\Theta(1)$      | $\Theta(n \space \log n)$ | $\Theta(N)^*$      | $\Theta(N)^*$                 | Bad cache (61c) performace                                                                                                    | No     |
| [[Insertion Sort]]                | $\Theta(1)$      | $\Theta(n^2)$             | $\Theta(n)$        | $\Theta(n^2)^*$               | $\Theta(n)$ if almost sorted                                                                                                  | Yes    |
| [[Merge Sort]]                    | $\Theta(n)$      |                           |                    | $\Theta(n \log n)^*$          |                                                                                                                               | Yes    |
| [[Quick Sort\|Random Quick Sort]] | $\Theta(\log n)$ | $\Theta(n^2)$             | $\Theta(n \log n)$ | $\Theta(n \log n)$ on average | The fastest algorithm. Memory usage is due to recursive calls, trivial though. Stable Quicksort exists but is a little slower | No     |
| [[Counting Sort]]                 | $\Theta(N+R)$    |                           |                    | $\Theta(N+R)$                 | Alphabet keys only                                                                                                            | Yes    |
| [[Radix Sort\|LSD Radix Sort]]    | $\Theta(N+R)$    | $\Theta(WN +WR)$          |                    |                               | Alphabet Only                                                                                                                 | Yes    |
| [[Radix Sort\|MSD Radix Sort]]    | $\Theta(N+WR)$   | $\Theta(WN+WR)$           | $\Theta(N+R)$      |                               | Bad Caching                                                                                                                   | Yes    |
\*: assumes a constant compare_to time 
N: number of keys, R: Size of Alphabet, W: Width of longest key



![[Pasted image 20241210224138.png]]

# References
too much