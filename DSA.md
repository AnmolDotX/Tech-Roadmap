# Problem Solving & DSA

Cover All & keep revising.
---

## 1. Arrays, Prefix Sums & Hashing

### Core Algorithmic Techniques

* **Prefix / Suffix Precomputation:** Prefix sums, prefix products, difference arrays (range updates in $O(1)$).
* **Kadane’s Algorithm & State Machine Variants:** Maximum subarray sum, maximum circular subarray sum, maximum product subarray.
* **Dutch National Flag / In-Place Partitioning:** 3-way partitioning for zero-memory overhead.
* **Hash Inversion & Frequency Mapping:** Storing indices or running sums in hash maps to convert $O(N^2)$ checks to $O(1)$.

### High-Yield Problems & Modern Caveats

| Problem Name | Target Companies | Core Pattern / Algorithmic Trick | Modern Interview Caveat & Follow-Up |
| --- | --- | --- | --- |
| **Next Permutation** | Amazon, Swiggy | Pivot discovery from the right, single swap, suffix reversal in $O(N)$ time and $O(1)$ space. | *Follow-up:* What if duplicate elements are present? What if you are asked to generate the $K$-th permutation directly without generating the intermediate $K-1$ states? |
| **Subarray Sum Equals K** | Amazon, INDmoney, Fractal | Running prefix sum with hash map counting occurrences of `prefix_sum - k`. | *Follow-up:* Can you solve it if array values can only be positive in $O(1)$ space? (Sliding Window). What if numbers are floating-point numbers with rounding precision limits? |
| **Product of Array Except Self** | Swiggy, Urban Company | Prefix and suffix accumulators; reuse output array to hit $O(1)$ auxiliary space. | *Follow-up:* Division is strictly disallowed. What if elements can cause integer overflow beyond 64-bit integer limits? |
| **Merge Overlapping Intervals** | Amazon, Swiggy, Urban Company | Sort by start time, greedy merge by tracking running `max(end_time)`. | *Follow-up:* How does this scale if the interval stream arrives continuously in real time? (Interval Tree / Segment Tree). |
| **Set Matrix Zeroes** | INDmoney, Amazon | In-place marker variables using row 0 and column 0. | *Follow-up:* What if the matrix is stored on disk in row-major order and cannot fit into memory simultaneously? |
| **First Missing Positive** | Amazon, Swiggy | Index-as-hash-key placement: cyclically place number $X$ at index $X-1$ in $O(N)$ time and $O(1)$ space. | *Follow-up:* Prove mathematically that this is $O(N)$ even with nested while loops (Amortized analysis: each element placed at most twice). |

---

## 2. Two Pointers & Sliding Window

### Core Algorithmic Techniques

* **Opposite-Direction Pointers:** Meeting in the middle for sorted array lookups or greedy bounding.
* **Dynamic-Size Sliding Window:** Expansion via right pointer, state validation, and contraction via left pointer.
* **Monotonic Deque Window:** Maintaining extreme elements (min/max) within sliding bounds in amortized $O(1)$ per operation.

### High-Yield Problems & Modern Caveats

| Problem Name | Target Companies | Core Pattern / Algorithmic Trick | Modern Interview Caveat & Follow-Up |
| --- | --- | --- | --- |
| **Trapping Rain Water** | Amazon, Swiggy, Urban Company | Two pointers inward tracking `left_max` and `right_max` in $O(1)$ space. | *Follow-up:* Extend to 2D (Trapping Rain Water II) using a Min-Heap. What if terrain elevations update dynamically? |
| **Longest Substring Without Repeating Characters** | Fractal, INDmoney, Amazon | Dynamic window with a hash map storing the latest seen index of each character to jump the left pointer. | *Follow-up:* Handle variable-byte UTF-8 inputs where code points span 1 to 4 bytes instead of ASCII. |
| **Minimum Window Substring** | Amazon, Swiggy | Frequency map tracking remaining character requirements; minimize window once valid. | *Follow-up:* Optimize character checks from $O(26)$ to $O(1)$ using an active `formed_characters` match counter. |
| **3Sum & 4Sum** | Amazon, Fractal, Urban Company | Sort first, fix $N-2$ variables, use two pointers for the rest; deduplicate by advancing past identical values. | *Follow-up:* What if the dataset is 500 GB and distributed across 10 worker nodes? (MapReduce bucketed join approach). |
| **Sliding Window Maximum** | Swiggy, Amazon | Monotonic Decreasing Deque storing indices to purge smaller and out-of-boundary elements. | *Follow-up:* Implement the window with $O(1)$ extra space by dividing the array into blocks of size $K$ (Prefix/Suffix array trick). |

