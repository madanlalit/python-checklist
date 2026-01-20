# Data Structures & Algorithms in Python — 0→100 Checklist (Roadmap + Python Tooling)

> Python DSA “superpower”: you’re not just learning structures/algorithms — you’re learning **which built-in type gives the right complexity** and how to compose them (`dict` + `list`, `deque` + `set`, `heapq` + `dict`, etc.).

**How to use**
- For every checkbox: (1) know definition, (2) know time/space, (3) can implement, (4) can apply to 5+ problems, (5) can explain why it’s correct.
- Prefer “solve → then study” loops: attempt a problem first, then map it back to a checklist item.

---

# Phase 0 — Foundations (start here)
## 0.1 Big‑O and reasoning
- [ ] Time complexity: O(1), O(log n), O(n), O(n log n), O(n²), O(2ⁿ), O(n!)
- [ ] Space complexity: auxiliary vs total
- [ ] Amortized analysis (dynamic array append, hash table behavior)
- [ ] Best/average/worst case and when each matters
- [ ] Lower bounds intuition (why sorting is Ω(n log n) for comparisons)

## 0.2 Problem solving workflow
- [ ] Translate problem → constraints → feasible complexity
- [ ] Identify structure: array/string, set/map, stack/queue, tree/graph, DP, greedy
- [ ] Invariants: what stays true at each step
- [ ] Edge cases: empty, 1 element, duplicates, negatives, overflow (less in Python but still logic)
- [ ] Testing strategy: small cases + randomized tests for confidence

## 0.3 Python DSA toolbox (must know)
- [ ] Core: `list`, `tuple`, `dict`, `set`
- [ ] `collections`: `deque`, `Counter`, `defaultdict`
- [ ] `heapq` (min-heap), and max-heap pattern via negatives
- [ ] `bisect` (binary search insertion points)
- [ ] `itertools` (combinatorics, grouping, windows)
- [ ] `functools.lru_cache` (DP memoization)
- [ ] `math` (gcd, isqrt, comb, prod)
- [ ] `typing` (helps design and avoid mistakes in complex DS)
- [ ] Practical constraints:
  - [ ] recursion depth limit (and iterative alternatives)
  - [ ] input speed patterns (e.g., `sys.stdin.readline` conceptually)

**Proof exercises**
- [ ] Given constraints, pick the highest acceptable complexity and justify it
- [ ] Write a brute force + optimized version and compare runtime on random data

---

# Phase 1 — Arrays & Strings (the most common substrate)
## 1.1 Arrays in Python (`list`) deep behavior
- [ ] Indexing, slicing, iteration
- [ ] Append/pop at end is amortized O(1)
- [ ] Insert/pop at front or middle is O(n)
- [ ] Copying pitfalls: slicing creates copies; aliasing issues

## 1.2 Core patterns
- [ ] Two pointers (inward, same-direction)
- [ ] Sliding window (fixed and variable size)
- [ ] Prefix sums (1D) and prefix sums (2D)
- [ ] Difference arrays / range updates
- [ ] Frequency arrays (when alphabet/range is small)
- [ ] Kadane’s algorithm (max subarray)
- [ ] Partition patterns (like quicksort partition)
- [ ] Cycle detection on indices (Floyd’s “tortoise-hare” on arrays)

## 1.3 Strings (Python specifics)
- [ ] Immutability of strings (build with list/join)
- [ ] `in` substring basics (but know it’s not always trivial complexity)
- [ ] Common string patterns:
  - [ ] anagrams via counts
  - [ ] palindromes via two pointers
  - [ ] run-length encoding
  - [ ] hashing intuition (later: rolling hash)

**Proof exercises**
- [ ] Solve 10 problems using sliding window + frequency map
- [ ] Implement 2D prefix sum and answer rectangle sum queries

---

# Phase 2 — Hashing: Sets & Maps (dict/set mastery)
## 2.1 `dict` and `set` fundamentals
- [ ] Membership is average O(1)
- [ ] Hashable vs unhashable types (tuples ok if contents hashable)
- [ ] Collisions conceptually and why worst-case exists
- [ ] Iteration patterns:
  - [ ] iterate keys, values, items
  - [ ] dictionary comprehension
- [ ] `defaultdict` vs `dict.get`
- [ ] `Counter` for frequency-heavy tasks

