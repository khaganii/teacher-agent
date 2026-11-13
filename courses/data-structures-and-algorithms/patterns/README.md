# Pattern kitabxanası

Pattern mövzu deyil — mövzunun tətbiq formasıdır. Ayrıca həftə tutmur.

## Necə verilir

- Məşğələnin **son 20 dəqiqəsi**: adı, şablon kod, eyni pattern-in iki fərqli görünüşü
- Həmin həftənin ev tapşırığı **qarışıq deyil** — hamısı eyni pattern-dən
- Tələbənin repo-sunda `patterns/` qovluğu yığılır: nə vaxt tanınır / şablon / mürəkkəblik
- **9-cu həftədən sonra** hər ev tapşırığına 1 "qarışıq" məsələ — pattern-i özləri tapsın

## Əsas dəst (həftədə bir)

| Həftə | Pattern | Nümunə məsələ |
|---|---|---|
| 2 | — (brute force, dövr + şərt) | FizzBuzz, Palindrome Number |
| 3 | **Two pointers** | Valid Palindrome, Reverse String, Two Sum II, Move Zeroes |
| 4 | **Frequency / counting array** | Majority Element, Contains Duplicate, Single Number |
| 5 | **Divide & conquer** | Merge Sorted Array, Sort an Array, Sort Colors |
| 6 | **Binary search şablonu** | Binary Search, Search Insert Position, First Bad Version, Sqrt(x) |
| 7 | **Fast & slow pointers** + stack balansı | Linked List Cycle, Middle of the Linked List, Valid Parentheses |
| 9 | **Tree DFS (rekursiv)** | Maximum Depth, Same Tree, Invert Binary Tree |
| 10 | **Frequency map / Top-K** | Two Sum, Valid Anagram, Kth Largest Element, Last Stone Weight |
| 11 | **Sortla, bir keçiddə seç** | Assign Cookies, Merge Intervals, Non-overlapping Intervals |
| 12 | **1D DP** | Climbing Stairs, Fibonacci, House Robber, Min Cost Climbing Stairs |
| 13 | **Grid DP** | Unique Paths, Minimum Path Sum, Maximum Subarray |
| 14 | **Grid DFS / flood fill** | Number of Islands, Flood Fill, Max Area of Island |

## İkinci mərtəbə — yalnız qrup rahat gedirsə

| Pattern | Hansı həftəyə |
|---|---|
| Sliding window (sabit və dəyişən ölçü) | 6 |
| Monotonic stack | 7 |
| Tree BFS / level order | 9 |
| Prefix sum + hashmap | 10 |
| Two heaps (median) | 10 |
| Backtracking (subsets, permutations) | 5 |
| 0/1 knapsack | 13 |
| BFS shortest path | 14 |
| Union-Find | 14 |
| Cyclic sort | 3 |
| Circular array (dövrü indeks, `% capacity`) | 7-8 (Queue) |

## Planda olmayanlar

Trie · String hashing / Rabin-Karp · KMP / Z-function · Meet in the middle ·
Segment tree · Bitmask DP · Interval DP · MST

Week 15 rezervində, vaxt qalsa. Və ya güclü tələbə üçün əlavə material.
