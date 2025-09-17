# Important Algorithms and Their Brief Description for Interview

## 🔹 Array Algorithms

### Kadane's Algorithm

**Description:** Finds the maximum sum of a contiguous subarray in O(n) time.
**Use Case:** Stock buy/sell problems, maximum subarray problems.
**Example:**

```
Array: [-2, 1, -3, 4, -1, 2, 1, -5, 4]
Maximum subarray: [4, -1, 2, 1] = 6
```

### Two Pointers / Sliding Window

**Description:** Uses two pointers to traverse array/string efficiently, often maintaining a window of elements.
**Use Case:** Subarray/substring problems, pair finding, removing duplicates.
**Example:**

```
Find pair with sum = 9 in sorted array [1, 2, 3, 4, 6]
Left=0, Right=4: 1+6=7 < 9, move left
Left=1, Right=4: 2+6=8 < 9, move left
Left=2, Right=4: 3+6=9 ✓
```

### Prefix Sum & Difference Array

**Description:** Precompute cumulative sums for fast range queries and updates.
**Use Case:** Range sum queries, subarray problems, interval updates.
**Example:**

```
Array: [1, 3, 5, 7, 9]
Prefix: [1, 4, 9, 16, 25]
Sum(1,3) = prefix[3] - prefix[0] = 16 - 1 = 15
```

### Binary Search Variants

**Description:** Efficiently search in sorted/rotated arrays using divide and conquer.
**Use Case:** Search rotated arrays, find first/last occurrence, bounds.
**Example:**

```
Find first occurrence of 3 in [1,2,3,3,3,4,5]
Binary search with condition: nums[mid] >= target
Result: index 2
```

## 🔹 String Algorithms

### KMP (Knuth-Morris-Pratt)

**Description:** Pattern matching algorithm that avoids redundant comparisons using failure function.
**Use Case:** Substring search, pattern matching in O(n+m).
**Example:**

```
Text: "ABABCABABA"
Pattern: "ABABA"
KMP finds pattern at index 5 without backtracking
```

### Rabin-Karp

**Description:** Uses rolling hash to find pattern occurrences efficiently.
**Use Case:** Plagiarism detection, multiple pattern search.
**Example:**

```
Text: "hello world"
Pattern: "llo"
Hash("hel") → Hash("ell") → Hash("llo") ✓
```

### Z-Algorithm

**Description:** Computes Z-array where Z[i] = length of longest substring starting from i matching prefix.
**Use Case:** String matching, pattern finding in O(n).
**Example:**

```
String: "aaabaaab"
Z-array: [0,2,1,0,3,2,1,0]
```

### Trie-based Solutions

**Description:** Tree structure for efficient string storage and prefix operations.
**Use Case:** Autocomplete, dictionary problems, prefix search.
**Example:**

```
Words: ["cat", "car", "card"]
Trie structure allows O(m) search for any prefix
```

## 🔹 Stack Algorithms

### Monotonic Stack

**Description:** Stack maintaining elements in increasing/decreasing order.
**Use Case:** Next greater/smaller element, histogram problems.
**Example:**

```
Array: [2, 1, 2, 4, 3, 1]
Next greater: [4, 2, 4, -1, -1, -1]
```

### Balanced Parentheses Check

**Description:** Use stack to match opening and closing brackets.
**Use Case:** Expression validation, compiler design.
**Example:**

```
"({[]})" → Valid (all brackets properly matched)
"({[})" → Invalid (mismatched brackets)
```

### Expression Evaluation

**Description:** Convert infix to postfix and evaluate using stack.
**Use Case:** Calculator implementation, expression parsing.
**Example:**

```
Infix: "3 + 4 * 2"
Postfix: "3 4 2 * +"
Evaluation: 3 + (4 * 2) = 11
```

## 🔹 Queue Algorithms

### Sliding Window Maximum (Deque)

**Description:** Find maximum in all subarrays of size k using deque.
**Use Case:** Window-based problems, real-time max/min tracking.
**Example:**

```
Array: [1,3,-1,-3,5,3,6,7], k=3
Maximums: [3,3,5,5,6,7]
```

### Circular Queue

**Description:** Queue with fixed size where end connects to beginning.
**Use Case:** Buffer implementation, resource scheduling.
**Example:**

```
Size 4: [_, _, _, _]
Enqueue 1,2,3,4: [1,2,3,4]
Dequeue, Enqueue 5: [5,2,3,4]
```

### BFS (Breadth-First Search)

**Description:** Level-order traversal using queue.
**Use Case:** Shortest path, level-order problems, graph connectivity.
**Example:**

```
Tree BFS: 1 → 2,3 → 4,5,6,7
Queue operations: [1] → [2,3] → [3,4,5] → [4,5,6,7]
```

## 🔹 Heap (Priority Queue) Algorithms

### Heap Sort