---

## 3. Binary Search & Search Space Reduction

### Core Algorithmic Techniques

* **Boundary Conditions & Invariants:** Strict avoidance of infinite loops using `low + (high - low) / 2` and unambiguous condition updates (`low = mid + 1` vs `high = mid`).
* **Search Space Reduction on Monotonic Functions:** "Binary Search on Answer" when testing feasibility $f(x) \in \{\text{True}, \text{False}\}$ is monotonic.
* **Rotated & Unsorted Search:** Locating which half is guaranteed to be sorted before pruning.

### High-Yield Problems & Modern Caveats

| Problem Name | Target Companies | Core Pattern / Algorithmic Trick | Modern Interview Caveat & Follow-Up |
| --- | --- | --- | --- |
| **Search in Rotated Sorted Array (I & II)** | Amazon, Swiggy, INDmoney | Identify the strictly sorted half; check if target falls within bounds. Part II degrades to $O(N)$ on duplicates. | *Follow-up:* Explain worst-case time complexity on an array containing identical elements (e.g., `[1, 1, 1, 2, 1, 1]`) and why binary search fails to achieve $O(\log N)$. |
| **Median of Two Sorted Arrays** | Amazon, Swiggy | Binary search on partition cut in the smaller array to equalize total left and right partition counts in $O(\log(\min(M, N)))$. | *Follow-up:* Adapt to find the $K$-th smallest element across two distributed streams without loading both streams to a single machine. |
| **Capacity to Ship Packages Within D Days** | Urban Company, Fractal | Binary search on the answer: range is $[\max(\text{weights}), \sum \text{weights}]$. Feasibility function greedily packs bins. | *Follow-up:* What if package order can be rearranged? (Reduces to the NP-hard Bin Packing Problem). |
| **Koko Eating Bananas** | Swiggy, Amazon | Binary search over speed $[1, \max(\text{piles})]$; sum ceil divisions $\lceil \text{pile} / k \rceil$. | *Follow-up:* Watch out for integer overflow when accumulating total hours if hour constraints are up to $10^9$. |
| **Find Peak Element** | Amazon, INDmoney | Binary search on unsorted array: move towards the strictly higher neighbor because a local peak is guaranteed to exist. | *Follow-up:* Prove convergence in $O(\log N)$ and generalize to finding a 2D peak in a grid in $O(N \log M)$. |

---

## 4. Stacks, Queues & Monotonic Sequences

### Core Algorithmic Techniques

* **Monotonic Stack:** Resolving Nearest Greater / Smaller Element queries in linear time.
* **Stack-based Evaluation:** Parsing nested structures, parenthesized expressions, and calculator engines.
* **Queue-based Simulators:** Sliding buffers, circular buffers, and event loop mechanics.

### High-Yield Problems & Modern Caveats

| Problem Name | Target Companies | Core Pattern / Algorithmic Trick | Modern Interview Caveat & Follow-Up |
| --- | --- | --- | --- |
| **Largest Rectangle in Histogram** | Amazon, Swiggy | Monotonic increasing stack storing indices; calculate area when popping an element using current index and new stack top. | *Follow-up:* How to solve in a single pass without extra padding zeroes? Generalize to Maximal Rectangle in a binary 2D matrix. |
| **Daily Temperatures / Next Greater Element II** | Swiggy, Fractal | Monotonic stack storing indices; loop array twice (`i % N`) for circular coverage. | *Follow-up:* What if temperature data arrives as an infinite stream and you must emit results within a 1-hour window? |
| **Basic Calculator (I, II, & III)** | Amazon, INDmoney | Stacks for operands and operators; handle precedence, unary signs, and parenthesized recursion. | *Follow-up:* Implement the parser without recursion using the Shunting-Yard Algorithm to convert to Reverse Polish Notation (RPN). |
| **Min Stack / Max Stack** | Amazon, Urban Company | Store paired records `(val, current_min)` or encode differences `2*val - min` to achieve $O(1)$ time and $O(1)$ auxiliary space. | *Follow-up:* Make the operations thread-safe under concurrent reader-writer access without coarse mutex locks on the whole structure. |

---

## 5. Linked Lists

### Core Algorithmic Techniques