## 2.2 Canonical hashing problem patterns
- [ ] Two-sum / k-sum with hashing
- [ ] Grouping (anagrams, buckets)
- [ ] Deduping and unique tracking
- [ ] First seen index / last seen index maps
- [ ] Prefix sum + hash map (subarray sum equals K)
- [ ] Sliding window with set/map for “distinct” constraints

**Proof exercises**
- [ ] Implement “subarray sum = K” and explain invariant
- [ ] Solve 10 problems where `dict` is the key optimization

---

# Phase 3 — Stacks, Queues, Deques (and monotonic structures)
## 3.1 Stack
- [ ] Implement stack with list
- [ ] Classic stack tasks:
  - [ ] valid parentheses / bracket matching
  - [ ] simplify paths / parsing
  - [ ] expression evaluation basics (optional)
- [ ] Monotonic stack:
  - [ ] next greater element
  - [ ] largest rectangle in histogram
  - [ ] daily temperatures / span problems

## 3.2 Queue / Deque
- [ ] `deque` vs list for queue (O(1) pops from left)
- [ ] BFS basics using `deque`
- [ ] Sliding window maximum via monotonic deque

**Proof exercises**
- [ ] Implement next greater element in O(n) using monotonic stack
- [ ] Implement sliding window maximum using monotonic deque

---

# Phase 4 — Searching & Sorting (core algorithmic literacy)
## 4.1 Binary search (and `bisect`)
- [ ] Binary search on sorted array
- [ ] Lower bound / upper bound semantics
- [ ] Binary search on answer (a.k.a. parametric search)
- [ ] Use `bisect_left` / `bisect_right` correctly

## 4.2 Sorting
- [ ] Python’s `sorted` / `.sort()`:
  - [ ] stable sorting
  - [ ] `key=` functions
  - [ ] sorting tuples and custom objects
- [ ] Know classic sorts conceptually:
  - [ ] merge sort, quicksort, heapsort (idea + complexity)
- [ ] Selection / order statistics:
  - [ ] quickselect concept (optional)

**Proof exercises**
- [ ] Write 5 “binary search on answer” solutions
- [ ] Solve interval problems that rely on sorting + sweep line

---

# Phase 5 — Linked Lists (less common in Python, common in interviews)
## 5.1 Implementation and operations
- [ ] Node structure, building a list
- [ ] Insert/delete
- [ ] Reverse a linked list
- [ ] Merge two sorted lists
- [ ] Detect cycle (Floyd)
- [ ] Find middle (fast/slow pointers)

**Proof exercises**
- [ ] Reverse list iteratively and recursively; explain tradeoffs
- [ ] Detect cycle and find cycle entry (proof sketch)

---

# Phase 6 — Trees (recursion, traversal, structure)
## 6.1 Tree basics
- [ ] Tree terminology: root, leaf, height, depth
- [ ] Representations:
  - [ ] Node objects
  - [ ] adjacency lists (for generic trees)
- [ ] Traversals:
  - [ ] DFS preorder/inorder/postorder
  - [ ] BFS level order
- [ ] Recursion vs iterative stack traversal

## 6.2 Binary search trees (BST)
- [ ] BST properties
- [ ] Validate BST
- [ ] Insert/search/delete conceptually

## 6.3 Tree problem patterns
- [ ] Path sums
- [ ] Lowest common ancestor (LCA) basics (advanced versions later)
- [ ] Diameter of tree
- [ ] Subtree computations (postorder DP)

**Proof exercises**
- [ ] Implement all traversals iteratively and recursively
- [ ] Solve 10 tree DFS problems (path/invariant based)

---

# Phase 7 — Heaps & Priority Queues (`heapq`)
## 7.1 Heap mechanics
- [ ] Min-heap operations: push, pop, heapify
- [ ] Max-heap pattern (negate values or store tuples)
- [ ] Heaps with tuples for custom priority
- [ ] Maintain top-K, streaming median (two heaps)

## 7.2 Heap-driven algorithms
- [ ] K-way merge
- [ ] Scheduling problems (min rooms, CPU tasks patterns)
- [ ] Dijkstra’s algorithm (later in graphs)

**Proof exercises**
- [ ] Implement top-K frequent elements with heap
- [ ] Implement streaming median with two heaps

---

# Phase 8 — Graphs (the big one)
## 8.1 Graph representations
- [ ] Adjacency list (dict/list of lists)
- [ ] Adjacency matrix (when dense / small)
- [ ] Edge list (for Kruskal / sorting edges)
- [ ] Directed vs undirected, weighted vs unweighted

