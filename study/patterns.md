# LeetCode Patterns Cheat Sheet

A living cheat sheet: one entry per pattern, with a recognition signal, the idea, a sample problem, and a solution in Python and C++. Every code block here was tested against a brute-force reference in both languages. Add an entry after you learn a new pattern (template at the bottom).

## Quick recognition table

| If the problem says... | Think |
|---|---|
| in place, O(1) space, remove / filter / compact | Read/write pointers |
| keep at most k copies of each value (sorted) | Read/write pointers, compare with `nums[write - k]` |
| move something to the back, keep the order of the rest | Read/write pointers with swap |
| each result depends on everything before it | Prefix sum |
| each result depends on everything after it | Scan from the right |
| longest run / streak in one pass | Running counter plus best-so-far |
| output is a rearrangement and positions are computable | Compute destination index |
| reorder into groups, keep order within groups | Buckets, then concatenate |
| merge into an array with free space at the end | Fill from the back |
| rotate an array | Reverse three times |
| duplicates, 'have I seen this', membership | Hash set (or map if you need a value) |

## Patterns

### 1. Read/write pointers (same-direction two pointers)

**Signal:** Change an array in place in O(1) space by filtering or compacting it: remove a value, remove duplicates, move zeros, keep at most k copies.

**Idea:** `i` reads every element once. `write` only moves when you keep an element. Invariant: everything before `write` is the finished answer for the part already read.

**Sample:** LC 27 Remove Element

Python:

```python
class Solution:
    def removeElement(self, nums: list[int], val: int) -> int:
        write = 0
        for x in nums:
            if x != val:
                nums[write] = x
                write += 1
        return write
```

C++:

```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int write = 0;
        for (int x : nums) {
            if (x != val) {
                nums[write] = x;
                write++;
            }
        }
        return write;
    }
};
```

**Complexity:** O(n) time, O(1) space.

**Also / watch out:** LC 26 (compare to `nums[write-1]`), LC 80 (below), LC 283 (below), LC 905.

### 2. Variation: keep at most k copies

**Signal:** Sorted array, each value may appear at most k times, in place.

**Idea:** Compare the new element with the element k places behind the write pointer (`nums[write - k]`). If equal, you already kept k copies, so skip it. Write the first k elements unconditionally.

**Sample:** LC 80 Remove Duplicates from Sorted Array II (k = 2)

Python:

```python
class Solution:
    def removeDuplicates(self, nums: list[int]) -> int:
        if len(nums) <= 2:
            return len(nums)
        write = 2
        for i in range(2, len(nums)):
            if nums[i] != nums[write - 2]:
                nums[write] = nums[i]
                write += 1
        return write
```

C++:

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int n = nums.size();
        if (n <= 2) return n;
        int write = 2;
        for (int i = 2; i < n; i++) {
            if (nums[i] != nums[write - 2]) {
                nums[write] = nums[i];
                write++;
            }
        }
        return write;
    }
};
```

**Complexity:** O(n) time, O(1) space.

**Also / watch out:** LC 26 is the k = 1 case. Compare against `nums[i - 2]` instead of `nums[write - 2]` and it breaks, because earlier slots were overwritten.

### 3. Variation: swap instead of overwrite

**Signal:** Same as read/write pointers, but the discarded elements must stay in the array (e.g. zeros pushed to the back).

**Idea:** Everything between `write` and `i - 1` is a discarded element, so swapping `nums[write]` with `nums[i]` puts it where it belongs. Skip the swap when `write == i` to avoid pointless writes. `write` still advances for every kept element.

**Sample:** LC 283 Move Zeroes

Python:

```python
class Solution:
    def moveZeroes(self, nums: list[int]) -> None:
        write = 0
        for i in range(len(nums)):
            if nums[i] != 0:
                if write != i:
                    nums[write], nums[i] = nums[i], nums[write]
                write += 1
```

C++:

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int write = 0;
        for (int i = 0; i < (int)nums.size(); i++) {
            if (nums[i] != 0) {
                if (write != i) swap(nums[write], nums[i]);
                write++;
            }
        }
    }
};
```

