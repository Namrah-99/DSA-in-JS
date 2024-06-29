# Approaches

### Top Interview 150
- Dynamic Programming (DP)
- Greedy Approach
- Two Pointer Approach


## Techniques 
All techniques used in `algorithm design` to solve specific types of problems efficiently

## Dynamic Programming (DP)
**Definition:** Dynamic Programming is a method for solving complex problems by breaking them down into simpler overlapping subproblems. It stores the results of subproblems so that each subproblem is only solved once, thus reducing computational complexity.

##### Characteristics:
- **Memoization or Tabulation:** DP can be implemented using either memoization (top-down approach with recursion and caching) or tabulation (bottom-up approach using iterative techniques and arrays).
- **Optimal Substructure:** The solution to a problem can be constructed efficiently from solutions to its subproblems.
- **Overlapping Subproblems:** The same subproblems are solved multiple times.

##### When to Use DP:
- When the problem can be broken down into smaller overlapping subproblems.
- When solutions to subproblems can be reused (optimal substructure property).
- **Examples:** Fibonacci sequence, shortest path problems (like Floyd-Warshall algorithm), longest common subsequence.

## Greedy Approach
**Definition:** Greedy algorithms make locally optimal choices at each stage with the hope of finding a global optimum. They do not necessarily guarantee an optimal solution but often produce solutions that are close to optimal.

##### Characteristics:
- **Decision Making:** At each step, make the choice that seems best at the moment.
- **No Backtracking:** Choices are irreversible; once made, they are never reconsidered.
- **Efficiency:** Generally faster than DP and easier to implement in many cases.

##### When to Use Greedy Approach:
- When a problem exhibits optimal substructure (making the locally optimal choice leads to a globally optimal solution).
- When a greedy choice can be proven to be safe and leads to an optimal solution.
- **Examples:** Minimum spanning tree (Prim's or Kruskal's algorithm), Dijkstra's algorithm for shortest path in a graph with non-negative weights.

## Two Pointer Approach
**Definition:** The two pointer technique is used for problems that involve searching or matching pairs in a sorted array (or interval of the array). It typically involves iterating through the array with two pointers or indices, manipulating them based on some conditions.

##### Characteristics:
- **Iterative:** It uses a simple iterative approach with two pointers (indices).
- **Efficiency:** Often operates in O(n) time complexity, where n is the size of the input.

##### When to Use Two Pointer Approach:
- When dealing with sorted arrays or intervals where you need to find a pair, triplets, or subarray that satisfies a condition.
- When you need to reduce the time complexity compared to naive methods (like O(n^2) solutions).
- **Examples:** Finding pairs in a sorted array that sum to a target (two sum problem), finding triplets in a sorted array that sum to a target (three sum problem).

## Problems solved by the Above mentioned techniques 

### Dynamic Programming (DP)
- Fibonacci Sequence: Calculate the nth Fibonacci number efficiently.
- Longest Common Subsequence (LCS): Find the longest subsequence common to two sequences.
- Shortest Paths: Compute shortest paths in graphs (e.g., Floyd-Warshall algorithm).
- Knapsack Problem: Optimize the selection of items to maximize profit without exceeding a weight limit.
- Matrix Chain Multiplication: Optimize the order of matrix multiplications to minimize computational cost.
- Subset Sum Problem: Determine whether there exists a subset of a set whose sum equals a given target.
- Coin Change Problem: Determine the minimum number of coins needed to make a certain amount.

### Greedy Approach
- Activity Selection: Select the maximum number of activities that do not overlap.
- Fractional Knapsack Problem: Optimize the selection of items to maximize profit per unit weight.
- Dijkstra's Algorithm: Find shortest paths from a source vertex to all vertices in a graph with non-negative weights.
- Prim's Algorithm: Construct a minimum spanning tree for a weighted undirected graph.
- Huffman Coding: Construct an optimal prefix-free binary encoding based on character frequencies.

### Two Pointer Approach
- Two Sum Problem: Find two numbers in a sorted array that sum up to a target value.
- Three Sum Problem: Find three numbers in a sorted array that sum up to a target value.
- Container With Most Water: Find the maximum area of water that can be trapped between vertical lines in an array.
- Merge Two Sorted Arrays: Merge two sorted arrays into a single sorted array.
- Trapping Rain Water: Calculate how much water can be trapped after raining between bars in an elevation map.

## Additional Problems
There are also problems that can be solved using combinations of these techniques or by adapting them creatively:

- **Dynamic Programming with Greedy Heuristics:** Some problems benefit from combining DP with greedy heuristics to improve efficiency.
- **Two Pointer with Binary Search:** Sometimes, the two pointer technique is combined with binary search to solve certain types of problems more efficiently.

These techniques are powerful tools in the algorithm designer's toolbox, each suited to different types of problems based on their specific characteristics and constraints.

## Choosing the Right Approach
- **Dynamic Programming:** Use when the problem can be divided into overlapping subproblems with optimal substructure. It’s suitable for optimization problems where the solution can be built from solutions to smaller subproblems.

- **Greedy Approach:** Use when the problem satisfies the greedy-choice property and optimal substructure can be proven by making locally optimal choices. It’s often used for optimization problems where a locally optimal choice leads to a globally optimal solution.

- **Two Pointer Approach:** Use when dealing with sorted arrays or intervals where you need to find pairs, triplets, or subarrays that satisfy specific conditions efficiently. It’s suitable for problems where you can use two pointers (or indices) to navigate through the array.

In practice, the choice often depends on the specific problem constraints, input size, and the properties of the problem itself (like whether it exhibits overlapping subproblems, optimal substructure, or requires searching through sorted data).
