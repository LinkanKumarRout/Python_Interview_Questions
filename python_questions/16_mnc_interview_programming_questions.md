## 16. MNC interview programming questions

Coding problems in the style reported from Amazon, Google, Microsoft, Meta, Apple, Adobe, Uber, Goldman Sachs, Flipkart, and similar loops. Statements are paraphrased for practice. Each answer names an approach, its complexity, and a Python sketch. A company tag means the problem is widely associated with that interview loop, not that one team asked this wording on a particular day.

### Q1. Basic

**Two Sum**

Commonly reported in interviews at Amazon, Google, Meta, Microsoft.

Given a list of integers and a target, return the indices of two different items that add up to the target. Exactly one answer exists.

Example: `nums = [2, 7, 11, 15]`, `target = 9` returns `[0, 1]`.

**Answer:**

One pass with a dictionary from value to index. For each number, look up `target - number` before storing the current index.

**Complexity:** Time O(n), space O(n).

```python
def two_sum(nums, target):
    seen = {}
    for i, n in enumerate(nums):
        j = seen.get(target - n)
        if j is not None:
            return [j, i]
        seen[n] = i
```

### Q2. Basic

**Contains Duplicate**

Commonly reported in interviews at Amazon, Apple, Adobe.

Return true when a list of integers contains any value more than once.

Example: `[1, 2, 3, 1]` is true. `[1, 2, 3]` is false.

**Answer:**

Insert values into a set. If a value is already present, it is a duplicate. Sorting also works if you can spend O(n log n) time and no extra memory.

**Complexity:** Time O(n), space O(n) with a set.

```python
def contains_duplicate(nums):
    return len(nums) != len(set(nums))
```

### Q3. Basic

**Best Time to Buy and Sell Stock**

Commonly reported in interviews at Amazon, Bloomberg, Microsoft.

You may complete one buy and one later sell. Return the maximum profit, or 0 if no profit is possible.

Example: `[7, 1, 5, 3, 6, 4]` returns `5` (buy at 1, sell at 6).

**Answer:**

Track the minimum price seen so far and the best difference `price - minimum`.

**Complexity:** Time O(n), space O(1).

```python
def max_profit(prices):
    best, low = 0, prices[0]
    for p in prices:
        low = min(low, p)
        best = max(best, p - low)
    return best
```

### Q4. Basic

**Move Zeroes**

Commonly reported in interviews at Facebook, Bloomberg.

Move every 0 to the end of the list while keeping the order of the non-zero numbers. Do it in place.

Example: `[0, 1, 0, 3, 12]` becomes `[1, 3, 12, 0, 0]`.

**Answer:**

Use a write index. Copy each non-zero forward, then fill the tail with zeros.

**Complexity:** Time O(n), space O(1).

```python
def move_zeroes(nums):
    w = 0
    for x in nums:
        if x != 0:
            nums[w] = x
            w += 1
    for i in range(w, len(nums)):
        nums[i] = 0
    return nums
```

### Q5. Basic

**Plus One**

Commonly reported in interviews at Google, Amazon.

A list of digits represents a non-negative integer. Return the digits of that integer plus one.

Example: `[1, 2, 9]` becomes `[1, 3, 0]`. `[9, 9]` becomes `[1, 0, 0]`.

**Answer:**

Walk from the right. Turn 9s into 0s until a digit can be incremented. If every digit was 9, insert a leading 1.

**Complexity:** Time O(n), space O(1) extra besides the answer.

```python
def plus_one(digits):
    for i in range(len(digits) - 1, -1, -1):
        if digits[i] < 9:
            digits[i] += 1
            return digits
        digits[i] = 0
    return [1] + digits
```

### Q6. Basic

**Remove Duplicates from Sorted Array**

Commonly reported in interviews at Microsoft, Amazon.

A sorted list may contain duplicates. Compact the unique values at the front and return how many unique values there are. Order must stay sorted.

Example: `[1, 1, 2, 2, 3]` becomes `[1, 2, 3, ...]` and the function returns `3`.

**Answer:**

Two pointers. The slow pointer marks the end of the unique prefix. Copy a value forward only when it differs from the last kept value.

**Complexity:** Time O(n), space O(1).

```python
def remove_duplicates(nums):
    if not nums:
        return 0
    w = 1
    for i in range(1, len(nums)):
        if nums[i] != nums[w - 1]:
            nums[w] = nums[i]
            w += 1
    return w
```

### Q7. Basic

**Merge Sorted Array**

Commonly reported in interviews at Facebook, Microsoft.

Two sorted lists `a` and `b`. `a` has enough trailing space for every element of `b`. Merge `b` into `a` so `a` is sorted.

Example: `a = [1, 3, 5, 0, 0]`, `b = [2, 4]` becomes `[1, 2, 3, 4, 5]`.

**Answer:**

Fill from the end so the empty slots are consumed first and no value in `a` is overwritten before it is placed.

**Complexity:** Time O(n + m), space O(1).

```python
def merge(a, m, b, n):
    i, j, k = m - 1, n - 1, m + n - 1
    while j >= 0:
        if i >= 0 and a[i] > b[j]:
            a[k] = a[i]
            i -= 1
        else:
            a[k] = b[j]
            j -= 1
        k -= 1
    return a
```

### Q8. Basic

**Majority Element**

Commonly reported in interviews at Amazon, Adobe.

A value appears more than `len(nums) // 2` times. Return it.

Example: `[2, 2, 1, 2, 3]` returns `2`.

**Answer:**

Boyer-Moore voting: keep a candidate and a count. The majority survives because every other value can cancel it at most once.

**Complexity:** Time O(n), space O(1).

```python
def majority(nums):
    cand = count = 0
    for n in nums:
        if count == 0:
            cand = n
        count += 1 if n == cand else -1
    return cand
```

### Q9. Basic

**Missing Number**

Commonly reported in interviews at Microsoft, Amazon.

The list contains `n` distinct numbers taken from `0` through `n`. Return the missing one.

Example: `[3, 0, 1]` returns `2`.

**Answer:**

XOR every index and every value, then XOR `n`. Pairs cancel and the missing number remains. The sum formula `n*(n+1)//2 - sum(nums)` also works.

**Complexity:** Time O(n), space O(1).

```python
def missing_number(nums):
    n = len(nums)
    xor = n
    for i, v in enumerate(nums):
        xor ^= i ^ v
    return xor
```

### Q10. Basic

**Single Number**

Commonly reported in interviews at Amazon, Google.

Every value appears twice except one value, which appears once. Return that value.

Example: `[4, 1, 2, 1, 2]` returns `4`.

**Answer:**

XOR the whole list. Identical pairs cancel to 0.

**Complexity:** Time O(n), space O(1).

```python
def single_number(nums):
    acc = 0
    for n in nums:
        acc ^= n
    return acc
```

### Q11. Basic

**Climbing Stairs**

Commonly reported in interviews at Amazon, Adobe, Uber.

You climb 1 or 2 stairs at a time. Return how many distinct ways there are to climb `n` stairs.

Example: `n = 3` returns `3`: 1+1+1, 1+2, 2+1.

**Answer:**

This is Fibonacci. Let `dp[i]` be ways to reach step `i`. Then `dp[i] = dp[i-1] + dp[i-2]`. Keep only two rolling values.

**Complexity:** Time O(n), space O(1).

```python
def climb(n):
    a, b = 1, 1
    for _ in range(n):
        a, b = b, a + b
    return a
```

### Q12. Basic

**Valid Parentheses**

Commonly reported in interviews at Amazon, Microsoft, Google.

A string contains only `()[]{}`. Return true when the brackets are correctly matched and nested.

Example: `()[]{}` is true. `(]` is false. `([)]` is false.

**Answer:**

Push opening brackets. On a closing bracket, the stack top must be its partner. The stack must end empty.

**Complexity:** Time O(n), space O(n).

```python
def is_valid(s):
    pair = {')': '(', ']': '[', '}': '{'}
    stack = []
    for ch in s:
        if ch in '([{':
            stack.append(ch)
        elif not stack or stack.pop() != pair[ch]:
            return False
    return not stack
```

### Q13. Basic

**Valid Anagram**

Commonly reported in interviews at Amazon, Bloomberg.

Return true when two strings are anagrams of each other. Comparison is case-sensitive and uses the raw characters.

Example: `anagram` and `nagaram` is true. `rat` and `car` is false.

**Answer:**

Count characters. For a small alphabet, an array of 26 is enough. A `Counter` equality test is the same idea.

**Complexity:** Time O(n), space O(1) for a fixed alphabet.

```python
def is_anagram(a, b):
    if len(a) != len(b):
        return False
    from collections import Counter
    return Counter(a) == Counter(b)
```

### Q14. Basic

**First Unique Character**

Commonly reported in interviews at Amazon, Goldman Sachs.

Return the index of the first character that appears once in a string, or -1.

Example: `leetcode` returns `0`. `aabb` returns `-1`.

**Answer:**

Count, then scan again for the first character whose count is 1. Two passes keep the original order.

**Complexity:** Time O(n), space O(1) for a fixed alphabet.

```python
def first_unique(s):
    from collections import Counter
    counts = Counter(s)
    for i, ch in enumerate(s):
        if counts[ch] == 1:
            return i
    return -1
```

### Q15. Basic

**Ransom Note**

Commonly reported in interviews at Apple, Amazon.

Return true when the note can be cut from the letters in a magazine. Each magazine character may be used once.

Example: Note `aab` and magazine `baa` is true.

**Answer:**

Count magazine letters and decrement. Fail when a needed letter is missing.

**Complexity:** Time O(n + m), space O(1) for a fixed alphabet.

```python
def can_construct(note, magazine):
    from collections import Counter
    have = Counter(magazine)
    for ch in note:
        if have[ch] == 0:
            return False
        have[ch] -= 1
    return True
```

### Q16. Basic

**Reverse Linked List**

Commonly reported in interviews at Amazon, Microsoft, Apple.

Reverse a singly linked list in place and return the new head. Nodes have `.val` and `.next`.

Example: `1 -> 2 -> 3` becomes `3 -> 2 -> 1`.

**Answer:**

Three pointers: previous, current, and next. Point current backward, then advance.

**Complexity:** Time O(n), space O(1).

```python
def reverse_list(head):
    prev = None
    cur = head
    while cur:
        nxt = cur.next
        cur.next = prev
        prev = cur
        cur = nxt
    return prev
```

### Q17. Basic

**Linked List Cycle**

Commonly reported in interviews at Amazon, Microsoft.

Return true when a singly linked list contains a cycle.

Example: A list whose tail points at an earlier node is true.

**Answer:**

Floyd's tortoise and hare. If they meet, there is a cycle. If the fast pointer reaches the end, there is not.

**Complexity:** Time O(n), space O(1).

```python
def has_cycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow is fast:
            return True
    return False
```

### Q18. Basic

**Maximum Depth of Binary Tree**

Commonly reported in interviews at Amazon, LinkedIn.

Return the number of nodes on the longest root-to-leaf path. An empty tree has depth 0.

Example: A single node returns 1.

**Answer:**

Depth is `1 + max(depth(left), depth(right))`. An iterative level-order count is the same answer.

**Complexity:** Time O(n), space O(h) for the recursion stack.

```python
def max_depth(root):
    if not root:
        return 0
    return 1 + max(max_depth(root.left), max_depth(root.right))
```

### Q19. Basic

**Same Tree**

Commonly reported in interviews at Bloomberg, Amazon.

Return true when two binary trees have the same shape and the same values.

Example: Both empty is true. One empty is false.

**Answer:**

Recurse: values must match and both pairs of children must match.

**Complexity:** Time O(n), space O(h).

```python
def is_same(a, b):
    if not a or not b:
        return a is b
    return a.val == b.val and is_same(a.left, b.left) and is_same(a.right, b.right)
```

### Q20. Basic

**Invert Binary Tree**

Commonly reported in interviews at Google.

Swap every left and right child and return the root.

Example: A tree `1 / 2,3` becomes `1 / 3,2`.

**Answer:**

Post-order or pre-order swap. Recursion is enough.

**Complexity:** Time O(n), space O(h).

```python
def invert(root):
    if root:
        root.left, root.right = invert(root.right), invert(root.left)
    return root
```

### Q21. Basic

**Binary Search**

Commonly reported in interviews at Every product company.

Given a sorted list of distinct integers, return the index of `target`, or -1.

Example: `[1, 3, 5, 7]`, target `5` returns `2`.

**Answer:**

Keep a half-open or closed window. Compare the middle and discard the half that cannot contain the target. Watch the midpoint so it does not overflow in fixed-width languages; Python ints do not overflow.

**Complexity:** Time O(log n), space O(1).

```python
def binary_search(nums, target):
    lo, hi = 0, len(nums) - 1
    while lo <= hi:
        mid = (lo + hi) // 2
        if nums[mid] == target:
            return mid
        if nums[mid] < target:
            lo = mid + 1
        else:
            hi = mid - 1
    return -1
```

### Q22. Basic

**Search Insert Position**

Commonly reported in interviews at Amazon, Adobe.

Given a sorted list of distinct integers, return the index of `target` if it exists, otherwise the index where it should be inserted to keep the list sorted.

Example: `[1, 3, 5, 6]`, target `2` returns `1`.

**Answer:**

Lower-bound binary search. When the loop ends, `lo` is the first index whose value is not less than the target.

**Complexity:** Time O(log n), space O(1).

```python
def search_insert(nums, target):
    lo, hi = 0, len(nums)
    while lo < hi:
        mid = (lo + hi) // 2
        if nums[mid] < target:
            lo = mid + 1
        else:
            hi = mid
    return lo
```

### Q23. Basic

**Implement Stack using a List**

Commonly reported in interviews at Amazon, Microsoft.

Implement `push`, `pop`, `top`, and `empty` for a stack. `pop` and `top` are called only when the stack is non-empty.

Example: push 1, push 2, top is 2, pop returns 2.

**Answer:**

A Python list already has amortized O(1) append and pop from the end. That end is the top.

**Complexity:** Each operation is amortized O(1). Space O(n).

```python
class Stack:
    def __init__(self):
        self.data = []
    def push(self, x):
        self.data.append(x)
    def pop(self):
        return self.data.pop()
    def top(self):
        return self.data[-1]
    def empty(self):
        return not self.data
```

### Q24. Basic

**Min Stack**

Commonly reported in interviews at Amazon, Bloomberg, Google.

Design a stack that also returns its current minimum in O(1).

Example: Push -2, push 0, push -3. Min is -3. After pop, min is -2.

**Answer:**

Keep a second stack of minima. On push, store `min(x, current_min)`. On pop, pop both stacks.

**Complexity:** Each operation O(1). Space O(n).

```python
class MinStack:
    def __init__(self):
        self.data = []
        self.mins = []
    def push(self, x):
        self.data.append(x)
        self.mins.append(x if not self.mins else min(x, self.mins[-1]))
    def pop(self):
        self.mins.pop()
        return self.data.pop()
    def top(self):
        return self.data[-1]
    def get_min(self):
        return self.mins[-1]
```

### Q25. Basic

**Fizz Buzz**

Commonly reported in interviews at Amazon, and many screening rounds.

Return a list of strings for numbers from 1 through `n`. Multiples of 3 are `Fizz`, multiples of 5 are `Buzz`, multiples of both are `FizzBuzz`, and the rest are the decimal number.

Example: `n = 5` gives `['1', '2', 'Fizz', '4', 'Buzz']`.

**Answer:**

Test 15 before 3 and 5, or build the word from the two conditions so the order of tests does not matter.

**Complexity:** Time O(n), space O(n) for the answer.

```python
def fizz_buzz(n):
    out = []
    for i in range(1, n + 1):
        word = ''
        if i % 3 == 0:
            word += 'Fizz'
        if i % 5 == 0:
            word += 'Buzz'
        out.append(word or str(i))
    return out
```

### Q26. Basic

**Maximum Subarray**

Commonly reported in interviews at Amazon, Microsoft, LinkedIn.

Return the largest sum of any contiguous subarray. The list contains at least one number and may contain negatives.

Example: `[-2, 1, -3, 4, -1, 2, 1, -5, 4]` returns `6` from `[4, -1, 2, 1]`.

**Answer:**

Kadane's algorithm. Either extend the current subarray or start over at the current element, whichever is larger. Track the best sum.

**Complexity:** Time O(n), space O(1).

```python
def max_subarray(nums):
    best = cur = nums[0]
    for n in nums[1:]:
        cur = max(n, cur + n)
        best = max(best, cur)
    return best
```

### Q27. Basic

**Pascal's Triangle Row**

Commonly reported in interviews at Amazon, Adobe.

Return the first `n` rows of Pascal's triangle. Each interior value is the sum of the two values above it. Rows are 0-indexed or 1-indexed; here `n` is the number of rows.

Example: `n = 3` returns `[[1], [1, 1], [1, 2, 1]]`.

**Answer:**

Build each row from the previous one. Edges are 1.

**Complexity:** Time O(n^2), space O(n^2) for the answer.

```python
def pascal(n):
    rows = []
    for r in range(n):
        row = [1] * (r + 1)
        for c in range(1, r):
            row[c] = rows[r - 1][c - 1] + rows[r - 1][c]
        rows.append(row)
    return rows
```

### Q28. Basic

**Merge Two Sorted Lists**

Commonly reported in interviews at Amazon, Microsoft, Apple.

Merge two sorted singly linked lists into one sorted list. You may reuse the nodes.

Example: `1 -> 3` and `2 -> 4` becomes `1 -> 2 -> 3 -> 4`.

**Answer:**

Dummy head. Always attach the smaller current node, then advance that list.

**Complexity:** Time O(n + m), space O(1).

```python
def merge_lists(a, b):
    dummy = tail = type(a)(0) if False else _Node(0)
    while a and b:
        if a.val <= b.val:
            tail.next, a = a, a.next
        else:
            tail.next, b = b, b.next
        tail = tail.next
    tail.next = a or b
    return dummy.next

class _Node:
    def __init__(self, val, next=None):
        self.val, self.next = val, next
```

### Q29. Basic

**Symmetric Tree**

Commonly reported in interviews at Microsoft, Amazon.

Return true when a binary tree is a mirror of itself.

Example: A tree with root 1 and children 2,2, each with outer child 3, is symmetric.

**Answer:**

Compare the left subtree with the right subtree as mirrors: left.left with right.right, and left.right with right.left.

**Complexity:** Time O(n), space O(h).

```python
def is_symmetric(root):
    def mirror(a, b):
        if not a or not b:
            return a is b
        return a.val == b.val and mirror(a.left, b.right) and mirror(a.right, b.left)
    return mirror(root.left, root.right) if root else True
```

### Q30. Basic

**Path Sum**

Commonly reported in interviews at Amazon, Adobe.

Return true when the tree has a root-to-leaf path whose values sum to `target`.

Example: Root 5 with a leaf path 4 then 11 then 2 sums to 22.

**Answer:**

Subtract the current value and recurse. A leaf succeeds only when the remaining target is 0.

**Complexity:** Time O(n), space O(h).

```python
def has_path_sum(root, target):
    if not root:
        return False
    if not root.left and not root.right:
        return target == root.val
    return has_path_sum(root.left, target - root.val) or has_path_sum(root.right, target - root.val)
```

### Q31. Intermediate

**Group Anagrams**

Commonly reported in interviews at Amazon, Uber, Facebook.

Group strings that are anagrams of each other. Order of groups does not matter.

Example: `['eat', 'tea', 'tan', 'ate', 'nat', 'bat']` forms three groups.

**Answer:**

The sorted tuple of characters is a signature. A count tuple of 26 letters also works and avoids the sort.

**Complexity:** Time O(n * k log k) with sorting, or O(n * k) with counts. Space O(n * k).

```python
def group_anagrams(words):
    from collections import defaultdict
    groups = defaultdict(list)
    for w in words:
        groups[tuple(sorted(w))].append(w)
    return list(groups.values())
```

### Q32. Intermediate

**Longest Substring Without Repeating Characters**

Commonly reported in interviews at Amazon, Google, Bloomberg.

Return the length of the longest substring that contains no repeated character.

Example: `abcabcbb` returns `3` (`abc`).

**Answer:**

Sliding window. Store the last index of each character. When a repeat falls inside the window, move the left edge to one past that index.

**Complexity:** Time O(n), space O(1) for a fixed alphabet, otherwise O(k).

```python
def length_of_longest_substring(s):
    last = {}
    left = best = 0
    for right, ch in enumerate(s):
        if ch in last and last[ch] >= left:
            left = last[ch] + 1
        last[ch] = right
        best = max(best, right - left + 1)
    return best
```

### Q33. Intermediate

**Product of Array Except Self**

Commonly reported in interviews at Amazon, Facebook, Microsoft.

Return a list where `out[i]` is the product of every element of `nums` except `nums[i]`. Do not use division. The answer may use extra space, but the running products should be O(1) extra besides the answer.

