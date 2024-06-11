List of the time and space complexities for each of the mentioned data structures:

## Fundamental Data Structures

### Arrays

- Access: O(1)
- Search: O(n)
- Insertion: O(n) (O(1) if inserting at the end in a dynamic array)
- Deletion: O(n)
- Space: O(n)

### Linked Lists

- Access: O(n)
- Search: O(n)
- Insertion: O(1)
- Deletion: O(1)
- Space: O(n)
- Doubly Linked List:
  - Same as Singly Linked List, but with additional space for storing previous pointers: O(2n)

### Stacks

- Access: O(n)
- Search: O(n)
- Insertion: O(1)
- Deletion: O(1)
- Space: O(n)

### Queues

- Access: O(n)
- Search: O(n)
- Insertion: O(1)
- Deletion: O(1)
- Space: O(n)
- Priority Queue:
  - Insertion: O(log n)
  - Deletion (Extract Max/Min): O(log n)
  - Space: O(n)
- Deque (Double-ended Queue):
  - Insertion: O(1)
  - Deletion: O(1)
  - Space: O(n)

## Trees and Graphs

- Binary Trees
  - Access/Search: O(n)
  - Insertion: O(n)
  - Deletion: O(n)
  - Space: O(n)
  - Binary Search Tree (BST):
    - Average case: Access/Search/Insertion/Deletion: O(log n)
    - Worst case (unbalanced): Access/Search/Insertion/Deletion: O(n)
    - Space: O(n)
  - Balanced Trees (AVL, Red-Black Tree):
    - Access/Search/Insertion/Deletion: O(log n)
    - Space: O(n)
  - Heaps (Max Heap, Min Heap):
    - Access (Max/Min): O(1)
    - Insertion: O(log n)
    - Deletion: O(log n)
    - Space: O(n)
  - B-Trees and B+ Trees:
    - Access/Search/Insertion/Deletion: O(log n)
    - Space: O(n)
- Graphs
  - Adjacency Matrix:
    - Access (Edge): O(1)
    - Insertion: O(1)
    - Deletion: O(1)
    - Space: O(V^2) (V is the number of vertices)
  - Adjacency List:
    - Access (Edge): O(V)
    - Insertion: O(1)
    - Deletion: O(E)
    - Space: O(V + E) (E is the number of edges)
  - Edge List:
    - Access: O(E)
    - Insertion: O(1)
    - Deletion: O(E)
    - Space: O(E)

### Hashing

- Hash Tables
  - Average case: Access/Search/Insertion/Deletion: O(1)
  - Worst case: Access/Search/Insertion/Deletion: O(n)
  - Space: O(n)

### Specialized Trees

  - Tries
    - Access/Search: O(m) (m is the length of the key)
    - Insertion: O(m)
    - Deletion: O(m)
    - Space: O(ALPHABET_SIZE * m * n) (for a node in each level)

  - Suffix Trees
    - Access/Search: O(m) (m is the length of the pattern)
    - Insertion: O(n) (n is the length of the string)
    - Space: O(n)

### Advanced Data Structures

- Segment Trees
  - Query: O(log n)
  - Update: O(log n)
  - Space: O(n)

- Fenwick Trees (Binary Indexed Trees)
  - Query: O(log n)
  - Update: O(log n)
  - Space: O(n)

- Disjoint Set (Union-Find)
  - Union: O(log* n) (Inverse Ackermann function, almost constant time)
  - Find: O(log* n)
  - Space: O(n)

- Sparse Tables
  - Query: O(1)
  - Preprocessing: O(n log n)
  - Space: O(n log n)

### Miscellaneous

- Matrix
  - Access: O(1)
  - Search: O(n)
  - Insertion: Not typically applicable
  - Deletion: Not typically applicable
  - Space: O(n)

- Bloom Filters
  - Query: O(k) (k is the number of hash functions)
  - Insertion: O(k)
  - Space: O(m) (m is the size of the bit array)

- Skip Lists
  - Access/Search: O(log n)
  - Insertion: O(log n)
  - Deletion: O(log n)
  - Space: O(n log n)

- Self-balancing Binary Search Trees
  - AVL Trees:
    - Access/Search/Insertion/Deletion: O(log n)
    - Space: O(n)
  - Red-Black Trees:
    - Access/Search/Insertion/Deletion: O(log n)
    - Space: O(n)

- Ternary Search Trees
    - Access/Search: O(log n)
    - Insertion: O(log n)
    - Deletion: O(log n)
    - Space: O(n)

- Suffix Arrays
  - Query: O(m + log n) (m is the length of the pattern)
  - Construction: O(n log n)
  - Space: O(n)

## Graph Algorithms Related Structures

- Edge Lists
  - Access: O(E)
  - Insertion: O(1)
  - Deletion: O(E)
  - Space: O(E)

- Incidence Matrix
  - Access: O(1)
  - Insertion: O(1)
  - Deletion: O(1)
  - Space: O(V * E)

- Network Flow Graphs
  - Varies by specific implementation and algorithm used (e.g., Ford-Fulkerson, Edmonds-Karp).
