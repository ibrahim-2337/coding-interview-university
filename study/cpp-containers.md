# C++ Containers Cheat Sheet

One table per container: how to make it, add, find, read, remove, and loop. Every call here was compiled and tested with `g++ -std=c++17`.

Setup for all of them: `#include <bits/stdc++.h>` and `using namespace std;`

## Which one do I want?

| I need... | Use |
|---|---|
| a list I index by position | `vector` |
| key -> value lookup (counts, indexes) | `unordered_map` |
| key -> value, keys kept sorted | `map` |
| "have I seen this?" | `unordered_set` |
| unique values kept sorted, or smallest/largest | `set` |
| sorted values with duplicates, take min and max | `multiset` |
| last in, first out (brackets, undo) | `stack` |
| first in, first out (lines, simulations) | `queue` |
| add/remove at both ends | `deque` |
| always grab the biggest (or smallest) next | `priority_queue` |

## vector

| Do | Code | Cost |
|---|---|---|
| make | `vector<int> v;` / `vector<int> v(n, 0);` / `vector<int> v = {1, 2, 3};` | |
| add at end | `v.push_back(x);` | O(1) amortized |
| insert at i | `v.insert(v.begin() + i, x);` | O(n) |
| read / write | `v[i]`, `v.front()`, `v.back()` | O(1) |
| remove end | `v.pop_back();` | O(1) |
| remove at i | `v.erase(v.begin() + i);` | O(n) |
| contains? | `find(v.begin(), v.end(), x) != v.end()` | O(n) |
| count x | `count(v.begin(), v.end(), x)` | O(n) |
| size / empty | `v.size()` / `v.empty()` | O(1) |
| sort up / down | `sort(v.begin(), v.end());` / `sort(v.rbegin(), v.rend());` | O(n log n) |
| reverse | `reverse(v.begin(), v.end());` | O(n) |
| min / max | `*min_element(v.begin(), v.end())` / `*max_element(...)` | O(n) |
| sum | `accumulate(v.begin(), v.end(), 0)` (use `0LL` for big sums) | O(n) |
| empty it | `v.clear();` | O(n) |
| loop | `for (int x : v)` / `for (auto& x : v)` to modify | |

## string

| Do | Code | Cost |
|---|---|---|
| add | `s += 'c';` / `s += "abc";` / `s.push_back('c');` | O(1) amortized per char |
| remove last | `s.pop_back();` | O(1) |
| read char | `s[i]` (a `char`) | O(1) |
| length | `s.size()` | O(1) |
| substring | `s.substr(start, length)` (length, not end index) | O(length) |
| find | `s.find("ab")` returns index, or `string::npos` if missing | O(n·m) |
| insert / erase | `s.insert(pos, "ab");` / `s.erase(pos, len);` | O(n) |
| number <-> text | `to_string(42)`, `stoi("123")`, `stoll("9000000000")` | |
| compare | `a == b`, `a < b` (alphabetical) | O(n) |
| split by spaces | `stringstream ss(s); string w; while (ss >> w) { ... }` | O(n) |
| char tests | `isalpha(c)`, `isdigit(c)`, `tolower(c)`, `toupper(c)`, `c - 'a'`, `c - '0'` | O(1) |

## unordered_map (hash map)

| Do | Code | Cost |
|---|---|---|
| make | `unordered_map<string, int> m;` | |
| set / overwrite | `m[k] = v;` | O(1) avg |
| count up | `m[k]++;` (missing key starts at 0) | O(1) avg |
| add only if missing | `m.insert({k, v});` (does NOT overwrite) | O(1) avg |
| contains? | `m.count(k)` (0 or 1) or `m.find(k) != m.end()` | O(1) avg |
| read safely | `auto it = m.find(k); if (it != m.end()) use it->second;` | O(1) avg |
| read | `m[k]` (CREATES the key if missing) / `m.at(k)` (crashes if missing) | O(1) avg |
| remove | `m.erase(k);` | O(1) avg |
| size | `m.size()` | O(1) |
| loop | `for (auto& [key, val] : m)` (no order) | O(n) |