Example: `[1, 2, 3, 4]` returns `[24, 12, 8, 6]`.

**Answer:**

Prefix products left to right, then suffix products right to left folded into the same output.

**Complexity:** Time O(n), extra space O(1) besides the answer.

```python
def product_except_self(nums):
    n = len(nums)
    out = [1] * n
    left = 1
    for i in range(n):
        out[i] = left
        left *= nums[i]
    right = 1
    for i in range(n - 1, -1, -1):
        out[i] *= right
        right *= nums[i]
    return out
```

### Q34. Intermediate

**3Sum**

Commonly reported in interviews at Amazon, Facebook, Google.

Return all unique triplets in a list of integers that sum to 0. The triplets should not repeat as sets of values.

Example: `[-1, 0, 1, 2, -1, -4]` returns `[[-1, -1, 2], [-1, 0, 1]]`.

**Answer:**

Sort. Fix one value and run two pointers on the remainder. Skip duplicate values at each pointer so the same triplet is not emitted twice.

**Complexity:** Time O(n^2), space O(1) extra besides the answer, or O(n) for the sort depending on the implementation.

```python
def three_sum(nums):
    nums = sorted(nums)
    out = []
    for i in range(len(nums)):
        if i and nums[i] == nums[i - 1]:
            continue
        lo, hi = i + 1, len(nums) - 1
        while lo < hi:
            s = nums[i] + nums[lo] + nums[hi]
            if s == 0:
                out.append([nums[i], nums[lo], nums[hi]])
                lo += 1
                hi -= 1
                while lo < hi and nums[lo] == nums[lo - 1]:
                    lo += 1
                while lo < hi and nums[hi] == nums[hi + 1]:
                    hi -= 1
            elif s < 0:
                lo += 1
            else:
                hi -= 1
    return out
```

### Q35. Intermediate

**Container With Most Water**

Commonly reported in interviews at Amazon, Google, Bloomberg.

Vertical lines stand at x positions 0..n-1 with the given heights. Pick two lines so the area of the container they form with the x-axis is maximized.

Example: `[1, 8, 6, 2, 5, 4, 8, 3, 7]` returns `49`.

**Answer:**

Two pointers at the ends. The area is limited by the shorter line. Move the shorter side inward, because width only shrinks and a taller partner on the short side is the only way to improve.

**Complexity:** Time O(n), space O(1).

```python
def max_area(height):
    lo, hi = 0, len(height) - 1
    best = 0
    while lo < hi:
        best = max(best, min(height[lo], height[hi]) * (hi - lo))
        if height[lo] < height[hi]:
            lo += 1
        else:
            hi -= 1
    return best
```

### Q36. Intermediate

**Merge Intervals**

Commonly reported in interviews at Facebook, Google, Amazon.

Given closed intervals, merge every pair that overlaps and return the result sorted by start.

Example: `[[1, 3], [2, 6], [8, 10], [15, 18]]` returns `[[1, 6], [8, 10], [15, 18]]`.

**Answer:**

Sort by start. If the current interval starts at or before the end of the last merged interval, extend that end. Otherwise append a new interval.

**Complexity:** Time O(n log n), space O(n) for the answer.

```python
def merge_intervals(intervals):
    intervals = sorted(intervals)
    out = [list(intervals[0])]
    for start, end in intervals[1:]:
        if start <= out[-1][1]:
            out[-1][1] = max(out[-1][1], end)
        else:
            out.append([start, end])
    return out
```

### Q37. Intermediate

**Insert Interval**

Commonly reported in interviews at Google, Amazon.

Insert a new interval into a sorted list of non-overlapping intervals and merge if needed.

Example: `[[1, 3], [6, 9]]` plus `[2, 5]` returns `[[1, 5], [6, 9]]`.

**Answer:**

Append intervals that end before the new one starts. Merge every interval that overlaps the new one. Append the rest.

**Complexity:** Time O(n), space O(n).

```python
def insert_interval(intervals, new):
    out = []
    i = 0
    while i < len(intervals) and intervals[i][1] < new[0]:
        out.append(intervals[i])
        i += 1
    while i < len(intervals) and intervals[i][0] <= new[1]:
        new[0] = min(new[0], intervals[i][0])
        new[1] = max(new[1], intervals[i][1])
        i += 1
    out.append(new)
    out.extend(intervals[i:])
    return out
```

### Q38. Intermediate

**Sort Colors**

Commonly reported in interviews at Microsoft, Amazon.

Sort a list that contains only 0, 1, and 2, in place, in one pass.

Example: `[2, 0, 2, 1, 1, 0]` becomes `[0, 0, 1, 1, 2, 2]`.

**Answer:**

Dutch national flag. Three pointers: next write position for 0, current scan, and next write position for 2.

**Complexity:** Time O(n), space O(1).

```python
def sort_colors(nums):
    lo, i, hi = 0, 0, len(nums) - 1
    while i <= hi:
        if nums[i] == 0:
            nums[lo], nums[i] = nums[i], nums[lo]
            lo += 1
            i += 1
        elif nums[i] == 2:
            nums[hi], nums[i] = nums[i], nums[hi]
            hi -= 1
        else:
            i += 1
    return nums
```

### Q39. Intermediate

**Set Matrix Zeroes**

Commonly reported in interviews at Amazon, Microsoft.

If an element of a matrix is 0, set its whole row and column to 0. Do it in place.

Example: A 3x3 matrix with a single 0 at the center becomes a cross of zeros.

**Answer:**

Use the first row and first column as markers, plus two booleans for whether those lines themselves must be cleared.

**Complexity:** Time O(m * n), extra space O(1).

```python
def set_zeroes(matrix):
    m, n = len(matrix), len(matrix[0])
    row0 = any(matrix[0][j] == 0 for j in range(n))
    col0 = any(matrix[i][0] == 0 for i in range(m))
    for i in range(1, m):
        for j in range(1, n):
            if matrix[i][j] == 0:
                matrix[i][0] = matrix[0][j] = 0
    for i in range(1, m):
        for j in range(1, n):
            if matrix[i][0] == 0 or matrix[0][j] == 0:
                matrix[i][j] = 0
    if row0:
        for j in range(n):
            matrix[0][j] = 0
    if col0:
        for i in range(m):
            matrix[i][0] = 0
    return matrix
```

### Q40. Intermediate

**Rotate Image**

Commonly reported in interviews at Amazon, Microsoft.

Rotate an n by n matrix 90 degrees clockwise, in place.

Example: `[[1, 2], [3, 4]]` becomes `[[3, 1], [4, 2]]`.

**Answer:**

Transpose across the main diagonal, then reverse each row. Or rotate four edges in cycles.

**Complexity:** Time O(n^2), space O(1).

```python
def rotate(matrix):
    n = len(matrix)
    for i in range(n):
        for j in range(i + 1, n):
            matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
    for row in matrix:
        row.reverse()
    return matrix
```

### Q41. Intermediate

**Spiral Matrix**

Commonly reported in interviews at Amazon, Microsoft, Apple.

Return the elements of a matrix in clockwise spiral order.

Example: `[[1, 2, 3], [4, 5, 6], [7, 8, 9]]` returns `[1, 2, 3, 6, 9, 8, 7, 4, 5]`.

**Answer:**

Maintain four bounds and walk right, down, left, up, shrinking the bounds after each side. Stop when the bounds cross.

**Complexity:** Time O(m * n), space O(1) extra besides the answer.

```python
def spiral(matrix):
    out = []
    top, bot = 0, len(matrix) - 1
    left, right = 0, len(matrix[0]) - 1
    while top <= bot and left <= right:
        for j in range(left, right + 1):
            out.append(matrix[top][j])
        top += 1
        for i in range(top, bot + 1):
            out.append(matrix[i][right])
        right -= 1
        if top <= bot:
            for j in range(right, left - 1, -1):
                out.append(matrix[bot][j])
            bot -= 1
        if left <= right:
            for i in range(bot, top - 1, -1):
                out.append(matrix[i][left])
            left += 1
    return out
```

### Q42. Intermediate

**Number of Islands**

Commonly reported in interviews at Amazon, Google, Microsoft.

A grid of `'1'` land and `'0'` water. Return how many 4-connected islands there are.

Example: One island of adjacent ones returns 1. Diagonal neighbors do not connect.

**Answer:**

For every unvisited land cell, run DFS or BFS and sink the island (mark cells visited) so it is counted once.

**Complexity:** Time O(m * n), space O(m * n) in the worst case for the recursion or queue.

```python
def num_islands(grid):
    if not grid:
        return 0
    m, n = len(grid), len(grid[0])
    def sink(i, j):
        if not (0 <= i < m and 0 <= j < n) or grid[i][j] != '1':
            return
        grid[i][j] = '0'
        sink(i + 1, j); sink(i - 1, j); sink(i, j + 1); sink(i, j - 1)
    count = 0
    for i in range(m):
        for j in range(n):
            if grid[i][j] == '1':
                sink(i, j)
                count += 1
    return count
```

### Q43. Intermediate

**Clone Graph**

Commonly reported in interviews at Amazon, Facebook.

Deep-copy an undirected graph. Each node has a value and a list of neighbors. The graph may contain cycles.

Example: A triangle of nodes 1, 2, 3 returns a distinct triangle with the same links.

**Answer:**

DFS or BFS with a map from original node to its clone. Create the clone the first time you see a node, then copy edges.

**Complexity:** Time O(V + E), space O(V).

```python
def clone_graph(node):
    if not node:
        return None
    clones = {}
    def dfs(n):
        if n in clones:
            return clones[n]
        copy = type(n)(n.val)
        clones[n] = copy
        copy.neighbors = [dfs(x) for x in n.neighbors]
        return copy
    return dfs(node)
```

### Q44. Intermediate

**Course Schedule**

Commonly reported in interviews at Amazon, Google, Uber.

There are `n` courses labeled 0..n-1 and a list of prerequisite pairs `[course, prereq]`. Return true when you can finish every course.

Example: `n = 2`, prerequisites `[[1, 0]]` is true. `[[1, 0], [0, 1]]` is false.

**Answer:**

This is cycle detection on a directed graph. Kahn's algorithm (indegree plus a queue) or DFS with three colors both work. Kahn's algorithm finishes every node exactly when the graph is a DAG.

**Complexity:** Time O(V + E), space O(V + E).

```python
def can_finish(n, prereqs):
    from collections import defaultdict, deque
    g = defaultdict(list)
    indeg = [0] * n
    for course, pre in prereqs:
        g[pre].append(course)
        indeg[course] += 1
    q = deque(i for i in range(n) if indeg[i] == 0)
    seen = 0
    while q:
        u = q.popleft()
        seen += 1
        for v in g[u]:
            indeg[v] -= 1
            if indeg[v] == 0:
                q.append(v)
    return seen == n
```

### Q45. Intermediate

**Course Schedule II**

Commonly reported in interviews at Amazon, Google.

Return one valid order in which to take `n` courses, or an empty list if the prerequisites contain a cycle.

Example: `n = 2`, `[[1, 0]]` returns `[0, 1]`.

**Answer:**

Kahn's algorithm records nodes as their indegree hits zero. If the recorded order is shorter than `n`, there is a cycle.

**Complexity:** Time O(V + E), space O(V + E).

```python
def order(n, prereqs):
    from collections import defaultdict, deque
    g = defaultdict(list)
    indeg = [0] * n
    for course, pre in prereqs:
        g[pre].append(course)
        indeg[course] += 1
    q = deque(i for i in range(n) if indeg[i] == 0)
    out = []
    while q:
        u = q.popleft()
        out.append(u)
        for v in g[u]:
            indeg[v] -= 1
            if indeg[v] == 0:
                q.append(v)
    return out if len(out) == n else []
```

### Q46. Intermediate

**Coin Change**

Commonly reported in interviews at Amazon, Goldman Sachs, Uber.

Return the fewest coins that sum to `amount`, or -1 if it is impossible. You have infinite supply of each denomination.

Example: Coins `[1, 2, 5]`, amount `11` returns `3` (5+5+1).

**Answer:**

Unbounded knapsack. `dp[x]` is the fewest coins that make `x`. Transition: `dp[x] = min(dp[x], dp[x - coin] + 1)`.

**Complexity:** Time O(amount * coins), space O(amount).

```python
def coin_change(coins, amount):
    dp = [0] + [amount + 1] * amount
    for x in range(1, amount + 1):
        for c in coins:
            if c <= x:
                dp[x] = min(dp[x], dp[x - c] + 1)
    return dp[amount] if dp[amount] <= amount else -1
```

### Q47. Intermediate

**House Robber**

Commonly reported in interviews at Amazon, Google.

Houses in a line hold non-negative money. You cannot rob two adjacent houses. Return the maximum you can rob.

Example: `[2, 7, 9, 3, 1]` returns `12` (2+9+1).

**Answer:**

`dp[i] = max(dp[i-1], dp[i-2] + nums[i])`. Roll two variables.

**Complexity:** Time O(n), space O(1).

```python
def rob(nums):
    prev = cur = 0
    for n in nums:
        prev, cur = cur, max(cur, prev + n)
    return cur
```

### Q48. Intermediate

**House Robber II**

Commonly reported in interviews at Amazon.

Houses form a circle, so the first and last are adjacent. Return the maximum you can rob.

Example: `[2, 3, 2]` returns `3`.

**Answer:**

Run the linear robber on `nums[:-1]` and on `nums[1:]`, and take the max. An empty or single-house input is a special case.

**Complexity:** Time O(n), space O(1).

```python
def rob_circle(nums):
    def linear(a):
        prev = cur = 0
        for n in a:
            prev, cur = cur, max(cur, prev + n)
        return cur
    if not nums:
        return 0
    if len(nums) == 1:
        return nums[0]
    return max(linear(nums[:-1]), linear(nums[1:]))
```

### Q49. Intermediate

**Jump Game**

Commonly reported in interviews at Amazon, Microsoft.

Each index holds how far you may jump forward from there. Return true when you can reach the last index starting from index 0.

Example: `[2, 3, 1, 1, 4]` is true. `[3, 2, 1, 0, 4]` is false.

**Answer:**

Track the farthest index reachable so far. If the scan index ever passes that farthest index, you are stuck.

**Complexity:** Time O(n), space O(1).

```python
def can_jump(nums):
    far = 0
    for i, n in enumerate(nums):
        if i > far:
            return False
        far = max(far, i + n)
    return True
```

### Q50. Intermediate

**Jump Game II**

Commonly reported in interviews at Amazon, Google.

Return the minimum number of jumps to reach the last index. A solution always exists.

Example: `[2, 3, 1, 1, 4]` returns `2`.

**Answer:**

BFS layers over the array. Inside the current jump's reach, find the farthest index the next jump can cover. Each layer is one jump.

**Complexity:** Time O(n), space O(1).

```python
def jump(nums):
    jumps = end = far = 0
    for i in range(len(nums) - 1):
        far = max(far, i + nums[i])
        if i == end:
            jumps += 1
            end = far
    return jumps
```

### Q51. Intermediate

**Unique Paths**

Commonly reported in interviews at Google, Amazon.

An m by n grid. You start at the top left and may only move right or down. Return how many paths reach the bottom right.

Example: `m = 3, n = 7` returns `28`.

**Answer:**

DP: each cell is the sum of the cell above and the cell to the left. The first row and column are all 1s. Combinatorics `C(m+n-2, m-1)` is the closed form.

**Complexity:** Time O(m * n), space O(n) with a rolling row.

```python
def unique_paths(m, n):
    row = [1] * n
    for _ in range(1, m):
        for j in range(1, n):
            row[j] += row[j - 1]
    return row[-1]
```

### Q52. Intermediate

**Minimum Path Sum**

Commonly reported in interviews at Amazon, Google.

A grid of non-negative numbers. Move only right or down. Return the path from top left to bottom right with the smallest sum.

Example: `[[1, 3, 1], [1, 5, 1], [4, 2, 1]]` returns `7`.

**Answer:**

DP in place or on a row: `dp[i][j] = grid[i][j] + min(from above, from left)`.

**Complexity:** Time O(m * n), space O(1) extra if you overwrite the grid, or O(n) with a row.

```python
def min_path(grid):
    m, n = len(grid), len(grid[0])
    for j in range(1, n):
        grid[0][j] += grid[0][j - 1]
    for i in range(1, m):
        grid[i][0] += grid[i - 1][0]
        for j in range(1, n):
            grid[i][j] += min(grid[i - 1][j], grid[i][j - 1])
    return grid[-1][-1]
```

### Q53. Intermediate

**Climbing Stairs with Cost**

Commonly reported in interviews at Amazon.

Paying `cost[i]` lets you climb one or two steps from step `i`. You may start at step 0 or step 1. Return the minimum cost to reach the top, which is just past the last step.

Example: `[10, 15, 20]` returns `15`.

**Answer:**

`dp[i]` is the min cost to reach step `i` before paying. The answer is the min of arriving from the last step or the one before it.

**Complexity:** Time O(n), space O(1).

```python
def min_cost_climbing(cost):
    a = b = 0
    for c in cost:
        a, b = b, min(a, b) + c
    return min(a, b)
```

### Q54. Intermediate

**Longest Common Subsequence**

Commonly reported in interviews at Amazon, Google, Goldman Sachs.

Return the length of the longest subsequence common to two strings. A subsequence need not be contiguous.

Example: `abcde` and `ace` returns `3`.

**Answer:**

DP: if characters match, `1 + diagonal`, otherwise the max of the cell above and the cell to the left.

**Complexity:** Time O(n * m), space O(min(n, m)) with a rolling row.

```python
def lcs(a, b):
    if len(a) < len(b):
        a, b = b, a
    prev = [0] * (len(b) + 1)
    for i in range(1, len(a) + 1):
        cur = [0]
        for j in range(1, len(b) + 1):
            if a[i - 1] == b[j - 1]:
                cur.append(prev[j - 1] + 1)
            else:
                cur.append(max(prev[j], cur[-1]))
        prev = cur
    return prev[-1]
```

### Q55. Intermediate

**Longest Increasing Subsequence**

Commonly reported in interviews at Amazon, Microsoft, Google.

Return the length of the longest strictly increasing subsequence.

Example: `[10, 9, 2, 5, 3, 7, 101, 18]` returns `4`.

**Answer:**

Patience sorting: keep the smallest tail of all increasing subsequences of each length. Replace with binary search (`bisect_left`). The number of tails is the length. This does not reconstruct one subsequence unless you store predecessors.

**Complexity:** Time O(n log n), space O(n).

```python
def lis(nums):
    import bisect
    tails = []
    for n in nums:
        i = bisect.bisect_left(tails, n)
        if i == len(tails):
            tails.append(n)
        else:
            tails[i] = n
    return len(tails)
```

### Q56. Intermediate

**Word Break**

Commonly reported in interviews at Amazon, Facebook, Google.

Return true when a string can be segmented into a space-separated sequence of dictionary words. Words may be reused.

Example: `leetcode` with dictionary `['leet', 'code']` is true.

**Answer:**

`dp[i]` means `s[:i]` can be segmented. For each end, try every word that matches the suffix and whose start is already reachable.

**Complexity:** Time O(n^2 * w) naively, better with a trie. Space O(n).

```python
def word_break(s, words):
    words = set(words)
    dp = [True] + [False] * len(s)
    for i in range(1, len(s) + 1):
        for j in range(i):
            if dp[j] and s[j:i] in words:
                dp[i] = True
                break
    return dp[-1]
```

### Q57. Intermediate

**Decode Ways**

Commonly reported in interviews at Amazon, Facebook, Google.

A string of digits encodes letters: `1` is A through `26` is Z. Return how many ways the string can be decoded. `0` alone is invalid.

Example: `226` returns `3`: BZ, VF, BBF.

**Answer:**

Fibonacci-like DP. A single digit 1-9 extends `dp[i-1]`. A two-digit number from 10 to 26 also extends `dp[i-2]`.

**Complexity:** Time O(n), space O(1).

```python
def num_decodings(s):
    if s[0] == '0':
        return 0
    a, b = 1, 1
    for i in range(1, len(s)):
        cur = 0
        if s[i] != '0':
            cur += b
        if 10 <= int(s[i - 1:i + 1]) <= 26:
            cur += a
        a, b = b, cur
    return b
```

### Q58. Intermediate

**Combination Sum**

Commonly reported in interviews at Amazon, Uber.

Return all unique combinations of candidates that sum to `target`. The same number may be chosen more than once, and the output must not contain duplicate combinations.

Example: Candidates `[2, 3, 6, 7]`, target `7` returns `[[2, 2, 3], [7]]`.

**Answer:**

Backtracking. At each step, either reuse the current candidate or move to the next. Sorting is optional when candidates are unique.

**Complexity:** Time exponential in the target. Space O(target / min(candidates)) for the recursion.

