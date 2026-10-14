## 6. List (list)

A mutable ordered sequence. Aliasing, slice assignment, and sorting stability are the usual follow-ups.

### Q1. Basic

What does this print?

```python
print(list())
```

**Answer:**

```text
[]
```

An empty call to `list()` builds a new empty list.

### Q2. Basic

What does this print?

```python
print([])
```

**Answer:**

```text
[]
```

The `[]` literal is the usual way to write an empty list.

### Q3. Basic

What does this print?

```python
print(list('ab'))
```

**Answer:**

```text
['a', 'b']
```

`list` on a string splits it into one-character strings.

### Q4. Basic

What does this print?

```python
print(list(range(3)))
```

**Answer:**

```text
[0, 1, 2]
```

`range(3)` yields 0, 1, 2. `list` materializes that sequence.

### Q5. Basic

What does this print?

```python
print(list((1, 2)))
```

**Answer:**

```text
[1, 2]
```

A tuple is iterable, so `list` copies its elements into a new list.

### Q6. Basic

What does this print?

```python
a = [1, 2, 3]
print(len(a), type(a))
```

**Answer:**

```text
3 <class 'list'>
```

Square brackets build a list. `len` counts elements.

### Q7. Basic

What does this print?

```python
print([1] * 3)
```

**Answer:**

```text
[1, 1, 1]
```

Repeating a list with `*` concatenates shallow copies of the same list object.

### Q8. Basic

What does this print?

```python
print([[0]] * 3)
```

**Answer:**

```text
[[0], [0], [0]]
```

Each slot references the same inner list. This is a common aliasing trap.

### Q9. Basic

What does this print?

```python
row = [[0]] * 3
row[0].append(1)
print(row)
```

**Answer:**

```text
[[0, 1], [0, 1], [0, 1]]
```

Mutating one inner list mutates all three slots because they alias one object.

### Q10. Basic

What does this print?

```python
print([None] * 4)
```

**Answer:**

```text
[None, None, None, None]
```

Repeating a list of immutables is safe: each slot holds the same `None`, which you do not mutate.

### Q11. Basic

What does this print?

```python
a = [10, 20, 30]
print(a[0], a[1], a[2])
```

**Answer:**

```text
10 20 30
```

Indices start at 0.

### Q12. Basic

What does this print?

```python
a = [10, 20, 30]
print(a[-1], a[-2], a[-3])
```

**Answer:**

```text
30 20 10
```

Negative indices count from the end. `-1` is the last element.

### Q13. Basic

What happens when this runs?

```python
a = [1, 2]
print(a[2])
```

**Answer:**

```text
IndexError: list index out of range
```

Index 2 is out of range for a two-element list.

### Q14. Basic

What happens when this runs?

```python
a = [1, 2]
print(a[-3])
```

**Answer:**

```text
IndexError: list index out of range
```

Index `-3` is out of range when `len(a)` is 2.

### Q15. Basic

What does this print?

```python
a = [1, 2, 3]
a[1] = 99
print(a)
```

**Answer:**

```text
[1, 99, 3]
```

Lists are mutable. Assignment at an index replaces one element.

### Q16. Intermediate

What does this print?

```python
a = [1, 2, 3, 4, 5]
print(a[1:4])
```

**Answer:**

```text
[2, 3, 4]
```

Slice `start:stop` includes `start` and excludes `stop`.

### Q17. Basic

What does this print?

```python
a = [1, 2, 3]
print(a[:2], a[2:])
```

**Answer:**

```text
[1, 2] [3]
```

Omitted bounds mean 'from the start' or 'through the end'.

### Q18. Basic

What does this print?

```python
a = [1, 2, 3]
print(a[::2])
```

**Answer:**

```text
[1, 3]
```

A step of 2 takes every other element.

### Q19. Basic

What does this print?

```python
a = [1, 2, 3]
print(a[::-1])
```

**Answer:**

```text
[3, 2, 1]
```

Step `-1` reverses a copy of the sequence.

### Q20. Intermediate

What does this print?

```python
a = [1, 2, 3]
b = a[1:2]
b.append(9)
print(a, b)
```

**Answer:**

```text
[1, 2, 3] [2, 9]
```

Slicing always produces a new list. Mutating `b` does not change `a`.

### Q21. Intermediate

What does this print?

```python
a = [1, 2, 3, 4]
a[1:3] = [20, 30, 40]
print(a)
```

**Answer:**

```text
[1, 20, 30, 40, 4]
```

Slice assignment can change the length by replacing a run with a different number of items.

### Q22. Intermediate

What does this print?

```python
a = [1, 2, 3, 4]
a[1:1] = [9]
print(a)
```

**Answer:**

```text
[1, 9, 2, 3, 4]
```

An empty slice at index 1 inserts without removing elements.

### Q23. Intermediate

What does this print?

```python
a = [1, 2, 3, 4]
del a[1:3]
print(a)
```

**Answer:**

```text
[1, 4]
```

`del a[i:j]` removes that slice in place.

### Q24. Advanced

What does this print?

```python
a = [0, 1, 2, 3, 4]
a[::2] = [10, 20, 30]
print(a)
```

**Answer:**

```text
[10, 1, 20, 3, 30]
```

Extended slice assignment requires the right-hand side length to match the number of slots selected by the step.

### Q25. Basic

What does this print?

```python
a = [1, 2]
b = a
b.append(3)
print(a, b)
```

**Answer:**

```text
[1, 2, 3] [1, 2, 3]
```

Assignment binds another name to the same list object.

### Q26. Intermediate

What does this print?

```python
a = [1, 2]
b = a
print(a is b)
```

**Answer:**

```text
True
```

Two names for one object compare identical with `is`.

### Q27. Intermediate

What does this print?

```python
a = [1, 2]
b = a[:]
b.append(3)
print(a, b)
```

**Answer:**

```text
[1, 2] [1, 2, 3]
```

A full slice `[:]` makes a shallow copy: new outer list, same inner objects if any.

### Q28. Intermediate

What does this print?

```python
import copy
a = [[1], [2]]
b = a[:]
b[0].append(9)
print(a, b)
```

**Answer:**

```text
[[1, 9], [2]] [[1, 9], [2]]
```

Shallow copy shares nested mutable objects.