* **Pointer Mutation Invariants:** Pointer manipulation using sentinel dummy heads to eliminate edge checks.
* **Floyd’s Cycle Detection:** Mathematical guarantee of tortoise and hare meeting point at $2(k - m) \equiv k \pmod C$.
* **In-Place Interleaving:** Splitting lists, reversing halves, and alternating merges.

### High-Yield Problems & Modern Caveats

| Problem Name | Target Companies | Core Pattern / Algorithmic Trick | Modern Interview Caveat & Follow-Up |
| --- | --- | --- | --- |
| **Reverse Nodes in k-Group** | Amazon, Swiggy | Count $K$ nodes ahead; reverse the inner block; re-link head and tail pointers. Repeat. | *Follow-up:* Solve strictly with $O(1)$ memory without recursive call stack overhead. |
| **LRU Cache** | Amazon, Swiggy, Urban Company, INDmoney | Hash Map + Doubly Linked List with dummy head and tail for $O(1)$ eviction and access. | *Follow-up:* **Crucial 24+ LPA check:** Make this thread-safe. Explain read-write locks (`sync.RWMutex`) and Lock Striping to avoid single-lock contention on cache hits. |
| **LFU Cache** | Amazon, Swiggy | Hash Map of keys to node, and Hash Map of frequencies to Doubly Linked Lists; maintain `min_frequency`. | *Follow-up:* Compare cache eviction under burst read traffic (where LRU fails due to scan pollution, but LFU retains hot keys). |
| **Copy List with Random Pointer** | Amazon, Fractal | Interweave cloned nodes adjacent to original nodes: `A -> A' -> B -> B'`. Copy random pointers, then unweave. | *Follow-up:* Do it in $O(1)$ auxiliary space without mutating the original list during read-only concurrent calls. |

---

## 6. Trees & Binary Search Trees

### Core Algorithmic Techniques

* **Bottom-Up DFS (Post-Order):** Collecting subtree metrics before making decisions at the parent node.
* **Tree DP / Diameter Patterns:** Tracking two values: the path contribution passing through the node vs. the path anchored at the node.
* **BST Properties:** In-order traversal yields strictly ascending order; range queries via binary pruning.
* **Level-Order BFS:** Queue-based traversal with size snapshotting per level.

### High-Yield Problems & Modern Caveats

| Problem Name | Target Companies | Core Pattern / Algorithmic Trick | Modern Interview Caveat & Follow-Up |
| --- | --- | --- | --- |
| **Lowest Common Ancestor in Binary Tree** | Amazon, Swiggy, Fractal | Post-order traversal: if left and right return non-null, root is LCA. | *Follow-up:* What if nodes $P$ or $Q$ are not guaranteed to exist in the tree? What if each node has a parent pointer? |
| **Binary Tree Maximum Path Sum** | Amazon, Swiggy | Global max update with `left_gain + right_gain + node.val`; return `node.val + max(left_gain, right_gain)` upward. | *Follow-up:* What if all node values are negative? Ensure the algorithm does not initialize the global maximum to `0`. |
| **Serialize and Deserialize Binary Tree** | Amazon, Urban Company | Pre-order traversal with `#` null markers or Level-order BFS with delimiter separation. | *Follow-up:* Minimize payload size for network transmission: replace text serialization with bit packing or parent-index array representations. |
| **Validate Binary Search Tree** | Amazon, INDmoney | Pass down strict dynamic bounds `(min_val, max_val)` or ensure strict monotonicity during in-order traversal. | *Follow-up:* Beware of `Integer.MIN_VALUE` and `Integer.MAX_VALUE` bounds checks. Use 64-bit bounds or `Optional` types. |
| **Construct Tree from Preorder and Inorder Traversal** | Amazon, Fractal | Preorder root index drives root creation; hash map lookups on Inorder split left and right subtree spans. | *Follow-up:* What if the tree contains duplicate values? (Unique reconstruction becomes mathematically impossible without structural markers). |
| **Vertical Order Traversal / Top View** | Swiggy, Amazon | BFS with `(node, column, row)` coordinates; sort column buckets by row, then value. | *Follow-up:* Why does simple DFS fail on vertical order unless values are sorted by both row coordinates and insertion sequences? |

---

## 7. Heaps & Priority Queues

### Core Algorithmic Techniques

* **Top-K Tracking:** Min-Heap of size $K$ for largest items; Max-Heap of size $K$ for smallest items.
* **Dual-Heap Pattern:** Balancing two heaps (Max-Heap on lower half, Min-Heap on upper half) to maintain continuous medians.
* **$K$-Way Merge:** Min-Heap storing `(val, array_index, element_index)` to merge sorted streams.

