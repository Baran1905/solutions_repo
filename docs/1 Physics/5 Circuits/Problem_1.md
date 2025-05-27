# Problem 1

##  Overview of the Solution
We'll:

1) Model the circuit as a weighted undirected graph.

2) Use graph traversal and simplification techniques to reduce the circuit iteratively:

   * Combine series resistors (linear chains).

   * Combine parallel resistors (multi-edges or cycles between the same nodes).

3) Return the final equivalent resistance between two terminals (e.g., source and sink nodes).


##  Algorithm Outline
**Key Ideas:**

* **Series Detection:** If a node has exactly 2 connections and is not a terminal, combine the two edges.

* **Parallel Detection:** Multiple edges between the same pair of nodes are reduced using the parallel resistance rule:

$$
\frac{1}{R_{eq}} = \sum_{i=1}^{n} \frac{1}{R_i}
$$

 
 

## Efficiency & Improvements

**Complexity:**

* **Parallel reduction:** O(E) per iteration

* **Series detection:** O(N) per iteration

* **Total iterations:** ≤ N (number of nodes)

**Improvements:**

* Use union-find to track components.

* Optimize detection of series/parallel structures with pattern matching.

* Integrate Kirchhoff’s laws + Laplacian matrix method (graph-theoretic method using Y-Δ transforms and node-voltage analysis).

## Final Thoughts
This approach is **systematic and generalizable**. It:

* Uses graph theory to model physical systems.

* Supports automation and scalability for complex networks.

* Bridges mathematical theory and engineering practice.



## Colab

[click to go colab](https://colab.research.google.com/drive/1vy_Iklm1AUIEgzHl_PPTnKtVMbs_9GzY?usp=sharing)