### Q29. Intermediate

What does this print?

```python
import copy
a = [[1], [2]]
b = copy.copy(a)
b[0].append(9)
print(a, b)
```

**Answer:**

```text
[[1, 9], [2]] [[1, 9], [2]]
```

`copy.copy` is also shallow for a list of lists.

### Q30. Advanced

What does this print?

```python
import copy
a = [[1], [2]]
b = copy.deepcopy(a)
b[0].append(9)
print(a, b)
```

**Answer:**

```text
[[1], [2]] [[1, 9], [2]]
```

`deepcopy` recursively duplicates nested mutables.

### Q31. Basic

What does this print?

```python
a = [1, 2]
b = [3]
print(a + b)
```

**Answer:**

```text
[1, 2, 3]
```

`+` builds a new list from the concatenation of two lists.

### Q32. Basic

What does this print?

```python
a = [1, 2]
a += [3]
print(a)
```

**Answer:**

```text
[1, 2, 3]
```

`+=` on a list extends in place (like `extend`), then rebinds the same object.

### Q33. Intermediate

What does this print?

```python
a = [1, 2]
b = a
a += [3]
print(a, b, a is b)
```

**Answer:**

```text
[1, 2, 3] [1, 2, 3] True
```

In-place extend keeps identity; `b` still refers to the same object.

### Q34. Basic

What does this print?

```python
a = [1, 2]
a.append([3])
print(a)
```

**Answer:**

```text
[1, 2, [3]]
```

`append` adds one object as a single new element, even when that object is a list.

### Q35. Basic

What does this print?

```python
a = [1, 2]
a.extend([3, 4])
print(a)
```

**Answer:**

```text
[1, 2, 3, 4]
```

`extend` iterates its argument and appends each item.

### Q36. Intermediate

What happens when this runs?

```python
a = [1, 2]
a.extend(3)
```

**Answer:**

```text
TypeError: 'int' object is not iterable
```

An int is not iterable, so `extend(3)` raises `TypeError`.

### Q37. Intermediate

What happens when this runs?

```python
a = [1, 2]
print(a + (3,))
```

**Answer:**

```text
TypeError: can only concatenate list (not "tuple") to list
```

List `+` requires another list; adding a tuple raises `TypeError`.

### Q38. Basic

What does this print?

```python
a = [1]
a = a + [2]
print(a)
```

**Answer:**

```text
[1, 2]
```

Rebinding `a` to `a + [2]` creates a new list; it does not mutate the old object unless something else still holds a reference.

### Q39. Basic

What does this print?

```python
a = [3, 1, 2]
print(sorted(a), a)
```

**Answer:**

```text
[1, 2, 3] [3, 1, 2]
```

`sorted` returns a new list and leaves the original unchanged.

### Q40. Basic

What does this print?

```python
a = [3, 1, 2]
a.sort()
print(a)
```

**Answer:**

```text
[1, 2, 3]
```

`list.sort` sorts in place and returns `None`.

### Q41. Intermediate

What does this print?

```python
a = [3, 1, 2]
print(a.sort())
```

**Answer:**

```text
None
```

The return value of `sort()` is `None`, which is what gets printed.

### Q42. Intermediate

What does this print?

```python
a = [(1, 'b'), (1, 'a'), (2, 'z')]
print(sorted(a))
```

**Answer:**

```text
[(1, 'a'), (1, 'b'), (2, 'z')]
```

Tuples compare lexicographically: first by the first element, then the second.

### Q43. Advanced

What does this print?

```python
from functools import cmp_to_key
a = [3, 1, 2]
print(sorted(a, key=cmp_to_key(lambda x, y: (y > x) - (y < x))))
```

**Answer:**

```text
[3, 2, 1]
```

A cmp-style key can emulate reverse numeric order. Prefer `reverse=True` in real code.

### Q44. Intermediate

What does this print?

```python
a = ['10', '2', '1']
print(sorted(a), sorted(a, key=int))
```

**Answer:**

```text
['1', '10', '2'] ['1', '2', '10']
```

Default sort is lexicographic on strings. `key=int` sorts by numeric value.

### Q45. Advanced

What does this print?

```python
a = [3, 1, 2, 1]
print(sorted(a, reverse=True))
```

**Answer:**

```text
[3, 2, 1, 1]
```

`reverse=True` requests descending order.

### Q46. Advanced

What does this print?

```python
a = [(0, 'a'), (0, 'b'), (1, 'c')]
print(sorted(a, key=lambda t: t[0]))
```

**Answer:**

```text
[(0, 'a'), (0, 'b'), (1, 'c')]
```

When keys tie, Python's sort is stable: relative order of equal keys is preserved.

### Q47. Basic

What does this print?

```python
a = [1, 2, 3]
print(a.pop(), a)
```

**Answer:**

```text
3 [1, 2]
```

`pop()` removes and returns the last item by default.

### Q48. Basic

What does this print?

```python
a = [1, 2, 3]
print(a.pop(0), a)
```

**Answer:**

```text
1 [2, 3]
```

`pop(i)` removes at index `i`.

### Q49. Basic

What does this print?

```python
a = [1, 2, 2, 3]
print(a.remove(2), a)
```

**Answer:**

```text
None [1, 2, 3]
```

`remove` deletes the first matching value and returns `None`.

### Q50. Intermediate

What happens when this runs?

```python
a = [1, 2, 3]
a.remove(9)
```

**Answer:**

```text
ValueError: list.remove(x): x not in list
```

If the value is missing, `remove` raises `ValueError`.

### Q51. Basic

What does this print?

```python
a = [1, 2, 3]
a.insert(1, 9)
print(a)
```

**Answer:**

```text
[1, 9, 2, 3]
```

`insert(i, x)` shifts elements at `i` and later to the right.

### Q52. Basic

What does this print?

```python
a = [1, 2, 2, 3]
print(a.index(2), a.count(2))
```

**Answer:**

```text
1 2
```

`index` finds the first position; `count` tallies all matches.

### Q53. Intermediate

What happens when this runs?

```python
a = [1, 2, 3]
print(a.index(9))
```

**Answer:**

```text
ValueError: 9 is not in list
```

`index` raises `ValueError` when the value is absent.

### Q54. Basic

What does this print?