### High-Yield Problems & Modern Caveats

| Problem Name | Target Companies | Core Pattern / Algorithmic Trick | Modern Interview Caveat & Follow-Up |
| --- | --- | --- | --- |
| **Find Median from Data Stream** | Amazon, Swiggy, Urban Company | Max-Heap for lower numbers, Min-Heap for higher numbers. Balance sizes so $\vert{}S_{\text{max}} - S_{\text{min}}\vert{} \le 1$. | *Follow-up:* What if 99% of values are within the range $[0, 100]$? (Optimize to $O(1)$ time using Bucket Counting arrays). |
| **Merge k Sorted Lists** | Amazon, Swiggy | Min-Heap initialized with head nodes of all $K$ lists; push next node on pop. $O(N \log K)$ time. | *Follow-up:* Compare Heap approach against Divide-and-Conquer merge sort ($O(N \log K)$ time, $O(1)$ space without heap overhead). |
| **Top K Frequent Elements** | Amazon, Fractal, INDmoney | Min-heap of size $K$ or $O(N)$ Bucket Sort by frequencies. | *Follow-up:* What if inputs are an unbounded stream and you need the top $K$ frequent elements across the last 24 hours? (Count-Min Sketch + Min-Heap). |
| **Task Scheduler** | Amazon, Swiggy | Greedy frequency calculation: $((\text{max\_freq} - 1) \times (n + 1)) + \text{count\_of\_max\_freq}$. | *Follow-up:* What if tasks have distinct execution durations instead of uniform unit times? (Becomes an NP-hard scheduling problem). |

---

## 8. Graphs: Traversal, Shortest Path & Connectivity

### Core Algorithmic Techniques

* **Topological Sort:** Kahn’s Algorithm (In-degree array + BFS) and DFS with 3-state tracking (`unvisited`, `visiting`, `visited`) for cycle detection in DAGs.
* **Shortest Path:**
* BFS for unweighted graphs.
* Dijkstra’s Algorithm ($O((V + E) \log V)$) using a priority queue for non-negative weighted graphs.
* Bellman-Ford ($O(V \cdot E)$) for handling negative edge weights.


* **Disjoint Set Union (DSU / Union-Find):** Path compression and union by rank/size for dynamic connectivity and Kruskal's MST.

### High-Yield Problems & Modern Caveats

| Problem Name | Target Companies | Core Pattern / Algorithmic Trick | Modern Interview Caveat & Follow-Up |
| --- | --- | --- | --- |
| **Course Schedule I & II** | Amazon, Swiggy, Fractal | Topological Sort via Kahn's algorithm; detect cycles if resolved node count $< V$. | *Follow-up:* What if there are multiple valid paths and the interviewer demands the lexicographically smallest ordering? (Use a Min-Heap instead of a Queue). |
| **Word Ladder (I & II)** | Amazon, Swiggy | Shortest path on unweighted graph: Bidirectional BFS to reduce search branching factor from $b^d$ to $2 \cdot b^{d/2}$. | *Follow-up:* In Word Ladder II (reconstructing paths), how do you avoid Out-Of-Memory errors on large dictionaries? (Run BFS for level distances, then DFS backwards). |
| **Number of Connected Components / Provinces** | Amazon, INDmoney | Disjoint Set Union (DSU) with path compression and union by rank. | *Follow-up:* Can you support dynamic edge deletions in sub-linear time? (Discuss Offline Dynamic Connectivity / Link-Cut Trees). |
| **Cheapest Flights Within K Stops** | Amazon, Swiggy | Modified Bellman-Ford or Dijkstra with state `(cost, node, stops_remaining)`. | *Follow-up:* Why does standard Dijkstra fail without tracking stops? (A cheaper path might consume more stops and block the valid path later). |
| **Critical Connections in a Network** | Amazon | Tarjan’s Algorithm for Bridges: DFS discovery times and `low` link values; bridge if `low[neighbor] > disc[node]`. | *Follow-up:* Explain how this identifies Single Points of Failure in a microservice mesh topology. |
| **Alien Dictionary** | Amazon, Swiggy, Urban Company | Compare adjacent lexicographical strings, build directed graph dependencies, run Topological Sort. | *Follow-up:* Explicitly handle prefix invalidation edge cases (e.g., `"apple"` appearing before `"app"` makes the dictionary strictly invalid). |

---

## 9. Dynamic Programming

### Core Algorithmic Techniques