**Description:** Sort array using heap data structure in O(n log n).
**Use Case:** In-place sorting, when consistent O(n log n) needed.
**Example:**

```
Array: [4,1,3,2,16,9,10,14,8,7]
Build max-heap → Extract max repeatedly
Result: [1,2,3,4,7,8,9,10,14,16]
```

### Top-K Elements

**Description:** Find k largest/smallest elements using min/max heap.
**Use Case:** Top K frequent elements, finding extremes.
**Example:**

```
Find 3 largest in [3,2,1,5,6,4]
Min-heap of size 3: [3,5,6] → Result: [4,5,6]
```

### Dijkstra's Algorithm

**Description:** Shortest path algorithm using min-heap for graph traversal.
**Use Case:** GPS navigation, network routing, shortest path.
**Example:**

```
Graph: A→B(4), A→C(2), B→C(1), B→D(5), C→D(8)
Shortest A→D: A→C→B→D = 2+1+5 = 8
```

### Median of Data Stream

**Description:** Maintain running median using two heaps (max + min).
**Use Case:** Real-time statistics, streaming data analysis.
**Example:**

```
Stream: [5,15,1,3]
Medians: [5, 10, 5, 4]
Max-heap: smaller half, Min-heap: larger half
```

## 🔹 Tree Algorithms

### DFS Traversals

**Description:** Depth-first tree traversal in three orders.
**Use Case:** Tree processing, expression trees, file systems.
**Example:**

```
Tree:    1
        / \
       2   3
Inorder: 2,1,3  Preorder: 1,2,3  Postorder: 2,3,1
```

### Lowest Common Ancestor (LCA)

**Description:** Find deepest common ancestor of two nodes.
**Use Case:** Tree queries, genealogy, hierarchical data.
**Example:**

```
Tree: 1(2(4,5),3(6,7))
LCA(4,5) = 2, LCA(4,6) = 1
```

### Binary Search Tree Operations

**Description:** Efficient search, insert, delete in ordered tree.
**Use Case:** Database indexing, ordered data storage.
**Example:**

```
BST: Insert 5,3,7,2,4,6,8
Search 4: 5→3→4 (O(log n))
```

### Segment Tree / Fenwick Tree

**Description:** Tree for efficient range queries and updates.
**Use Case:** Range sum/min/max queries, competitive programming.
**Example:**

```
Array: [1,3,5,7,9,11]
Range sum(1,3): query in O(log n)
Update index 2: update in O(log n)
```

## 🔹 Graph Algorithms

### BFS / DFS

**Description:** Graph traversal algorithms for connectivity and paths.
**Use Case:** Connected components, cycle detection, pathfinding.
**Example:**

```
Graph: 1-2-3, 2-4
BFS from 1: 1→2→3,4
DFS from 1: 1→2→3, backtrack, 2→4
```

### Dijkstra's Algorithm

**Description:** Shortest path from source to all vertices (non-negative weights).
**Use Case:** GPS systems, network protocols, flight connections.
**Example:**

```
A→B(10), A→C(3), B→C(1), B→D(2), C→D(8)
Shortest A→D: A→C→B→D = 3+1+2 = 6
```

### Bellman-Ford

**Description:** Shortest path algorithm that handles negative weights.
**Use Case:** Currency arbitrage, network with negative costs.
**Example:**

```
Graph with negative edge: A→B(1), B→C(-3), A→C(4)
Shortest A→C: A→B→C = 1+(-3) = -2
```

### Floyd-Warshall

**Description:** All-pairs shortest path using dynamic programming.
**Use Case:** Dense graphs, transitive closure, shortest paths matrix.
**Example:**

```
3x3 distance matrix → compute shortest paths between all pairs
dist[i][j] = min(dist[i][j], dist[i][k] + dist[k][j])
```

### Topological Sort

**Description:** Linear ordering of vertices in directed acyclic graph.
**Use Case:** Task scheduling, course prerequisites, build systems.
**Example:**

```
Dependencies: A→B, A→C, B→D, C→D
Valid order: A, B, C, D or A, C, B, D
```

### Union-Find (DSU)

**Description:** Disjoint set data structure for connectivity queries.
**Use Case:** Kruskal's MST, connected components, cycle detection.
**Example:**

```
Sets: {1}, {2}, {3}, {4}
Union(1,2): {1,2}, {3}, {4}
Find(1) == Find(2): true (same component)
```

### Prim's Algorithm

**Description:** Greedy algorithm for finding minimum spanning tree.
**Use Case:** Network design, clustering, minimum cost connectivity.
**Example:**

```
Graph edges with weights: A-B(2), A-C(3), B-C(1), B-D(4)
MST: A-B(2), B-C(1), B-D(4) = total weight 7
```

## 🔹 Dynamic Programming (DP)

### Knapsack Variants