## map (sorted by key)

Same calls as `unordered_map`, but O(log n) each, and loops go in key order. Extra:

| Do | Code |
|---|---|
| smallest key | `m.begin()->first` |
| largest key | `m.rbegin()->first` |
| first key >= k | `m.lower_bound(k)->first` (check `!= m.end()` first) |
| first key > k | `m.upper_bound(k)->first` |

## unordered_set / set

| Do | Code | Cost (unordered / set) |
|---|---|---|
| make | `unordered_set<int> s;` / `set<int> s = {5, 1, 3};` | |
| add | `s.insert(x);` (duplicates ignored) | O(1) avg / O(log n) |
| contains? | `s.count(x)` | O(1) avg / O(log n) |
| remove | `s.erase(x);` | O(1) avg / O(log n) |
| size | `s.size()` | O(1) |
| smallest / largest (set only) | `*s.begin()` / `*s.rbegin()` | O(1) |
| first >= x (set only) | `*s.lower_bound(x)` (check `!= s.end()` first) | O(log n) |

## multiset (sorted, keeps duplicates)

| Do | Code | Cost |
|---|---|---|
| add | `ms.insert(x);` | O(log n) |
| how many x | `ms.count(x)` | O(log n + count) |
| remove ONE copy of x | `ms.erase(ms.find(x));` (check `find` isn't `end()` first) | O(log n) |
| remove ALL copies of x | `ms.erase(x);` (trap: easy to do by accident) | O(log n + count) |
| smallest / largest | `*ms.begin()` / `*ms.rbegin()` | O(1) |
| remove smallest | `ms.erase(ms.begin());` | O(1) amortized |
| remove largest | `ms.erase(prev(ms.end()));` | O(1) amortized |

## stack, queue, deque

| Do | stack | queue | deque |
|---|---|---|---|
| make | `stack<int> st;` | `queue<int> q;` | `deque<int> dq;` |
| add | `st.push(x);` | `q.push(x);` (back) | `dq.push_back(x);` / `dq.push_front(x);` |
| look | `st.top()` | `q.front()` / `q.back()` | `dq.front()` / `dq.back()` / `dq[i]` |
| remove | `st.pop();` | `q.pop();` (front) | `dq.pop_back();` / `dq.pop_front();` |
| empty / size | `st.empty()` / `st.size()` | `q.empty()` / `q.size()` | `dq.empty()` / `dq.size()` |

All operations are O(1). `pop()` returns nothing: read `top()` or `front()` first, then pop. Check `empty()` before reading or popping.

## priority_queue (heap)

| Do | Code | Cost |
|---|---|---|
| max-heap (biggest on top) | `priority_queue<int> pq;` | |
| min-heap (smallest on top) | `priority_queue<int, vector<int>, greater<int>> pq;` | |
| add | `pq.push(x);` | O(log n) |
| look at top | `pq.top()` | O(1) |
| remove top | `pq.pop();` | O(log n) |
| empty / size | `pq.empty()` / `pq.size()` | O(1) |

Pairs work too: `priority_queue<pair<int, int>>` orders by `.first`, then `.second`.

## pair

| Do | Code |
|---|---|
| make | `pair<int, string> p = {1, "x"};` |
| read | `p.first`, `p.second` |
| sort a vector of pairs | `sort(vp.begin(), vp.end());` (by first, then second) |

## Traps

- `m[k]` inserts `k` when it's missing. Use `count` or `find` to check without inserting.
- `ms.erase(x)` removes every copy. Use `ms.erase(ms.find(x))` for one.
- `pop()` on stack, queue and priority_queue returns nothing.
- Reading `top()`, `front()` or `*begin()` on an empty container crashes or returns garbage.
- `size()` is unsigned: `v.size() - 1` on an empty vector is a huge number.
- `unordered_*` have no order. Use `map` or `set` when you need sorted output.
