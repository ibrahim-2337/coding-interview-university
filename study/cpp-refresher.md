# C++ Refresher for Problem Solving

Only what interview and exam problems use. Compiled and checked with `g++ -std=c++17 -Wall`.

## Setup

```cpp
#include <bits/stdc++.h>   // everything; if the exam restricts headers, include
using namespace std;       // <vector> <string> <unordered_map> <algorithm> etc. individually
```

## Numbers

```cpp
int a = 7, b = 2;
a / b        // 3  (integer division)
a % b        // 1
(double)a / b // 3.5
long long big = 1LL * INT_MAX * 2;  // use long long when sums/products can exceed ~2e9
INT_MAX, INT_MIN                    // from <climits>
```

## Bit manipulation

You already know binary. Two facts are enough to start:
- Bits are numbered **from the right, starting at 0**. In `1101` (13), bit 0 is the last `1`, bit 1 is `0`, bit 2 is `1`, bit 3 is `1`.
- Bit tricks work on unsigned numbers, so use `uint32_t` (from `<cstdint>`, already in `bits/stdc++.h`) for puzzles. Negative `int`s shift in surprising ways.

### The six operators, with binary examples

```cpp
// a & b   1 only where BOTH have a 1       1100 & 1010 = 1000     (12 & 10 = 8)
// a | b   1 where AT LEAST ONE has a 1     1100 | 1010 = 1110     (12 | 10 = 14)
// a ^ b   1 where they DIFFER (xor)        1100 ^ 1010 = 0110     (12 ^ 10 = 6)
// ~a      flips every bit                  ~0101 = ...1010        (use & 0xF to keep 4 bits: (~5u) & 0xF = 10)
// a << k  slides bits left, fills 0s       0101 << 2 = 10100      (5 << 2 = 20, same as 5 * 4)
// a >> k  slides bits right, drops the     1101 >> 2 = 0011       (13 >> 2 = 3, same as 13 / 4, rounded down)
//         lowest k bits
```

### Reading and changing one bit

A **mask** is a number with only the bit you care about switched on. `1u << i` is the mask for bit i: `1u << 3` is `1000`.

```cpp
(x >> i) & 1         // read bit i: slide it to the end, then keep only the last bit
                     //   x = 1101: i=2 -> (1101 >> 2) & 1 = 11 & 1 = 1;  i=1 -> (110 & 1) = 0
x & 1                // is x odd? (this is bit 0)       13 & 1 = 1, 12 & 1 = 0
x | (1u << i)        // set bit i to 1                  1000 | (1u << 0) = 1000 | 0001 = 1001  (8 -> 9)
x & ~(1u << i)       // clear bit i to 0                1101 & ~(1u << 2) = 1101 & ...1011 = 1001  (13 -> 9)
x ^ (1u << i)        // flip bit i                      1101 ^ (1u << 0) = 1101 ^ 0001 = 1100  (13 -> 12)
```

### Counting and checking

```cpp
__builtin_popcount(x)      // number of 1 bits:  __builtin_popcount(13) = 3   (1101 has three 1s)
                           // for long long use __builtin_popcountll

n & (n - 1)                // clears the LOWEST 1 bit:  12 (1100) & 11 (1011) = 1000  (8)
// so this counts the 1 bits by hand (LeetCode 191), once per 1 bit:
int count = 0;
while (n) { n &= n - 1; count++; }       // 13: 1101 -> 1100 -> 1000 -> 0, count = 3

// or: look at the last bit, then slide it away
while (n) { count += n & 1; n >>= 1; }   // 13: 1 + 0 + 1 + 1 = 3

x > 0 && (x & (x - 1)) == 0   // power of two? it has exactly one 1 bit:  8 (1000) yes, 6 (110) no
```

### Pulling out a chunk

```cpp
x & 0xFF                   // lowest byte (8 bits):         0x12345678 & 0xFF = 0x78
(x >> (8 * k)) & 0xFF      // byte number k, from the right: k=1 -> (0x12345678 >> 8) & 0xFF = 0x56
x & 0xF                    // lowest 4 bits (one hex digit): 0x2B & 0xF = 0xB
```