**Description:** Optimization problems with capacity constraints.
**Use Case:** Resource allocation, subset selection, coin change.
**Example:**

```
0/1 Knapsack: items with weights/values, maximize value ≤ capacity
Items: (w=1,v=1), (w=3,v=4), (w=4,v=5), capacity=4
Optimal: item 2 + item 1 = value 5
```

### Longest Common Subsequence (LCS)

**Description:** Find longest subsequence common to two sequences.
**Use Case:** DNA sequencing, diff algorithms, text comparison.
**Example:**

```
"ABCDGH" and "AEDFHR"
LCS: "ADH" (length 3)
DP[i][j] = LCS length for first i and j characters
```

### Longest Increasing Subsequence (LIS)

**Description:** Find longest subsequence with increasing elements.
**Use Case:** Patience sorting, box stacking, activity selection.
**Example:**

```
Array: [10,22,9,33,21,50,41,60]
LIS: [10,22,33,50,60] (length 5)
Can use DP + Binary Search for O(n log n)
```

### Matrix DP

**Description:** DP on 2D grids for path and optimization problems.
**Use Case:** Path counting, minimum cost paths, edit distance.
**Example:**

```
Grid paths from (0,0) to (m,n):
dp[i][j] = dp[i-1][j] + dp[i][j-1]
Each cell = sum of paths from top and left
```

### DP on Trees

**Description:** Dynamic programming on tree structures.
**Use Case:** Tree diameter, maximum path sum, subtree problems.
**Example:**

```
Tree diameter: longest path between any two nodes
For each node: max(left_depth + right_depth + 1)
```

### Bitmask DP

**Description:** DP using bitmasks to represent subsets.
**Use Case:** Traveling salesman, subset enumeration, state compression.
**Example:**

```
TSP with 4 cities: bitmask 1011 = visited cities 0,1,3
dp[mask][i] = minimum cost to visit cities in mask, ending at i
```

## 🔹 Greedy Algorithms

### Interval Scheduling

**Description:** Select maximum non-overlapping intervals.
**Use Case:** Meeting scheduling, resource allocation, activity selection.
**Example:**

```
Intervals: [(1,3), (2,4), (3,5), (4,6)]
Greedy: sort by end time, select non-overlapping
Result: [(1,3), (3,5)] or [(1,3), (4,6)]
```

### Huffman Encoding

**Description:** Optimal prefix-free encoding using frequency-based tree.
**Use Case:** Data compression, encoding optimization.
**Example:**

```
Characters: A(5), B(9), C(12), D(13), E(16), F(45)
Build tree from least frequent pairs
Shorter codes for frequent characters
```

### Kruskal's MST

**Description:** Find minimum spanning tree by sorting edges and using Union-Find.
**Use Case:** Network design, clustering, minimum cost connections.
**Example:**

```
Edges: A-B(1), B-C(2), A-C(3), C-D(4)
Sort by weight: (1,2,3,4)
Add edges if no cycle: A-B, B-C, C-D
```

### Job Sequencing

**Description:** Schedule jobs with deadlines to maximize profit.
**Use Case:** Task scheduling, profit maximization, deadline management.
**Example:**

```
Jobs: (profit=20, deadline=2), (profit=15, deadline=2), (profit=10, deadline=1)
Schedule: Job1 at time 2, Job3 at time 1
Total profit: 30
```

### Greedy Coin Change

**Description:** Make change using minimum coins (works for canonical systems).
**Use Case:** Currency systems, making change, resource optimization.
**Example:**

```
Coins: [1,5,10,25], Amount: 30
Greedy: 25 + 5 = 2 coins
Works for standard coin systems
```

## ✅ Interview Strategy

### Array/String Problems

- **Pattern Recognition:** Look for subarray/substring patterns
- **Common Techniques:** Two pointers, sliding window, prefix sums
- **Time Complexity:** Aim for O(n) or O(n log n) solutions

### Stack/Queue/Heap Problems

- **When to Use:** Monotonic properties, top-k problems, scheduling
- **Optimization:** Replace brute force O(n²) with O(n) using stack
- **Heap Usage:** Priority-based problems, streaming data

### Tree/Graph Problems

- **Traversal Mastery:** Know BFS, DFS, and their applications
- **Advanced:** LCA, shortest paths, MST for complex problems
- **Practice:** Tree DP, graph connectivity, topological ordering

### DP/Greedy Problems

- **Pattern Recognition:** Overlapping subproblems → DP, Greedy choice → Greedy
- **Classic Patterns:** Knapsack variations, LCS/LIS, interval problems
- **Approach:** Start with brute force, identify overlapping subproblems, optimize

### Key Interview Tips

1. **Always clarify constraints** and edge cases
2. **Start with brute force**, then optimize
3. **Think out loud** - explain your thought process
4. **Test with examples** before coding
5. **Consider time/space complexity** tradeoffs