```python
a = [1, 2, 3]
print(2 in a, 9 in a)
```

**Answer:**

```text
True False
```

`in` membership tests scan the list.

### Q55. Basic

What does this print?

```python
a = [3, 1, 4]
print(min(a), max(a), sum(a))
```

**Answer:**

```text
1 4 8
```

These builtins accept any iterable; for lists they scan all elements.

### Q56. Basic

What does this print?

```python
print(sum([1, 2, 3], 10))
```

**Answer:**

```text
16
```

The optional `start` argument is added into the total.

### Q57. Intermediate

What does this print?

```python
a = ['bb', 'a', 'ccc']
print(min(a), max(a))
```

**Answer:**

```text
a ccc
```

Strings compare lexicographically.

### Q58. Intermediate

What happens when this runs?

```python
print(min([]))
```

**Answer:**

```text
ValueError: min() iterable argument is empty
```

An empty iterable has no minimum.

### Q59. Basic

What does this print?

```python
print([x * 2 for x in [1, 2, 3]])
```

**Answer:**

```text
[2, 4, 6]
```

A list comprehension builds a new list from an expression over an iterable.

### Q60. Basic

What does this print?

```python
print([x for x in range(5) if x % 2])
```

**Answer:**

```text
[1, 3]
```

The `if` clause filters which values enter the result.

### Q61. Intermediate

What does this print?

```python
print([[i * j for j in range(1, 3)] for i in range(1, 3)])
```

**Answer:**

```text
[[1, 2], [2, 4]]
```

Nested comprehensions build a list of lists.

### Q62. Intermediate

What does this print?

```python
a = [1, 2, 3]
b = [x for x in a]
print(a is b, a == b)
```

**Answer:**

```text
False True
```

Comprehension over a list produces a new list with equal contents, not the same object.

### Q63. Advanced

What does this print?

```python
print([x for x in [1, 2, 3] for y in [10, 20]])
```

**Answer:**

```text
[1, 1, 2, 2, 3, 3]
```

Nested loops in a comprehension follow left-to-right nesting order.

### Q64. Advanced

What does this print?

```python
matrix = [[1, 2], [3, 4]]
print([c for row in matrix for c in row])
```

**Answer:**

```text
[1, 2, 3, 4]
```

This flattens one level by iterating rows then cells.

### Q65. Basic

What does this print?

```python
a, b, c = [1, 2, 3]
print(b)
```

**Answer:**

```text
2
```

Unpacking assigns one name per slot; there must be exactly as many names as elements.

### Q66. Intermediate

What does this print?

```python
first, *rest = [1, 2, 3, 4]
print(first, rest)
```

**Answer:**

```text
1 [2, 3, 4]
```

Star unpacking collects leftover items into a list.

### Q67. Basic

What does this print?

```python
print(list(zip([1, 2], ['a', 'b'])))
```

**Answer:**

```text
[(1, 'a'), (2, 'b')]
```

`zip` pairs elements until the shortest input is exhausted.

### Q68. Intermediate

What does this print?

```python
print(list(zip([1, 2], ['a', 'b'], strict=True)))
```

**Answer:**

```text
[(1, 'a'), (2, 'b')]
```

With equal lengths, `strict=True` behaves like ordinary `zip`.

### Q69. Intermediate

What happens when this runs?

```python
print(list(zip([1, 2, 3], ['a', 'b'], strict=True)))
```

**Answer:**

```text
ValueError: zip() argument 2 is shorter than argument 1
```

With unequal lengths, strict zip raises `ValueError`.

### Q70. Basic

What does this print?

```python
print(list(enumerate(['a', 'b'])))
```

**Answer:**

```text
[(0, 'a'), (1, 'b')]
```

`enumerate` yields `(index, value)` pairs.

### Q71. Intermediate

What does this print?

```python
print(list(map(str, [1, 2, 3])))
```

**Answer:**

```text
['1', '2', '3']
```

`map` applies a function to each item and returns an iterator; `list` consumes it.

### Q72. Intermediate

What does this print?

```python
print(list(filter(None, [0, 1, '', 'x'])))
```

**Answer:**

```text
[1, 'x']
```

`filter(None, ...)` keeps values that are truthy.

### Q73. Intermediate

What does this print?

```python
print([str(x) for x in [1, 2, 3]])
```

**Answer:**

```text
['1', '2', '3']
```

A comprehension is often clearer than `map` when the transformation is a simple expression.

### Q74. Advanced

What happens when this runs?

```python
a = [1, 2, 3, 4]
for x in a:
    if x % 2 == 0:
        a.remove(x)
print(a)
```

**Answer:**

```text
[1, 3]
```

Removing items while iterating forward skips the next element after a deletion.

### Q75. Advanced

What does this print?

```python
a = [1, 2, 3, 4]
for x in list(a):
    if x % 2 == 0:
        a.remove(x)
print(a)
```

**Answer:**

```text
[1, 3]
```

Iterating a snapshot (`list(a)`) avoids skipping during in-place removal.

### Q76. Advanced

What does this print?

```python
a = [1, 2, 3]
for i, x in enumerate(a):
    a[i] = x * 10
print(a)
```

**Answer:**

```text
[10, 20, 30]
```

Replacing by index while iterating the same length is safe here because the length stays fixed.

### Q77. Basic

What does this print?

```python
print(bool([]), bool([0]))
```

**Answer:**

```text
False True
```

An empty list is falsy. A non-empty list is truthy even if elements are falsy.

### Q78. Basic

What does this print?

```python
a = [1, 2, 3]
print(a * 0, a * 1)
```

**Answer:**

```text
[] [1, 2, 3]
```

Multiplying a list by 0 yields `[]`; by 1 yields an equal-length copy of references.

### Q79. Intermediate

What does this print?

```python
a = [1, 2]
print(id(a), id(a[:]))
```

**Answer:**

```text
136103314576512 136103314502272
```

A slice copy is a new object with a different `id`.

### Q80. Intermediate

What does this print?

```python
a = [1, 2, 3]
print(a[100:200])
```

**Answer:**

```text
[]
```

Slices clamp out-of-range indices instead of raising.

### Q81. Intermediate

What does this print?

```python
a = [1, 2, 3]
print(a[-100:100])
```

**Answer:**

```text
[1, 2, 3]
```