```python
def combination_sum(candidates, target):
    out = []
    def bt(start, remain, path):
        if remain == 0:
            out.append(path[:])
            return
        for i in range(start, len(candidates)):
            c = candidates[i]
            if c > remain:
                continue
            path.append(c)
            bt(i, remain - c, path)
            path.pop()
    bt(0, target, [])
    return out
```

### Q59. Intermediate

**Subsets**

Commonly reported in interviews at Amazon, Facebook, Google.

Return every subset of a list of distinct integers.

Example: `[1, 2]` returns `[[], [1], [2], [1, 2]]` in any order.

**Answer:**

For each number, the new subsets are the old ones plus that number. Cascading doubling builds the power set in O(n * 2^n).

**Complexity:** Time O(n * 2^n), space O(n * 2^n) for the answer.

```python
def subsets(nums):
    out = [[]]
    for n in nums:
        out += [cur + [n] for cur in out]
    return out
```

### Q60. Intermediate

**Permutations**

Commonly reported in interviews at Amazon, Microsoft, LinkedIn.

Return all permutations of a list of distinct integers.

Example: `[1, 2]` returns `[[1, 2], [2, 1]]`.

**Answer:**

Backtracking with an in-place swap, or recursion that picks each unused element. There are n! results.

**Complexity:** Time O(n * n!), space O(n) extra besides the answer.

```python
def permute(nums):
    out = []
    def bt(path, rest):
        if not rest:
            out.append(path[:])
            return
        for i, n in enumerate(rest):
            bt(path + [n], rest[:i] + rest[i + 1:])
    bt([], nums)
    return out
```

### Q61. Intermediate

**Letter Combinations of a Phone Number**

Commonly reported in interviews at Amazon, Uber.

A digit string uses the phone mapping (`2` is abc, `3` is def, and so on through `9`). Return every possible letter string.

Example: `23` returns the 9 strings from `ad` through `cf`.

**Answer:**

Backtracking or BFS. Each digit multiplies the current set of prefixes by its letters.

**Complexity:** Time O(4^n * n), space O(4^n * n) for the answer.

```python
def letter_combinations(digits):
    if not digits:
        return []
    pad = {'2': 'abc', '3': 'def', '4': 'ghi', '5': 'jkl', '6': 'mno', '7': 'pqrs', '8': 'tuv', '9': 'wxyz'}
    out = ['']
    for d in digits:
        out = [p + ch for p in out for ch in pad[d]]
    return out
```

### Q62. Intermediate

**Generate Parentheses**

Commonly reported in interviews at Amazon, Google, Microsoft.

Return every string of `n` pairs of parentheses that is correctly matched.

Example: `n = 2` returns `['(())', '()()']`.

**Answer:**

Backtracking. You may add `(` when opens remain, and `)` when it would not exceed the opens already placed.

**Complexity:** Time proportional to the Catalan number. Space O(n) for the recursion besides the answer.

```python
def generate_parentheses(n):
    out = []
    def bt(path, opened, closed):
        if len(path) == 2 * n:
            out.append(''.join(path))
            return
        if opened < n:
            path.append('(')
            bt(path, opened + 1, closed)
            path.pop()
        if closed < opened:
            path.append(')')
            bt(path, opened, closed + 1)
            path.pop()
    bt([], 0, 0)
    return out
```

### Q63. Intermediate

**Top K Frequent Elements**

Commonly reported in interviews at Amazon, Facebook, Uber.

Return the `k` most frequent values in any order.

Example: `[1, 1, 1, 2, 2, 3]`, `k = 2` returns `[1, 2]`.

**Answer:**

Count, then use a heap of size k or bucket-sort by frequency. Bucket sort is O(n) because frequencies are at most n.

**Complexity:** Time O(n) with buckets, or O(n log k) with a heap. Space O(n).

```python
def top_k(nums, k):
    from collections import Counter
    buckets = [[] for _ in range(len(nums) + 1)]
    for val, freq in Counter(nums).items():
        buckets[freq].append(val)
    out = []
    for freq in range(len(buckets) - 1, 0, -1):
        out.extend(buckets[freq])
        if len(out) >= k:
            return out[:k]
    return out
```

### Q64. Intermediate

**Kth Largest Element**

Commonly reported in interviews at Amazon, Facebook, LinkedIn.

Return the kth largest element of an unsorted list. It is the kth item in sorted order, not the kth distinct item.

Example: `[3, 2, 1, 5, 6, 4]`, `k = 2` returns `5`.

**Answer:**

Quickselect averages O(n). A min-heap of size k is O(n log k) and simpler to write correctly under time pressure. Python's `heapq.nlargest` is that idea.

**Complexity:** Average O(n) with quickselect. Worst case O(n^2) unless you randomize the pivot. Heap is O(n log k).

```python
def kth_largest(nums, k):
    import heapq
    return heapq.nlargest(k, nums)[-1]
```

### Q65. Intermediate

**Find Minimum in Rotated Sorted Array**

Commonly reported in interviews at Amazon, Microsoft.

A sorted array of distinct values was rotated. Return the minimum.

Example: `[3, 4, 5, 1, 2]` returns `1`.

**Answer:**

Binary search. If the middle is greater than the right end, the minimum is to the right of mid. Otherwise it is at mid or to the left.

**Complexity:** Time O(log n), space O(1).

```python
def find_min(nums):
    lo, hi = 0, len(nums) - 1
    while lo < hi:
        mid = (lo + hi) // 2
        if nums[mid] > nums[hi]:
            lo = mid + 1
        else:
            hi = mid
    return nums[lo]
```

### Q66. Intermediate

**Search in Rotated Sorted Array**

Commonly reported in interviews at Amazon, Facebook, Microsoft.

A sorted array of distinct values was rotated. Return the index of `target`, or -1.

Example: `[4, 5, 6, 7, 0, 1, 2]`, target `0` returns `4`.

**Answer:**

Binary search. One half is always sorted. If the target lies inside the sorted half, search there. Otherwise search the other half.

**Complexity:** Time O(log n), space O(1).

```python
def search_rotated(nums, target):
    lo, hi = 0, len(nums) - 1
    while lo <= hi:
        mid = (lo + hi) // 2
        if nums[mid] == target:
            return mid
        if nums[lo] <= nums[mid]:
            if nums[lo] <= target < nums[mid]:
                hi = mid - 1
            else:
                lo = mid + 1
        else:
            if nums[mid] < target <= nums[hi]:
                lo = mid + 1
            else:
                hi = mid - 1
    return -1
```

### Q67. Intermediate

**Validate Binary Search Tree**

Commonly reported in interviews at Amazon, Microsoft, Facebook.

Return true when a binary tree is a BST. Every node on the left is strictly less than the node, and every node on the right is strictly greater. Duplicates are not allowed.

Example: A tree `2 / 1,3` is true. A tree `5 / 1,4` with 4 having left child 3 is false, because 3 is in the right subtree of 5.

**Answer:**

Pass a valid `(low, high)` window down the recursion. Comparing a node only with its parent is not enough.

**Complexity:** Time O(n), space O(h).

```python
def is_bst(root):
    def ok(node, low, high):
        if not node:
            return True
        if not low < node.val < high:
            return False
        return ok(node.left, low, node.val) and ok(node.right, node.val, high)
    return ok(root, float('-inf'), float('inf'))
```

### Q68. Intermediate

**Kth Smallest in a BST**

Commonly reported in interviews at Amazon, Google.

Return the kth smallest value in a BST. `k` is 1-based.

Example: An inorder walk of a BST is sorted, so the 1st smallest is the leftmost node.

**Answer:**

Iterative inorder, stopping after k pops. If the node count is available on each subtree, you can walk in O(h).

**Complexity:** Time O(h + k), space O(h).

```python
def kth_smallest(root, k):
    stack = []
    cur = root
    while cur or stack:
        while cur:
            stack.append(cur)
            cur = cur.left
        cur = stack.pop()
        k -= 1
        if k == 0:
            return cur.val
        cur = cur.right
```

### Q69. Intermediate

**Lowest Common Ancestor of a Binary Tree**

Commonly reported in interviews at Amazon, Facebook, Microsoft.

Given two nodes that exist in a binary tree, return their lowest common ancestor.

Example: In a tree rooted at 3 with children 5 and 1, the LCA of 5 and 1 is 3.

**Answer:**

If the current node is either target, return it. Otherwise recurse both sides. If both sides return a node, the current node is the LCA. If only one side does, pass that node up.

**Complexity:** Time O(n), space O(h).

```python
def lca(root, p, q):
    if not root or root is p or root is q:
        return root
    left = lca(root.left, p, q)
    right = lca(root.right, p, q)
    if left and right:
        return root
    return left or right
```

### Q70. Intermediate

**Lowest Common Ancestor of a BST**

Commonly reported in interviews at Amazon, Microsoft.

Both nodes exist in a BST. Return their lowest common ancestor.

Example: If both values are smaller than the root, the LCA is in the left subtree.

**Answer:**

Walk down. The first node whose value sits between the two targets, inclusive, is the LCA.

**Complexity:** Time O(h), space O(1) iterative.

```python
def lca_bst(root, p, q):
    while root:
        if p.val < root.val and q.val < root.val:
            root = root.left
        elif p.val > root.val and q.val > root.val:
            root = root.right
        else:
            return root
```

### Q71. Intermediate

**Binary Tree Level Order Traversal**

Commonly reported in interviews at Amazon, Microsoft, Bloomberg.

Return the values of a binary tree level by level, left to right.

Example: Root 1 with children 2 and 3 returns `[[1], [2, 3]]`.

**Answer:**

BFS with a queue. Snapshot the queue length at the start of each level so the next level is not mixed in.

**Complexity:** Time O(n), space O(n).

```python
def level_order(root):
    from collections import deque
    if not root:
        return []
    out, q = [], deque([root])
    while q:
        level = []
        for _ in range(len(q)):
            node = q.popleft()
            level.append(node.val)
            if node.left:
                q.append(node.left)
            if node.right:
                q.append(node.right)
        out.append(level)
    return out
```

### Q72. Intermediate

**Binary Tree Right Side View**

Commonly reported in interviews at Amazon, Bloomberg.

Return the values visible if you stand on the right of the tree, top to bottom.

Example: A complete tree returns the right spine. A missing right child exposes the left child on that level.

**Answer:**

Level order, and keep the last node of each level. DFS that visits the right child first and records the first node at each depth also works.

**Complexity:** Time O(n), space O(n).

```python
def right_view(root):
    from collections import deque
    if not root:
        return []
    out, q = [], deque([root])
    while q:
        out.append(q[-1].val)
        for _ in range(len(q)):
            node = q.popleft()
            if node.left:
                q.append(node.left)
            if node.right:
                q.append(node.right)
    return out
```

### Q73. Intermediate

**Diameter of Binary Tree**

Commonly reported in interviews at Amazon, Google, Facebook.

Return the length of the longest path between any two nodes, measured in edges. The path need not pass through the root.

Example: A straight line of three nodes has diameter 2.

**Answer:**

At each node the best path through that node is `left height + right height`. The answer is the max of those. Return the height to the parent and keep the diameter in a closure.

**Complexity:** Time O(n), space O(h).

```python
def diameter(root):
    best = 0
    def height(node):
        nonlocal best
        if not node:
            return 0
        L, R = height(node.left), height(node.right)
        best = max(best, L + R)
        return 1 + max(L, R)
    height(root)
    return best
```

### Q74. Intermediate

**Balanced Binary Tree**

Commonly reported in interviews at Amazon, Microsoft.

Return true when the depths of the two subtrees of every node differ by at most 1.

Example: A complete tree is balanced. A long chain is not.

**Answer:**

Return the height, or a sentinel such as -1 when a subtree is already unbalanced. That avoids a second walk.

**Complexity:** Time O(n), space O(h).

```python
def is_balanced(root):
    def height(node):
        if not node:
            return 0
        L, R = height(node.left), height(node.right)
        if L < 0 or R < 0 or abs(L - R) > 1:
            return -1
        return 1 + max(L, R)
    return height(root) >= 0
```

### Q75. Intermediate

**Serialize and Deserialize Binary Tree**

Commonly reported in interviews at Amazon, Google, LinkedIn.

Design a way to turn a binary tree into a string and back, including structure. Empty children must be recorded.

Example: A root 1 with left 2 becomes a string that rebuilds that same shape.

**Answer:**

Preorder with null markers. Split the string and rebuild with an iterator. BFS with null markers also works.

**Complexity:** Time O(n), space O(n).

```python
def serialize(root):
    out = []
    def dfs(node):
        if not node:
            out.append('#')
            return
        out.append(str(node.val))
        dfs(node.left)
        dfs(node.right)
    dfs(root)
    return ','.join(out)

def deserialize(data):
    it = iter(data.split(','))
    def dfs():
        token = next(it)
        if token == '#':
            return None
        node = _T(int(token))
        node.left = dfs()
        node.right = dfs()
        return node
    return dfs()

class _T:
    def __init__(self, val):
        self.val, self.left, self.right = val, None, None
```

### Q76. Intermediate

**Construct Tree from Preorder and Inorder**

Commonly reported in interviews at Amazon, Microsoft.

Values are distinct. Build the binary tree from its preorder and inorder lists.

Example: Preorder `[3, 9, 20, 15, 7]`, inorder `[9, 3, 15, 20, 7]` has root 3, left child 9, right subtree rooted at 20.

**Answer:**

The first preorder value is the root. Find it in inorder to split left and right sizes. Recurse. An index map makes the split O(1).

**Complexity:** Time O(n), space O(n).

```python
def build_tree(preorder, inorder):
    idx = {v: i for i, v in enumerate(inorder)}
    pre_i = 0
    def build(lo, hi):
        nonlocal pre_i
        if lo > hi:
            return None
        val = preorder[pre_i]
        pre_i += 1
        node = _T(val)
        mid = idx[val]
        node.left = build(lo, mid - 1)
        node.right = build(mid + 1, hi)
        return node
    return build(0, len(inorder) - 1)

class _T:
    def __init__(self, val):
        self.val, self.left, self.right = val, None, None
```

### Q77. Intermediate

**Binary Tree Maximum Path Sum**

Commonly reported in interviews at Amazon, Google, Facebook.

A path is any connected sequence of nodes. Return the maximum sum of node values along any path. Values may be negative.

Example: A tree `-10 / 9,20` with 20 having children 15 and 7 returns `42`.

**Answer:**

At each node, the best gain you can offer a parent is `value + max(0, left gain, right gain)`. The best path through the node also adds both sides when they are positive. Track that global best.

**Complexity:** Time O(n), space O(h).

```python
def max_path_sum(root):
    best = root.val
    def gain(node):
        nonlocal best
        if not node:
            return 0
        L = max(0, gain(node.left))
        R = max(0, gain(node.right))
        best = max(best, node.val + L + R)
        return node.val + max(L, R)
    gain(root)
    return best
```

### Q78. Intermediate

**Subtree of Another Tree**

Commonly reported in interviews at Amazon, Facebook.

Return true when `sub` is identical to some subtree of `root`, including `root` itself.

Example: A single matching node is true.

**Answer:**

For every node, run the same-tree check. A serialization of both trees with sentinels can also be searched as a string.

**Complexity:** Time O(n * m), space O(h).

```python
def is_subtree(root, sub):
    def same(a, b):
        if not a or not b:
            return a is b
        return a.val == b.val and same(a.left, b.left) and same(a.right, b.right)
    def walk(node):
        if not node:
            return False
        return same(node, sub) or walk(node.left) or walk(node.right)
    return walk(root)
```

### Q79. Intermediate

**LRU Cache**

Commonly reported in interviews at Amazon, Google, Microsoft, Facebook.

Design a cache with `get` and `put` in average O(1). Capacity is fixed. The least recently used key is evicted.

Example: Capacity 2. Put 1, put 2, get 1, put 3. Key 2 is evicted.

**Answer:**

Hash map plus a doubly linked list. The map points at list nodes. Move a node to the front on access. Evict the tail.

**Complexity:** Each operation average O(1). Space O(capacity).

```python
class LRU:
    def __init__(self, cap):
        from collections import OrderedDict
        self.cap = cap
        self.data = OrderedDict()
    def get(self, key):
        if key not in self.data:
            return -1
        self.data.move_to_end(key)
        return self.data[key]
    def put(self, key, value):
        if key in self.data:
            self.data.move_to_end(key)
        self.data[key] = value
        if len(self.data) > self.cap:
            self.data.popitem(last=False)
```

### Q80. Advanced

**Trapping Rain Water**

Commonly reported in interviews at Amazon, Google, Goldman Sachs.

Elevation bars of width 1 stand in a row. Return how many units of water they trap after raining.

Example: `[0, 1, 0, 2, 1, 0, 1, 3, 2, 1, 2, 1]` returns `6`.

**Answer:**

Two pointers. Water at a position is `min(max_left, max_right) - height`. Move the side whose max is smaller, because that max is the limiting wall.

**Complexity:** Time O(n), space O(1).

```python
def trap(height):
    lo, hi = 0, len(height) - 1
    left_max = right_max = water = 0
    while lo < hi:
        if height[lo] < height[hi]:
            left_max = max(left_max, height[lo])
            water += left_max - height[lo]
            lo += 1
        else:
            right_max = max(right_max, height[hi])
            water += right_max - height[hi]
            hi -= 1
    return water
```

### Q81. Advanced

**Sliding Window Maximum**

Commonly reported in interviews at Amazon, Google.

Return the maximum of every contiguous window of size `k`.

Example: `[1, 3, -1, -3, 5, 3, 6, 7]`, `k = 3` returns `[3, 3, 5, 5, 6, 7]`.

**Answer:**

A deque stores indices in decreasing value order. Drop indices that fall out of the window from the front, and drop smaller values from the back before pushing.

**Complexity:** Time O(n), space O(k).

```python
def max_sliding(nums, k):
    from collections import deque
    dq, out = deque(), []
    for i, n in enumerate(nums):
        while dq and dq[0] <= i - k:
            dq.popleft()
        while dq and nums[dq[-1]] <= n:
            dq.pop()
        dq.append(i)
        if i >= k - 1:
            out.append(nums[dq[0]])
    return out
```

### Q82. Advanced

**Minimum Window Substring**

Commonly reported in interviews at Facebook, Amazon, Google.

Return the shortest substring of `s` that contains every character of `t`, including duplicates. If none exists, return an empty string.

Example: `s = 'ADOBECODEBANC'`, `t = 'ABC'` returns `'BANC'`.

**Answer:**

Sliding window with required counts. Expand the right edge until the window is valid, then shrink the left edge while it stays valid, recording the best window.

**Complexity:** Time O(n + m), space O(1) for a fixed alphabet.

```python
def min_window(s, t):
    from collections import Counter
    need = Counter(t)
    missing = len(t)
    best = ''
    left = 0
    for right, ch in enumerate(s):
        if need[ch] > 0:
            missing -= 1
        need[ch] -= 1
        while missing == 0:
            if not best or right - left + 1 < len(best):
                best = s[left:right + 1]
            need[s[left]] += 1
            if need[s[left]] > 0:
                missing += 1
            left += 1
    return best
```

### Q83. Advanced

**Longest Repeating Character Replacement**

Commonly reported in interviews at Google, Amazon.

You may replace at most `k` characters. Return the length of the longest substring that can be made of one repeated character.

Example: `AABABBA`, `k = 1` returns `4`.

**Answer:**

Sliding window. The window is valid while `length - max_frequency <= k`. You do not have to shrink `max_frequency` perfectly on every pop; only expand the best length when the window is valid.

**Complexity:** Time O(n), space O(1) for a fixed alphabet.

```python
def character_replacement(s, k):
    from collections import Counter
    counts = Counter()
    left = best = most = 0
    for right, ch in enumerate(s):
        counts[ch] += 1
        most = max(most, counts[ch])
        while right - left + 1 - most > k:
            counts[s[left]] -= 1
            left += 1
        best = max(best, right - left + 1)
    return best
```

### Q84. Advanced

**Find All Anagrams in a String**

Commonly reported in interviews at Amazon, Facebook.

Return the start indices of every substring of `s` that is an anagram of `p`.

Example: `s = 'cbaebabacd'`, `p = 'abc'` returns `[0, 6]`.

**Answer:**

Fixed-size sliding window of length `len(p)` with character counts. Compare counts, or keep a `matched` counter so each step is O(1).

**Complexity:** Time O(n), space O(1) for a fixed alphabet.

```python
def find_anagrams(s, p):
    from collections import Counter
    if len(p) > len(s):
        return []
    need, window = Counter(p), Counter(s[:len(p)])
    out = [0] if need == window else []
    for i in range(len(p), len(s)):
        window[s[i]] += 1
        left = s[i - len(p)]
        window[left] -= 1
        if window[left] == 0:
            del window[left]
        if window == need:
            out.append(i - len(p) + 1)
    return out
```

### Q85. Advanced

**Subarray Sum Equals K**

