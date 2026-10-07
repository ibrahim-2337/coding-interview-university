# Study Progress

53 subtopics in 17 topics, 265 problems. No Hards yet. Problems come from NeetCode 250 / LeetCode; numbers were written from memory and are verified by web search when each subtopic is started (see PROTOCOL.md, step 0). Until then, if a number and title disagree, trust the title.

**Legend:** Status is one of `Not started`, `In progress`, `Completed`. (E) = Easy, (M) = Medium. Process: see [PROTOCOL.md](PROTOCOL.md).

**Current subtopic:** 1.1

---

## 1. Arrays, Strings & Hashing

README section: Data Structures > Arrays, Hash table

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 1.1 Array basics

**Status:** In progress

Problems verified by search: yes

- [x] 1480. Running Sum of 1d Array (E)
- [x] 1672. Richest Customer Wealth (E)
- [x] 485. Max Consecutive Ones (E)
- [x] 1295. Find Numbers with Even Number of Digits (E)
- [x] 414. Third Maximum Number (E)

Extra problems (added at the student's request; the first extra lists were scrapped, none were attempted):

- [ ] 1470. Shuffle the Array (E)
- [ ] 1431. Kids With the Greatest Number of Candies (E)
- [ ] 896. Monotonic Array (E)
- [ ] 1389. Create Target Array in the Given Order (E)
- [ ] 2149. Rearrange Array Elements by Sign (M)
- [ ] 2161. Partition Array According to Given Pivot (M)
- [ ] 665. Non-decreasing Array (M)
- [ ] 1535. Find the Winner of an Array Game (M, difficulty not confirmed by search)

- [ ] Verbal quiz done
- Weak spots: cost of inserting at the front of an array (said O(1); it is O(n) because every element shifts). Dynamic-array resizing: right idea (occasional O(n) copy to a bigger array), but thinks of growth as jumping between bit-width sizes (2^32 -> 2^64); in reality capacity starts small and doubles (16, 32, 64...), which is why append is amortized O(1). Quiz problems 4-5 (second smallest distinct; row with most 1s) skipped at student's request.

### 1.2 In-place array operations

**Status:** Not started

Problems verified by search: yes

- [ ] 26. Remove Duplicates from Sorted Array (E)
- [ ] 27. Remove Element (E)
- [ ] 283. Move Zeroes (E)
- [ ] 88. Merge Sorted Array (E)
- [ ] 189. Rotate Array (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 1.3 String basics

**Status:** Not started

- [ ] 709. To Lower Case (E)
- [ ] 58. Length of Last Word (E)
- [ ] 28. Find the Index of the First Occurrence in a String (E)
- [ ] 459. Repeated Substring Pattern (E)
- [ ] 520. Detect Capital (E)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 1.4 String parsing & conversion

**Status:** Not started

- [ ] 929. Unique Email Addresses (E)
- [ ] 165. Compare Version Numbers (M)
- [ ] 8. String to Integer (atoi) (M)
- [ ] 38. Count and Say (M)
- [ ] 6. Zigzag Conversion (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 1.5 Duplicates & membership

**Status:** Not started

- [ ] 217. Contains Duplicate (E)
- [ ] 242. Valid Anagram (E)
- [ ] 1. Two Sum (E)
- [ ] 349. Intersection of Two Arrays (E)
- [ ] 202. Happy Number (E)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 1.6 Frequency counting

**Status:** Not started

- [ ] 387. First Unique Character in a String (E)
- [ ] 383. Ransom Note (E)
- [ ] 169. Majority Element (E)
- [ ] 347. Top K Frequent Elements (M)
- [ ] 49. Group Anagrams (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 1.7 Prefix sums & subarrays

**Status:** Not started

- [ ] 303. Range Sum Query - Immutable (E)
- [ ] 724. Find Pivot Index (E)
- [ ] 238. Product of Array Except Self (M)
- [ ] 560. Subarray Sum Equals K (M)
- [ ] 128. Longest Consecutive Sequence (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 1.8 Matrices

**Status:** Not started

- [ ] 463. Island Perimeter (E)
- [ ] 36. Valid Sudoku (M)
- [ ] 73. Set Matrix Zeroes (M)
- [ ] 48. Rotate Image (M)
- [ ] 54. Spiral Matrix (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 2. Two Pointers

README section: More Knowledge (general technique)

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 2.1 Opposite-end pointers

**Status:** Not started

- [ ] 125. Valid Palindrome (E)
- [ ] 344. Reverse String (E)
- [ ] 977. Squares of a Sorted Array (E)
- [ ] 680. Valid Palindrome II (E)
- [ ] 167. Two Sum II - Input Array Is Sorted (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 2.2 Sorted arrays & n-sum

**Status:** Not started

- [ ] 15. 3Sum (M)
- [ ] 16. 3Sum Closest (M)
- [ ] 11. Container With Most Water (M)
- [ ] 611. Valid Triangle Number (M)
- [ ] 1679. Max Number of K-Sum Pairs (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 3. Stack & Queue

README section: Data Structures > Stack, Queue

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 3.1 Stack & queue basics

**Status:** Not started

- [ ] 20. Valid Parentheses (E)
- [ ] 232. Implement Queue using Stacks (E)
- [ ] 225. Implement Stack using Queues (E)
- [ ] 844. Backspace String Compare (E)
- [ ] 155. Min Stack (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 3.2 Expression evaluation

**Status:** Not started

- [ ] 1047. Remove All Adjacent Duplicates In String (E)
- [ ] 150. Evaluate Reverse Polish Notation (M)
- [ ] 71. Simplify Path (M)
- [ ] 394. Decode String (M)
- [ ] 227. Basic Calculator II (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 3.3 Monotonic stack

**Status:** Not started

- [ ] 496. Next Greater Element I (E)
- [ ] 739. Daily Temperatures (M)
- [ ] 503. Next Greater Element II (M)
- [ ] 901. Online Stock Span (M)
- [ ] 853. Car Fleet (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 4. Linked List

README section: Data Structures > Linked Lists

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 4.1 List basics

**Status:** Not started

- [ ] 206. Reverse Linked List (E)
- [ ] 21. Merge Two Sorted Lists (E)
- [ ] 83. Remove Duplicates from Sorted List (E)
- [ ] 203. Remove Linked List Elements (E)
- [ ] 876. Middle of the Linked List (E)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 4.2 Fast & slow pointers

**Status:** Not started

- [ ] 141. Linked List Cycle (E)
- [ ] 234. Palindrome Linked List (E)
- [ ] 160. Intersection of Two Linked Lists (E)
- [ ] 142. Linked List Cycle II (M)
- [ ] 287. Find the Duplicate Number (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 4.3 Pointer manipulation

**Status:** Not started

- [ ] 19. Remove Nth Node From End of List (M)
- [ ] 24. Swap Nodes in Pairs (M)
- [ ] 2. Add Two Numbers (M)
- [ ] 143. Reorder List (M)
- [ ] 138. Copy List with Random Pointer (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 4.4 Design data structures

**Status:** Not started

- [ ] 705. Design HashSet (E)
- [ ] 706. Design HashMap (E)
- [ ] 707. Design Linked List (M)
- [ ] 622. Design Circular Queue (M)
- [ ] 146. LRU Cache (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 5. Binary Search

README section: More Knowledge > Binary search

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 5.1 Classic binary search

**Status:** Not started

- [ ] 704. Binary Search (E)
- [ ] 35. Search Insert Position (E)
- [ ] 69. Sqrt(x) (E)
- [ ] 278. First Bad Version (E)
- [ ] 744. Find Smallest Letter Greater Than Target (E)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 5.2 Rotated arrays, 2D & peaks

**Status:** Not started

- [ ] 74. Search a 2D Matrix (M)
- [ ] 34. Find First and Last Position of Element in Sorted Array (M)
- [ ] 153. Find Minimum in Rotated Sorted Array (M)
- [ ] 33. Search in Rotated Sorted Array (M)
- [ ] 162. Find Peak Element (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 5.3 Binary search on the answer

**Status:** Not started

- [ ] 875. Koko Eating Bananas (M)
- [ ] 1011. Capacity To Ship Packages Within D Days (M)
- [ ] 1283. Find the Smallest Divisor Given a Threshold (M)
- [ ] 981. Time Based Key-Value Store (M)
- [ ] 540. Single Element in a Sorted Array (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 6. Bit Manipulation & Math

README section: More Knowledge > Bitwise operations

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 6.1 Bit basics

**Status:** Not started

- [ ] 136. Single Number (E)
- [ ] 191. Number of 1 Bits (E)
- [ ] 338. Counting Bits (E)
- [ ] 190. Reverse Bits (E)
- [ ] 268. Missing Number (E)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 6.2 Bit tricks

**Status:** Not started

- [ ] 231. Power of Two (E)
- [ ] 371. Sum of Two Integers (M)
- [ ] 137. Single Number II (M)
- [ ] 260. Single Number III (M)
- [ ] 201. Bitwise AND of Numbers Range (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 6.3 Math

**Status:** Not started

- [ ] 66. Plus One (E)
- [ ] 9. Palindrome Number (E)
- [ ] 13. Roman to Integer (E)
- [ ] 204. Count Primes (M)
- [ ] 50. Pow(x, n) (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 7. Sorting

README section: Sorting

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 7.1 Sorting applications

**Status:** Not started

- [ ] 1122. Relative Sort Array (E)
- [ ] 976. Largest Perimeter Triangle (E)
- [ ] 179. Largest Number (M)
- [ ] 75. Sort Colors (M)
- [ ] 912. Sort an Array (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 8. Sliding Window

README section: More Knowledge (general technique)

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 8.1 Fixed-size window

**Status:** Not started

- [ ] 643. Maximum Average Subarray I (E)
- [ ] 1343. Number of Sub-arrays of Size K and Average Greater than or Equal to Threshold (M)
- [ ] 1456. Maximum Number of Vowels in a Substring of Given Length (M)
- [ ] 567. Permutation in String (M)
- [ ] 438. Find All Anagrams in a String (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 8.2 Variable-size window

**Status:** Not started

- [ ] 121. Best Time to Buy and Sell Stock (E)
- [ ] 3. Longest Substring Without Repeating Characters (M)
- [ ] 209. Minimum Size Subarray Sum (M)
- [ ] 1004. Max Consecutive Ones III (M)
- [ ] 424. Longest Repeating Character Replacement (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 9. Trees

README section: Trees

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 9.1 Traversals & depth

**Status:** Not started

- [ ] 94. Binary Tree Inorder Traversal (E)
- [ ] 144. Binary Tree Preorder Traversal (E)
- [ ] 145. Binary Tree Postorder Traversal (E)
- [ ] 104. Maximum Depth of Binary Tree (E)
- [ ] 226. Invert Binary Tree (E)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 9.2 Recursion on trees

**Status:** Not started

- [ ] 100. Same Tree (E)
- [ ] 101. Symmetric Tree (E)
- [ ] 572. Subtree of Another Tree (E)
- [ ] 110. Balanced Binary Tree (E)
- [ ] 543. Diameter of Binary Tree (E)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 9.3 Level-order (BFS)

**Status:** Not started

- [ ] 637. Average of Levels in Binary Tree (E)
- [ ] 102. Binary Tree Level Order Traversal (M)
- [ ] 199. Binary Tree Right Side View (M)
- [ ] 103. Binary Tree Zigzag Level Order Traversal (M)
- [ ] 513. Find Bottom Left Tree Value (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 9.4 Binary search trees

**Status:** Not started

- [ ] 700. Search in a Binary Search Tree (E)
- [ ] 98. Validate Binary Search Tree (M)
- [ ] 230. Kth Smallest Element in a BST (M)
- [ ] 235. Lowest Common Ancestor of a Binary Search Tree (M)
- [ ] 701. Insert into a Binary Search Tree (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 9.5 Paths, ancestors & construction

**Status:** Not started

- [ ] 112. Path Sum (E)
- [ ] 1448. Count Good Nodes in Binary Tree (M)
- [ ] 236. Lowest Common Ancestor of a Binary Tree (M)
- [ ] 437. Path Sum III (M)
- [ ] 105. Construct Binary Tree from Preorder and Inorder Traversal (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 10. Heap / Priority Queue

README section: Trees > Heap / Priority Queue / Binary Heap

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 10.1 Heap basics

**Status:** Not started

- [ ] 703. Kth Largest Element in a Stream (E)
- [ ] 1046. Last Stone Weight (E)
- [ ] 1337. The K Weakest Rows in a Matrix (E)
- [ ] 215. Kth Largest Element in an Array (M)
- [ ] 973. K Closest Points to Origin (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 10.2 Heap applications

**Status:** Not started

- [ ] 451. Sort Characters By Frequency (M)
- [ ] 767. Reorganize String (M)
- [ ] 621. Task Scheduler (M)
- [ ] 378. Kth Smallest Element in a Sorted Matrix (M)
- [ ] 355. Design Twitter (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 11. Intervals

README section: Even More Knowledge (general technique)

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 11.1 Interval problems

**Status:** Not started

- [ ] 228. Summary Ranges (E)
- [ ] 56. Merge Intervals (M)
- [ ] 57. Insert Interval (M)
- [ ] 435. Non-overlapping Intervals (M)
- [ ] 452. Minimum Number of Arrows to Burst Balloons (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 12. Tries

README section: Even More Knowledge > Tries

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 12.1 Trie

**Status:** Not started

- [ ] 14. Longest Common Prefix (E)
- [ ] 208. Implement Trie (Prefix Tree) (M)
- [ ] 648. Replace Words (M)
- [ ] 1268. Search Suggestions System (M)
- [ ] 211. Design Add and Search Words Data Structure (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 13. Backtracking

README section: Even More Knowledge > Recursion

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 13.1 Subsets & combinations

**Status:** Not started

- [ ] 78. Subsets (M)
- [ ] 90. Subsets II (M)
- [ ] 77. Combinations (M)
- [ ] 39. Combination Sum (M)
- [ ] 40. Combination Sum II (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 13.2 Permutations & strings

**Status:** Not started

- [ ] 46. Permutations (M)
- [ ] 47. Permutations II (M)
- [ ] 17. Letter Combinations of a Phone Number (M)
- [ ] 22. Generate Parentheses (M)
- [ ] 131. Palindrome Partitioning (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 13.3 Search & partition

**Status:** Not started

- [ ] 784. Letter Case Permutation (M)
- [ ] 216. Combination Sum III (M)
- [ ] 79. Word Search (M)
- [ ] 93. Restore IP Addresses (M)
- [ ] 473. Matchsticks to Square (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 14. Graphs

README section: Graphs

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 14.1 Graph traversal basics

**Status:** Not started

- [ ] 1971. Find if Path Exists in Graph (E)
- [ ] 997. Find the Town Judge (E)
- [ ] 133. Clone Graph (M)
- [ ] 797. All Paths From Source to Target (M)
- [ ] 841. Keys and Rooms (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 14.2 Grid DFS / BFS

**Status:** Not started

- [ ] 733. Flood Fill (E)
- [ ] 200. Number of Islands (M)
- [ ] 695. Max Area of Island (M)
- [ ] 130. Surrounded Regions (M)
- [ ] 417. Pacific Atlantic Water Flow (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 14.3 BFS shortest path (unweighted)

**Status:** Not started

- [ ] 994. Rotting Oranges (M)
- [ ] 542. 01 Matrix (M)
- [ ] 1091. Shortest Path in Binary Matrix (M)
- [ ] 909. Snakes and Ladders (M)
- [ ] 1926. Nearest Exit from Entrance in Maze (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 14.4 Cycles & topological sort

**Status:** Not started

- [ ] 207. Course Schedule (M)
- [ ] 210. Course Schedule II (M)
- [ ] 802. Find Eventual Safe States (M)
- [ ] 785. Is Graph Bipartite? (M)
- [ ] 310. Minimum Height Trees (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 14.5 Union-Find & components

**Status:** Not started

- [ ] 547. Number of Provinces (M)
- [ ] 684. Redundant Connection (M)
- [ ] 721. Accounts Merge (M)
- [ ] 990. Satisfiability of Equality Equations (M)
- [ ] 1319. Number of Operations to Make Network Connected (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 14.6 Weighted shortest paths

**Status:** Not started

- [ ] 743. Network Delay Time (M)
- [ ] 787. Cheapest Flights Within K Stops (M)
- [ ] 1631. Path With Minimum Effort (M)
- [ ] 1514. Path with Maximum Probability (M)
- [ ] 399. Evaluate Division (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 15. Greedy

README section: Even More Knowledge (general technique)

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 15.1 Greedy basics

**Status:** Not started

- [ ] 455. Assign Cookies (E)
- [ ] 860. Lemonade Change (E)
- [ ] 605. Can Place Flowers (E)
- [ ] 1005. Maximize Sum Of Array After K Negations (E)
- [ ] 561. Array Partition (E)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 15.2 Greedy choices

**Status:** Not started

- [ ] 55. Jump Game (M)
- [ ] 45. Jump Game II (M)
- [ ] 134. Gas Station (M)
- [ ] 846. Hand of Straights (M)
- [ ] 763. Partition Labels (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 16. Dynamic Programming - 1D

README section: Even More Knowledge > Dynamic Programming

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 16.1 Fibonacci-style

**Status:** Not started

- [ ] 70. Climbing Stairs (E)
- [ ] 746. Min Cost Climbing Stairs (E)
- [ ] 509. Fibonacci Number (E)
- [ ] 1137. N-th Tribonacci Number (E)
- [ ] 198. House Robber (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 16.2 Linear DP

**Status:** Not started

- [ ] 53. Maximum Subarray (M)
- [ ] 213. House Robber II (M)
- [ ] 152. Maximum Product Subarray (M)
- [ ] 300. Longest Increasing Subsequence (M)
- [ ] 91. Decode Ways (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 16.3 Knapsack & coin change

**Status:** Not started

- [ ] 322. Coin Change (M)
- [ ] 518. Coin Change II (M)
- [ ] 416. Partition Equal Subset Sum (M)
- [ ] 494. Target Sum (M)
- [ ] 377. Combination Sum IV (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 16.4 String & partition DP

**Status:** Not started

- [ ] 139. Word Break (M)
- [ ] 647. Palindromic Substrings (M)
- [ ] 5. Longest Palindromic Substring (M)
- [ ] 279. Perfect Squares (M)
- [ ] 343. Integer Break (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---

## 17. Dynamic Programming - 2D

README section: Even More Knowledge > Dynamic Programming

**Topic checkpoint** (5 new problems across all subtopics + overall refresher): Not started

Checkpoint problems: _chosen when every subtopic below is Completed_

### 17.1 Grid DP

**Status:** Not started

- [ ] 62. Unique Paths (M)
- [ ] 63. Unique Paths II (M)
- [ ] 64. Minimum Path Sum (M)
- [ ] 120. Triangle (M)
- [ ] 221. Maximal Square (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 17.2 Two-string DP

**Status:** Not started

- [ ] 1143. Longest Common Subsequence (M)
- [ ] 583. Delete Operation for Two Strings (M)
- [ ] 718. Maximum Length of Repeated Subarray (M)
- [ ] 97. Interleaving String (M)
- [ ] 72. Edit Distance (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

### 17.3 State-machine & sequence DP

**Status:** Not started

- [ ] 122. Best Time to Buy and Sell Stock II (M)
- [ ] 309. Best Time to Buy and Sell Stock with Cooldown (M)
- [ ] 714. Best Time to Buy and Sell Stock with Transaction Fee (M)
- [ ] 740. Delete and Earn (M)
- [ ] 1049. Last Stone Weight II (M)

- [ ] Verbal quiz done
- Weak spots: _none logged_

---