**Complexity:** O(n) time, O(1) space, fewest possible writes.

**Also / watch out:** LC 905 Sort Array By Parity. Trap: if you put `write != i` into the same `if` as `nums[i] != 0`, `write` stops advancing and the order breaks.

### 4. Running (prefix) sum

**Signal:** Each answer depends on the sum of everything before it, or on a range sum.

**Idea:** Each position equals the previous position's total plus its own value. Do it in place if you may modify the input.

**Sample:** LC 1480 Running Sum of 1d Array

Python:

```python
class Solution:
    def runningSum(self, nums: list[int]) -> list[int]:
        for i in range(1, len(nums)):
            nums[i] += nums[i - 1]
        return nums
```

C++:

```cpp
class Solution {
public:
    vector<int> runningSum(vector<int>& nums) {
        for (int i = 1; i < (int)nums.size(); i++) {
            nums[i] += nums[i - 1];
        }
        return nums;
    }
};
```

**Complexity:** O(n) time, O(1) extra space (modifies the input; ask first in an interview).

**Also / watch out:** Range sum = `prefix[r] - prefix[l - 1]`. Later: Subarray Sum Equals K, Product of Array Except Self.

### 5. Scan from the right with a running max

**Signal:** Each answer depends on everything to its right, such as the maximum to the right.

**Idea:** Walk right to left, keeping the best value seen so far. Assign the answer first, then update the running value with the old element.

**Sample:** LC 1299 Replace Elements with Greatest Element on Right Side

Python:

```python
class Solution:
    def replaceElements(self, arr: list[int]) -> list[int]:
        mx = -1
        for i in range(len(arr) - 1, -1, -1):
            arr[i], mx = mx, max(mx, arr[i])
        return arr
```

C++:

```cpp
class Solution {
public:
    vector<int> replaceElements(vector<int>& arr) {
        int mx = -1;
        for (int i = (int)arr.size() - 1; i >= 0; i--) {
            int old = arr[i];
            arr[i] = mx;
            mx = max(mx, old);
        }
        return arr;
    }
};
```

**Complexity:** O(n) time, O(1) extra space.

**Also / watch out:** Same direction trick for 'everything to the left' by scanning left to right.

### 6. Running counter with a best-so-far

**Signal:** Longest streak or run of something in one pass.

**Idea:** Keep `cur` for the current run and `best` for the maximum. Update `best` as soon as `cur` grows, so you don't need a final `max` after the loop. Reset `cur` when the run breaks.

**Sample:** LC 485 Max Consecutive Ones

Python:

```python
class Solution:
    def findMaxConsecutiveOnes(self, nums: list[int]) -> int:
        best = cur = 0
        for x in nums:
            if x == 1:
                cur += 1
                best = max(best, cur)
            else:
                cur = 0
        return best
```

C++:

```cpp
class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& nums) {
        int best = 0, cur = 0;
        for (int x : nums) {
            if (x == 1) {
                cur++;
                best = max(best, cur);
            } else {
                cur = 0;
            }
        }
        return best;
    }
};
```

**Complexity:** O(n) time, O(1) space.

**Also / watch out:** Bug to remember: if you only update `best` when the streak breaks, an array that ends on a streak (or is all ones) is missed.

### 7. Compute each element's destination index

**Signal:** Output is a rearrangement of the input and you can work out where each input element lands.

**Idea:** Create the output at its final size, loop over the input (or half of it), and write straight to the computed index. Write the index formula down for small examples first.

**Sample:** LC 1470 Shuffle the Array

Python:

```python
class Solution:
    def shuffle(self, nums: list[int], n: int) -> list[int]:
        ans = [0] * (2 * n)
        for i in range(n):
            ans[2 * i] = nums[i]
            ans[2 * i + 1] = nums[i + n]
        return ans
```

C++:

```cpp
class Solution {
public:
    vector<int> shuffle(vector<int>& nums, int n) {
        vector<int> ans(2 * n);
        for (int i = 0; i < n; i++) {
            ans[2 * i] = nums[i];
            ans[2 * i + 1] = nums[i + n];
        }
        return ans;
    }
};
```