Commonly reported in interviews at Facebook, Google, Amazon.

Return how many contiguous subarrays sum to `k`. Values may be negative.

Example: `[1, 1, 1]`, `k = 2` returns `2`.

**Answer:**

Prefix sums. A map counts how often each prefix has occurred. At prefix `sum`, add the count of `sum - k`.

**Complexity:** Time O(n), space O(n).

```python
def subarray_sum(nums, k):
    from collections import defaultdict
    seen = defaultdict(int)
    seen[0] = 1
    total = ans = 0
    for n in nums:
        total += n
        ans += seen[total - k]
        seen[total] += 1
    return ans
```

### Q86. Advanced

**Longest Consecutive Sequence**

Commonly reported in interviews at Google, Facebook.

Return the length of the longest run of consecutive integers. The values are unsorted, and the expected time is O(n).

Example: `[100, 4, 200, 1, 3, 2]` returns `4` because of `1, 2, 3, 4`.

**Answer:**

Put the values in a set. Only start a walk from a value whose predecessor is absent, then count upward.

**Complexity:** Time O(n), space O(n).

```python
def longest_consecutive(nums):
    s = set(nums)
    best = 0
    for n in s:
        if n - 1 in s:
            continue
        length = 1
        while n + length in s:
            length += 1
        best = max(best, length)
    return best
```

### Q87. Advanced

**First Missing Positive**

Commonly reported in interviews at Amazon, Microsoft.

Return the smallest missing positive integer. Expected time is O(n) and extra space is O(1).

Example: `[3, 4, -1, 1]` returns `2`.

**Answer:**

Place each value `x` into index `x - 1` when `x` is in `1..n`, by swapping. Then scan for the first index whose value is not `index + 1`.

**Complexity:** Time O(n), space O(1).

```python
def first_missing_positive(nums):
    n = len(nums)
    for i in range(n):
        while 1 <= nums[i] <= n and nums[nums[i] - 1] != nums[i]:
            j = nums[i] - 1
            nums[i], nums[j] = nums[j], nums[i]
    for i, v in enumerate(nums):
        if v != i + 1:
            return i + 1
    return n + 1
```

### Q88. Advanced

**Merge K Sorted Lists**

Commonly reported in interviews at Amazon, Google, Facebook.

Merge `k` sorted linked lists into one sorted list.

Example: Lists `[1, 4, 5]`, `[1, 3, 4]`, `[2, 6]` become `1, 1, 2, 3, 4, 4, 5, 6`.

**Answer:**

A min-heap of the current head of each list. Push the next node whenever you pop one. Divide and conquer merging is also O(N log k).

**Complexity:** Time O(N log k), space O(k), where N is the total number of nodes.

```python
def merge_k(lists):
    import heapq
    heap = []
    for i, node in enumerate(lists):
        if node:
            heapq.heappush(heap, (node.val, i, node))
    dummy = tail = _Node(0)
    while heap:
        _, i, node = heapq.heappop(heap)
        tail.next = node
        tail = node
        if node.next:
            heapq.heappush(heap, (node.next.val, i, node.next))
    return dummy.next

class _Node:
    def __init__(self, val, next=None):
        self.val, self.next = val, next
```

### Q89. Advanced

**Find Median from Data Stream**

Commonly reported in interviews at Google, Amazon.

Support adding a number and finding the median of all numbers added so far.

Example: Add 1, then 2. The median becomes 1.5.

**Answer:**

Two heaps. A max-heap holds the smaller half and a min-heap holds the larger half. Rebalance so their sizes differ by at most 1.

**Complexity:** Add is O(log n). Median is O(1). Space O(n).

```python
class MedianFinder:
    def __init__(self):
        import heapq
        self.heapq = heapq
        self.low = []
        self.high = []
    def add(self, n):
        hq = self.heapq
        hq.heappush(self.low, -n)
        hq.heappush(self.high, -hq.heappop(self.low))
        if len(self.high) > len(self.low):
            hq.heappush(self.low, -hq.heappop(self.high))
    def median(self):
        if len(self.low) > len(self.high):
            return -self.low[0]
        return (-self.low[0] + self.high[0]) / 2
```

### Q90. Advanced

**Reverse Nodes in k-Group**

Commonly reported in interviews at Amazon, Microsoft.

Reverse every group of `k` nodes in a linked list. Leave a trailing group shorter than `k` unchanged.

Example: `1 -> 2 -> 3 -> 4 -> 5`, `k = 2` becomes `2 -> 1 -> 4 -> 3 -> 5`.

**Answer:**

Count k nodes. If they exist, reverse that segment and stitch it between the previous tail and the next group.

**Complexity:** Time O(n), space O(1).

```python
def reverse_k(head, k):
    def rev(start, k):
        prev, cur = None, start
        for _ in range(k):
            nxt = cur.next
            cur.next = prev
            prev, cur = cur, nxt
        return prev, start, cur
    dummy = _Node(0, head)
    group_prev = dummy
    while True:
        kth = group_prev
        for _ in range(k):
            kth = kth.next
            if not kth:
                return dummy.next
        new_head, new_tail, nxt = rev(group_prev.next, k)
        group_prev.next = new_head
        new_tail.next = nxt
        group_prev = new_tail

class _Node:
    def __init__(self, val, next=None):
        self.val, self.next = val, next
```

### Q91. Advanced

**Copy List with Random Pointer**

Commonly reported in interviews at Amazon, Microsoft, Bloomberg.

A linked list node has `next` and `random`. Return a deep copy.

Example: A two-node list where the first random pointer points at the second must copy both links.

**Answer:**

Interleave cloned nodes (`A -> A' -> B -> B'`), set random pointers, then split the lists. A hash map from original to clone is the simpler O(n) space version.

**Complexity:** Time O(n). The map version uses O(n) extra space. The interleave version uses O(1) extra space.

```python
def copy_random(head):
    clones = {}
    cur = head
    while cur:
        clones[cur] = _R(cur.val)
        cur = cur.next
    cur = head
    while cur:
        clones[cur].next = clones.get(cur.next)
        clones[cur].random = clones.get(cur.random)
        cur = cur.next
    return clones.get(head)

class _R:
    def __init__(self, val):
        self.val = val
        self.next = self.random = None
```

### Q92. Advanced

**Linked List Cycle II**

Commonly reported in interviews at Amazon, Microsoft.

Return the node where a cycle begins, or null if there is no cycle.

Example: A tail that points at the second node returns that second node.

**Answer:**

After tortoise and hare meet, reset one pointer to the head. Advance both one step. They meet at the entrance. The proof is that the distance from head to entrance equals the distance from the meeting point around to the entrance.

**Complexity:** Time O(n), space O(1).

```python
def detect_cycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow is fast:
            slow = head
            while slow is not fast:
                slow = slow.next
                fast = fast.next
            return slow
    return None
```

### Q93. Advanced

**Remove Nth Node From End**

Commonly reported in interviews at Amazon, Microsoft.

Remove the nth node from the end of a singly linked list and return the head. `n` is always valid.

Example: `1 -> 2 -> 3 -> 4 -> 5`, `n = 2` becomes `1 -> 2 -> 3 -> 5`.

**Answer:**

A fast pointer moves n steps ahead. Then both pointers move until fast reaches the end. The slow pointer sits just before the node to delete. A dummy head handles deleting the first node.

**Complexity:** Time O(n), space O(1).

```python
def remove_nth(head, n):
    dummy = _Node(0, head)
    fast = slow = dummy
    for _ in range(n + 1):
        fast = fast.next
    while fast:
        fast = fast.next
        slow = slow.next
    slow.next = slow.next.next
    return dummy.next

class _Node:
    def __init__(self, val, next=None):
        self.val, self.next = val, next
```

### Q94. Advanced

**Add Two Numbers**

Commonly reported in interviews at Amazon, Microsoft, Bloomberg.

Two non-negative integers are stored as linked lists of digits in reverse order. Return their sum in the same form.

Example: `2 -> 4 -> 3` plus `5 -> 6 -> 4` is `7 -> 0 -> 8`, meaning 342 + 465 = 807.

**Answer:**

Walk both lists, add digits plus carry, and append `total % 10`. Continue while either list or the carry remains.

**Complexity:** Time O(max(n, m)), space O(max(n, m)) for the answer.

```python
def add_two(a, b):
    dummy = tail = _Node(0)
    carry = 0
    while a or b or carry:
        total = carry
        if a:
            total += a.val
            a = a.next
        if b:
            total += b.val
            b = b.next
        carry, digit = divmod(total, 10)
        tail.next = _Node(digit)
        tail = tail.next
    return dummy.next

class _Node:
    def __init__(self, val, next=None):
        self.val, self.next = val, next
```

### Q95. Advanced

**Palindrome Linked List**

Commonly reported in interviews at Amazon, Facebook.

Return true when the values of a singly linked list form a palindrome. Aim for O(1) extra space.

Example: `1 -> 2 -> 2 -> 1` is true.

**Answer:**

Find the middle with slow and fast pointers, reverse the second half, compare, and optionally reverse it back.

**Complexity:** Time O(n), space O(1).

```python
def is_palindrome_list(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    prev = None
    while slow:
        nxt = slow.next
        slow.next = prev
        prev, slow = slow, nxt
    while prev:
        if head.val != prev.val:
            return False
        head, prev = head.next, prev.next
    return True
```

### Q96. Advanced

**Reorder List**

Commonly reported in interviews at Amazon, Facebook.

Reorder `L0 -> L1 -> ... -> Ln` into `L0 -> Ln -> L1 -> Ln-1 -> ...` in place.

Example: `1 -> 2 -> 3 -> 4` becomes `1 -> 4 -> 2 -> 3`.

**Answer:**

Find the middle, reverse the second half, then merge the two halves one node at a time.

**Complexity:** Time O(n), space O(1).

```python
def reorder(head):
    if not head:
        return
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    prev, cur = None, slow.next
    slow.next = None
    while cur:
        nxt = cur.next
        cur.next = prev
        prev, cur = cur, nxt
    a, b = head, prev
    while b:
        a.next, a = b, a.next
        b.next, b = a, b.next
```

### Q97. Advanced

**Edit Distance**

Commonly reported in interviews at Google, Amazon, Uber.

Return the minimum insertions, deletions, and replacements that turn string `a` into string `b`.

Example: `horse` to `ros` returns `3`.

**Answer:**

DP. If characters match, copy the diagonal. Otherwise `1 + min(insert, delete, replace)`.

**Complexity:** Time O(n * m), space O(min(n, m)) with a rolling row.

```python
def edit_distance(a, b):
    prev = list(range(len(b) + 1))
    for i, ca in enumerate(a, 1):
        cur = [i]
        for j, cb in enumerate(b, 1):
            if ca == cb:
                cur.append(prev[j - 1])
            else:
                cur.append(1 + min(prev[j], cur[-1], prev[j - 1]))
        prev = cur
    return prev[-1]
```

### Q98. Advanced

**Regular Expression Matching**

Commonly reported in interviews at Google, Facebook.

Implement `.` and `*`. A dot matches any single character. A star matches zero or more of the preceding element. The match must cover the whole string.

Example: `a*b` matches `b` and `aaab`. It does not match `a`.

**Answer:**

DP. `dp[i][j]` means `s[:i]` matches `p[:j]`. A star can consume nothing (`dp[i][j-2]`) or one more character when the current character matches (`dp[i-1][j]`).

**Complexity:** Time O(n * m), space O(n * m).

```python
def is_match(s, p):
    n, m = len(s), len(p)
    dp = [[False] * (m + 1) for _ in range(n + 1)]
    dp[0][0] = True
    for j in range(2, m + 1):
        if p[j - 1] == '*':
            dp[0][j] = dp[0][j - 2]
    for i in range(1, n + 1):
        for j in range(1, m + 1):
            if p[j - 1] == '*':
                dp[i][j] = dp[i][j - 2] or (dp[i - 1][j] and p[j - 2] in {s[i - 1], '.'})
            elif p[j - 1] in {s[i - 1], '.'}:
                dp[i][j] = dp[i - 1][j - 1]
    return dp[n][m]
```

### Q99. Advanced

**Wildcard Matching**

Commonly reported in interviews at Google, Facebook.

`?` matches one character and `*` matches any sequence, including empty. Match the whole string.

Example: `a*b` matches `axb`. `?` matches one character only.

**Answer:**

DP similar to regex, but `*` is a lone pattern character. It matches empty (`dp[i][j-1]`) or one more text character (`dp[i-1][j]`).

**Complexity:** Time O(n * m), space O(n * m).

```python
def is_wildcard(s, p):
    n, m = len(s), len(p)
    dp = [[False] * (m + 1) for _ in range(n + 1)]
    dp[0][0] = True
    for j in range(1, m + 1):
        dp[0][j] = dp[0][j - 1] and p[j - 1] == '*'
    for i in range(1, n + 1):
        for j in range(1, m + 1):
            if p[j - 1] == '*':
                dp[i][j] = dp[i][j - 1] or dp[i - 1][j]
            elif p[j - 1] in {s[i - 1], '?'}:
                dp[i][j] = dp[i - 1][j - 1]
    return dp[n][m]
```

### Q100. Advanced

**Longest Palindromic Substring**

Commonly reported in interviews at Amazon, Microsoft.

Return the longest palindromic substring. If several have the same length, any one is acceptable.

Example: `babad` returns `bab` or `aba`.

**Answer:**

Expand around each center. There are `2n - 1` centers because a palindrome can be odd or even length. Manacher's algorithm is the linear alternative.

**Complexity:** Time O(n^2), space O(1) besides the answer.

```python
def longest_palindrome(s):
    def expand(l, r):
        while l >= 0 and r < len(s) and s[l] == s[r]:
            l -= 1
            r += 1
        return s[l + 1:r]
    best = ''
    for i in range(len(s)):
        best = max(best, expand(i, i), expand(i, i + 1), key=len)
    return best
```

### Q101. Advanced

**Palindromic Substrings**

Commonly reported in interviews at Facebook, Amazon.

Count how many substrings are palindromes. Single letters count.

Example: `aaa` returns `6`.

**Answer:**

Expand around each of the `2n - 1` centers and count every successful expansion.

**Complexity:** Time O(n^2), space O(1).

```python
def count_palindromes(s):
    def expand(l, r):
        count = 0
        while l >= 0 and r < len(s) and s[l] == s[r]:
            count += 1
            l -= 1
            r += 1
        return count
    return sum(expand(i, i) + expand(i, i + 1) for i in range(len(s)))
```

### Q102. Advanced

**Partition Equal Subset Sum**

Commonly reported in interviews at Amazon, Facebook.

Return true when the list can be split into two subsets with the same sum.

Example: `[1, 5, 11, 5]` is true because `11` and `1+5+5` both sum to 11.

**Answer:**

The target is `total / 2`, so the total must be even. Then it is a 0/1 knapsack: can a subset sum to that target?

**Complexity:** Time O(n * sum), space O(sum).

```python
def can_partition(nums):
    total = sum(nums)
    if total % 2:
        return False
    target = total // 2
    dp = [True] + [False] * target
    for n in nums:
        for s in range(target, n - 1, -1):
            dp[s] = dp[s] or dp[s - n]
    return dp[target]
```

### Q103. Advanced

**Target Sum**

Commonly reported in interviews at Facebook, Google.

Add `+` or `-` before each integer so the expression equals `target`. Return how many ways.

Example: `[1, 1, 1, 1, 1]`, target `3` returns `5`.

**Answer:**

This reduces to counting subsets that sum to `(total + target) / 2`. A 0/1 knapsack count does it. DFS with memo is the same DP.

**Complexity:** Time O(n * sum), space O(sum).

```python
def find_target_sum(nums, target):
    total = sum(nums)
    if (total + target) % 2 or abs(target) > total:
        return 0
    goal = (total + target) // 2
    dp = [1] + [0] * goal
    for n in nums:
        for s in range(goal, n - 1, -1):
            dp[s] += dp[s - n]
    return dp[goal]
```

### Q104. Advanced

**Coin Change II**

Commonly reported in interviews at Amazon, Goldman Sachs.

Return the number of combinations that make `amount`. Order does not matter, so `1+2` and `2+1` are one combination. Coins may be reused.

Example: Coins `[1, 2, 5]`, amount `5` returns `4`.

**Answer:**

Unbounded knapsack over combinations. Iterate coins in the outer loop and amounts in the inner loop so each combination is counted once.

**Complexity:** Time O(amount * coins), space O(amount).

```python
def change(amount, coins):
    dp = [1] + [0] * amount
    for c in coins:
        for x in range(c, amount + 1):
            dp[x] += dp[x - c]
    return dp[amount]
```

### Q105. Advanced

**Maximal Square**

Commonly reported in interviews at Amazon, Google.

A binary matrix contains `'0'` and `'1'`. Return the area of the largest square of ones.

Example: A 2x2 block of ones has area 4.

**Answer:**

DP: the largest square ending at `(i, j)` is `1 + min(up, left, diagonal)` when the cell is 1.

**Complexity:** Time O(m * n), space O(n).

```python
def maximal_square(matrix):
    if not matrix:
        return 0
    m, n = len(matrix), len(matrix[0])
    prev = [0] * (n + 1)
    best = 0
    for i in range(1, m + 1):
        cur = [0] * (n + 1)
        for j in range(1, n + 1):
            if matrix[i - 1][j - 1] == '1':
                cur[j] = 1 + min(prev[j], cur[j - 1], prev[j - 1])
                best = max(best, cur[j])
        prev = cur
    return best * best
```

### Q106. Advanced

**Word Search**

Commonly reported in interviews at Amazon, Microsoft.

Return true when a word can be formed by adjacent letters on a board. A cell may not be reused in the same path. Adjacent means four directions.

Example: Board with `AB` / `CD` contains `AC` and does not contain `ABD` if D is not adjacent to B... `AB` is true along the first row.

**Answer:**

DFS from every cell that matches the first letter. Mark the cell visited, recurse, then unmark.

**Complexity:** Time O(m * n * 4^L), space O(L) for the recursion.

```python
def exist(board, word):
    m, n = len(board), len(board[0])
    def dfs(i, j, k):
        if k == len(word):
            return True
        if not (0 <= i < m and 0 <= j < n) or board[i][j] != word[k]:
            return False
        ch, board[i][j] = board[i][j], '#'
        found = any(dfs(i + di, j + dj, k + 1) for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)))
        board[i][j] = ch
        return found
    return any(dfs(i, j, 0) for i in range(m) for j in range(n))
```

### Q107. Advanced

**N-Queens**

Commonly reported in interviews at Amazon, Google.

Place `n` queens on an `n` by `n` board so none share a row, column, or diagonal. Return every board.

Example: `n = 4` has two solutions.

**Answer:**

Backtracking row by row. Track used columns and both diagonal directions (`row - col` and `row + col`).

**Complexity:** Time roughly exponential. Space O(n) besides the answer.

```python
def solve_nqueens(n):
    out = []
    cols, d1, d2 = set(), set(), set()
    board = [['.'] * n for _ in range(n)]
    def bt(r):
        if r == n:
            out.append([''.join(row) for row in board])
            return
        for c in range(n):
            if c in cols or r - c in d1 or r + c in d2:
                continue
            cols.add(c); d1.add(r - c); d2.add(r + c)
            board[r][c] = 'Q'
            bt(r + 1)
            board[r][c] = '.'
            cols.remove(c); d1.remove(r - c); d2.remove(r + c)
    bt(0)
    return out
```

### Q108. Advanced

**Sudoku Solver**

Commonly reported in interviews at Amazon, Uber, Microsoft.

Fill a 9 by 9 board in place. Empty cells are `'.'`. A standard Sudoku has one solution in this problem.

Example: A partially filled valid board is completed.

**Answer:**

Backtracking. For each empty cell try digits 1-9 that are free in the row, column, and 3x3 box. Bit masks make the availability test O(1).

**Complexity:** Time exponential in the number of empty cells. Space O(1) besides the board and the recursion.

```python
def solve_sudoku(board):
    rows = [0] * 9
    cols = [0] * 9
    boxes = [0] * 9
    empties = []
    for i in range(9):
        for j in range(9):
            if board[i][j] == '.':
                empties.append((i, j))
            else:
                bit = 1 << int(board[i][j])
                rows[i] |= bit
                cols[j] |= bit
                boxes[(i // 3) * 3 + j // 3] |= bit
    def bt(k):
        if k == len(empties):
            return True
        i, j = empties[k]
        b = (i // 3) * 3 + j // 3
        for d in range(1, 10):
            bit = 1 << d
            if rows[i] & bit or cols[j] & bit or boxes[b] & bit:
                continue
            rows[i] |= bit; cols[j] |= bit; boxes[b] |= bit
            board[i][j] = str(d)
            if bt(k + 1):
                return True
            rows[i] ^= bit; cols[j] ^= bit; boxes[b] ^= bit
            board[i][j] = '.'
        return False
    bt(0)
    return board
```