* **State Identification & Space Optimization:** Transition from 2D matrices $O(N \times M)$ down to two 1D rows $O(M)$ or a single 1D array.
* **Subsequence vs. Substring Formulations:** Matching, alignment, and edit transitions.
* **Knapsack Patterns:** 0/1 Knapsack (reverse iteration for 1D arrays) vs. Unbounded Knapsack (forward iteration).
* **Partition / Interval DP:** Looping through subproblem lengths and choosing split points $k$.

### High-Yield Problems & Modern Caveats

| Problem Name | Target Companies | Core Pattern / Algorithmic Trick | Modern Interview Caveat & Follow-Up |
| --- | --- | --- | --- |
| **Longest Increasing Subsequence (LIS)** | Amazon, Swiggy, Fractal | Binary search approach (`tails` array + `lower_bound`) in $O(N \log N)$ time. | *Follow-up:* Print the actual lexicographically first subsequence in $O(N \log N)$ time (requires tracking parent pointers at insertion indices). |
| **Coin Change & Coin Change II** | Swiggy, INDmoney, Urban Company | Unbounded Knapsack: 1D array updated forward. Part I minimizes counts; Part II sums combinations. | *Follow-up:* What if you must find permutations instead of combinations? (Swap the outer and inner loops: loop over amounts outside, coins inside). |
| **Edit Distance** | Amazon, Fractal | 2D DP comparing character equality: match takes diagonal; mismatch takes $1 + \min(\text{insert}, \text{delete}, \text{replace})$. | *Follow-up:* What if different operations have asymmetric costs ($C_{\text{ins}} \neq C_{\text{del}} \neq C_{\text{rep}}$)? |
| **Maximum Profit in Job Scheduling** | Swiggy, Amazon | Sort jobs by end time. DP with binary search on the latest non-conflicting job end time in $O(N \log N)$. | *Follow-up:* How to reconstruct and return the exact set of selected jobs without increasing complexity? |
| **Word Break (I & II)** | Amazon, Swiggy | 1D DP checking dictionary lookups for suffixes; Part II requires DFS + memoization to generate sentences. | *Follow-up:* Optimize dictionary queries using a Trie instead of Hash Set lookups to prune early on dead prefixes. |
| **Burst Balloons** | Amazon | Interval DP: identify the *last* balloon to burst within range $[i, j]$ to decouple subproblems cleanly. | *Follow-up:* Explain why thinking of the *first* balloon to burst fails to produce independent subproblems. |

---

## 10. Backtracking & Combinatorics

### Core Algorithmic Techniques

* **Pruning & Branch Bounding:** Cutting recursive trees early via feasibility checks.
* **State Restoral:** Mutating state prior to recursive call and resetting it immediately after.
* **Combinatorial Duplication Handling:** Sorting input first and skipping siblings with `if (i > start && nums[i] == nums[i-1]) continue;`.

### High-Yield Problems & Modern Caveats

| Problem Name | Target Companies | Core Pattern / Algorithmic Trick | Modern Interview Caveat & Follow-Up |
| --- | --- | --- | --- |
| **N-Queens** | Amazon, Fractal | Place queens row by row. Track occupied columns, left diagonals, and right diagonals using hash sets or bitmasks. | *Follow-up:* Optimize diagonal collision lookups to $O(1)$ using bit manipulation masks. |
| **Word Search (I & II)** | Amazon, Swiggy, Urban Company | Grid DFS backtracking. In Part II, combine grid DFS with a Prefix Trie to search all words simultaneously. | *Follow-up:* In Word Search II, remove leaf words from the Trie dynamically upon discovery to prevent redundant explorations. |
| **Combination Sum (I, II, & III)** | Amazon, INDmoney | Backtracking with reusable vs non-reusable elements; prune branches where running sum exceeds target. | *Follow-up:* Analyze exact space complexity of the recursion stack vs. heap allocation for returned combinations. |
| **Sudoku Solver** | Amazon, Swiggy | Constraint satisfaction DFS; track valid numbers across rows, columns, and $3 \times 3$ sub-boxes. | *Follow-up:* What heuristic accelerates search? (Most Constrained Variable: fill cells with the fewest candidate choices first). |

---

## 11. Tries & Advanced String Algorithms

### Core Algorithmic Techniques

* **Prefix Trees (Trie):** Array or Hash Map-based node transitions for prefix matching.
* **Bitwise / XOR Trie:** Storing binary representations of integers to maximize/minimize bitwise XOR in $O(32)$ or $O(64)$ per query.
* **Rolling Hashes (Rabin-Karp):** String pattern matching in linear time using polynomial hashing and modulo arithmetic.