**Complexity:** O(n) time, O(n) space for the output.

**Also / watch out:** LC 2149 Rearrange Array Elements by Sign (positives to even slots, negatives to odd). Writing by index is O(1); inserting in the middle is O(n).

### 8. Stable partition into buckets, then concatenate

**Signal:** Reorder elements into groups while keeping the original order inside each group.

**Idea:** One pass, appending each element to the right bucket. Identical elements (like the pivot) only need a count. Join the buckets at the end.

**Sample:** LC 2161 Partition Array According to Given Pivot

Python:

```python
class Solution:
    def pivotArray(self, nums: list[int], pivot: int) -> list[int]:
        less, greater = [], []
        count = 0
        for x in nums:
            if x == pivot:
                count += 1
            elif x < pivot:
                less.append(x)
            else:
                greater.append(x)
        return less + [pivot] * count + greater
```

C++:

```cpp
class Solution {
public:
    vector<int> pivotArray(vector<int>& nums, int pivot) {
        vector<int> less, greater;
        int count = 0;
        for (int x : nums) {
            if (x == pivot) count++;
            else if (x < pivot) less.push_back(x);
            else greater.push_back(x);
        }
        vector<int> ans = less;
        ans.insert(ans.end(), count, pivot);
        ans.insert(ans.end(), greater.begin(), greater.end());
        return ans;
    }
};
```

**Complexity:** O(n) time, O(n) space.

**Also / watch out:** Name buckets after what they hold (`less`, `greater`), not `pos`/`neg`.

### 9. Fill from the back

**Signal:** Merging into an array that has free space at the end, or any in-place write that would overwrite values you still need.

**Idea:** Start from the end, where the free space is, and place the largest remaining element each time. Nothing unread is ever overwritten.

**Sample:** LC 88 Merge Sorted Array

Python:

```python
class Solution:
    def merge(self, nums1: list[int], m: int, nums2: list[int], n: int) -> None:
        i, j, k = m - 1, n - 1, m + n - 1
        while j >= 0:
            if i >= 0 and nums1[i] > nums2[j]:
                nums1[k] = nums1[i]
                i -= 1
            else:
                nums1[k] = nums2[j]
                j -= 1
            k -= 1
```

C++:

```cpp
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int i = m - 1, j = n - 1, k = m + n - 1;
        while (j >= 0) {
            if (i >= 0 && nums1[i] > nums2[j]) {
                nums1[k] = nums1[i];
                i--;
            } else {
                nums1[k] = nums2[j];
                j--;
            }
            k--;
        }
    }
};
```

**Complexity:** O(m + n) time, O(1) space.

**Also / watch out:** Loop on `j >= 0` only: once `nums2` is used up, the rest of `nums1` is already in place.

### 10. Rotate by reversing

**Signal:** Rotate an array by k positions in place.

**Idea:** Reverse the whole array, then reverse the first k, then reverse the rest. Always do `k %= n` first, because k can exceed n.

**Sample:** LC 189 Rotate Array

Python:

```python
class Solution:
    def rotate(self, nums: list[int], k: int) -> None:
        n = len(nums)
        k %= n

        def rev(l, r):
            while l < r:
                nums[l], nums[r] = nums[r], nums[l]
                l += 1
                r -= 1

        rev(0, n - 1)
        rev(0, k - 1)
        rev(k, n - 1)
```

C++:

```cpp
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        int n = nums.size();
        k %= n;
        reverse(nums.begin(), nums.end());
        reverse(nums.begin(), nums.begin() + k);
        reverse(nums.begin() + k, nums.end());
    }
};
```

**Complexity:** O(n) time, O(1) space. The simple version (new array, `temp[(i + k) % n] = nums[i]`) is O(n) space.

**Also / watch out:** Element at index i moves to `(i + k) % n` when rotating right.

### 11. Hash set for 'have I seen this?'

**Signal:** Duplicates, membership, 'does X exist' questions where order doesn't matter.

**Idea:** For each element: if it is already in the set, answer immediately. Otherwise add it. Check before you add.