### Q109. Advanced

**Word Ladder**

Commonly reported in interviews at Amazon, Google, Facebook.

Begin at `beginWord` and change one letter at a time. Every intermediate word must be in the word list. Return the length of the shortest transformation to `endWord`, counting both ends, or 0 if none exists.

Example: `hit` to `cog` with the list containing `hot, dot, dog, lot, log, cog` returns `5`.

**Answer:**

BFS. The branching factor is 26 times the word length if you try every one-letter change and test set membership.

**Complexity:** Time O(N * L * 26), space O(N * L).

```python
def ladder_length(begin, end, word_list):
    from collections import deque
    words = set(word_list)
    if end not in words:
        return 0
    q = deque([(begin, 1)])
    while q:
        word, dist = q.popleft()
        if word == end:
            return dist
        for i in range(len(word)):
            for ch in 'abcdefghijklmnopqrstuvwxyz':
                nxt = word[:i] + ch + word[i + 1:]
                if nxt in words:
                    words.remove(nxt)
                    q.append((nxt, dist + 1))
    return 0
```

### Q110. Advanced

**Alien Dictionary**

Commonly reported in interviews at Facebook, Google, Airbnb.

Words are sorted in an alien language's lexicographic order. Return one valid character order, or an empty string if the order is invalid.

Example: `['wrt', 'wrf', 'er', 'ett', 'rftt']` implies an order such as `wertf`.

**Answer:**

Compare adjacent words to extract directed edges (the first differing character). Topologically sort the graph. A cycle or a longer word appearing before its prefix means the input is invalid.

**Complexity:** Time O(total characters + alphabet size), space O(alphabet).

```python
def alien_order(words):
    from collections import defaultdict, deque
    g = defaultdict(set)
    indeg = {ch: 0 for w in words for ch in w}
    for a, b in zip(words, words[1:]):
        if len(a) > len(b) and a.startswith(b):
            return ''
        for ca, cb in zip(a, b):
            if ca != cb:
                if cb not in g[ca]:
                    g[ca].add(cb)
                    indeg[cb] += 1
                break
    q = deque(ch for ch, d in indeg.items() if d == 0)
    out = []
    while q:
        u = q.popleft()
        out.append(u)
        for v in g[u]:
            indeg[v] -= 1
            if indeg[v] == 0:
                q.append(v)
    return ''.join(out) if len(out) == len(indeg) else ''
```

### Q111. Advanced

**Network Delay Time**

Commonly reported in interviews at Amazon, Google.

There are `n` nodes and directed weighted edges. A signal starts at node `k`. Return how long it takes to reach every node, or -1 if some node is unreachable.

Example: Edges `[[2, 1, 1], [2, 3, 1], [3, 4, 1]]`, `n = 4`, `k = 2` returns `2`.

**Answer:**

Dijkstra with a min-heap. The answer is the maximum distance among reached nodes.

**Complexity:** Time O(E log V) with a binary heap. Space O(V + E).

```python
def network_delay(times, n, k):
    import heapq
    from collections import defaultdict
    g = defaultdict(list)
    for u, v, w in times:
        g[u].append((v, w))
    dist = {}
    heap = [(0, k)]
    while heap:
        d, u = heapq.heappop(heap)
        if u in dist:
            continue
        dist[u] = d
        for v, w in g[u]:
            if v not in dist:
                heapq.heappush(heap, (d + w, v))
    return max(dist.values()) if len(dist) == n else -1
```

### Q112. Advanced

**Cheapest Flights Within K Stops**

Commonly reported in interviews at Amazon, Expedia-style screens, Google.

Find the cheapest price from `src` to `dst` with at most `k` stops. Return -1 if no such route exists.

Example: A direct expensive flight can lose to a cheaper one-stop flight when `k` allows it.

**Answer:**

Bellman-Ford relaxed for `k + 1` edges, or a Dijkstra state `(cost, node, stops_used)`. The stop limit makes plain Dijkstra on nodes incorrect.

**Complexity:** Time O((k + 1) * E) for Bellman-Ford. Space O(V).

```python
def find_cheapest(n, flights, src, dst, k):
    inf = 10 ** 15
    dist = [inf] * n
    dist[src] = 0
    for _ in range(k + 1):
        nxt = dist[:]
        for u, v, w in flights:
            if dist[u] + w < nxt[v]:
                nxt[v] = dist[u] + w
        dist = nxt
    return dist[dst] if dist[dst] < inf else -1
```

### Q113. Advanced

**Swim in Rising Water**

Commonly reported in interviews at Amazon, Google.

An n by n grid of heights. At time `t` you may enter any adjacent cell whose height is at most `t`. You start at the top left. Return the least `t` that lets you reach the bottom right.

Example: A grid `[[0, 2], [1, 3]]` returns `3`.

**Answer:**

Dijkstra, where the cost of a path is the maximum height along it. Always extend the path with the smallest such cost.

**Complexity:** Time O(n^2 log n), space O(n^2).

```python
def swim(grid):
    import heapq
    n = len(grid)
    heap = [(grid[0][0], 0, 0)]
    seen = {(0, 0)}
    while heap:
        t, i, j = heapq.heappop(heap)
        if i == n - 1 and j == n - 1:
            return t
        for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)):
            ni, nj = i + di, j + dj
            if 0 <= ni < n and 0 <= nj < n and (ni, nj) not in seen:
                seen.add((ni, nj))
                heapq.heappush(heap, (max(t, grid[ni][nj]), ni, nj))
    return -1
```

### Q114. Advanced

**Rotten Oranges**

Commonly reported in interviews at Amazon, Microsoft.

Each minute, a rotten orange rots its 4-adjacent fresh oranges. Return the minutes until every fresh orange is rotten, or -1 if some fresh orange can never rot.

Example: A single rotten orange next to one fresh orange returns 1.

**Answer:**

Multi-source BFS from every rotten orange. The answer is the maximum distance. If a fresh orange remains, return -1.

**Complexity:** Time O(m * n), space O(m * n).

```python
def oranges(grid):
    from collections import deque
    m, n = len(grid), len(grid[0])
    q = deque()
    fresh = 0
    for i in range(m):
        for j in range(n):
            if grid[i][j] == 2:
                q.append((i, j, 0))
            elif grid[i][j] == 1:
                fresh += 1
    minutes = 0
    while q:
        i, j, d = q.popleft()
        minutes = d
        for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)):
            ni, nj = i + di, j + dj
            if 0 <= ni < m and 0 <= nj < n and grid[ni][nj] == 1:
                grid[ni][nj] = 2
                fresh -= 1
                q.append((ni, nj, d + 1))
    return minutes if fresh == 0 else -1
```

### Q115. Advanced

**Pacific Atlantic Water Flow**

Commonly reported in interviews at Google, Amazon.

Water flows from a cell to an adjacent cell of equal or lower height. Return coordinates that can reach both the Pacific (top and left borders) and the Atlantic (bottom and right borders).

Example: On a strictly decreasing path to both borders, the high cell qualifies.

**Answer:**

Reverse the flow. BFS or DFS from each ocean's border, moving to equal or higher cells. The intersection of the two reachable sets is the answer.

**Complexity:** Time O(m * n), space O(m * n).

```python
def pacific_atlantic(heights):
    if not heights:
        return []
    m, n = len(heights), len(heights[0])
    def reach(starts):
        seen = set(starts)
        stack = list(starts)
        while stack:
            i, j = stack.pop()
            for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)):
                ni, nj = i + di, j + dj
                if 0 <= ni < m and 0 <= nj < n and (ni, nj) not in seen and heights[ni][nj] >= heights[i][j]:
                    seen.add((ni, nj))
                    stack.append((ni, nj))
        return seen
    pac = reach([(i, 0) for i in range(m)] + [(0, j) for j in range(n)])
    atl = reach([(i, n - 1) for i in range(m)] + [(m - 1, j) for j in range(n)])
    return list(pac & atl)
```

### Q116. Advanced

**Accounts Merge**

Commonly reported in interviews at Facebook, Amazon.

Each account is a name plus email addresses. Merge accounts that share any email. Return the merged accounts with sorted unique emails.

Example: Two John records that share one email become one record.

**Answer:**

Union-find on emails. Map each email to an account index, union indices that share an email, then group emails by root and sort.

**Complexity:** Time O(n log n) from sorting emails, where n is the total number of emails. Union-find itself is nearly O(n).

```python
def accounts_merge(accounts):
    parent = {}
    def find(x):
        parent.setdefault(x, x)
        while parent[x] != x:
            parent[x] = parent[parent[x]]
            x = parent[x]
        return x
    def union(a, b):
        parent[find(a)] = find(b)
    email_to_name = {}
    for name, *emails in accounts:
        for e in emails:
            email_to_name[e] = name
            union(emails[0], e)
    groups = {}
    for e in email_to_name:
        groups.setdefault(find(e), []).append(e)
    return [[email_to_name[root], *sorted(emails)] for root, emails in groups.items()]
```

### Q117. Advanced

**Redundant Connection**

Commonly reported in interviews at Google, Amazon.

A tree of `n` nodes gained one extra edge and became cyclic. Edges are given in order. Return the edge that can be removed to restore a tree, preferring the one that appears last.

Example: `[[1, 2], [1, 3], [2, 3]]` returns `[2, 3]`.

**Answer:**

Union-find. The first edge whose endpoints are already connected is the redundant one.

**Complexity:** Time nearly O(n), space O(n).

```python
def redundant(edges):
    parent = list(range(len(edges) + 1))
    def find(x):
        while parent[x] != x:
            parent[x] = parent[parent[x]]
            x = parent[x]
        return x
    for a, b in edges:
        ra, rb = find(a), find(b)
        if ra == rb:
            return [a, b]
        parent[ra] = rb
```

### Q118. Advanced

**Number of Provinces**

Commonly reported in interviews at Amazon, Microsoft.

An adjacency matrix describes an undirected graph. Return the number of connected components.

Example: Two disconnected pairs return 2.

**Answer:**

DFS, BFS, or union-find. Count how many times you start a search from an unvisited node.

**Complexity:** Time O(n^2) for a matrix. Space O(n).

```python
def provinces(is_connected):
    n = len(is_connected)
    seen = [False] * n
    def dfs(u):
        seen[u] = True
        for v in range(n):
            if is_connected[u][v] and not seen[v]:
                dfs(v)
    count = 0
    for i in range(n):
        if not seen[i]:
            dfs(i)
            count += 1
    return count
```

### Q119. Advanced

**Surrounded Regions**

Commonly reported in interviews at Amazon, Google.

A board of `'X'` and `'O'`. Capture every region of `'O'` that is fully surrounded by flipping it to `'X'`. Border-connected `'O'` cells stay.

Example: An `'O'` on the border stays. An `'O'` enclosed by `'X'` flips.

**Answer:**

Mark every `'O'` reachable from the border, then flip the unmarked `'O'` cells.

**Complexity:** Time O(m * n), space O(m * n).

```python
def solve_regions(board):
    if not board:
        return board
    m, n = len(board), len(board[0])
    def dfs(i, j):
        if not (0 <= i < m and 0 <= j < n) or board[i][j] != 'O':
            return
        board[i][j] = 'T'
        dfs(i + 1, j); dfs(i - 1, j); dfs(i, j + 1); dfs(i, j - 1)
    for i in range(m):
        dfs(i, 0); dfs(i, n - 1)
    for j in range(n):
        dfs(0, j); dfs(m - 1, j)
    for i in range(m):
        for j in range(n):
            board[i][j] = 'O' if board[i][j] == 'T' else 'X'
    return board
```

### Q120. Advanced

**Median of Two Sorted Arrays**

Commonly reported in interviews at Google, Amazon, Goldman Sachs.

Two sorted arrays. Return the median of the combined values in O(log(min(n, m))) time.

Example: `[1, 3]` and `[2]` returns `2.0`.

**Answer:**

Binary search the cut in the smaller array. The cut is correct when the left half's max is at most the right half's min. The median is then the max of the left or the average of the two middle values.

**Complexity:** Time O(log(min(n, m))), space O(1).

```python
def find_median(a, b):
    if len(a) > len(b):
        a, b = b, a
    m, n = len(a), len(b)
    lo, hi = 0, m
    half = (m + n + 1) // 2
    while lo <= hi:
        i = (lo + hi) // 2
        j = half - i
        left_a = a[i - 1] if i else float('-inf')
        right_a = a[i] if i < m else float('inf')
        left_b = b[j - 1] if j else float('-inf')
        right_b = b[j] if j < n else float('inf')
        if left_a <= right_b and left_b <= right_a:
            if (m + n) % 2:
                return float(max(left_a, left_b))
            return (max(left_a, left_b) + min(right_a, right_b)) / 2
        if left_a > right_b:
            hi = i - 1
        else:
            lo = i + 1
```

### Q121. Advanced

**Pow(x, n)**

Commonly reported in interviews at Facebook, Amazon, Google.

Implement exponentiation. `n` may be negative. Do better than multiplying one factor at a time.

Example: `2.0 ** 10` is `1024.0`. `2.0 ** -2` is `0.25`.

**Answer:**

Exponentiation by squaring. Halve the exponent each step. For a negative exponent, invert the result. Watch the edge `n = -2**31` in fixed-width integers; in Python, negate carefully by using a wider int.

**Complexity:** Time O(log |n|), space O(1) iterative.

```python
def my_pow(x, n):
    if n < 0:
        x, n = 1 / x, -n
    ans = 1.0
    while n:
        if n & 1:
            ans *= x
        x *= x
        n >>= 1
    return ans
```

### Q122. Advanced

**Koko Eating Bananas**

Commonly reported in interviews at Amazon, Google.

Piles of bananas. Koko eats at a constant integer speed and chooses one pile per hour. Return the minimum speed that finishes every pile within `h` hours.

Example: Piles `[3, 6, 7, 11]`, `h = 8` returns `4`.

**Answer:**

Binary search the speed from 1 to `max(piles)`. Hours needed at speed `s` is the sum of `ceil(pile / s)`.

**Complexity:** Time O(n log M), space O(1).

```python
def min_eating_speed(piles, h):
    lo, hi = 1, max(piles)
    while lo < hi:
        mid = (lo + hi) // 2
        hours = sum((p + mid - 1) // mid for p in piles)
        if hours <= h:
            hi = mid
        else:
            lo = mid + 1
    return lo
```

### Q123. Advanced

**Capacity to Ship Packages Within D Days**

Commonly reported in interviews at Amazon.

Packages must ship in order. Each day you load a contiguous prefix that does not exceed the ship's capacity. Return the minimum capacity that ships everything within `days` days.

Example: Weights `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`, `days = 5` returns `15`.

**Answer:**

Binary search capacity from `max(weights)` to `sum(weights)`. Greedily count how many days that capacity needs.

**Complexity:** Time O(n log S), space O(1).

```python
def ship(weights, days):
    lo, hi = max(weights), sum(weights)
    while lo < hi:
        mid = (lo + hi) // 2
        need = 1
        load = 0
        for w in weights:
            if load + w > mid:
                need += 1
                load = 0
            load += w
        if need <= days:
            hi = mid
        else:
            lo = mid + 1
    return lo
```

### Q124. Advanced

**Split Array Largest Sum**

Commonly reported in interviews at Google, Amazon.

Split a non-empty array into `m` contiguous non-empty parts. Minimize the largest part sum.

Example: `[7, 2, 5, 10, 8]`, `m = 2` returns `18`.

**Answer:**

Same binary-search-on-answer pattern as shipping. The capacity is the largest allowed part sum, and you count how many parts that limit needs.

**Complexity:** Time O(n log S), space O(1).

```python
def split_array(nums, m):
    lo, hi = max(nums), sum(nums)
    while lo < hi:
        mid = (lo + hi) // 2
        parts = 1
        total = 0
        for n in nums:
            if total + n > mid:
                parts += 1
                total = 0
            total += n
        if parts <= m:
            hi = mid
        else:
            lo = mid + 1
    return lo
```

### Q125. Advanced

**Find Peak Element**

Commonly reported in interviews at Google, Microsoft.

A peak is strictly greater than its neighbors. The ends have one neighbor. Return any peak index. Neighboring values are never equal.

Example: `[1, 2, 3, 1]` returns `2`.

**Answer:**

Binary search. If the middle is less than its right neighbor, a peak exists on the right. Otherwise a peak exists at mid or on the left.

**Complexity:** Time O(log n), space O(1).

```python
def find_peak(nums):
    lo, hi = 0, len(nums) - 1
    while lo < hi:
        mid = (lo + hi) // 2
        if nums[mid] < nums[mid + 1]:
            lo = mid + 1
        else:
            hi = mid
    return lo
```

### Q126. Advanced

**Search a 2D Matrix**

Commonly reported in interviews at Amazon, Microsoft.

Each row is sorted, and the first value of each row is greater than the last value of the previous row. Return true when `target` is present.

Example: A matrix that flattens to a sorted list can be binary searched as one array.

**Answer:**

Treat the matrix as a flat sorted array of length `m * n`. Convert the mid index back to `(mid // n, mid % n)`.

**Complexity:** Time O(log(m * n)), space O(1).

```python
def search_matrix(matrix, target):
    if not matrix or not matrix[0]:
        return False
    m, n = len(matrix), len(matrix[0])
    lo, hi = 0, m * n - 1
    while lo <= hi:
        mid = (lo + hi) // 2
        val = matrix[mid // n][mid % n]
        if val == target:
            return True
        if val < target:
            lo = mid + 1
        else:
            hi = mid - 1
    return False
```

### Q127. Advanced

**Time Based Key-Value Store**

Commonly reported in interviews at Google, Amazon.

Support `set(key, value, timestamp)` and `get(key, timestamp)`. Get returns the value with the largest timestamp less than or equal to the query, or an empty string.

Example: Set foo=bar at time 1. Get foo at time 1 returns bar. Get foo at time 3 still returns bar if nothing newer was stored.

**Answer:**

Append `(timestamp, value)` pairs. Timestamps for a key arrive in increasing order, so binary search the list.

**Complexity:** Set is O(1) amortized. Get is O(log n). Space O(n).

```python
class TimeMap:
    def __init__(self):
        from collections import defaultdict
        self.data = defaultdict(list)
    def set(self, key, value, timestamp):
        self.data[key].append((timestamp, value))
    def get(self, key, timestamp):
        import bisect
        arr = self.data[key]
        i = bisect.bisect_right(arr, (timestamp, chr(127))) - 1
        return arr[i][1] if i >= 0 else ''
```

### Q128. Advanced

**Implement Trie**

Commonly reported in interviews at Amazon, Google, Microsoft.

Implement insert, search, and starts-with for lowercase words.

Example: Insert `apple`. Search `apple` is true. Search `app` is false. Prefix `app` is true.

**Answer:**

Each node is a dict of children plus a terminal flag. Insert walks or creates edges. Search requires the terminal flag. Prefix search does not.

**Complexity:** Insert and lookup are O(L) where L is the word length. Space is proportional to the number of distinct prefixes.

```python
class Trie:
    def __init__(self):
        self.root = {}
    def insert(self, word):
        node = self.root
        for ch in word:
            node = node.setdefault(ch, {})
        node['#'] = True
    def _walk(self, word):
        node = self.root
        for ch in word:
            if ch not in node:
                return None
            node = node[ch]
        return node
    def search(self, word):
        node = self._walk(word)
        return bool(node and node.get('#'))
    def startswith(self, prefix):
        return self._walk(prefix) is not None
```

### Q129. Advanced

**Design Twitter**

Commonly reported in interviews at Amazon, Twitter-style design rounds.

Support post, follow, unfollow, and a news feed of the 10 most recent tweets from yourself and people you follow. Tweets are ordered by a global increasing id.

Example: User 1 posts, follows user 2, and sees both tweets in reverse time order.

**Answer:**

Store each user's tweets as a list and each follow set. For the feed, use a heap over the heads of the relevant tweet lists, like merging k sorted lists.

**Complexity:** Post and follow are O(1). Feed is O(k log u) for 10 tweets across followed users. Space O(tweets + follows).

```python
class Twitter:
    def __init__(self):
        from collections import defaultdict
        self.time = 0
        self.tweets = defaultdict(list)
        self.follows = defaultdict(set)
    def post(self, user, tweet):
        self.time += 1
        self.tweets[user].append((self.time, tweet))
    def follow(self, follower, followee):
        if follower != followee:
            self.follows[follower].add(followee)
    def unfollow(self, follower, followee):
        self.follows[follower].discard(followee)
    def feed(self, user):
        import heapq
        users = self.follows[user] | {user}
        heap = []
        for u in users:
            if self.tweets[u]:
                heap.append((-self.tweets[u][-1][0], u, len(self.tweets[u]) - 1))
        heapq.heapify(heap)
        out = []
        while heap and len(out) < 10:
            _, u, i = heapq.heappop(heap)
            out.append(self.tweets[u][i][1])
            if i:
                heapq.heappush(heap, (-self.tweets[u][i - 1][0], u, i - 1))
        return out
```