Both bounds are clamped to the list length.

### Q82. Intermediate

What does this print?

```python
print(list({1: 'a', 2: 'b'}))
```

**Answer:**

```text
[1, 2]
```

Iterating a dict yields its keys; `list(dict)` is those keys in insertion order.

### Q83. Intermediate

What does this print?

```python
print(sorted(set([3, 1, 2, 2])))
```

**Answer:**

```text
[1, 2, 3]
```

`set` removes duplicates; `sorted` returns a new list.

### Q84. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a.__iadd__([4]) or a)
```

**Answer:**

```text
[1, 2, 3, 4]
```

`__iadd__` extends in place; the expression value is `None`, so `or` yields `a`.

### Q85. Advanced

What does this print?

```python
print([*range(3), *range(3, 5)])
```

**Answer:**

```text
[0, 1, 2, 3, 4]
```

Unpacking inside a display splices iterables into one list.

### Q86. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a[::-1][::-1] == a)
```

**Answer:**

```text
True
```

Double reversal with slices yields an equal list, but still a copy unless assigned back.

### Q87. Intermediate

What does this print?

```python
print([1, 2] == [1.0, 2.0])
```

**Answer:**

```text
True
```

List equality compares elements with `==`, so int and float can match.

### Q88. Advanced

What does this print?

```python
a = []
a.append(a)
print(len(a), a[0] is a)
```

**Answer:**

```text
1 True
```

A list can contain itself; `a[0] is a` shows the self-reference.

### Q89. Intermediate

What does this print?

```python
print(list(reversed([1, 2, 3])))
```

**Answer:**

```text
[3, 2, 1]
```

`reversed` returns an iterator; `list` materializes reversed order.

### Q90. Basic

What does this print?

```python
a = [3, 1, 2]
print(list(reversed(sorted(a))))
```

**Answer:**

```text
[3, 2, 1]
```

Sort ascending, then reverse that order for descending sorted output.