**Sample:** LC 217 Contains Duplicate

Python:

```python
class Solution:
    def containsDuplicate(self, nums: list[int]) -> bool:
        seen = set()
        for x in nums:
            if x in seen:
                return True
            seen.add(x)
        return False
```

C++:

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_set<int> seen;
        for (int x : nums) {
            if (seen.count(x)) return true;
            seen.insert(x);
        }
        return false;
    }
};
```

**Complexity:** O(n) time on average, O(n) space.

**Also / watch out:** Use a hash map instead when you need a value per key (counts, indices): Two Sum, Valid Anagram.

## Cost cheat sheet: Python list vs C++ vector

| Operation | Python `list` | C++ `vector` | Cost |
|---|---|---|---|
| read / write by index | `a[i]` | `v[i]` | O(1) |
| add at the end | `a.append(x)` | `v.push_back(x)` | amortized O(1) |
| remove from the end | `a.pop()` | `v.pop_back()` | O(1) |
| insert at index i | `a.insert(i, x)` | `v.insert(v.begin() + i, x)` | O(n - i); O(n) at the front |
| remove at index i | `a.pop(i)` | `v.erase(v.begin() + i)` | O(n - i); O(n) at the front |
| membership test | `x in a` | `find(v.begin(), v.end(), x)` | O(n) |
| membership in a set | `x in s` | `s.count(x)` | O(1) average (hash), O(log n) for ordered `set` |
| sort | `a.sort()` | `sort(v.begin(), v.end())` | O(n log n) |
| length | `len(a)` | `v.size()` (unsigned!) | O(1) |

Why append is amortized O(1): the array doubles in capacity when full (16, 32, 64, ...), and each rare O(n) copy is spread over many appends.

## Python to C++ syntax

| Python | C++ |
|---|---|
| `for x in nums:` | `for (int x : nums)` (copy) / `for (auto& x : nums)` (modify) |
| `for i in range(n):` | `for (int i = 0; i < n; i++)` |
| `range(n - 1, -1, -1)` | `for (int i = n - 1; i >= 0; i--)` |
| `nums[-1]` | `nums.back()` (negative indexes don't work) |
| `a, b = b, a` | `swap(a, b)` |
| `[0] * n` | `vector<int> v(n, 0)` |
| `max(a, b)` | `max(a, b)` |
| `and` / `or` / `not` | `&&` / `||` / `!` |
| `elif` | `else if` |
| `a // b` | `a / b` (both ints) |
| `len(s)` | `s.size()` |
| `s[a:b]` | `s.substr(a, b - a)` (second argument is a length) |
| `d[k] = d.get(k, 0) + 1` | `m[k]++` |

## Traps

- Return statement placed inside the loop instead of after it (happened twice).
- Only updating `best` when a streak breaks: misses a streak that runs to the end.
- `write != i` combined with the keep-condition: `write` stops advancing.
- Comparing with `nums[i - 2]` after overwriting: compare with the write pointer instead.
- Forgetting `k %= n` when rotating.
- `v.size() - 1` on an empty vector (unsigned wrap-around). Store `int n = v.size();` first.
- Writing `ans[i]` on an empty `vector<int> ans;`. Give it a size or use `push_back`.
- Missing `;` in C++, and `=` vs `==` in conditions.
- Bit width is not capacity: dynamic arrays grow by doubling, not between 2^32 and 2^64.

## Patterns to add next

- Opposite-end two pointers (palindrome, Two Sum II, 3Sum)
- Sliding window, fixed and variable
- Frequency map (anagrams, first unique character)
- Hash map for Two Sum (value to index)
- Monotonic stack
- Fast/slow pointers on linked lists
- Binary search, including on the answer
- BFS / DFS on grids and trees

## Template for a new entry

```
### N. Pattern name
**Signal:** how to recognize it from the problem statement
**Idea:** the invariant or core step, in two sentences
**Sample:** LC number and title
Python / C++ code blocks (test them against a brute-force reference)
**Complexity:** time and space
**Also / watch out:** related problems, traps
```