### Q130. Advanced

**LFU Cache**

Commonly reported in interviews at Amazon, Google, Microsoft.

Design a cache with get and put in average O(1). Evict the least frequently used key. Break ties by least recently used.

Example: Capacity 2. Two gets of key 1 make key 2 the eviction candidate when a third key arrives.

**Answer:**

Map key to value and frequency. Map frequency to an ordered dict of keys. Track the minimum frequency. `OrderedDict` gives O(1) recency inside a frequency bucket.

**Complexity:** Each operation average O(1). Space O(capacity).

```python
class LFU:
    def __init__(self, cap):
        from collections import defaultdict, OrderedDict
        self.cap = cap
        self.min_f = 0
        self.values = {}
        self.freq = {}
        self.buckets = defaultdict(OrderedDict)
    def _touch(self, key):
        f = self.freq[key]
        del self.buckets[f][key]
        if not self.buckets[f] and self.min_f == f:
            self.min_f += 1
        self.freq[key] = f + 1
        self.buckets[f + 1][key] = None
    def get(self, key):
        if key not in self.values:
            return -1
        self._touch(key)
        return self.values[key]
    def put(self, key, value):
        if self.cap == 0:
            return
        if key in self.values:
            self.values[key] = value
            self._touch(key)
            return
        if len(self.values) == self.cap:
            old, _ = self.buckets[self.min_f].popitem(last=False)
            del self.values[old]
            del self.freq[old]
        self.values[key] = value
        self.freq[key] = 1
        self.buckets[1][key] = None
        self.min_f = 1
```

### Q131. Advanced

**Insert Delete GetRandom O(1)**

Commonly reported in interviews at Google, Facebook.

Design a set that supports insert, remove, and get-random, each in average O(1). Get-random returns each present value with equal probability.

Example: Insert 1, insert 2, remove 1. Random returns 2.

**Answer:**

A list gives O(1) random index. A dict maps value to index. Remove by swapping the target with the last element and popping.

**Complexity:** Average O(1) each. Space O(n).

```python
class RandomizedSet:
    def __init__(self):
        import random
        self.random = random
        self.vals = []
        self.idx = {}
    def insert(self, val):
        if val in self.idx:
            return False
        self.idx[val] = len(self.vals)
        self.vals.append(val)
        return True
    def remove(self, val):
        if val not in self.idx:
            return False
        i = self.idx[val]
        last = self.vals[-1]
        self.vals[i] = last
        self.idx[last] = i
        self.vals.pop()
        del self.idx[val]
        return True
    def get_random(self):
        return self.random.choice(self.vals)
```

### Q132. Advanced

**Range Sum Query - Mutable**

Commonly reported in interviews at Amazon, Google.

Support updating one index and querying the sum of a range, both faster than a linear scan.

Example: Array `[1, 3, 5]`. Sum from 0 through 2 is 9. After setting index 1 to 2, the sum is 8.

**Answer:**

A Fenwick tree (binary indexed tree) or a segment tree. The Fenwick version is short: add at an index and prefix-sum by stripping the lowest set bit.

**Complexity:** Build O(n). Update and query O(log n). Space O(n).

```python
class Fenwick:
    def __init__(self, nums):
        self.n = len(nums)
        self.bit = [0] * (self.n + 1)
        self.nums = [0] * self.n
        for i, v in enumerate(nums):
            self.update(i, v)
    def update(self, i, val):
        delta = val - self.nums[i]
        self.nums[i] = val
        i += 1
        while i <= self.n:
            self.bit[i] += delta
            i += i & -i
    def prefix(self, i):
        s = 0
        while i:
            s += self.bit[i]
            i -= i & -i
        return s
    def query(self, left, right):
        return self.prefix(right + 1) - self.prefix(left)
```

### Q133. Advanced

**Count of Smaller Numbers After Self**

Commonly reported in interviews at Google, Amazon.

For each index, count how many later elements are strictly smaller.

Example: `[5, 2, 6, 1]` returns `[2, 1, 1, 0]`.

**Answer:**

Merge sort the indexes. When the right half contributes a value during the merge, it is smaller than every remaining left-half value, so add that count. A Fenwick tree on compressed ranks also works, scanning from the right.

**Complexity:** Time O(n log n), space O(n).

```python
def count_smaller(nums):
    n = len(nums)
    ans = [0] * n
    items = list(enumerate(nums))
    def sort(arr):
        if len(arr) <= 1:
            return arr
        mid = len(arr) // 2
        left, right = sort(arr[:mid]), sort(arr[mid:])
        merged = []
        j = 0
        for i, (idx, val) in enumerate(left):
            while j < len(right) and right[j][1] < val:
                merged.append(right[j])
                j += 1
            ans[idx] += j
            merged.append((idx, val))
        merged.extend(right[j:])
        return merged
    sort(items)
    return ans
```

### Q134. Advanced

**Largest Rectangle in Histogram**

Commonly reported in interviews at Amazon, Google.

Each bar has width 1 and the given height. Return the area of the largest rectangle that fits under the bars.

Example: `[2, 1, 5, 6, 2, 3]` returns `10`.

**Answer:**

Monotonic increasing stack of indices. When a bar is shorter than the stack top, the top is the limiting height of a rectangle that extends to the current index.

**Complexity:** Time O(n), space O(n).

```python
def largest_rectangle(heights):
    stack = [-1]
    best = 0
    heights = heights + [0]
    for i, h in enumerate(heights):
        while stack[-1] != -1 and heights[stack[-1]] > h:
            height = heights[stack.pop()]
            width = i - stack[-1] - 1
            best = max(best, height * width)
        stack.append(i)
    return best
```

### Q135. Advanced

**Maximal Rectangle**

Commonly reported in interviews at Amazon, Google.

A binary matrix. Return the area of the largest rectangle of ones.

Example: A 2x3 block of ones has area 6.

**Answer:**

Treat each row as the base of a histogram whose bar height is the number of consecutive ones ending at that cell. Run the histogram algorithm on every row.

**Complexity:** Time O(m * n), space O(n).

```python
def maximal_rectangle(matrix):
    if not matrix:
        return 0
    n = len(matrix[0])
    height = [0] * n
    best = 0
    for row in matrix:
        for j in range(n):
            height[j] = height[j] + 1 if row[j] == '1' else 0
        stack = [-1]
        hist = height + [0]
        for i, h in enumerate(hist):
            while stack[-1] != -1 and hist[stack[-1]] > h:
                H = hist[stack.pop()]
                best = max(best, H * (i - stack[-1] - 1))
            stack.append(i)
    return best
```

### Q136. Advanced

**Basic Calculator**

Commonly reported in interviews at Google, Amazon.

Evaluate a string expression of non-negative integers, `+`, `-`, parentheses, and spaces.

Example: `'(1+(4+5+2)-3)+(6+8)'` returns `23`.

**Answer:**

A stack of signs or of partial results. On `(`, push the current result and the sign before the parenthesis, then start a fresh result. On `)`, combine with the saved sign and result.

**Complexity:** Time O(n), space O(n).

```python
def calculate(s):
    stack = []
    result = 0
    sign = 1
    n = 0
    for ch in s:
        if ch.isdigit():
            n = n * 10 + int(ch)
        elif ch in '+-':
            result += sign * n
            n = 0
            sign = 1 if ch == '+' else -1
        elif ch == '(':
            stack.append(result)
            stack.append(sign)
            result, sign = 0, 1
        elif ch == ')':
            result += sign * n
            n = 0
            result *= stack.pop()
            result += stack.pop()
    return result + sign * n
```

### Q137. Advanced

**Basic Calculator II**

Commonly reported in interviews at Facebook, Amazon.

Evaluate an expression with non-negative integers, `+`, `-`, `*`, `/`, and spaces. Division truncates toward zero. There are no parentheses.

Example: `'3+2*2'` returns `7`. `'14-3/2'` returns `13`.

**Answer:**

Keep a stack of terms. On `+` or `-`, push the signed number. On `*` or `/`, combine with the stack top immediately. Sum the stack at the end.

**Complexity:** Time O(n), space O(n).

```python
def calculate_ii(s):
    stack = []
    n = 0
    op = '+'
    for i, ch in enumerate(s + '+'):
        if ch.isdigit():
            n = n * 10 + int(ch)
        elif ch in '+-*/':
            if op == '+':
                stack.append(n)
            elif op == '-':
                stack.append(-n)
            elif op == '*':
                stack.append(stack.pop() * n)
            else:
                prev = stack.pop()
                stack.append(int(prev / n))
            op, n = ch, 0
    return sum(stack)
```

### Q138. Advanced

**The Skyline Problem**

Commonly reported in interviews at Google, Facebook, Microsoft.

Buildings are triples `[left, right, height]`. Return the skyline as key points `[x, height]` where the height of the silhouette changes.

Example: Two adjacent buildings produce a rise, a step where the shorter one is hidden, and a fall back to zero.

**Answer:**

Sweep line. Events are left edges (`+height`) and right edges (`-height`). A max-heap, or a sorted multiset, tracks active heights. Emit a point when the current max changes. Python's heap needs lazy deletion.

**Complexity:** Time O(n log n), space O(n).

```python
def skyline(buildings):
    import heapq
    events = []
    for L, R, H in buildings:
        events.append((L, -H, R))
        events.append((R, 0, 0))
    events.sort()
    heap = [(0, float('inf'))]
    out = []
    for x, neg_h, R in events:
        while heap[0][1] <= x:
            heapq.heappop(heap)
        if neg_h:
            heapq.heappush(heap, (neg_h, R))
        height = -heap[0][0]
        if not out or out[-1][1] != height:
            out.append([x, height])
    return out
```

### Q139. Advanced

**Bus Routes**

Commonly reported in interviews at Google, Amazon.

Each bus route is a cycle of stops. The cost of a trip is the number of buses taken. Return the minimum buses needed to go from `source` to `target`, or -1.

Example: If source and target share a route, the answer is 1. If source equals target, the answer is 0.

**Answer:**

BFS on buses, or on stops where you mark a route used once you board it. Boarding a route visits all of its stops at cost +1.

**Complexity:** Time O(total stops across routes), space O(total stops).

```python
def num_buses(routes, source, target):
    from collections import defaultdict, deque
    if source == target:
        return 0
    stop_to_buses = defaultdict(set)
    for i, route in enumerate(routes):
        for stop in route:
            stop_to_buses[stop].add(i)
    q = deque([(source, 0)])
    seen_stops = {source}
    seen_buses = set()
    while q:
        stop, buses = q.popleft()
        for b in stop_to_buses[stop]:
            if b in seen_buses:
                continue
            seen_buses.add(b)
            for nxt in routes[b]:
                if nxt == target:
                    return buses + 1
                if nxt not in seen_stops:
                    seen_stops.add(nxt)
                    q.append((nxt, buses + 1))
    return -1
```

### Q140. Advanced

**Critical Connections**

Commonly reported in interviews at Amazon.

An undirected connected graph. Return every bridge: an edge whose removal increases the number of connected components.

Example: A tree edge is always a bridge. An edge on a cycle is not.

**Answer:**

Tarjan's DFS. Record discovery time and the lowest discovery time reachable from the subtree. An edge `u-v` is a bridge when `low[v] > disc[u]`.

**Complexity:** Time O(V + E), space O(V + E).

```python
def critical_connections(n, connections):
    from collections import defaultdict
    g = defaultdict(list)
    for u, v in connections:
        g[u].append(v)
        g[v].append(u)
    disc = [-1] * n
    low = [0] * n
    time = 0
    out = []
    def dfs(u, parent):
        nonlocal time
        disc[u] = low[u] = time
        time += 1
        for v in g[u]:
            if v == parent:
                continue
            if disc[v] == -1:
                dfs(v, u)
                low[u] = min(low[u], low[v])
                if low[v] > disc[u]:
                    out.append([u, v])
            else:
                low[u] = min(low[u], disc[v])
    dfs(0, -1)
    return out
```

### Q141. Advanced

**Word Search II**

Commonly reported in interviews at Amazon, Microsoft.

Given a board and a list of words, return every word that can be formed by a 4-directional path without reusing a cell.

Example: A board containing `oath` and `pea` returns those words when both are in the dictionary and present as paths.

**Answer:**

Insert the words into a trie. DFS from each cell, walking the trie. When a word ends, record it and erase the terminal mark so it is not found twice. Prune dead branches.

**Complexity:** Time O(m * n * 4^L) in the worst case, much less with trie pruning. Space O(total characters).

```python
def find_words(board, words):
    trie = {}
    for w in words:
        node = trie
        for ch in w:
            node = node.setdefault(ch, {})
        node['#'] = w
    m, n = len(board), len(board[0])
    found = []
    def dfs(i, j, node):
        ch = board[i][j]
        nxt = node.get(ch)
        if not nxt:
            return
        word = nxt.pop('#', None)
        if word:
            found.append(word)
        board[i][j] = '.'
        for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)):
            ni, nj = i + di, j + dj
            if 0 <= ni < m and 0 <= nj < n:
                dfs(ni, nj, nxt)
        board[i][j] = ch
        if not nxt:
            node.pop(ch, None)
    for i in range(m):
        for j in range(n):
            dfs(i, j, trie)
    return found
```

### Q142. Advanced

**Employee Free Time**

Commonly reported in interviews at Amazon, Google, Airbnb-style.

Each employee has a sorted list of busy intervals. Return the finite gaps when every employee is free, in sorted order.

Example: If one person is busy 1-3 and another is busy 2-4, the merged busy block is 1-4 and there is no finite common free gap inside that block.

**Answer:**

Collect every interval, sort by start, and merge. A gap between merged blocks is common free time.

**Complexity:** Time O(n log n), space O(n).

```python
def free_time(schedule):
    busy = sorted(iv for person in schedule for iv in person)
    merged = [list(busy[0])]
    for start, end in busy[1:]:
        if start <= merged[-1][1]:
            merged[-1][1] = max(merged[-1][1], end)
        else:
            merged.append([start, end])
    gaps = []
    for a, b in zip(merged, merged[1:]):
        gaps.append([a[1], b[0]])
    return gaps
```

### Q143. Advanced

**Meeting Rooms II**

Commonly reported in interviews at Amazon, Google, Facebook.

Given meeting intervals, return the minimum number of rooms required so that no two meetings in the same room overlap.

Example: `[[0, 30], [5, 10], [15, 20]]` returns `2`.

**Answer:**

Sort starts and ends separately. Sweep with two pointers. A start before the next end opens a room. An end at or before the next start frees a room.

**Complexity:** Time O(n log n), space O(n).

```python
def min_rooms(intervals):
    starts = sorted(s for s, e in intervals)
    ends = sorted(e for s, e in intervals)
    rooms = used = 0
    j = 0
    for s in starts:
        if s < ends[j]:
            used += 1
            rooms = max(rooms, used)
        else:
            j += 1
    return rooms
```

### Q144. Advanced

**Non-overlapping Intervals**

Commonly reported in interviews at Amazon.

Return the minimum number of intervals to remove so the rest do not overlap. Touching at an endpoint is allowed.

Example: `[[1, 2], [2, 3], [3, 4], [1, 3]]` returns `1`.

**Answer:**

Sort by end time. Keep an interval when it starts at or after the last kept end. Otherwise it is the one to drop, because it ends later or conflicts.

**Complexity:** Time O(n log n), space O(1) extra besides sorting.

```python
def erase_overlap(intervals):
    intervals = sorted(intervals, key=lambda iv: iv[1])
    end = float('-inf')
    removed = 0
    for s, e in intervals:
        if s >= end:
            end = e
        else:
            removed += 1
    return removed
```

### Q145. Advanced

**Task Scheduler**

Commonly reported in interviews at Facebook, Amazon.

Tasks are letters. The same letter must be separated by at least `n` intervals. A CPU cycle can be idle. Return the minimum cycles needed to finish every task.

Example: Tasks `AAABBB`, `n = 2` can be scheduled as `A B idle A B idle A B` in some equivalent order and takes 8.

**Answer:**

The most frequent task determines a frame pattern. If the most frequent task appears `f` times and `k` tasks share that frequency, the answer is `max(len(tasks), (f - 1) * (n + 1) + k)`.

**Complexity:** Time O(n), space O(1) for a fixed alphabet.

```python
def least_interval(tasks, n):
    from collections import Counter
    counts = Counter(tasks)
    f = max(counts.values())
    k = sum(v == f for v in counts.values())
    return max(len(tasks), (f - 1) * (n + 1) + k)
```

### Q146. Advanced

**Queue Reconstruction by Height**

Commonly reported in interviews at Amazon, Google.

People are pairs `[h, k]` meaning height `h` and exactly `k` people in front who are at least as tall. Reconstruct the queue.

Example: `[[7, 0], [4, 4], [7, 1], [5, 0], [6, 1], [5, 2]]` has a known unique arrangement.

**Answer:**

Sort by height descending, and by `k` ascending within a height. Insert each person at index `k`. Taller people are already placed, so index `k` is exactly the number of taller-or-equal people in front.

**Complexity:** Time O(n^2) because of list insertion. Space O(n).

```python
def reconstruct_queue(people):
    people = sorted(people, key=lambda p: (-p[0], p[1]))
    out = []
    for p in people:
        out.insert(p[1], p)
    return out
```

### Q147. Advanced

**Odd Even Linked List**

Commonly reported in interviews at Amazon.

Group nodes at odd positions before nodes at even positions, preserving relative order. The first node is position 1. Do it in place.

Example: `1 -> 2 -> 3 -> 4 -> 5` becomes `1 -> 3 -> 5 -> 2 -> 4`.

**Answer:**

Split into two lists with two tails, then attach the even head after the odd tail.

**Complexity:** Time O(n), space O(1).

```python
def odd_even(head):
    if not head:
        return head
    odd, even, even_head = head, head.next, head.next
    while even and even.next:
        odd.next = even.next
        odd = odd.next
        even.next = odd.next
        even = even.next
    odd.next = even_head
    return head
```

### Q148. Advanced

**Flatten Binary Tree to Linked List**

Commonly reported in interviews at Microsoft, Facebook.

Flatten a binary tree into a right spine in preorder, in place. Left children become null.

Example: Root 1, left 2, right 5 becomes `1 -> 2 -> ... -> 5` along `right`.

**Answer:**

Reverse postorder (right, left, root) with a previous pointer, or find the rightmost node of the left subtree and stitch the original right subtree there.

**Complexity:** Time O(n), space O(1) for the stitch method if you do not use recursion, or O(h) recursive.

```python
def flatten(root):
    cur = root
    while cur:
        if cur.left:
            pred = cur.left
            while pred.right:
                pred = pred.right
            pred.right = cur.right
            cur.right = cur.left
            cur.left = None
        cur = cur.right
    return root
```

### Q149. Advanced

**Populating Next Right Pointers**

Commonly reported in interviews at Amazon, Microsoft.

Each node of a perfect binary tree has a `next` pointer. Point every node at its level's right neighbor, or null if it is the rightmost.

Example: On a perfect tree, the left child's next is the right child. A right child's next is the parent's next's left child.

**Answer:**

Use the `next` pointers already established on the current level to wire the level below. No queue is required.

**Complexity:** Time O(n), space O(1).

```python
def connect(root):
    left = root
    while left and left.left:
        cur = left
        while cur:
            cur.left.next = cur.right
            if cur.next:
                cur.right.next = cur.next.left
            cur = cur.next
        left = left.left
    return root
```

### Q150. Advanced

**Binary Tree Zigzag Level Order**

Commonly reported in interviews at Amazon, Microsoft.

Return level order, but alternate the direction of each level.

Example: Level 0 left to right, level 1 right to left, and so on.

**Answer:**

Ordinary BFS. Reverse the collected level when the level index is odd, or use a deque and insert at the front on alternate levels.

**Complexity:** Time O(n), space O(n).

```python
def zigzag(root):
    from collections import deque
    if not root:
        return []
    out, q, flip = [], deque([root]), False
    while q:
        level = []
        for _ in range(len(q)):
            node = q.popleft()
            level.append(node.val)
            if node.left:
                q.append(node.left)
            if node.right:
                q.append(node.right)
        out.append(level[::-1] if flip else level)
        flip = not flip
    return out
```

### Q151. Advanced

**Path Sum III**

Commonly reported in interviews at Amazon.

Count the paths that sum to `target`. A path must go downward (parent to child) but does not have to start at the root or end at a leaf.

Example: Several downward paths can share a prefix and still be counted separately.

**Answer:**

Prefix sums on the DFS path. At each node, add the number of earlier prefixes equal to `current_sum - target`. A map keeps those counts. Backtrack the count when you leave a node.

**Complexity:** Time O(n), space O(n).