### Q91. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a.clear(), a)
```

**Answer:**

```text
None []
```

`clear()` removes all items in place and returns `None`.

### Q92. Intermediate

What does this print?

```python
a = [1, 2, 3]
print(a.copy(), a)
```

**Answer:**

```text
[1, 2, 3] [1, 2, 3]
```

`copy()` is equivalent to `[:]` for lists: shallow copy of the outer list.

### Q93. Advanced

What does this print?

```python
import operator
a = [5, 2, 8]
print(sorted(a, key=operator.itemgetter(0)) if False else sorted(a))
```

**Answer:**

```text
[2, 5, 8]
```

Plain sort on ints uses numeric order: 2, 5, 8.

### Q94. Intermediate

What does this print?

```python
print([i for i in range(3)])
print([i for i in range(3)])
```

**Answer:**

```text
[0, 1, 2]
[0, 1, 2]
```

Each comprehension creates a fresh list; two equal lists are not necessarily the same object.

### Q95. Advanced

What does this print?

```python
a = [1, 2, 3, 4]
print(a[1:-1])
```

**Answer:**

```text
[2, 3]
```

Slice end `-1` excludes the last element.

### Q96. Basic

What does this print?

```python
print(list(''))
```

**Answer:**

```text
[]
```

The empty string yields an empty list.

### Q97. Basic

What does this print?

```python
print(list(map(int, ['1', '2'])))
```

**Answer:**

```text
[1, 2]
```

Map can convert each string before `list` collects results.

### Q98. Basic

What does this print?

```python
a = [1, 2, 3]
print(a[0:0])
```

**Answer:**

```text
[]
```

A zero-width slice at the start is an empty new list.

### Q99. Basic

What does this print?

```python
print([1, 2] == [1, 2])
```

**Answer:**

```text
True
```

List equality compares length and each element with `==`.

### Q100. Basic

What does this print?

```python
print([1] < [2])
```

**Answer:**

```text
True
```

Lists compare lexicographically element by element.

### Q101. Basic

What does this print?

```python
print([2] < [1, 9])
```

**Answer:**

```text
False
```

When prefixes match, the shorter list is smaller.

### Q102. Basic

What does this print?

```python
a = [1, 2, 3]
print(1 in a, [1, 2] in a)
```

**Answer:**

```text
True False
```

Membership uses equality on elements; sublists are single elements.

### Q103. Basic

What does this print?

```python
a = [1, 2, 3]
print(a[-0])
```

**Answer:**

```text
1
```

`-0` is `0`, so this is the first element.

### Q104. Basic

What does this print?

```python
print(list(range(1, 5, 2)))
```

**Answer:**

```text
[1, 3]
```

`range` with a step skips values.

### Q105. Basic

What does this print?

```python
a = [10, 20]
print(a.pop(), len(a))
```

**Answer:**

```text
20 1
```

After one pop, one element remains.

### Q106. Basic

What does this print?

```python
a = [1, 2, 3]
del a[0]
print(a)
```

**Answer:**

```text
[2, 3]
```

`del a[0]` removes the head in place.

### Q107. Basic

What does this print?

```python
print([None, 0, ''][::1])
```

**Answer:**

```text
[None, 0, '']
```

A full slice with step 1 copies all elements into a new list.

### Q108. Basic

What does this print?

```python
a = [1, 2]
print(a * 2)
```

**Answer:**

```text
[1, 2, 1, 2]
```

Replication concatenates the list with itself.

### Q109. Basic

What does this print?

```python
print(len([[]]))
```

**Answer:**

```text
1
```

The outer list has one element (an inner list).

### Q110. Basic

What does this print?

```python
a = [3, 1, 2]
print(min(a), sorted(a)[0])
```

**Answer:**

```text
1 1
```

Minimum equals the first element of ascending sort for distinct values.

### Q111. Basic

What does this print?

```python
print(sum([[1], [2]], []))
```

**Answer:**

```text
[1, 2]
```

Starting `sum` with `[]` concatenates nested lists when adding list elements.

### Q112. Basic

What does this print?

```python
a = [1, 2, 3]
print(a.index(1), a.index(3))
```

**Answer:**

```text
0 2
```

`index` returns the position of the first match.

### Q113. Basic

What does this print?

```python
print(bool([False]))
```

**Answer:**

```text
True
```

The list itself is non-empty, so it is truthy.

### Q114. Basic

What does this print?

```python
a = [1, 2, 3]
print(a + [])
```

**Answer:**

```text
[1, 2, 3]
```

Adding an empty list returns a new copy with the same elements.

### Q115. Basic

What does this print?

```python
a = [1, 2, 3]
a.reverse()
print(a)
```

**Answer:**

```text
[3, 2, 1]
```

`reverse()` mutates order in place.

### Q116. Basic

What does this print?

```python
print(list('xy'))
```

**Answer:**

```text
['x', 'y']
```

Strings iterate by character.

### Q117. Basic

What does this print?

```python
print([*'ab'])
```

**Answer:**

```text
['a', 'b']
```

Unpacking a string inside a display splices characters.

### Q118. Basic

What does this print?

```python
a = [1, 2, 3]
print(a[1:3] + a[3:])
```

**Answer:**

```text
[2, 3]
```

Concatenating slices rebuilds the tail without sharing.

### Q119. Basic

What does this print?

```python
print([x for x in 'abc'])
```

**Answer:**

```text
['a', 'b', 'c']
```

Comprehension over a string yields characters.

### Q120. Intermediate

What does this print?

```python
a = [1, 2, 3]
b = a
a = a + [4]
print(b, a)
```

**Answer:**

```text
[1, 2, 3] [1, 2, 3, 4]
```

Rebinding `a` after `+` leaves `b` pointing at the original list.

### Q121. Intermediate

What does this print?

```python
a = [1, 2, 3]
print(a[5:10])
```

**Answer:**

```text
[]
```

Out-of-range slice endpoints are clamped; result is empty here.

### Q122. Intermediate

What does this print?

```python
a = list(range(5))
print(a[2:4], a[4:2])
```

**Answer:**

```text
[2, 3] []
```

If start exceeds stop with a positive step, the slice is empty.

### Q123. Intermediate

What does this print?

```python
a = [1, 2, 3, 4]
print(a[::-2])
```

**Answer:**

```text
[4, 2]
```

Negative step walks from the end toward the start.

### Q124. Intermediate

What does this print?

```python
a = [1, 2, 3, 4, 5]
print(a[1:4:2])
```

**Answer:**

```text
[2, 4]
```

Extended slicing takes indices 1 and 3.

### Q125. Intermediate

What does this print?

```python
a = [1, 2, 3]
a[0:2] = []
print(a)
```

**Answer:**

```text
[3]
```

Assigning an empty list to a slice deletes that span.

### Q126. Intermediate

What does this print?

```python
a = [1, 2, 3]
print(list(reversed(a)), a)
```

**Answer:**

```text
[3, 2, 1] [1, 2, 3]
```

`reversed` does not mutate; the original order stays.

### Q127. Intermediate

What does this print?

```python
a = [(1, 2), (0, 9)]
print(sorted(a))
```

**Answer:**

```text
[(0, 9), (1, 2)]
```

Tuples sort by first element, then second.

### Q128. Intermediate

What does this print?

```python
a = ['a', 'B']
print(sorted(a, key=str.lower))
```

**Answer:**

```text
['a', 'B']
```

`key` transforms each item before comparison.

### Q129. Intermediate

What does this print?

```python
a = [1, 2, 3]
print(list(zip(a, a)))
```

**Answer:**

```text
[(1, 1), (2, 2), (3, 3)]
```

Zipping a list with itself pairs each index with itself.

### Q130. Intermediate

What does this print?

```python
print(list(zip(*[(1, 'a'), (2, 'b')])))
```

**Answer:**

```text
[(1, 2), ('a', 'b')]
```

Star-unpacking `zip` transposes rows to columns.

### Q131. Intermediate

What does this print?

```python
a = [1, 2, 3]
print([x for x in a if x > 1])
```

**Answer:**

```text
[2, 3]
```

Filtered comprehension keeps only matching elements.

### Q132. Intermediate

What does this print?

```python
print([n for n in range(6) if n % 2 == 0 if n % 3 == 0])
```

**Answer:**

```text
[0]
```

Multiple `if` clauses act as successive filters (values divisible by 6).

### Q133. Intermediate

What does this print?

```python
a = [1, 2, 3]
print([*a, 4])
```

**Answer:**

```text
[1, 2, 3, 4]
```

Unpacking splices elements into a new list literal.

### Q134. Intermediate

What does this print?

```python
print(list({3, 1, 2}))
```

**Answer:**

```text
[1, 2, 3]
```

Set iteration order is insertion-based; `list` captures current order.

### Q135. Intermediate

What does this print?

```python
a = [1, 2, 3]
print(a == a[:])
```

**Answer:**

```text
True
```

A shallow copy compares equal to the original.

### Q136. Intermediate

What does this print?

```python
import copy
a = [1, [2]]
b = copy.copy(a)
print(a == b, a[1] is b[1])
```

**Answer:**

```text
True True
```

Shallow copy duplicates the outer list but shares inner objects.

### Q137. Intermediate

What does this print?

```python
a = [1, 2, 3]
print(a.pop(1), a)
```

**Answer:**

```text
2 [1, 3]
```

Pop at index 1 removes the middle element.

### Q138. Intermediate

What happens when this runs?

```python
a = []
print(a.pop())
```

**Answer:**

```text
IndexError: pop from empty list
```

Pop from empty list raises `IndexError`.

### Q139. Intermediate

What does this print?

```python
a = [1, 2, 3, 2]
print(a.index(2, 2))
```

**Answer:**

```text
3
```

Optional start offset searches from that index.

### Q140. Intermediate

What does this print?

```python
print(list(filter(lambda x: x % 2, [1, 2, 3, 4])))
```

**Answer:**

```text
[1, 3]
```

`filter` keeps elements where the predicate is truthy.

### Q141. Intermediate

What does this print?

```python
print(list(map(lambda x: x + 1, [1, 2, 3])))
```

**Answer:**

```text
[2, 3, 4]
```

`map` with a lambda adds one to each item.

### Q142. Intermediate

What does this print?

```python
a = [1, 2, 3]
print(any(x > 2 for x in a), all(x > 0 for x in a))
```

**Answer:**

```text
True True
```

Aggregates short-circuit over iterable logic.

### Q143. Intermediate

What does this print?

```python
a = [3, 1, 2]
print(sorted(a, key=lambda x: -x))
```

**Answer:**

```text
[3, 2, 1]
```

Negated key sorts descending without `reverse=True`.

### Q144. Intermediate

What does this print?

```python
a = [1, 2, 3]
print(a[::])
```

**Answer:**

```text
[1, 2, 3]
```

Slice with default step copies the whole list into a new object.

### Q145. Intermediate

What does this print?

```python
a = [1, 2, 3]
print(a[::-1][0])
```

**Answer:**

```text
3
```

Reversed copy's first element is the original last.

### Q146. Intermediate

What does this print?

```python
print(list(zip([1, 2], [3, 4], [5, 6])))
```

**Answer:**

```text
[(1, 3, 5), (2, 4, 6)]
```

Three-way zip when lengths match.

### Q147. Intermediate

What does this print?

```python
a = [1, 2, 3]
print(a * -1)
```

**Answer:**

```text
[]
```

Negative repetition count yields an empty list.

### Q148. Intermediate

What does this print?

```python
a = [1, 2, 3]
print(a + a)
```

**Answer:**

```text
[1, 2, 3, 1, 2, 3]
```

Concatenation duplicates content in a new list.

### Q149. Advanced

What does this print?

```python
a = [1, 2, 3, 4]
a[1:3] = a[1:3]
print(a)
```

**Answer:**

```text
[1, 2, 3, 4]
```

Assigning a slice of `a` to itself is allowed and leaves order unchanged here.

### Q150. Advanced

What does this print?

```python
a = [1, 2, 3, 4, 5]
del a[::2]
print(a)
```

**Answer:**

```text
[2, 4]
```

Deleting every other element compacts the list.

### Q151. Advanced

What does this print?

```python
a = [1, 2, 3]
a.sort(key=lambda x: -x)
print(a)
```

**Answer:**

```text
[3, 2, 1]
```

In-place sort with a negated key orders descending.

### Q152. Advanced

What does this print?

```python
a = [(1, 'z'), (1, 'a')]
print(sorted(a))
```

**Answer:**

```text
[(1, 'a'), (1, 'z')]
```

When the first tuple elements tie, comparison continues to the second element; `'a' < 'z'`.

### Q153. Advanced

What does this print?

```python
data = [('a', 3), ('b', 1), ('c', 2)]
print(sorted(data, key=lambda t: t[1]))
```

**Answer:**

```text
[('b', 1), ('c', 2), ('a', 3)]
```

Sort by the numeric second field.

### Q154. Advanced

What does this print?

```python
a = [3, 1, 4, 1, 5]
print(sorted(set(a)))
```

**Answer:**

```text
[1, 3, 4, 5]
```

Set removes duplicates before sorting.

### Q155. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a.__getitem__(slice(1, 3)))
```