## 8.2 Traversals and components
- [ ] BFS (shortest path in unweighted graph)
- [ ] DFS (recursive + iterative)
- [ ] Connected components / islands counting
- [ ] Cycle detection:
  - [ ] undirected via parent tracking / DSU
  - [ ] directed via recursion stack colors

## 8.3 DAG algorithms
- [ ] Topological sort (Kahn’s BFS and DFS-based)
- [ ] Longest path in DAG (DP on topo order)

## 8.4 Shortest paths
- [ ] Dijkstra (non-negative weights) with heap
- [ ] Bellman-Ford (negative weights; detect negative cycles)
- [ ] Floyd–Warshall (all-pairs, small n)

## 8.5 Minimum spanning tree (MST)
- [ ] Kruskal (requires DSU)
- [ ] Prim (heap-based)

## 8.6 Advanced graph topics (optional but powerful)
- [ ] Strongly connected components (Kosaraju / Tarjan)
- [ ] Bipartite check (BFS coloring)
- [ ] Union-Find (DSU) deep:
  - [ ] path compression
  - [ ] union by rank/size
- [ ] Network flow (Edmonds–Karp / Dinic) (advanced/optional)

**Proof exercises**
- [ ] Solve shortest path in grid (BFS) + weighted grid (Dijkstra)
- [ ] Implement DSU and use it to solve Kruskal MST

---

# Phase 9 — Dynamic Programming (DP) (pattern mastery)
## 9.1 DP foundations
- [ ] When DP applies: overlapping subproblems + optimal substructure
- [ ] States, transitions, base cases
- [ ] Memoization (top-down) with `lru_cache`
- [ ] Tabulation (bottom-up)
- [ ] Space optimization (rolling arrays)

## 9.2 DP archetypes (must cover)
- [ ] 1D DP (stairs, house robber)
- [ ] 2D grid DP (unique paths, min path sum)
- [ ] Knapsack family:
  - [ ] 0/1 knapsack
  - [ ] unbounded knapsack
- [ ] Subsequence DP:
  - [ ] LIS (O(n²) and O(n log n) idea)
  - [ ] LCS (classic)
- [ ] Interval DP (merge stones style) (advanced)
- [ ] Bitmask DP (small n) (advanced)
- [ ] Tree DP basics (rerooting optional)

## 9.3 Correctness and optimization
- [ ] Prove recurrence correctness via induction
- [ ] Identify state size and transition cost
- [ ] Recognize when DP becomes infeasible and how to reduce state

**Proof exercises**
- [ ] Write both memoized and tabulated versions of same problem
- [ ] Solve 20 DP problems across 5 archetypes (track which archetype)

---

# Phase 10 — Greedy Algorithms (prove or don’t trust it)
## 10.1 Greedy fundamentals
- [ ] Greedy choice property and exchange arguments (proof mindset)
- [ ] Sorting-first greedy patterns:
  - [ ] interval scheduling
  - [ ] meeting rooms
  - [ ] activity selection
- [ ] Heap + greedy hybrids (scheduling, maximizing min)
- [ ] Graph greedy:
  - [ ] MST (Kruskal/Prim) as greedy
- [ ] Huffman coding concept (optional)

**Proof exercises**
- [ ] For 5 greedy problems, write the “why greedy works” argument

---

# Phase 11 — Backtracking & Recursion Patterns
- [ ] Recursion trees and pruning
- [ ] Permutations, combinations, subsets
- [ ] Constraint satisfaction:
  - [ ] N-Queens
  - [ ] Sudoku solver concept
- [ ] Backtracking with:
  - [ ] used sets/bitmasks
  - [ ] ordering heuristics (choose tightest first)

**Proof exercises**
- [ ] Implement subsets and permutations iteratively and recursively
- [ ] Solve 5 backtracking problems with pruning notes

---

# Phase 12 — String Algorithms (beyond basic)
## 12.1 Core string techniques
- [ ] Two pointers / sliding window for strings
- [ ] Prefix function / failure function concept
- [ ] Rolling hash (Rabin–Karp) concept + collision awareness

## 12.2 Classical algorithms (advanced)
- [ ] KMP (pattern search) (implement + explain)
- [ ] Z-algorithm (implement + explain)
- [ ] Trie:
  - [ ] insert/search/prefix
  - [ ] word search on board
- [ ] Suffix array / suffix automaton concepts (very advanced/optional)

**Proof exercises**
- [ ] Implement Trie and use it in autocomplete / prefix search
- [ ] Implement KMP or Z and compare to naive search