```python
def path_sum_iii(root, target):
    from collections import defaultdict
    seen = defaultdict(int)
    seen[0] = 1
    def dfs(node, total):
        if not node:
            return 0
        total += node.val
        ans = seen[total - target]
        seen[total] += 1
        ans += dfs(node.left, total) + dfs(node.right, total)
        seen[total] -= 1
        return ans
    return dfs(root, 0)
```

### Q152. Advanced

**House Robber III**

Commonly reported in interviews at Uber, Amazon.

Houses form a binary tree. You cannot rob two directly connected nodes. Return the maximum amount.

Example: Robbing a node forbids its children. Robbing the children forbids the node.

**Answer:**

Return a pair `(rob_this, skip_this)` from each subtree. `rob_this` is the node value plus the skip values of the children. `skip_this` is the max of each child's pair.

**Complexity:** Time O(n), space O(h).

```python
def rob_tree(root):
    def dfs(node):
        if not node:
            return 0, 0
        L, R = dfs(node.left), dfs(node.right)
        rob = node.val + L[1] + R[1]
        skip = max(L) + max(R)
        return rob, skip
    return max(dfs(root))
```

### Q153. Advanced

**Decode String**

Commonly reported in interviews at Google, Amazon, Bloomberg.

The encoding is `k[encoded]`, meaning `encoded` repeated `k` times. Encodings nest. Return the decoded string.

Example: `3[a2[c]]` returns `accaccacc`.

**Answer:**

A stack of `(previous_string, k)`. On `]`, pop and repeat. Digits may have more than one character.

**Complexity:** Time O(n) relative to the output length. Space O(n).

```python
def decode_string(s):
    stack = []
    cur = ''
    k = 0
    for ch in s:
        if ch.isdigit():
            k = k * 10 + int(ch)
        elif ch == '[':
            stack.append((cur, k))
            cur, k = '', 0
        elif ch == ']':
            prev, times = stack.pop()
            cur = prev + cur * times
        else:
            cur += ch
    return cur
```

### Q154. Advanced

**Daily Temperatures**

Commonly reported in interviews at Amazon, Facebook.

For each day, return how many days you must wait until a warmer temperature. If none exists, that entry is 0.

Example: `[73, 74, 75, 71, 69, 72, 76, 73]` returns `[1, 1, 4, 2, 1, 1, 0, 0]`.

**Answer:**

Monotonic decreasing stack of indices. When today's temperature is warmer than the stack top, that day has found its answer.

**Complexity:** Time O(n), space O(n).

```python
def daily_temperatures(temps):
    ans = [0] * len(temps)
    stack = []
    for i, t in enumerate(temps):
        while stack and temps[stack[-1]] < t:
            j = stack.pop()
            ans[j] = i - j
        stack.append(i)
    return ans
```

### Q155. Advanced

**Next Greater Element II**

Commonly reported in interviews at Amazon, Google.

A circular list. For each position, return the next greater element, searching forward and wrapping around. Use -1 when none exists.

Example: `[1, 2, 1]` returns `[2, -1, 2]`.

**Answer:**

Monotonic stack over indexes `0 .. 2n-2`, using `i % n` to read the circular array. Each index is pushed once.

**Complexity:** Time O(n), space O(n).

```python
def next_greater_circular(nums):
    n = len(nums)
    ans = [-1] * n
    stack = []
    for i in range(2 * n):
        while stack and nums[stack[-1]] < nums[i % n]:
            ans[stack.pop()] = nums[i % n]
        if i < n:
            stack.append(i)
    return ans
```

### Q156. Advanced

**Online Stock Span**

Commonly reported in interviews at Amazon, Bloomberg.

The span of today's price is the number of consecutive days ending today whose price is less than or equal to today's price. Support a stream of `next(price)` calls.

Example: Prices 100, 80, 60, 70, 60, 75, 85 produce spans 1, 1, 1, 2, 1, 4, 6.

**Answer:**

Monotonic decreasing stack of `(price, span)`. Pop every previous day that is less than or equal, and add its span to today.

**Complexity:** Each call is amortized O(1). Space O(n).

```python
class StockSpanner:
    def __init__(self):
        self.stack = []
    def next(self, price):
        span = 1
        while self.stack and self.stack[-1][0] <= price:
            span += self.stack.pop()[1]
        self.stack.append((price, span))
        return span
```

### Q157. Advanced

**Car Fleet**

Commonly reported in interviews at Amazon, Google.

Cars drive at constant speeds toward a destination and cannot pass. A fleet is cars that bunch up at the same position and speed. Return how many fleets arrive.

Example: Target 12, positions `[10, 8, 0, 5, 3]`, speeds `[2, 4, 1, 1, 3]` returns `3`.

**Answer:**

Sort cars by position descending (closest to the destination first). A car joins the fleet ahead when its arrival time is less than or equal to that fleet's time. Otherwise it starts a new fleet.

**Complexity:** Time O(n log n), space O(n).

```python
def car_fleet(target, position, speed):
    cars = sorted(zip(position, speed), reverse=True)
    fleets = 0
    lead = -1.0
    for pos, spd in cars:
        time = (target - pos) / spd
        if time > lead:
            fleets += 1
            lead = time
    return fleets
```

### Q158. Advanced

**Asteroid Collision**

Commonly reported in interviews at Amazon.

Asteroids move right if positive and left if negative. When two collide, the smaller explodes. Equal sizes both explode. Return the state after every collision.

Example: `[5, 10, -5]` returns `[5, 10]`. `[8, -8]` returns `[]`.

**Answer:**

A stack of asteroids still in play. Only a right-moving stack top collides with a new left-moving asteroid. Resolve that pair before pushing.

**Complexity:** Time O(n), space O(n).

```python
def asteroid_collision(asteroids):
    stack = []
    for a in asteroids:
        alive = True
        while alive and stack and stack[-1] > 0 and a < 0:
            if stack[-1] < -a:
                stack.pop()
            elif stack[-1] == -a:
                stack.pop()
                alive = False
            else:
                alive = False
        if alive:
            stack.append(a)
    return stack
```

### Q159. Advanced

**Gas Station**

Commonly reported in interviews at Amazon, Uber.

Circular route. `gas[i]` is the fuel at station `i` and `cost[i]` is the fuel to reach the next station. Return the starting station index that completes the circuit, or -1. A solution is unique when it exists.

Example: If the total gas is less than the total cost, return -1.

**Answer:**

If the running tank drops below zero, no station in that segment can be the start. Reset the candidate to the next station and reset the tank. Also check that total gas covers total cost.

**Complexity:** Time O(n), space O(1).

```python
def can_complete(gas, cost):
    if sum(gas) < sum(cost):
        return -1
    tank = start = 0
    for i, (g, c) in enumerate(zip(gas, cost)):
        tank += g - c
        if tank < 0:
            start = i + 1
            tank = 0
    return start
```

### Q160. Advanced

**Candy**

Commonly reported in interviews at Amazon.

Children stand in a line with ratings. Each child gets at least one candy. A child with a strictly higher rating than a neighbor gets more candies than that neighbor. Return the minimum candies.

Example: `[1, 0, 2]` returns `5` (2, 1, 2).

**Answer:**

Two passes. Left to right enforces the left neighbor. Right to left enforces the right neighbor by taking the max.

**Complexity:** Time O(n), space O(n).

```python
def candy(ratings):
    n = len(ratings)
    candies = [1] * n
    for i in range(1, n):
        if ratings[i] > ratings[i - 1]:
            candies[i] = candies[i - 1] + 1
    for i in range(n - 2, -1, -1):
        if ratings[i] > ratings[i + 1]:
            candies[i] = max(candies[i], candies[i + 1] + 1)
    return sum(candies)
```

### Q161. Advanced

**H-Index**

Commonly reported in interviews at Google, Bloomberg.

A researcher has citation counts. The h-index is the largest `h` such that at least `h` papers have at least `h` citations each.

Example: `[3, 0, 6, 1, 5]` returns `3`.

**Answer:**

Sort descending and find the largest `i` with `citations[i] >= i + 1`. Counting sort is O(n) because any count above `n` can be bucketed at `n`.

**Complexity:** Time O(n) with counting, or O(n log n) with sorting. Space O(n) or O(1) extra.

```python
def h_index(citations):
    citations = sorted(citations, reverse=True)
    h = 0
    for i, c in enumerate(citations):
        if c >= i + 1:
            h = i + 1
        else:
            break
    return h
```

### Q162. Advanced

**Find the Duplicate Number**

Commonly reported in interviews at Amazon, Microsoft.

The list contains `n + 1` integers, each in `1..n`. Exactly one value is repeated, possibly more than once. Find it without modifying the list and with O(1) extra space.

Example: `[1, 3, 4, 2, 2]` returns `2`.

**Answer:**

Treat indexes and values as a linked list. The duplicate is the entrance of the cycle. Floyd's algorithm finds it. Binary search on the value range also works if you can count how many items are `<= mid`.

**Complexity:** Time O(n), space O(1).

```python
def find_duplicate(nums):
    slow = fast = nums[0]
    while True:
        slow = nums[slow]
        fast = nums[nums[fast]]
        if slow == fast:
            break
    slow = nums[0]
    while slow != fast:
        slow = nums[slow]
        fast = nums[fast]
    return slow
```

### Q163. Advanced

**Majority Element II**

Commonly reported in interviews at Amazon.

Return every value that appears more than `len(nums) // 3` times. There are at most two such values.

Example: `[1, 1, 1, 3, 3, 2, 2, 2]` returns `[1, 2]`.

**Answer:**

Boyer-Moore with two candidates. A second pass confirms that each candidate really exceeds `n / 3`, because the voting pass can leave a non-qualifier when no value is that frequent.

**Complexity:** Time O(n), space O(1).

```python
def majority_ii(nums):
    c1 = c2 = None
    k1 = k2 = 0
    for n in nums:
        if n == c1:
            k1 += 1
        elif n == c2:
            k2 += 1
        elif k1 == 0:
            c1, k1 = n, 1
        elif k2 == 0:
            c2, k2 = n, 1
        else:
            k1 -= 1
            k2 -= 1
    return [c for c in (c1, c2) if c is not None and nums.count(c) > len(nums) // 3]
```

### Q164. Advanced

**Subsets II**

Commonly reported in interviews at Amazon, Facebook.

Return all unique subsets. The input may contain duplicates.

Example: `[1, 2, 2]` returns subsets that include `[2]` once and `[2, 2]` once.

**Answer:**

Sort. Backtrack. After choosing a value, the next recursive call may skip duplicate siblings at the same depth.

**Complexity:** Time O(n * 2^n), space O(n) besides the answer.

```python
def subsets_with_dup(nums):
    nums = sorted(nums)
    out = []
    def bt(start, path):
        out.append(path[:])
        for i in range(start, len(nums)):
            if i > start and nums[i] == nums[i - 1]:
                continue
            path.append(nums[i])
            bt(i + 1, path)
            path.pop()
    bt(0, [])
    return out
```

### Q165. Advanced

**Permutations II**

Commonly reported in interviews at Amazon, LinkedIn.

Return all unique permutations. The input may contain duplicates.

Example: `[1, 1, 2]` returns three permutations, not six.

**Answer:**

Sort and skip a duplicate that would be placed in the same position as an unused identical predecessor. A used-array makes that test easy.

**Complexity:** Time O(n * n!), space O(n) besides the answer.

```python
def permute_unique(nums):
    nums = sorted(nums)
    used = [False] * len(nums)
    out = []
    def bt(path):
        if len(path) == len(nums):
            out.append(path[:])
            return
        for i, n in enumerate(nums):
            if used[i]:
                continue
            if i and nums[i] == nums[i - 1] and not used[i - 1]:
                continue
            used[i] = True
            path.append(n)
            bt(path)
            path.pop()
            used[i] = False
    bt([])
    return out
```

### Q166. Advanced

**Combination Sum II**

Commonly reported in interviews at Amazon.

Each candidate may be used once. The input may contain duplicates. Return unique combinations that sum to `target`.

Example: `[10, 1, 2, 7, 6, 1, 5]`, target `8` includes `[1, 1, 6]` and `[2, 6]` among others.

**Answer:**

Sort, then backtrack. Move the start index forward so a number is not reused, and skip duplicate siblings.

**Complexity:** Time exponential. Space O(n) besides the answer.

```python
def combination_sum2(candidates, target):
    candidates = sorted(candidates)
    out = []
    def bt(start, remain, path):
        if remain == 0:
            out.append(path[:])
            return
        for i in range(start, len(candidates)):
            if i > start and candidates[i] == candidates[i - 1]:
                continue
            if candidates[i] > remain:
                break
            path.append(candidates[i])
            bt(i + 1, remain - candidates[i], path)
            path.pop()
    bt(0, target, [])
    return out
```

### Q167. Advanced

**Palindrome Partitioning**

Commonly reported in interviews at Amazon, Bloomberg.

Partition a string so every part is a palindrome. Return all such partitions.

Example: `aab` returns `[['a', 'a', 'b'], ['aa', 'b']]`.

**Answer:**

Backtracking. At each start index, try every end that makes `s[start:end]` a palindrome, then recurse. Precompute a palindrome DP table if you want faster checks.

**Complexity:** Time exponential in the number of cuts. Space O(n) besides the answer.

```python
def partition(s):
    out = []
    def is_pal(a):
        return a == a[::-1]
    def bt(start, path):
        if start == len(s):
            out.append(path[:])
            return
        for end in range(start + 1, len(s) + 1):
            piece = s[start:end]
            if is_pal(piece):
                path.append(piece)
                bt(end, path)
                path.pop()
    bt(0, [])
    return out
```

### Q168. Advanced

**Restore IP Addresses**

Commonly reported in interviews at Amazon, Microsoft.

A string of digits may be split into four integers that form a valid IPv4 address. No leading zeros are allowed, and each part is at most 255. Return every valid address.

Example: `25525511135` returns `['255.255.11.135', '255.255.111.35']`.

**Answer:**

Backtracking with four parts. A part is one to three digits, has no leading zero unless it is exactly `0`, and is at most 255.

**Complexity:** Time is bounded by a small constant. Space O(1) besides the answer.

```python
def restore_ip(s):
    out = []
    def bt(start, parts):
        if len(parts) == 4:
            if start == len(s):
                out.append('.'.join(parts))
            return
        for length in range(1, 4):
            if start + length > len(s):
                break
            piece = s[start:start + length]
            if (piece[0] == '0' and length > 1) or int(piece) > 255:
                continue
            parts.append(piece)
            bt(start + length, parts)
            parts.pop()
    bt(0, [])
    return out
```

### Q169. Advanced

**Word Break II**

Commonly reported in interviews at Google, Amazon.

Return every way to segment a string into dictionary words, with spaces between words.

Example: `catsanddog` with `cat, cats, and, sand, dog` returns both `cats and dog` and `cat sand dog`.

**Answer:**

Backtracking with memoization on the start index. The memo stores the list of sentences that segment the suffix. Without memo, overlapping subproblems explode.

**Complexity:** Time exponential in the worst case because the output can be exponential. Memoized time is polynomial in the number of segmentations explored.

```python
def word_break_ii(s, word_dict):
    words = set(word_dict)
    memo = {}
    def bt(start):
        if start in memo:
            return memo[start]
        if start == len(s):
            return ['']
        out = []
        for end in range(start + 1, len(s) + 1):
            w = s[start:end]
            if w in words:
                for rest in bt(end):
                    out.append(w + (' ' + rest if rest else ''))
        memo[start] = out
        return out
    return bt(0)
```

### Q170. Advanced

**Burst Balloons**

Commonly reported in interviews at Google.

Balloons have numbers. Bursting balloon `i` scores `left * nums[i] * right`, where left and right are the still-present neighbors. Ends are treated as 1. Return the maximum score.

Example: `[3, 1, 5, 8]` returns `167`.

**Answer:**

Interval DP, but think about the last balloon burst in an open interval. `dp[l][r]` is the best score bursting everything strictly between `l` and `r`.

**Complexity:** Time O(n^3), space O(n^2).

```python
def max_coins(nums):
    a = [1] + [n for n in nums if n > 0] + [1]
    n = len(a)
    dp = [[0] * n for _ in range(n)]
    for length in range(2, n):
        for left in range(n - length):
            right = left + length
            for k in range(left + 1, right):
                dp[left][right] = max(dp[left][right], a[left] * a[k] * a[right] + dp[left][k] + dp[k][right])
    return dp[0][n - 1]
```

### Q171. Advanced

**Distinct Subsequences**

Commonly reported in interviews at Google.

Return how many distinct ways `t` appears as a subsequence of `s`.

Example: `s = 'rabbbit'`, `t = 'rabbit'` returns `3`.

**Answer:**

DP. `dp[i][j]` is ways to form the first `j` characters of `t` from the first `i` of `s`. Always carry the ways that skip `s[i]`. If characters match, also add the ways that use this match.

**Complexity:** Time O(n * m), space O(m).

```python
def num_distinct(s, t):
    dp = [1] + [0] * len(t)
    for ch in s:
        for j in range(len(t), 0, -1):
            if ch == t[j - 1]:
                dp[j] += dp[j - 1]
    return dp[-1]
```

### Q172. Advanced

**Interleaving String**

Commonly reported in interviews at Google, Amazon.

Return true when `s3` is formed by interleaving `s1` and `s2` while preserving the order of each.

Example: `aabcc` and `dbbca` can form `aadbbcbcac`. They cannot form `aadbbbaccc`.

**Answer:**

DP. `dp[i][j]` means the first `i+j` characters of `s3` are an interleaving of the prefixes. A rolling boolean row is enough.

**Complexity:** Time O(n * m), space O(m).

```python
def is_interleave(s1, s2, s3):
    if len(s1) + len(s2) != len(s3):
        return False
    dp = [False] * (len(s2) + 1)
    dp[0] = True
    for j in range(1, len(s2) + 1):
        dp[j] = dp[j - 1] and s2[j - 1] == s3[j - 1]
    for i in range(1, len(s1) + 1):
        dp[0] = dp[0] and s1[i - 1] == s3[i - 1]
        for j in range(1, len(s2) + 1):
            take1 = dp[j] and s1[i - 1] == s3[i + j - 1]
            take2 = dp[j - 1] and s2[j - 1] == s3[i + j - 1]
            dp[j] = take1 or take2
    return dp[-1]
```

### Q173. Advanced

**Longest Valid Parentheses**

Commonly reported in interviews at Google, Amazon.

Return the length of the longest substring of correctly matched parentheses.

Example: `')()())'` returns `4`.

**Answer:**

A stack of indices, starting with `-1` as a base. On `)`, pop and the distance to the new top is a valid length. If the stack empties, push the current index as the new base. DP is an alternative.

**Complexity:** Time O(n), space O(n).

```python
def longest_valid_parentheses(s):
    stack = [-1]
    best = 0
    for i, ch in enumerate(s):
        if ch == '(':
            stack.append(i)
        else:
            stack.pop()
            if not stack:
                stack.append(i)
            else:
                best = max(best, i - stack[-1])
    return best
```

### Q174. Advanced

**Minimum Number of Taps / Jump coverage**

Commonly reported in interviews at Amazon, Google.

On a line of length `n`, tap `i` waters `[i - ranges[i], i + ranges[i]]`. Return the minimum taps that water `[0, n]`, or -1.

Example: This is the jump-game coverage problem in disguise.

**Answer:**

Convert each tap into the farthest reach achievable from each start point. Then run the jump-game-II greedy scan.

**Complexity:** Time O(n), space O(n).

```python
def min_taps(n, ranges):
    reach = [0] * (n + 1)
    for i, r in enumerate(ranges):
        left, right = max(0, i - r), min(n, i + r)
        reach[left] = max(reach[left], right)
    taps = end = far = 0
    for i in range(n + 1):
        if i > far:
            return -1
        if i > end:
            taps += 1
            end = far
        far = max(far, reach[i])
    return taps
```

### Q175. Advanced

**Shortest Path in a Grid with Obstacles Elimination**

Commonly reported in interviews at Google.

A grid has empty cells and obstacles. You may eliminate up to `k` obstacles. Return the shortest 4-directional path from the top left to the bottom right, or -1.

Example: With `k = 1`, one obstacle on the only short path can still be crossed.

**Answer:**

BFS state is `(row, col, eliminations_left)`. Visit each state once. The first time you reach the target is the shortest path.

**Complexity:** Time O(m * n * k), space O(m * n * k).

```python
def shortest_path(grid, k):
    from collections import deque
    m, n = len(grid), len(grid[0])
    q = deque([(0, 0, k, 0)])
    seen = {(0, 0, k)}
    while q:
        i, j, left, dist = q.popleft()
        if i == m - 1 and j == n - 1:
            return dist
        for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)):
            ni, nj = i + di, j + dj
            if not (0 <= ni < m and 0 <= nj < n):
                continue
            nleft = left - grid[ni][nj]
            if nleft >= 0 and (ni, nj, nleft) not in seen:
                seen.add((ni, nj, nleft))
                q.append((ni, nj, nleft, dist + 1))
    return -1
```