**Answer:**

```text
[2, 3]
```

Slice objects route through `__getitem__` like subscript syntax.

### Q156. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a[True], a[False])
```

**Answer:**

```text
2 1
```

Bool is a subclass of int, so indices 1 and 0 are valid.

### Q157. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a[1:2] is a[1:2])
```

**Answer:**

```text
False
```

Each slice expression builds a fresh list object.

### Q158. Advanced

What does this print?

```python
import itertools
print(list(itertools.chain([1, 2], [3])))
```

**Answer:**

```text
[1, 2, 3]
```

`chain` flattens iterables without nesting.

### Q159. Advanced

What does this print?

```python
a = [1, 2, 3]
print(list(a), a)
```

**Answer:**

```text
[1, 2, 3] [1, 2, 3]
```

`list(iterable)` copies elements when the iterable is already a list.

### Q160. Advanced

What does this print?

```python
a = [1, 2, 3]
print(iter(a) is iter(a))
```

**Answer:**

```text
False
```

Each call to `iter` on a list returns a new iterator object.

### Q161. Advanced

What does this print?

```python
a = [1, 2, 3]
it = iter(a)
print(next(it), next(it))
```

**Answer:**

```text
1 2
```

Manual iteration consumes elements sequentially.

### Q162. Advanced

What happens when this runs?

```python
a = [1, 2, 3]
it = iter(a)
next(it); next(it); next(it); next(it)
```

**Answer:**

```text
StopIteration: 
```

Fourth `next` on a three-item iterator raises `StopIteration`.

### Q163. Advanced

What does this print?

```python
a = [1, 2, 3, 4]
print([a[i] for i in range(len(a)-1, -1, -1)])
```

**Answer:**

```text
[4, 3, 2, 1]
```

Index loop can reverse without slice.

### Q164. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a + [4] is a)
```

**Answer:**

```text
False
```

Concatenation always allocates a new list.

### Q165. Advanced

What does this print?

```python
a = [1, 2, 3]
a.extend(a)
print(a)
```

**Answer:**

```text
[1, 2, 3, 1, 2, 3]
```

Extending with itself appends a copy of the current contents, doubling the list.

### Q166. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a.sort(key=abs, reverse=True) or a)
```

**Answer:**

```text
[3, 2, 1]
```

`sort` returns `None`; `or` yields the mutated list.

### Q167. Advanced

What does this print?

```python
pairs = [(1, 'b'), (1, 'a')]
print(sorted(pairs, key=lambda t: (t[0], t[1])))
```

**Answer:**

```text
[(1, 'a'), (1, 'b')]
```

Explicit composite key matches default tuple ordering.

### Q168. Advanced

What does this print?

```python
a = [1, 2, 3]
print([*a[:1], *a[1:]])
```

**Answer:**

```text
[1, 2, 3]
```

Unpacking two slices rebuilds a copy with the same order.

### Q169. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a[::-1] == list(reversed(a)))
```

**Answer:**

```text
True
```

Reversal via slice and via `reversed` yield equal lists.

### Q170. Advanced

What does this print?

```python
a = [1, 2, 3, 4]
print([x for x in a if (a.remove(x) or True) and False])
```

**Answer:**

```text
[]
```

Side effects in comprehensions are discouraged; here the filter is always false so result is empty.

### Q171. Advanced

What does this print?

```python
a = [1, 2, 3, 4]
print([x for x in a if (a.remove(x) or True) and False], a)
```

**Answer:**

```text
[] [2, 4]
```

Each loop removes the current head; skipped even values remain, so `a` ends as `[2, 4]`.

### Q172. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a[::-1][::-1] == a, a[::-1][::-1] is a)
```

