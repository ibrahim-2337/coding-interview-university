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

## vector

```cpp
vector<int> v = {5, 3, 8, 1};
vector<int> z(4, 0);                         // size 4, all zeros
vector<vector<int>> g(rows, vector<int>(cols, 0));
v.push_back(9);  v.pop_back();               // O(1) at the end
v.insert(v.begin() + i, x);                  // O(n)
v.erase(v.begin() + i);                      // O(n)
v.size(); v.empty(); v.front(); v.back(); v[i];
sort(v.begin(), v.end());
sort(v.begin(), v.end(), [](int x, int y) { return x > y; });  // descending
reverse(v.begin(), v.end());
swap(v[i], v[j]);
int mx = *max_element(v.begin(), v.end());   // note the *
int sum = accumulate(v.begin(), v.end(), 0); // <numeric>

for (int i = 0; i < (int)v.size(); i++) { }  // cast size() to int
for (int x : v) { }                          // copy of each element
for (auto& x : v) { x++; }                   // reference: modifies the vector
```

## string

```cpp
string s = "hello";
s.size(); s[i]; s += 'x'; s += "yz";
s.substr(1, 3);                    // start index, LENGTH (not end index)
s.find("ll");                      // index, or string::npos if not found
stoi("123"); to_string(45);
c - 'a'  // 0..25 for lowercase letters;   c - '0' // digit value
isalpha(c); isdigit(c); toupper(c); tolower(c);
sort(s.begin(), s.end()); reverse(s.begin(), s.end());
```

## Maps and sets

```cpp
unordered_map<string, int> m;
m["a"]++;                          // missing key is created as 0 first
m.count("a");                      // 0 or 1
m.find("a") != m.end();            // present?
m.erase("a");
for (auto& [k, val] : m) { }       // C++17
map<int, int> om;                  // sorted by key, O(log n)
set<int> st;  unordered_set<int> us;
st.insert(1); us.count(1); *st.begin();
```

## pair, stack, queue, heap

```cpp
pair<int, int> p = {1, 2};  p.first; p.second;   // vector<pair<int,int>> sorts by first, then second
stack<int> stk;  stk.push(1); stk.top(); stk.pop(); stk.empty();
queue<int> q;    q.push(1);   q.front(); q.pop();
priority_queue<int> maxHeap;                                  // largest on top
priority_queue<int, vector<int>, greater<int>> minHeap;       // smallest on top
```

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