---

# Phase 13 — Math & Bit Manipulation (interview + competitive staples)
## 13.1 Number theory basics
- [ ] gcd / lcm
- [ ] modular arithmetic and modular exponentiation
- [ ] primality testing (simple)
- [ ] sieve of Eratosthenes
- [ ] combinatorics:
  - [ ] nCk (`math.comb`)
  - [ ] factorials, permutations
- [ ] integer sqrt (`math.isqrt`) usage patterns

## 13.2 Bit tricks
- [ ] bitwise ops (`& | ^ ~ << >>`)
- [ ] check/set/clear/toggle bit
- [ ] count bits (popcount) patterns
- [ ] XOR properties (pairing/cancellation)
- [ ] bitmask enumeration (subsets)

**Proof exercises**
- [ ] Solve 10 problems using XOR/bitmask patterns
- [ ] Implement sieve and use it to answer prime queries

---

# Phase 14 — Advanced Data Structures (optional “100+” tier)
> These are less common in day-to-day Python, but huge for algorithmic depth.

- [ ] Fenwick tree (Binary Indexed Tree)
- [ ] Segment tree (range queries/updates)
- [ ] Sparse table (static RMQ)
- [ ] LCA:
  - [ ] binary lifting
  - [ ] Euler tour + RMQ concept
- [ ] Heavy-light decomposition concept (very advanced)
- [ ] Ordered set/map concept:
  - [ ] emulate with `bisect` on list (with O(n) updates)
  - [ ] know external libs exist (if allowed) (concept only)
- [ ] Trie variants:
  - [ ] bitwise trie for max XOR
- [ ] Sweep line + event processing patterns (geometry/interval heavy)
- [ ] Randomized structures/algorithms (treaps concept) (optional)

**Proof exercises**
- [ ] Implement Fenwick for prefix sums with point updates
- [ ] Implement segment tree and solve range min / range sum queries

---

# Phase 15 — Python Performance for DSA (make solutions pass)
- [ ] Choose data structures for constant factors (e.g., `deque` vs `list`)
- [ ] Avoid O(n²) string concatenation; use `''.join`
- [ ] Replace recursion with iterative stack when depth is large
- [ ] Use `lru_cache` effectively (and know recursion overhead)
- [ ] Prefer local variables inside tight loops (micro-optimization concept)
- [ ] Use `heapq` patterns efficiently (don’t rebuild heaps repeatedly)
- [ ] Understand memory implications (storing whole graph vs streaming edges)
- [ ] Know when PyPy can help (conceptual)
- [ ] Profiling basics: identify bottleneck vs guess

---

# Appendix A — Python complexity quick sheet (memorize the *shape*)
- [ ] `list`:
  - [ ] index: O(1)
  - [ ] append/pop end: amortized O(1)
  - [ ] insert/pop front/middle: O(n)
- [ ] `deque`:
  - [ ] append/pop both ends: O(1)
- [ ] `dict` / `set`:
  - [ ] get/add/remove/membership: average O(1)
- [ ] `heapq`:
  - [ ] push/pop: O(log n)
  - [ ] heapify: O(n)
- [ ] `bisect`:
  - [ ] search position: O(log n)
  - [ ] insertion into list: O(n) due to shifting

---

# Appendix B — Canonical “pattern buckets” (use as your practice map)
- [ ] Two pointers
- [ ] Sliding window
- [ ] Prefix sums / difference arrays
- [ ] Hash map counting
- [ ] Monotonic stack / monotonic deque
- [ ] Binary search on answer
- [ ] BFS/DFS on grids and graphs
- [ ] Topological sort
- [ ] Dijkstra / shortest paths
- [ ] Union-Find
- [ ] DP (1D/2D/knapsack/subsequence/interval/bitmask)
- [ ] Greedy (intervals/scheduling/heap-greedy)
- [ ] Backtracking (subsets/perms/constraints)
- [ ] String algorithms (Trie/KMP/Z/rolling hash)
- [ ] Bit manipulation + math

---

# Appendix C — 0→100 suggested learning order (simple path)
1) Arrays/strings patterns → hashing (`dict/set`) → stacks/queues  
2) Sorting + binary search → heaps  
3) Trees → graphs (BFS/DFS → topo → Dijkstra/MST)  
4) DP → greedy → backtracking  
5) String algorithms + bit/math  
6) Advanced DS (Fenwick/segment/LCA) + performance tuning

---