### Q176. Advanced

**Sliding Window Median**

Commonly reported in interviews at Google.

Return the median of every window of size `k`.

Example: `[1, 3, -1, -3, 5, 3, 6, 7]`, `k = 3` returns the medians of each window.

**Answer:**

Two heaps do not support deletion of an arbitrary outgoing element in O(log k) without lazy deletion. Lazy deletion plus a balance step works. In Python, `SortedList` from `sortedcontainers` makes the intent obvious; a balanced policy with two heaps is the dependency-free version.

**Complexity:** Time O(n log k), space O(k).

```python
def median_sliding(nums, k):
    import heapq
    low, high = [], []
    delayed = {}
    def prune(heap):
        while heap:
            v = -heap[0] if heap is low else heap[0]
            if delayed.get(v, 0):
                delayed[v] -= 1
                if delayed[v] == 0:
                    del delayed[v]
                heapq.heappop(heap)
            else:
                break
    def balance():
        if len(low) > len(high) + 1:
            heapq.heappush(high, -heapq.heappop(low))
        elif len(high) > len(low):
            heapq.heappush(low, -heapq.heappop(high))
        prune(low); prune(high)
    out = []
    for i, n in enumerate(nums):
        if not low or n <= -low[0]:
            heapq.heappush(low, -n)
        else:
            heapq.heappush(high, n)
        balance()
        if i >= k:
            old = nums[i - k]
            delayed[old] = delayed.get(old, 0) + 1
            if low and old <= -low[0]:
                prune(low)
            else:
                prune(high)
            balance()
        if i >= k - 1:
            if k % 2:
                out.append(float(-low[0]))
            else:
                out.append((-low[0] + high[0]) / 2)
    return out
```

### Q177. Intermediate

**Maximum Product Subarray**

Commonly reported in interviews at Amazon, LinkedIn, Google.

Return the largest product of any contiguous subarray. Values may be negative or zero.

Example: `[2, 3, -2, 4]` returns `6`. `[-2, 0, -1]` returns `0`.

**Answer:**

Track both the maximum and the minimum product ending here, because a negative value can turn the minimum into the maximum. A zero resets both.

**Complexity:** Time O(n), space O(1).

```python
def max_product(nums):
    best = hi = lo = nums[0]
    for n in nums[1:]:
        cands = (n, hi * n, lo * n)
        hi, lo = max(cands), min(cands)
        best = max(best, hi)
    return best
```

### Q178. Intermediate

**Next Permutation**

Commonly reported in interviews at Google, Amazon.

Rearrange a list of integers into the next greater permutation in lexicographic order. If it is already the last permutation, rearrange it into the lowest one. Do it in place.

Example: `[1, 2, 3]` becomes `[1, 3, 2]`. `[3, 2, 1]` becomes `[1, 2, 3]`.

**Answer:**

Find the rightmost ascent `nums[i] < nums[i+1]`. Swap `nums[i]` with the smallest later value that is still larger, then reverse the suffix.

**Complexity:** Time O(n), space O(1).

```python
def next_permutation(nums):
    i = len(nums) - 2
    while i >= 0 and nums[i] >= nums[i + 1]:
        i -= 1
    if i >= 0:
        j = len(nums) - 1
        while nums[j] <= nums[i]:
            j -= 1
        nums[i], nums[j] = nums[j], nums[i]
    nums[i + 1:] = reversed(nums[i + 1:])
    return nums
```

### Q179. Intermediate

**Find First and Last Position**

Commonly reported in interviews at Amazon, Facebook, Bloomberg.

A sorted list may contain duplicates. Return the first and last index of `target`, or `[-1, -1]`.

Example: `[5, 7, 7, 8, 8, 10]`, target `8` returns `[3, 4]`.

**Answer:**

Two binary searches: a lower bound for `target`, and a lower bound for `target + 1` minus one.

**Complexity:** Time O(log n), space O(1).

```python
def search_range(nums, target):
    def lower(x):
        lo, hi = 0, len(nums)
        while lo < hi:
            mid = (lo + hi) // 2
            if nums[mid] < x:
                lo = mid + 1
            else:
                hi = mid
        return lo
    left = lower(target)
    if left == len(nums) or nums[left] != target:
        return [-1, -1]
    return [left, lower(target + 1) - 1]
```

### Q180. Basic

**Integer Square Root**

Commonly reported in interviews at Amazon, Facebook, Microsoft.

Return the floor of the square root of a non-negative integer. Do not use a library sqrt.

Example: `8` returns `2`. `16` returns `4`.

**Answer:**

Binary search the answer from 0 through `n`. Compare `mid * mid` with `n`. Python integers do not overflow.

**Complexity:** Time O(log n), space O(1).

```python
def my_sqrt(n):
    lo, hi, ans = 0, n, 0
    while lo <= hi:
        mid = (lo + hi) // 2
        if mid * mid <= n:
            ans = mid
            lo = mid + 1
        else:
            hi = mid - 1
    return ans
```

### Q181. Basic

**Roman to Integer**

Commonly reported in interviews at Amazon, Microsoft, Google.

Convert a valid Roman numeral to an integer. Subtractive pairs are `IV`, `IX`, `XL`, `XC`, `CD`, and `CM`.

Example: `MCMXCIV` is `1994`.

**Answer:**

Walk left to right. If the current value is less than the next value, subtract it. Otherwise add it.

**Complexity:** Time O(n), space O(1).

```python
def roman_to_int(s):
    val = {'I': 1, 'V': 5, 'X': 10, 'L': 50, 'C': 100, 'D': 500, 'M': 1000}
    total = 0
    for i, ch in enumerate(s):
        if i + 1 < len(s) and val[ch] < val[s[i + 1]]:
            total -= val[ch]
        else:
            total += val[ch]
    return total
```

### Q182. Intermediate

**Integer to Roman**

Commonly reported in interviews at Amazon, Microsoft.

Convert an integer from 1 through 3999 into a Roman numeral using the standard subtractive forms.

Example: `1994` becomes `MCMXCIV`.

**Answer:**

Greedy. Walk a table of value-symbol pairs from 1000 down through 1, appending the symbol as many times as it fits.

**Complexity:** Time O(1) because the input is bounded. Space O(1).

```python
def int_to_roman(num):
    table = [(1000, 'M'), (900, 'CM'), (500, 'D'), (400, 'CD'), (100, 'C'), (90, 'XC'), (50, 'L'), (40, 'XL'), (10, 'X'), (9, 'IX'), (5, 'V'), (4, 'IV'), (1, 'I')]
    out = []
    for value, symbol in table:
        while num >= value:
            out.append(symbol)
            num -= value
    return ''.join(out)
```

### Q183. Intermediate

**String to Integer**

Commonly reported in interviews at Amazon, Microsoft, Bloomberg.

Parse a 32-bit signed integer from the start of a string. Skip leading spaces, accept an optional sign, and read digits. Clamp to `[-2**31, 2**31 - 1]`. Stop at the first non-digit. If no digit is found, return 0.

Example: `'   -42'` returns `-42`. `'4193 with words'` returns `4193`.

**Answer:**

A small state scan. Accumulate the number and clamp as soon as it leaves the 32-bit range.

**Complexity:** Time O(n), space O(1).

```python
def my_atoi(s):
    s = s.lstrip()
    if not s:
        return 0
    sign = 1
    i = 0
    if s[0] in '+-':
        sign = -1 if s[0] == '-' else 1
        i = 1
    n = 0
    while i < len(s) and s[i].isdigit():
        n = n * 10 + int(s[i])
        i += 1
    n *= sign
    return max(-2**31, min(2**31 - 1, n))
```

### Q184. Basic

**Valid Palindrome**

Commonly reported in interviews at Facebook, Microsoft, Apple.

Return true when the string is a palindrome after ignoring non-alphanumeric characters and case.

Example: `'A man, a plan, a canal: Panama'` is true.

**Answer:**

Two pointers. Skip characters that are not letters or digits, and compare with `casefold`.

**Complexity:** Time O(n), space O(1).

```python
def is_palindrome(s):
    lo, hi = 0, len(s) - 1
    while lo < hi:
        while lo < hi and not s[lo].isalnum():
            lo += 1
        while lo < hi and not s[hi].isalnum():
            hi -= 1
        if s[lo].casefold() != s[hi].casefold():
            return False
        lo += 1
        hi -= 1
    return True
```

### Q185. Basic

**Longest Common Prefix**

Commonly reported in interviews at Amazon, Google.

Return the longest prefix shared by every string in a non-empty list. Return an empty string when there is no common prefix.

Example: `['flower', 'flow', 'flight']` returns `'fl'`.

**Answer:**

Horizontal scan: start with the first string and shorten it until every other string starts with it. Vertical scan compares one character column at a time.

**Complexity:** Time O(total characters), space O(1) extra besides the answer.

```python
def longest_common_prefix(strs):
    prefix = strs[0]
    for word in strs[1:]:
        while not word.startswith(prefix):
            prefix = prefix[:-1]
            if not prefix:
                return ''
    return prefix
```

### Q186. Intermediate

**Evaluate Reverse Polish Notation**

Commonly reported in interviews at Amazon, LinkedIn, Google.

Tokens are integers or the operators `+`, `-`, `*`, and `/`. Division truncates toward zero. Evaluate the postfix expression.

Example: `['2', '1', '+', '3', '*']` returns `9`.

**Answer:**

A stack. Operands are pushed. An operator pops the right operand, then the left, and pushes the result. Python's `int(a / b)` truncates toward zero.

**Complexity:** Time O(n), space O(n).

```python
def eval_rpn(tokens):
    stack = []
    for tok in tokens:
        if tok in '+-*/':
            b, a = stack.pop(), stack.pop()
            if tok == '+':
                stack.append(a + b)
            elif tok == '-':
                stack.append(a - b)
            elif tok == '*':
                stack.append(a * b)
            else:
                stack.append(int(a / b))
        else:
            stack.append(int(tok))
    return stack[0]
```

### Q187. Intermediate

**Perfect Squares**

Commonly reported in interviews at Amazon, Google.

Return the least number of perfect squares that sum to `n`.

Example: `12` returns `3` because `4 + 4 + 4`. `13` returns `2` because `4 + 9`.

**Answer:**

Unbounded knapsack, or BFS over remainders. `dp[x] = 1 + min(dp[x - s])` for every square `s <= x`. Lagrange's four-square theorem says the answer is at most 4, which can prune a math solution.

**Complexity:** Time O(n * sqrt(n)), space O(n).

```python
def num_squares(n):
    dp = [0] + [n] * n
    for x in range(1, n + 1):
        s = 1
        while s * s <= x:
            dp[x] = min(dp[x], dp[x - s * s] + 1)
            s += 1
    return dp[n]
```

### Q188. Intermediate

**Unique Paths II**

Commonly reported in interviews at Amazon, Google.

Same as unique paths, but some cells are obstacles and cannot be entered. Return the number of paths from the top left to the bottom right.

Example: A grid with one obstacle in the only corridor returns 0.

**Answer:**

DP. An obstacle cell is 0. Any other cell is the sum of the ways to arrive from the left and from above.

**Complexity:** Time O(m * n), space O(n).

```python
def unique_paths_with_obstacles(grid):
    n = len(grid[0])
    row = [0] * n
    row[0] = 1
    for r in grid:
        for j in range(n):
            if r[j] == 1:
                row[j] = 0
            elif j:
                row[j] += row[j - 1]
    return row[-1]
```

### Q189. Basic

**Best Time to Buy and Sell Stock II**

Commonly reported in interviews at Amazon, Bloomberg.

You may complete as many buy-sell transactions as you want, but you may not hold more than one share. Return the maximum profit.

Example: `[7, 1, 5, 3, 6, 4]` returns `7`.

**Answer:**

Add every upward difference. Each ascent can be captured by buying before it and selling after it, and overlapping transactions are unnecessary.

**Complexity:** Time O(n), space O(1).

```python
def max_profit_ii(prices):
    return sum(max(0, b - a) for a, b in zip(prices, prices[1:]))
```

### Q190. Advanced

**Best Time to Buy and Sell Stock with Cooldown**

Commonly reported in interviews at Google, Amazon.

You may complete as many transactions as you want, but after you sell you must wait one day before buying again. Return the maximum profit.

Example: `[1, 2, 3, 0, 2]` returns `3`.

**Answer:**

Three states: holding, sold today (cooling), and free to buy. Roll them forward one day at a time.

**Complexity:** Time O(n), space O(1).

```python
def max_profit_cooldown(prices):
    hold, sold, rest = float('-inf'), 0, 0
    for p in prices:
        prev_sold = sold
        sold = hold + p
        hold = max(hold, rest - p)
        rest = max(rest, prev_sold)
    return max(sold, rest)
```

### Q191. Intermediate

**01 Matrix**

Commonly reported in interviews at Amazon, Google.

A binary matrix. For each cell, return the distance to the nearest 0. Movement is 4-directional.

Example: A cell that is already 0 has distance 0. Its neighbor has distance 1.

**Answer:**

Multi-source BFS from every 0. The first time a cell is reached is its shortest distance.

**Complexity:** Time O(m * n), space O(m * n).

```python
def update_matrix(mat):
    from collections import deque
    m, n = len(mat), len(mat[0])
    q = deque()
    dist = [[-1] * n for _ in range(m)]
    for i in range(m):
        for j in range(n):
            if mat[i][j] == 0:
                dist[i][j] = 0
                q.append((i, j))
    while q:
        i, j = q.popleft()
        for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)):
            ni, nj = i + di, j + dj
            if 0 <= ni < m and 0 <= nj < n and dist[ni][nj] < 0:
                dist[ni][nj] = dist[i][j] + 1
                q.append((ni, nj))
    return dist
```

### Q192. Intermediate

**Is Graph Bipartite**

Commonly reported in interviews at Amazon, Facebook, Google.

An undirected graph is given as an adjacency list. Return true when the nodes can be colored with two colors so every edge connects different colors.

Example: A triangle is not bipartite. A square is.

**Answer:**

BFS or DFS coloring. If a neighbor already has the same color, the graph is not bipartite. Repeat for every component.

**Complexity:** Time O(V + E), space O(V).

```python
def is_bipartite(graph):
    color = {}
    def dfs(u, c):
        if u in color:
            return color[u] == c
        color[u] = c
        return all(dfs(v, 1 - c) for v in graph[u])
    return all(u in color or dfs(u, 0) for u in range(len(graph)))
```

### Q193. Advanced

**Count Complete Tree Nodes**

Commonly reported in interviews at Google, LinkedIn.

A complete binary tree has every level filled except possibly the last, which is filled from the left. Return the number of nodes faster than a full traversal in the average case.

Example: A perfect tree of height h has `2^(h+1) - 1` nodes.

**Answer:**

Compare the left-spine height with the right-spine height. If they match, the tree is perfect. Otherwise recurse into the child that is not a perfect subtree you already counted. This is O(h^2).

**Complexity:** Time O(h^2), which is O((log n)^2). Space O(h).

```python
def count_nodes(root):
    def height(node):
        h = 0
        while node:
            h += 1
            node = node.left
        return h
    if not root:
        return 0
    L, R = height(root.left), height(root.right)
    if L == R:
        return (1 << L) + count_nodes(root.right)
    return (1 << R) + count_nodes(root.left)
```

### Q194. Intermediate

**Binary Search Tree Iterator**

Commonly reported in interviews at Facebook, Amazon, Microsoft.

Implement an iterator over a BST that returns the next smallest value, with `next` and `has_next` amortized O(1) and O(h) memory.

Example: The sequence of `next` calls is the inorder traversal.

**Answer:**

Keep an explicit stack of the left spine. `next` pops a node and pushes the left spine of its right child.

**Complexity:** Construction and each `next` are amortized O(1). Space O(h).

```python
class BSTIterator:
    def __init__(self, root):
        self.stack = []
        self._push(root)
    def _push(self, node):
        while node:
            self.stack.append(node)
            node = node.left
    def next(self):
        node = self.stack.pop()
        self._push(node.right)
        return node.val
    def has_next(self):
        return bool(self.stack)
```

### Q195. Basic

**Convert Sorted Array to BST**

Commonly reported in interviews at Amazon, Microsoft.

Build a height-balanced BST from a sorted list of distinct integers.

Example: `[-10, -3, 0, 5, 9]` has 0 as a valid root.

**Answer:**

The middle element is the root. Recurse on the left half and the right half.

**Complexity:** Time O(n), space O(log n) for the recursion of a balanced tree.

```python
def sorted_array_to_bst(nums):
    def build(lo, hi):
        if lo > hi:
            return None
        mid = (lo + hi) // 2
        node = _T(nums[mid])
        node.left = build(lo, mid - 1)
        node.right = build(mid + 1, hi)
        return node
    return build(0, len(nums) - 1)

class _T:
    def __init__(self, val):
        self.val, self.left, self.right = val, None, None
```

### Q196. Intermediate

**Intersection of Two Linked Lists**

Commonly reported in interviews at Amazon, Microsoft, Bloomberg.

Two singly linked lists may merge and share a tail. Return the first shared node, or null. Do not modify the lists.

Example: If the lists are different lengths, the shared node is not at the same index from each head.

**Answer:**

Walk both pointers. When one reaches the end, redirect it to the other head. They meet at the intersection after at most two passes, or both become null.

**Complexity:** Time O(n + m), space O(1).

```python
def intersection(a, b):
    p, q = a, b
    while p is not q:
        p = p.next if p else b
        q = q.next if q else a
    return p
```

### Q197. Intermediate

**Minimum Size Subarray Sum**

Commonly reported in interviews at Amazon, Facebook.

A list of positive integers. Return the length of the shortest contiguous subarray whose sum is at least `target`, or 0 if none exists.

Example: `target = 7`, `[2, 3, 1, 2, 4, 3]` returns `2` because of `[4, 3]`.

**Answer:**

Sliding window. Expand the right edge, and shrink the left edge while the sum stays at least the target.

**Complexity:** Time O(n), space O(1).

```python
def min_subarray_len(target, nums):
    left = total = 0
    best = len(nums) + 1
    for right, n in enumerate(nums):
        total += n
        while total >= target:
            best = min(best, right - left + 1)
            total -= nums[left]
            left += 1
    return best if best <= len(nums) else 0
```

### Q198. Basic

**Rotate Array**

Commonly reported in interviews at Microsoft, Amazon.

Rotate a list to the right by `k` steps. `k` may be larger than the length.

Example: `[1, 2, 3, 4, 5]`, `k = 2` becomes `[4, 5, 1, 2, 3]`.

**Answer:**

Reduce `k` modulo n. Reverse the whole list, then reverse the first `k` items, then reverse the rest. Three reversals do it in place.

**Complexity:** Time O(n), space O(1).

```python
def rotate(nums, k):
    n = len(nums)
    k %= n
    def rev(a, b):
        while a < b:
            nums[a], nums[b] = nums[b], nums[a]
            a += 1
            b -= 1
    rev(0, n - 1)
    rev(0, k - 1)
    rev(k, n - 1)
    return nums
```

### Q199. Intermediate

**Multiply Strings**

Commonly reported in interviews at Facebook, Amazon.

Two non-negative integers are given as strings. Return their product as a string. Do not convert the whole inputs with `int` if you want to show the grade-school algorithm; the result must still be exact.

Example: `'123'` times `'45'` is `'5535'`.

**Answer:**

Grade-school multiplication into an array of digit places. `num1[i] * num2[j]` lands at index `i + j + 1`, then carry forward.

**Complexity:** Time O(n * m), space O(n + m).

```python
def multiply(num1, num2):
    if num1 == '0' or num2 == '0':
        return '0'
    places = [0] * (len(num1) + len(num2))
    for i, a in enumerate(reversed(num1)):
        for j, b in enumerate(reversed(num2)):
            places[i + j] += int(a) * int(b)
    carry = 0
    for i, val in enumerate(places):
        carry, places[i] = divmod(val + carry, 10)
    while places and places[-1] == 0:
        places.pop()
    return ''.join(str(d) for d in reversed(places))
```

### Q200. Basic

**Number of 1 Bits**

Commonly reported in interviews at Amazon, Apple, Microsoft.

Return how many `1` bits the two's-complement representation of a non-negative integer contains. In a 32-bit interview variant, only the low 32 bits count; here count every bit of the Python int.

Example: `11` is `1011` and returns `3`.

**Answer:**

`n & (n - 1)` clears the lowest set bit. Count how many times you can do that. Python 3.10+ also has `int.bit_count()`.

**Complexity:** Time O(number of set bits), space O(1).

```python
def hamming_weight(n):
    count = 0
    while n:
        n &= n - 1
        count += 1
    return count
```

*Section size: 200 questions (Basic 38, Intermediate 63, Advanced 99).*

---

Total questions: 3200.