### Building a number one bit at a time

To append a bit to the end of a number: shift left to open an empty slot, then `|` the bit in.

```cpp
result = (result << 1) | bit;
// append 1, 1, 0 starting from result = 0:
//   0 -> (0 << 1) | 1 = 1 -> (1 << 1) | 1 = 11 -> (11 << 1) | 0 = 110   (= 6)
```

### Worked problems

```cpp
// Reverse all 32 bits (LeetCode 190): peel the last bit off n, append it to r.
// Loop exactly 32 times (not `while (n)`): trailing 0s of n must become leading 0s of r.
//   4-bit picture, n = 0011: peel 1, 1, 0, 0 and append each:  r = 1 -> 11 -> 110 -> 1100
uint32_t r = 0;
for (int k = 0; k < 32; k++) { r = (r << 1) | (n & 1); n >>= 1; }

// Swap the 4 bytes (endian swap): move each byte to the opposite end.
//   0x12345678 -> 0x78563412
uint32_t sw = (x >> 24) | ((x >> 8) & 0xFF00u) | ((x << 8) & 0xFF0000u) | (x << 24);

// Number to hex (LeetCode 405): take 4 bits at a time with & 0xF, look up the digit.
// Cast negatives to unsigned first so -1 becomes ffffffff.
uint32_t u = (uint32_t)num; string h;
do { h += "0123456789abcdef"[u & 0xF]; u >>= 4; } while (u);
reverse(h.begin(), h.end());           // 26 -> "1a",  -1 -> "ffffffff"
```

### Traps

- `&` binds looser than `==`: `x & 1 == 0` means `x & (1 == 0)`. Write `(x & 1) == 0`.
- `1 << 31` overflows `int`. Write `1u << 31` (or `1LL << k` for 64-bit).
- Shifting by the bit width or more (`x << 32` on a 32-bit value) is undefined.
- `>>` on a negative `int` keeps filling with 1s, so `while (n) n >>= 1` never ends. Use unsigned.
- `~x` on an unsigned number flips all 32 bits, not just the ones you were looking at. Mask with `& 0xF` etc. if you want fewer.

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

## Functions and references

```cpp
void addOne(vector<int>& v) { for (auto& x : v) x++; }   // & = modifies caller's vector
int total(const vector<int>& v) { /* read only, no copy */ }
```

Passing `vector<int> v` (no `&`) makes a full copy, which is O(n).

## Linked list and tree nodes

```cpp
struct ListNode { int val; ListNode* next; ListNode(int x) : val(x), next(nullptr) {} };
struct TreeNode { int val; TreeNode *left, *right; TreeNode(int x) : val(x), left(nullptr), right(nullptr) {} };
for (ListNode* cur = head; cur != nullptr; cur = cur->next) { }
```

## Input and output (only if the exam reads stdin)

```cpp
int n; cin >> n;
vector<int> a(n);
for (auto& x : a) cin >> x;
string line; getline(cin, line);
cout << ans << "\n";
```

## Traps

- `v.size()` is unsigned. `v.size() - 1` on an empty vector becomes a huge number. Cast to `int` or check `empty()` first.
- Out-of-bounds `v[i]` does not raise an error. It silently reads garbage or crashes.
- `m[key]` inserts the key. Use `count` or `find` to check without inserting.
- `substr(pos, len)` takes a length, not an end index.
- `a / b` with two ints truncates. `/` on negative numbers rounds toward zero.
- Mixing `int` and `long long`: `INT_MAX + 1` overflows; write `1LL * x * y` before it happens.
- Forgetting `&` on a parameter you meant to modify.
- Forgetting the `;` after a `struct` definition.
- `ms.erase(x)` removes every copy. Use `ms.erase(ms.find(x))` for one.
- `pop()` on stack, queue and priority_queue returns nothing.
- Reading `top()`, `front()` or `*begin()` on an empty container crashes or returns garbage.
- `unordered_*` have no order. Use `map` or `set` when you need sorted output.