**Answer:**

```text
True False
```

Double reversal equals the original but still uses distinct list objects.

### Q173. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a[::] is a)
```

**Answer:**

```text
False
```

Full slice copy is a new object, not the same as `a`.

### Q174. Advanced

What does this print?

```python
import bisect
a = [1, 3, 3, 5]
print(bisect.bisect_left(a, 3), bisect.bisect_right(a, 3))
```

**Answer:**

```text
1 3
```

`bisect_left` returns first 3 index; `bisect_right` returns index after run of 3.

### Q175. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a[-4:4])
```

**Answer:**

```text
[1, 2, 3]
```

Slice clamps out-of-range bounds instead of raising.

### Q176. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a[1:10:2])
```

**Answer:**

```text
[2]
```

Step with clamped stop picks index 1 only.

### Q177. Advanced

What does this print?

```python
print([*(1, 2, 3)])
```

**Answer:**

```text
[1, 2, 3]
```

Unpacking a tuple into a list literal.

### Q178. Advanced

What does this print?

```python
a = [1, 2, 3]
print(list(map(list, [a, a[:]])))
```

**Answer:**

```text
[[1, 2, 3], [1, 2, 3]]
```

Mapping `list` over list copies produces two equal top-level lists.

### Q179. Advanced

What does this print?

```python
a = [1, 2, 3]
print([a.pop() for _ in range(3)])
```

**Answer:**

```text
[3, 2, 1]
```

Comprehension can pop until empty, collecting from the end.

### Q180. Advanced

What does this print?

```python
a = [1, 2, 3]
print([a.pop(0) for _ in range(3)])
```

**Answer:**

```text
[1, 2, 3]
```

Repeated pop(0) shifts elements; order collected is 1, 2, 3.

### Q181. Advanced

What does this print?

```python
a = [1, 2, 3, 2, 1]
print([i for i, x in enumerate(a) if x == 2])
```

**Answer:**

```text
[1, 3]
```

Enumerate helps gather indices matching a value.

### Q182. Advanced

What does this print?

```python
a = [1, 2, 3]
print(list(zip(a, range(10))))
```

**Answer:**

```text
[(1, 0), (2, 1), (3, 2)]
```

Zip stops at the shorter iterable (length 3).

### Q183. Advanced

What does this print?

```python
a = [1, 2, 3]
print(sorted(a, key=lambda x: (x % 2, x)))
```

**Answer:**

```text
[2, 1, 3]
```

Sort by parity then value.

### Q184. Advanced

What does this print?

```python
a = [3, 1, 2, 1]
print(sorted(a, key=lambda x: x) == sorted(a))
```

**Answer:**

```text
True
```

Identity key matches default sort order.

### Q185. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a.__reversed__())
```

**Answer:**

```text
<list_reverseiterator object at 0x7bc905b84dc0>
```

Lists implement `__reversed__` returning an iterator.

### Q186. Advanced

What does this print?

```python
a = [1, 2, 3]
print(list(a.__reversed__()))
```

**Answer:**

```text
[3, 2, 1]
```

Materializing the reversed iterator yields descending order.

### Q187. Advanced

What does this print?

```python
a = [1, 2, 3]
print(a[2:1:-1])
```

**Answer:**

```text
[3]
```

Negative step with start > stop walks backward between indices 2 and 1 exclusive of stop.

### Q188. Basic

Write `running_sum(nums)` returning prefix sums: `[nums[0], nums[0]+nums[1], ...]`.

**Answer:**

```python
def running_sum(nums):
    out = []
    total = 0
    for x in nums:
        total += x
        out.append(total)
    return out
```

- `running_sum([])  =>  []`
- `running_sum([1, 2, 3])  =>  [1, 3, 6]`
- `running_sum([4, -1, 2])  =>  [4, 3, 5]`

One pass accumulates `total` and appends after each step.

### Q189. Basic

Write `reverse_inplace(a)` that reverses list `a` in place without calling `a.reverse()` or slicing assignment tricks that rebind `a`.

**Answer:**

```python
def reverse_inplace(a):
    i, j = 0, len(a) - 1
    while i < j:
        a[i], a[j] = a[j], a[i]
        i += 1
        j -= 1
    return a
```

- `reverse_inplace([1, 2, 3])  =>  [3, 2, 1]`
- `reverse_inplace([])  =>  []`
- `reverse_inplace([1])  =>  [1]`

Swap elements from both ends moving inward.

### Q190. Basic

Write `chunk(a, n)` returning consecutive sublists of length at most `n`. Assume `n >= 1`.

**Answer:**

```python
def chunk(a, n):
    return [a[i : i + n] for i in range(0, len(a), n)]
```

- `chunk([], 2)  =>  []`
- `chunk([1, 2, 3, 4, 5], 2)  =>  [[1, 2], [3, 4], [5]]`
- `chunk([1, 2, 3], 3)  =>  [[1, 2, 3]]`

Step the start index by `n` and slice each window.

### Q191. Basic

Write `move_zeros(nums)` that moves all zeros to the end while preserving the order of non-zero elements. Mutate `nums` in place.

**Answer:**

```python
def move_zeros(nums):
    write = 0
    for x in nums:
        if x != 0:
            nums[write] = x
            write += 1
    for i in range(write, len(nums)):
        nums[i] = 0
    return nums
```

- `move_zeros([0, 1, 0, 3, 12])  =>  [1, 3, 12, 0, 0]`
- `move_zeros([0, 0, 1])  =>  [1, 0, 0]`
- `move_zeros([])  =>  []`

Compact non-zeros to the front, then fill the tail with zeros.

### Q192. Intermediate

Write `dedupe_preserve(a)` returning a new list with first occurrences kept and order preserved.

**Answer:**

```python
def dedupe_preserve(a):
    seen = set()
    out = []
    for x in a:
        if x not in seen:
            seen.add(x)
            out.append(x)
    return out
```

- `dedupe_preserve([])  =>  []`
- `dedupe_preserve([1, 2, 1, 3, 2])  =>  [1, 2, 3]`
- `dedupe_preserve(['a', 'a', 'b'])  =>  ['a', 'b']`