### High-Yield Problems & Modern Caveats

| Problem Name | Target Companies | Core Pattern / Algorithmic Trick | Modern Interview Caveat & Follow-Up |
| --- | --- | --- | --- |
| **Implement Trie (Prefix Tree)** | Amazon, Swiggy | Node with child pointers array of size 26 and a boolean `is_terminal_word`. | *Follow-up:* What if keys are Unicode instead of English lowercase? (Switch from array `[26]` to a Hash Map or Ternary Search Tree to avoid memory explosion). |
| **Maximum XOR of Two Numbers in an Array** | Swiggy, Amazon | Bitwise Trie: insert 32-bit binary representations; query by greedily taking the opposite bit branch if present. | *Follow-up:* Scale to range queries: find the maximum XOR of a given value $X$ with any element in the array with value $\le M$ (Sort queries + offline Trie insertion). |
| **Design Add and Search Words Data Structure** | Amazon, Fractal | Trie traversal; handle `.` wildcards by recursively checking all 26 existing child branches. | *Follow-up:* How do you prevent worst-case exponential time $O(26^M)$ on consecutive wildcards `.....`? |

---

## 12. Bit Manipulation & Math

### Core Algorithmic Techniques

* **Bitwise Arithmetic Invariants:**
* Clear lowest set bit: `n & (n - 1)`.
* Isolate lowest set bit: `n & (-n)`.
* XOR cancellation: $a \oplus a = 0$ and $a \oplus 0 = a$.


* **Fast Modular Exponentiation:** Multiplying base squares in $O(\log N)$ with continuous modulo reduction.
* **Reservoir Sampling:** Selecting $K$ items uniformly at random from an unknown/infinite stream.

### High-Yield Problems & Modern Caveats

| Problem Name | Target Companies | Core Pattern / Algorithmic Trick | Modern Interview Caveat & Follow-Up |
| --- | --- | --- | --- |
| **Single Number (I, II, & III)** | Swiggy, Amazon, Fractal | Part I: cumulative XOR. Part II: bitwise mod-3 counting. Part III: XOR partition via lowest set bit. | *Follow-up:* For Part II, generalize to finding an element appearing once while all others appear $K$ times using bitwise state counters. |
| **Pow(x, n)** | Amazon, INDmoney | Binary exponentiation in $O(\log N)$; handle negative powers and edge cases where $n = -2^{31}$. | *Follow-up:* Why does `-n` overflow a 32-bit signed integer when $n = -2^{31}$? (Must promote to a 64-bit integer before inverting sign). |
| **Random Pick Index (Reservoir Sampling)** | Amazon, Swiggy | For the $i$-th matching element, choose it with probability $1/i$ to guarantee uniform distribution over streams. | *Follow-up:* Prove by mathematical induction that every element in an infinite stream has an exact equal probability $1/N$ of being chosen. |

---

## 13. System Constraints & Real-World Follow-Ups

In 24+ LPA interviews, interviewers frequently modify clean algorithmic setups with real-world infrastructure constraints:

### "What if the data cannot fit into RAM?" (External Memory Algorithms)

* **Array Sorting:** Replace QuickSort with **2-Way External Merge Sort**. Read chunks into RAM, sort internally, flush to scratch disks as sorted runs, and merge using a Min-Heap.
* **Duplicate Detection:** Use a **Bloom Filter** for probabilistic checking with zero false negatives, backed by a persistent key-value store for true confirmations.
* **Frequency Counting:** Use a **Count-Min Sketch** to track streaming frequencies approximately using sub-linear space.

### "What if this runs in a high-concurrency production service?"

* **Thread-Safe Caches:** A global lock (`Mutex`) turns your service into a single-threaded bottleneck. Use **Lock Striping** (e.g., splitting a cache into 16 or 32 independent shards based on hash value) or read-write locks (`RWMutex`) to allow unlimited concurrent readers.
* **Data Structure Immutability:** Utilize persistent data structures or Copy-On-Write (COW) paradigms so background workers can read historical snapshots without taking locks.

### "What if the numbers exceed standard data types?"

* **Modulo Arithmetic Rules:** Apply modulo at every addition and multiplication stage: $(A \times B) \pmod M = ((A \pmod M) \times (B \pmod M)) \pmod M$.
* **BigInteger Implementations:** Represent large values as arrays of base-$10^9$ chunks and implement grade-school multiplication with carry propagation.