A set tracks what you have already emitted.

### Q193. Intermediate

Write `flatten_one(nested)` that flattens one level: lists inside become elements spliced in; non-lists stay as elements.

**Answer:**

```python
def flatten_one(nested):
    out = []
    for x in nested:
        if type(x) is list:
            out.extend(x)
        else:
            out.append(x)
    return out
```

- `flatten_one([])  =>  []`
- `flatten_one([1, [2, 3], 4])  =>  [1, 2, 3, 4]`
- `flatten_one([[1], [2, [3]]])  =>  [1, 2, [3]]`

Only unwrap lists one level deep; deeper nesting stays nested.

### Q194. Intermediate

Write `rotate(a, k)` rotating list `a` to the right by `k` positions in place. Empty lists stay empty.

**Answer:**

```python
def rotate(a, k):
    n = len(a)
    if n == 0:
        return a
    k %= n
    if k == 0:
        return a
    a[:] = a[-k:] + a[:-k]
    return a
```

- `rotate([1, 2, 3, 4], 1)  =>  [4, 1, 2, 3]`
- `rotate([1, 2, 3], 3)  =>  [1, 2, 3]`
- `rotate([1, 2, 3, 4, 5], 2)  =>  [4, 5, 1, 2, 3]`

Reduce `k` modulo length, then slice-assign the reordered elements.

### Q195. Intermediate

Write `merge_sorted(a, b)` merging two sorted lists into one sorted list.

**Answer:**

```python
def merge_sorted(a, b):
    i = j = 0
    out = []
    while i < len(a) and j < len(b):
        if a[i] <= b[j]:
            out.append(a[i])
            i += 1
        else:
            out.append(b[j])
            j += 1
    out.extend(a[i:])
    out.extend(b[j:])
    return out
```

- `merge_sorted([], [1, 2])  =>  [1, 2]`
- `merge_sorted([1, 3, 5], [2, 4, 6])  =>  [1, 2, 3, 4, 5, 6]`
- `merge_sorted([1, 2, 2], [2, 3])  =>  [1, 2, 2, 2, 3]`

Two-pointer merge like merge sort's combine step. `<=` keeps stability for equal keys from `a`.

### Q196. Intermediate

Write `two_sum_indices(nums, target)` returning indices `(i, j)` with `i < j` and `nums[i] + nums[j] == target`, or `None` if none exist.

**Answer:**

```python
def two_sum_indices(nums, target):
    seen = {}
    for i, x in enumerate(nums):
        need = target - x
        if need in seen:
            return (seen[need], i)
        seen[x] = i
    return None
```

- `two_sum_indices([2, 7, 11, 15], 9)  =>  (0, 1)`
- `two_sum_indices([3, 3], 6)  =>  (0, 1)`
- `two_sum_indices([1, 2], 4)  =>  None`

Store each value's index; check whether its complement was seen earlier.

### Q197. Advanced

Write `binary_search(a, x)` returning the index of `x` in sorted list `a`, or `-1` if missing.

**Answer:**

```python
def binary_search(a, x):
    lo, hi = 0, len(a) - 1
    while lo <= hi:
        mid = (lo + hi) // 2
        if a[mid] == x:
            return mid
        if a[mid] < x:
            lo = mid + 1
        else:
            hi = mid - 1
    return -1
```

- `binary_search([], 1)  =>  -1`
- `binary_search([1, 3, 5, 7], 5)  =>  2`
- `binary_search([1, 3, 5, 7], 4)  =>  -1`

Standard inclusive bounds binary search on a sorted list.

### Q198. Advanced

Write `max_subarray_sum(nums)` returning the largest sum of any contiguous subarray (Kadane). For an empty list return `0`.

**Answer:**

```python
def max_subarray_sum(nums):
    best = cur = 0
    for x in nums:
        cur = max(x, cur + x)
        best = max(best, cur)
    return best
```

- `max_subarray_sum([])  =>  0`
- `max_subarray_sum([-2, 1, -3, 4, -1, 2, 1, -5, 4])  =>  6`
- `max_subarray_sum([-1, -2])  =>  0`

Track the best ending-here sum `cur`. Empty input uses the convention that the empty subarray sums to 0.

### Q199. Advanced

Write `product_except_self(nums)` returning a list where output `i` is the product of all elements except `nums[i]`. Use O(n) time and no division.

**Answer:**

```python
def product_except_self(nums):
    n = len(nums)
    out = [1] * n
    prefix = 1
    for i in range(n):
        out[i] = prefix
        prefix *= nums[i]
    suffix = 1
    for i in range(n - 1, -1, -1):
        out[i] *= suffix
        suffix *= nums[i]
    return out
```

- `product_except_self([1, 2, 3, 4])  =>  [24, 12, 8, 6]`
- `product_except_self([2, 3])  =>  [3, 2]`
- `product_except_self([0, 1, 2])  =>  [2, 0, 0]`

Prefix products left-to-right, then multiply by suffix products right-to-left.

### Q200. Advanced

Write `spiral_order(matrix)` returning elements of a 2D list of lists in clockwise spiral order. Empty matrix returns `[]`.

**Answer:**

```python
def spiral_order(matrix):
    if not matrix:
        return []
    top, bottom = 0, len(matrix) - 1
    left, right = 0, len(matrix[0]) - 1
    out = []
    while top <= bottom and left <= right:
        for c in range(left, right + 1):
            out.append(matrix[top][c])
        top += 1
        for r in range(top, bottom + 1):
            out.append(matrix[r][right])
        right -= 1
        if top <= bottom:
            for c in range(right, left - 1, -1):
                out.append(matrix[bottom][c])
            bottom -= 1
        if left <= right:
            for r in range(bottom, top - 1, -1):
                out.append(matrix[r][left])
            left += 1
    return out
```

- `spiral_order([])  =>  []`
- `spiral_order([[1, 2], [3, 4]])  =>  [1, 2, 4, 3]`
- `spiral_order([[1, 2, 3], [4, 5, 6], [7, 8, 9]])  =>  [1, 2, 3, 6, 9, 8, 7, 4, 5]`

Shrink top/bottom/left/right borders after each lap around the matrix.

*Section size: 200 questions (Basic 70, Intermediate 70, Advanced 60).*

