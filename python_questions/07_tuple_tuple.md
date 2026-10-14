## 7. Tuple (tuple)

An immutable ordered sequence. It is hashable only when every item is hashable.

### Q1. Basic

What does this print?

```python
print(type((1, 2)))
```

**Answer:**

```text
<class 'tuple'>
```

Parentheses with commas make a `tuple`, not grouping for arithmetic.

### Q2. Basic

What does this print?

```python
print(type(()))
```

**Answer:**

```text
<class 'tuple'>
```

The empty tuple is written `()`. Its type is `tuple`.

### Q3. Basic

What does this print?

```python
print(len(()))
```

**Answer:**

```text
0
```

An empty tuple has length 0.

### Q4. Basic

What does this print?

```python
print(type((1,)))
```

**Answer:**

```text
<class 'tuple'>
```

A trailing comma after one value makes a one-element tuple.

### Q5. Basic

What does this print?

```python
print((1,))
```

**Answer:**

```text
(1,)
```

The comma, not the parentheses, creates the tuple.

### Q6. Basic

What does this print?

```python
print(type((1)))
```

**Answer:**

```text
<class 'int'>
```

Without a comma, `(1)` is just the int `1` in parentheses.

### Q7. Basic

What does this print?

```python
t = 1, 2, 3
print(t, type(t))
```

**Answer:**

```text
(1, 2, 3) <class 'tuple'>
```

Tuple packing works without parentheses on the right-hand side.

### Q8. Basic

What does this print?

```python
a, b, c = (1, 2, 3)
print(b)
```

**Answer:**

```text
2
```

Unpacking assigns by position.

### Q9. Basic

What does this print?

```python
a, *rest, z = (1, 2, 3, 4)
print(rest, z)
```

**Answer:**

```text
[2, 3] 4
```

Star unpacking collects the middle into a list.

### Q10. Basic

What does this print?

```python
print((1, 2)[0], (1, 2)[-1])
```

**Answer:**

```text
1 2
```

Tuples support forward and negative indexing like sequences.

### Q11. Basic

What does this print?

```python
print((1, 2, 3, 4)[1:3])
```

**Answer:**

```text
(2, 3)
```

Slicing returns a new tuple with the selected elements.

### Q12. Basic

What does this print?

```python
print((1, 2) + (3, 4))
```

**Answer:**

```text
(1, 2, 3, 4)
```

Concatenation builds a new tuple from two tuples.

### Q13. Basic

What does this print?

```python
print((0,) * 4)
```

**Answer:**

```text
(0, 0, 0, 0)
```

Repetition repeats the whole tuple.

### Q14. Basic

What does this print?

```python
print(len((1, 2, 3)))
```

**Answer:**

```text
3
```

`len` counts elements.

### Q15. Basic

What does this print?

```python
print((1, 2, 2, 3).count(2))
```

**Answer:**

```text
2
```

`count` counts equal elements.

### Q16. Basic

What does this print?

```python
print((10, 20, 10, 30).index(10))
```

**Answer:**

```text
0
```

`index` returns the first matching position.

### Q17. Basic

What does this print?

```python
print((1, 2) == (1, 2))
```

**Answer:**

```text
True
```

Equal tuples compare equal element-wise.

### Q18. Basic

What does this print?

```python
print((1, 2) < (1, 3))
```

**Answer:**

```text
True
```

Lexicographic order compares the first unequal element.

### Q19. Basic

What does this print?

```python
print((1, 2) < (2, 0))
```

**Answer:**

```text
True
```

When the first elements differ, later elements are ignored.

### Q20. Basic

What does this print?

```python
print((1,) < (1, 2))
```

**Answer:**

```text
True
```

Shorter tuple is a prefix: it compares less when all shared elements match.

### Q21. Basic

What does this print?

```python
print(list((1, 2)))
```

**Answer:**

```text
[1, 2]
```

`list(tuple)` copies elements into a new list.

### Q22. Basic

What does this print?

```python
print(tuple([1, 2, 3]))
```

**Answer:**

```text
(1, 2, 3)
```

`tuple(list)` copies elements into a new tuple.

### Q23. Basic

What does this print?

```python
t = (1, 2)
print(t[0])
```

**Answer:**

```text
1
```

Reading an element is allowed.

### Q24. Basic

What happens when this runs?

```python
t = (1, 2)
t[0] = 9
```

**Answer:**

```text
TypeError: 'tuple' object does not support item assignment
```

Tuples are immutable: item assignment raises `TypeError`.

### Q25. Basic

What happens when this runs?

```python
t = (1, 2)
t.append(3)
```

**Answer:**

```text
AttributeError: 'tuple' object has no attribute 'append'
```

Tuples have no `append` method.

### Q26. Basic

What does this print?

```python
print(hash((1, 2)))
```

**Answer:**

```text
-3550055125485641917
```

A tuple of hashable items is hashable.

### Q27. Basic

What does this print?

```python
d = {(1, 2): 'ok'}
print(d[(1, 2)])
```

**Answer:**

```text
ok
```

Hashable tuples can be dict keys.

### Q28. Basic

What does this print?

```python
s = {(1,), (2,)}
print(len(s))
```

**Answer:**

```text
2
```

Distinct hashable tuples can live in a set.

### Q29. Basic

What does this print?

```python
print((1, 2) * 0)
```

**Answer:**

```text
()
```

Multiplying by zero yields an empty tuple.

### Q30. Basic

What does this print?

```python
print(bool(()), bool((0,)))
```

**Answer:**

```text
False True
```

Empty tuple is falsy; any non-empty tuple is truthy.

### Q31. Basic

What does this print?

```python
x, y = y, x = 1, 2
print(x, y)
```

**Answer:**

```text
2 1
```

Parallel assignment swaps without a temporary.

### Q32. Basic

What does this print?

```python
print(tuple())
```

**Answer:**

```text
()
```

`tuple()` with no argument is the empty tuple.

### Q33. Basic

What does this print?

```python
print(tuple('ab'))
```

**Answer:**

```text
('a', 'b')
```

Any iterable can be turned into a tuple of its elements.

### Q34. Basic

What does this print?

```python
print((1, 2, 3)[::2])
```

**Answer:**

```text
(1, 3)
```

Extended slicing works on tuples.

### Q35. Basic

What does this print?

```python
print(1 in (1, 2, 3))
```

**Answer:**

```text
True
```

Membership uses equality on elements.

### Q36. Basic

What does this print?

```python
print((1, 2) == [1, 2])
```

**Answer:**

```text
False
```

A tuple never equals a list, even with the same values.

### Q37. Basic

What does this print?

```python
print(min((3, 1, 2)), max((3, 1, 2)))
```

**Answer:**

```text
1 3
```

Min and max use the tuple's ordering.

### Q38. Basic

What does this print?

```python
print(sum((1, 2, 3)))
```

**Answer:**

```text
6
```

`sum` adds numeric elements.

### Q39. Basic

What does this print?

```python
print(all((1, 0, 3)), any((0, 0, 3)))
```

**Answer:**

```text
False True
```

`all` and `any` consume truthiness of elements.

### Q40. Basic

What does this print?

```python
print(reversed((1, 2, 3)))
print(tuple(reversed((1, 2, 3))))
```

**Answer:**

```text
<reversed object at 0x7bc905b87940>
(3, 2, 1)
```

`reversed` returns an iterator; materialize with `tuple` to see elements.

### Q41. Basic

What does this print?

```python
print(sorted((3, 1, 2)))
```

**Answer:**

```text
[1, 2, 3]
```

`sorted` returns a list, not a tuple.

### Q42. Basic

What does this print?

```python
print(tuple(sorted((3, 1, 2))))
```

**Answer:**

```text
(1, 2, 3)
```

Wrap `sorted` if you need a tuple result.

### Q43. Basic

What does this print?

```python
a = (1, 2)
b = (1, 2)
print(a == b)
```

**Answer:**

```text
True
```

Two tuples with equal contents compare equal.

### Q44. Basic

What does this print?

```python
print((None, 1)[0])
```

**Answer:**

```text
None
```

`None` is a valid tuple element.

### Q45. Basic

What does this print?

```python
print((True, False)[0], (True, False)[1])
```

**Answer:**

```text
True False
```

Bools are valid elements and keep their values.

### Q46. Basic

What does this print?

```python
print((1, 2.0) == (1.0, 2))
```

**Answer:**

```text
True
```

Numeric equality applies inside tuple comparison.

### Q47. Basic

What does this print?

```python
print((1, 2, 3).count(9))
```

**Answer:**

```text
0
```

`count` returns 0 when the value is absent.

### Q48. Basic

What happens when this runs?

```python
print((1, 2, 3).index(9))
```

**Answer:**

```text
ValueError: tuple.index(x): x not in tuple
```

Missing value in `index` raises `ValueError`.

### Q49. Basic

What does this print?

```python
print((1, 2) * 2)
```

**Answer:**

```text
(1, 2, 1, 2)
```

Repetition duplicates the whole sequence.

### Q50. Basic

What does this print?

```python
print(2 * (1, 2))
```

**Answer:**

```text
(1, 2, 1, 2)
```

Repetition is commutative.

### Q51. Basic

What does this print?

```python
print((1,) + (2,) + (3,))
```

**Answer:**

```text
(1, 2, 3)
```

Chained concatenation builds one tuple.

### Q52. Basic

What does this print?

```python
print((1, 2, 3)[-2:])
```

**Answer:**

```text
(2, 3)
```

Negative slice start counts from the end.

### Q53. Basic

What does this print?

```python
print((1, 2, 3)[:0])
```

**Answer:**

```text
()
```

Zero-width slice is empty.

### Q54. Basic

What does this print?

```python
print((1, 2, 3)[1:1])
```

**Answer:**

```text
()
```

Equal start and stop yields empty.

### Q55. Basic

What does this print?

```python
print((1, 2, 3)[::-1])
```

**Answer:**

```text
(3, 2, 1)
```

Step -1 reverses.

### Q56. Basic

What does this print?

```python
print((1, 2) == (1, 2, 3))
```

**Answer:**

```text
False
```

Different lengths make tuples unequal.

### Q57. Basic

What does this print?

```python
print((1, '2') < (1, '10'))
```

**Answer:**

```text
False
```

String elements compare lexicographically as strings.

### Q58. Basic

What does this print?

```python
print((1, '2') < (1, '3'))
```

**Answer:**

```text
True
```

Same rule for the next element when prefixes match.

### Q59. Basic

What does this print?

```python
print(tuple(range(3)))
```

**Answer:**

```text
(0, 1, 2)
```

A range converts to a tuple of ints.

### Q60. Basic

What does this print?

```python
print((0, 1, 2)[1])
```

**Answer:**

```text
1
```

Middle element of three.

### Q61. Basic

What does this print?

```python
print((0, 1, 2)[-1])
```

**Answer:**

```text
2
```

Last element via negative index.

### Q62. Basic

What does this print?

```python
print((0, 1, 2)[-3])
```

**Answer:**

```text
0
```

First element via negative index.

### Q63. Basic

What does this print?

```python
print((1, 2, 1, 2).count(1))
```

**Answer:**

```text
2
```

`count` tallies all matches.

### Q64. Basic

What does this print?

```python
print((1, 2, 1, 2).index(2))
```

**Answer:**

```text
1
```

First index of 2.

### Q65. Intermediate

What does this print?

```python
print((1, 2, 1, 2).index(2, 2))
```

**Answer:**

```text
3
```

Start position skips earlier matches.

### Q66. Intermediate

What does this print?

```python
print((1, 2, 3) > (1, 2))
```

**Answer:**

```text
True
```

Longer tuple with matching prefix is greater.

### Q67. Intermediate

What does this print?

```python
print((1, 2, 3) >= (1, 2, 3))
```

**Answer:**

```text
True
```

Equal tuples satisfy `>=`.

### Q68. Intermediate

What does this print?

```python
print((1, 2, 3) != (1, 2, 4))
```

**Answer:**

```text
True
```

One differing element makes inequality true.

### Q69. Basic

What does this print?

```python
print(isinstance((1, 2), tuple) and isinstance([1, 2], list))
```

**Answer:**

```text
True
```

Tuples and lists are distinct types.

### Q70. Intermediate

What does this print?

```python
print((1, 2).__class__.__name__)
```

**Answer:**

```text
tuple
```

The class name is `tuple`.

### Q71. Intermediate

What does this print?

```python
print((1, 2).__len__())
```

**Answer:**

```text
2
```

Dunder length matches `len`.

### Q72. Intermediate

What does this print?

```python
print((1, 2).__getitem__(0))
```

**Answer:**

```text
1
```

Dunder getitem matches indexing.

### Q73. Intermediate

What does this print?

```python
print((1, 2).__contains__(1))
```

**Answer:**

```text
True
```

Dunder contains matches `in`.

### Q74. Intermediate

What does this print?

```python
print((1, 2).__iter__())
```

**Answer:**

```text
<tuple_iterator object at 0x7bc905b87730>
```

Tuples are iterable; `__iter__` returns an iterator.

### Q75. Intermediate

What does this print?

```python
print((1, 2).__add__((3,)))
```

**Answer:**

```text
(1, 2, 3)
```

Dunder add matches `+`.

### Q76. Intermediate

What does this print?

```python
print((1, 2).__mul__(2))
```

**Answer:**

```text
(1, 2, 1, 2)
```

Dunder mul matches `*`.

### Q77. Basic

What does this print?

```python
t = ([1],)
t[0].append(2)
print(t)
```

**Answer:**

```text
([1, 2],)
```

The tuple cannot change size or rebind slots, but a mutable element inside can still be mutated.

### Q78. Basic

What does this print?

```python
t = ([],)
print(len(t[0]))
```

**Answer:**

```text
0
```

The inner list starts empty.

### Q79. Intermediate

What does this print?

```python
t = (1, [2])
print(t[1][0])
```

**Answer:**

```text
2
```

Indexing reaches inside the nested list.

### Q80. Intermediate

What happens when this runs?

```python
t = (1, [2])
t[1] = [3]
```

**Answer:**

```text
TypeError: 'tuple' object does not support item assignment
```

Rebinding an inner slot is forbidden even when the new value is a list.

### Q81. Intermediate

What does this print?

```python
t = (1, [2])
t[1].append(3)
print(t)
```

**Answer:**

```text
(1, [2, 3])
```

Mutating the list in place is allowed.

### Q82. Advanced

What does this print?

```python
t = ({'a': 1},)
t[0]['b'] = 2
print(sorted(t[0].items()))
```

**Answer:**

```text
[('a', 1), ('b', 2)]
```

Dict inside a tuple can grow in place.

### Q83. Basic

What happens when this runs?

```python
print(hash((1, [2])))
```

**Answer:**

```text
TypeError: unhashable type: 'list'
```

If any element is unhashable, the tuple is unhashable.

### Q84. Basic

What happens when this runs?

```python
print({(1, [2]): 0})
```

**Answer:**

```text
TypeError: unhashable type: 'list'
```

Unhashable tuple cannot be a dict key.

### Q85. Intermediate

What happens when this runs?

```python
print(hash((1, {2: 3})))
```

**Answer:**

```text
TypeError: unhashable type: 'dict'
```

Dict elements make the tuple unhashable.

### Q86. Intermediate

What happens when this runs?

```python
print({(1, {2: 3}): 0})
```

**Answer:**

```text
TypeError: unhashable type: 'dict'
```

Same rule for dict keys.

### Q87. Intermediate

What does this print?

```python
print(hash((1, (2, 3))))
```

**Answer:**

```text
7267574591690527098
```

Nested tuples are hashable when every leaf is hashable.

### Q88. Advanced

What does this print?

```python
print(hash((1, frozenset({2, 3}))))
```

**Answer:**

```text
-1095706916655466107
```

Frozenset inside a tuple is hashable.

### Q89. Intermediate

What does this print?

```python
print((1, 2) < (1, 2, 0))
```

**Answer:**

```text
True
```

Equal prefix; shorter tuple is less.

### Q90. Intermediate

What does this print?

```python
print((1, 2, 3) < (1, 2, 2))
```

**Answer:**

```text
False
```

Third element 3 is greater than 2.

### Q91. Intermediate

What does this print?

```python
print((2, 0) < (1, 9))
```

**Answer:**

```text
False
```

First element dominates.

### Q92. Intermediate

What does this print?

```python
print(('a', 'b') < ('a', 'c'))
```

**Answer:**

```text
True
```

String comparison at second position.

### Q93. Intermediate

What does this print?

```python
print((0, 1) < (0, 1, 0))
```

**Answer:**

```text
True
```

Longer with matching prefix is greater.

### Q94. Intermediate

What does this print?

```python
print((1,) < (1, 0))
```

**Answer:**

```text
True
```

One-element prefix vs longer.

### Q95. Intermediate

What does this print?

```python
print((1, 2, 3) == (1, 2, 4))
```

**Answer:**

```text
False
```

Equality requires same length and equal elements.

### Q96. Intermediate

What does this print?

```python
print((1, 2, 3) != (1, 2, 4))
```

**Answer:**

```text
True
```

Any mismatch makes inequality true.

### Q97. Intermediate

What does this print?

```python
print((1, 2, 3) <= (1, 2, 4))
```

**Answer:**

```text
True
```

Less-or-equal allows equality.

### Q98. Intermediate

What does this print?

```python
print((1, 2, 3) >= (1, 2, 4))
```

**Answer:**

```text
False
```

Greater-or-equal allows equality.

### Q99. Intermediate

What does this print?

```python
print((1, 2, 3) < (1, 2, 4))
```

**Answer:**

```text
True
```

Strict less when lex order says so.

### Q100. Intermediate

What does this print?

```python
print((1, 2, 3) > (1, 2, 4))
```

**Answer:**

```text
False
```

Strict greater when lex order says so.

### Q101. Intermediate

What does this print?

```python
first, *middle, last = (1, 2, 3, 4, 5)
print(first, middle, last)
```

**Answer:**

```text
1 [2, 3, 4] 5
```

Star middle collects a list of inner elements.

### Q102. Intermediate

What does this print?

```python
a, b = (1, 2)
print(a, b)
```

**Answer:**

```text
1 2
```

Two-name unpack.

### Q103. Intermediate

What does this print?

```python
*only, = (1, 2, 3)
print(only)
```

**Answer:**

```text
[1, 2, 3]
```

Unpack entire tuple into one list name.

### Q104. Intermediate

What does this print?

```python
x, y, z = 1, 2, 3
print(x, y, z)
```

**Answer:**

```text
1 2 3
```

Right-side packing then unpack.

### Q105. Intermediate

What does this print?

```python
print(*(1, 2, 3))
```

**Answer:**

```text
1 2 3
```

Unpacking in a call spreads arguments.

### Q106. Intermediate

What does this print?

```python
def f(a, b, c):
    return a + b + c
print(f(*(1, 2, 3)))
```

**Answer:**

```text
6
```

Function call unpacking.

### Q107. Advanced

What does this print?

```python
pairs = [(1, 'a'), (2, 'b')]
print([b for _, b in pairs])
```

**Answer:**

```text
['a', 'b']
```

Unpack in comprehension ignores first slot.

### Q108. Advanced

What does this print?

```python
d = {'x': 1, 'y': 2}
print(list(d.items()))
print([k for k, v in d.items() if v == 2])
```

**Answer:**

```text
[('x', 1), ('y', 2)]
['y']
```

`.items()` yields 2-tuples for unpacking.

### Q109. Intermediate

What does this print?

```python
print([1, 2] == (1, 2))
```

**Answer:**

```text
False
```

Different types never compare equal with `==` here.

### Q110. Intermediate

What does this print?

```python
print(tuple([1, 2]) == (1, 2))
```

**Answer:**

```text
True
```

Fresh tuple from list equals literal tuple.

### Q111. Intermediate

What does this print?

```python
print((1, 2).__eq__([1, 2]))
```

**Answer:**

```text
NotImplemented
```

Tuple's `__eq__` returns `NotImplemented` for list; Python tries reversed and gets False.

### Q112. Advanced

What does this print?

```python
import sys
print(sys.getsizeof((1, 2, 3)) < sys.getsizeof([1, 2, 3]))
```

**Answer:**

```text
True
```

Tuples often use less overhead than lists for small fixed sequences (CPython detail).

### Q113. Advanced

What does this print?

```python
from collections import namedtuple
Point = namedtuple('Point', 'x y')
p = Point(1, 2)
print(p.x, p.y)
```

**Answer:**

```text
1 2
```

Named tuples expose fields by name while staying tuple-like.

### Q114. Advanced

What does this print?

```python
from collections import namedtuple
Row = namedtuple('Row', ['a', 'b'])
r = Row(a=3, b=4)
print(r[0], r.b)
```

**Answer:**

```text
3 4
```

Fields are accessible by index and name.

### Q115. Advanced

What does this print?

```python
from collections import namedtuple
T = namedtuple('T', 'v')
t = T(5)
print(t._replace(v=6))
```

**Answer:**

```text
T(v=6)
```

`_replace` returns a new instance with selected fields changed.

### Q116. Advanced

What does this print?

```python
from collections import namedtuple
T = namedtuple('T', 'x y')
print(T(1, 2)._asdict())
```

**Answer:**

```text
{'x': 1, 'y': 2}
```

`_asdict` maps field names to values.

### Q117. Intermediate

What does this print?

```python
print((1, 2, 3).index(2, 1, 3))
```

**Answer:**

```text
1
```

Slice bounds limit the search region.

### Q118. Intermediate

What happens when this runs?

```python
print((1, 2, 3).index(2, 2, 3))
```

**Answer:**

```text
ValueError: tuple.index(x): x not in tuple
```

Start after the only occurrence: `ValueError`.

### Q119. Intermediate

What does this print?

```python
print((1, 2, 2, 3).count(2))
```

**Answer:**

```text
2
```

Both twos are counted.

### Q120. Intermediate

What does this print?

```python
print((1, 2) + () )
```

**Answer:**

```text
(1, 2)
```

Adding empty tuple leaves contents unchanged.

### Q121. Intermediate

What does this print?

```python
print(() + (1,))
```

**Answer:**

```text
(1,)
```

Empty on the left still produces `(1,)`.

### Q122. Intermediate

What does this print?

```python
print((1, 2) == (1, 2.0))
```

**Answer:**

```text
True
```

Numeric equality inside elements.

### Q123. Intermediate

What does this print?

```python
print((1, 2) < (1, 2.5))
```

**Answer:**

```text
True
```

Float compared at second position.

### Q124. Intermediate

What does this print?

```python
print(tuple(map(lambda x: x * 2, (1, 2, 3))))
```

**Answer:**

```text
(2, 4, 6)
```

`map` over tuple yields tuple via constructor.

### Q125. Intermediate

What does this print?

```python
print(tuple(filter(lambda x: x % 2, (1, 2, 3, 4))))
```

**Answer:**

```text
(1, 3)
```

`filter` keeps odd values here.

### Q126. Intermediate

What does this print?

```python
print((1, 2) * 3)
```

**Answer:**

```text
(1, 2, 1, 2, 1, 2)
```

Triple repetition.

### Q127. Intermediate

What does this print?

```python
print((1,) * 5)
```

**Answer:**

```text
(1, 1, 1, 1, 1)
```

Five copies of one element.

### Q128. Intermediate

What does this print?

```python
print((1, 2, 3)[::3])
```

**Answer:**

```text
(1,)
```

Every third element.

### Q129. Intermediate

What does this print?

```python
print((1, 2, 3)[1::-1])
```

**Answer:**

```text
(2, 1)
```

Slice from index 1 down to start.

### Q130. Intermediate

What does this print?

```python
print((1, 2, 3)[-2:-1])
```

**Answer:**

```text
(2,)
```

Negative slice endpoints.

### Q131. Intermediate

What does this print?

```python
print(not () )
```

**Answer:**

```text
True
```

Empty tuple is falsy.

### Q132. Intermediate

What does this print?

```python
print(not (0,) )
```

**Answer:**

```text
False
```

Tuple containing falsy value is still truthy.

### Q133. Intermediate

What does this print?

```python
print((0,) == (False,))
```

**Answer:**

```text
True
```

`0 == False` is True, so tuples compare equal.

### Q134. Intermediate

What does this print?

```python
print((1,) == (1.0,))
```

**Answer:**

```text
True
```

Single element numeric equality makes the tuples equal.

### Q135. Intermediate

What does this print?

```python
print(not ((1,) != (1.0,)))
```

**Answer:**

```text
True
```

Inequality is false when numeric equality holds.

### Q136. Intermediate

What does this print?

```python
print(len((1, 2) + (3, 4, 5)))
```

**Answer:**

```text
5
```

Concatenated length is sum of lengths.

### Q137. Advanced

What does this print?

```python
print((1, 2, 3) < (1, 2, 3, -1))
```

**Answer:**

```text
True
```

Prefix rule: shorter `(1,2,3)` is less than longer sharing prefix.

### Q138. Advanced

What does this print?

```python
print((1, 2, 3) > (1, 2, 3, -1))
```

**Answer:**

```text
False
```

Longer tuple with same prefix is greater.

### Q139. Advanced

What does this print?

```python
print((float('nan'),) == (float('nan'),))
```

**Answer:**

```text
False
```

Tuple equality uses `==` on each element. `nan == nan` is False, so the tuples are unequal.

### Q140. Advanced

What does this print?

```python
print((1, 2) < (1, 2, 0))
```

**Answer:**

```text
True
```

Classic prefix comparison.

### Q141. Advanced

What does this print?

```python
print((1, 2, 0) > (1, 2))
```

**Answer:**

```text
True
```

Longer extension after shared prefix.

### Q142. Advanced

What does this print?

```python
t = (object(), object())
print(t[0] is t[1])
```

**Answer:**

```text
False
```

Distinct object elements are not identical.

### Q143. Advanced

What does this print?

```python
print(tuple(i for i in range(3)))
```

**Answer:**

```text
(0, 1, 2)
```

Generator inside constructor.

### Q144. Advanced

What does this print?

```python
print((1, 2).count(1.0))
```

**Answer:**

```text
1
```

`1 == 1.0` so count finds it.

### Q145. Advanced

What does this print?

```python
print((1, 2).index(1.0))
```

**Answer:**

```text
0
```

Same for index.

### Q146. Advanced

What does this print?

```python
print(hash((1, 'a')) == hash((1, 'a')))
```

**Answer:**

```text
True
```

Equal hashable tuples have equal hashes.

### Q147. Advanced

What happens when this runs?

```python
d = {}
d[[1]] = 0
```

**Answer:**

```text
TypeError: unhashable type: 'list'
```

Lists cannot be keys; tuples can when hashable.

### Q148. Advanced

What happens when this runs?

```python
d = {}
d[(1, [2])] = 0
```

**Answer:**

```text
TypeError: unhashable type: 'list'
```

Tuple containing a list is unhashable and cannot be used as a dict key.

### Q149. Basic

Write `swap_pair(t)` that takes a 2-tuple and returns a new tuple with elements reversed.

**Answer:**

```python
def swap_pair(t):
    a, b = t
    return b, a
```

- `swap_pair((1, 2))  =>  (2, 1)`
- `swap_pair(('x', 'y'))  =>  ('y', 'x')`

Unpack and return in opposite order. The input tuple is not mutated.

### Q150. Intermediate

Write `pair_frequency(items)` where `items` is an iterable of 2-tuples. Return a dict mapping each sorted pair `(min(a,b), max(a,b))` to its count.

**Answer:**

```python
def pair_frequency(items):
    out = {}
    for a, b in items:
        key = (a, b) if a <= b else (b, a)
        out[key] = out.get(key, 0) + 1
    return out
```

- `pair_frequency([(1, 2), (2, 1), (1, 2)])  =>  {(1, 2): 3}`
- `pair_frequency([(3, 1)])  =>  {(1, 3): 1}`

Normalize order so `(2,1)` and `(1,2)` share one key.

### Q151. Advanced

Write `freeze_rows(rows)` that takes a list of lists and returns a tuple of tuples with the same data (a hashable snapshot).

**Answer:**

```python
def freeze_rows(rows):
    return tuple(tuple(r) for r in rows)
```

- `freeze_rows([[1, 2], [3]])  =>  ((1, 2), (3,))`
- `hash(freeze_rows([[1], [2]]))  =>  2441169688291153174`

Outer tuple holds inner tuples so the structure can be hashed when elements are hashable.

### Q152. Advanced

Write `sort_records(records, key_index)` that sorts a list of tuples by the element at `key_index` without mutating the original list.

**Answer:**

```python
def sort_records(records, key_index):
    return sorted(records, key=lambda t: t[key_index])
```

- `sort_records([(2, 'b'), (1, 'a'), (1, 'c')], 0)  =>  [(1, 'a'), (1, 'c'), (2, 'b')]`
- `sort_records([(2, 'b'), (1, 'a')], 1)  =>  [(1, 'a'), (2, 'b')]`

Use `sorted` with a key on the chosen index. Stable sort keeps `(1,'a')` before `(1,'c)`.

### Q153. Intermediate

What does this print?

```python
print((1, 2, 3)[2:10])
```

**Answer:**

```text
(3,)
```

Slice stop beyond length is clamped.

### Q154. Intermediate

What does this print?

```python
print((1, 2, 3)[-10:2])
```

**Answer:**

```text
(1, 2)
```

Negative start clamps to 0.

### Q155. Intermediate

What does this print?

```python
print((1, 2, 3)[::2])
```

**Answer:**

```text
(1, 3)
```

Step 2 takes every other element.

### Q156. Intermediate

What does this print?

```python
print((1, 2, 3)[1::2])
```

**Answer:**

```text
(2,)
```

Step with offset.

### Q157. Advanced

What does this print?

```python
print((1, 2) + (3,) * 0)
```

**Answer:**

```text
(1, 2)
```

Multiplying empty pattern then concat.

### Q158. Advanced

What does this print?

```python
print(((1,),) * 2)
```

**Answer:**

```text
((1,), (1,))
```

Tuple of tuple repeated.

### Q159. Advanced

What does this print?

```python
print(((1,),)[0][0])
```

**Answer:**

```text
1
```

Double indexing into nested one-tuples.

### Q160. Advanced

What does this print?

```python
print(len((1, 2) * 0 + (3,)))
```

**Answer:**

```text
1
```

Combine repetition and concat.

### Q161. Advanced

What does this print?

```python
print(tuple(zip((1, 2), ('a', 'b'))))
```

**Answer:**

```text
((1, 'a'), (2, 'b'))
```

`zip` pairs into 2-tuples.

### Q162. Advanced

What does this print?

```python
print(list(enumerate(('a', 'b'))))
```

**Answer:**

```text
[(0, 'a'), (1, 'b')]
```

`enumerate` yields `(index, value)` tuples.

### Q163. Advanced

What does this print?

```python
print((1, 2, 3).count(True))
```

**Answer:**

```text
1
```

`True` equals `1`, so one match at first slot.

### Q164. Advanced

What does this print?

```python
print((0, 1, 2).count(False))
```

**Answer:**

```text
1
```

`False` equals `0`.

### Q165. Advanced

What does this print?

```python
print((1, 2, 3).index(True))
```

**Answer:**

```text
0
```

First element matches `True` via `==`.

### Q166. Advanced

What does this print?

```python
print((1, 2) == (1, 2) == (1, 2))
```

**Answer:**

```text
True
```

Chained equality.

### Q167. Advanced

What does this print?

```python
print((1, 2) < (1, 2) < (1, 3))
```

**Answer:**

```text
False
```

Chained comparison on tuples.

### Q168. Advanced

What does this print?

```python
print(all((True, 1, 3)))
```

**Answer:**

```text
True
```

All elements truthy.

### Q169. Advanced

What does this print?

```python
print(any((0, False, 3)))
```

**Answer:**

```text
True
```

Third element makes `any` true.

### Q170. Advanced

What does this print?

```python
print(tuple({1, 2, 3}))
```

**Answer:**

```text
(1, 2, 3)
```

Set iteration order varies; length is 3.

### Q171. Advanced

What does this print?

```python
t = (1, 2)
print(id(t), id(t + ()))
```

**Answer:**

```text
136103314260608 136103314260608
```

`t + ()` creates a new tuple object.

### Q172. Advanced

What does this print?

```python
print((1, 2).count(1) + (1, 2).count(2))
```

**Answer:**

```text
2
```

Sum of counts equals length when elements distinct.

### Q173. Intermediate

What does this print?

```python
print((1, 2, 3).index(3))
```

**Answer:**

```text
2
```

Last index is 2.

### Q174. Intermediate

What does this print?

```python
print((1, 2, 3).index(1, 1))
```

**Answer:**

```text
ValueError: tuple.index(x): x not in tuple
```

Searching from index 1 skips the first 1.

### Q175. Intermediate

What does this print?

```python
print((1, 2, 1).index(1, 1))
```

**Answer:**

```text
2
```

Second 1 starts at index 2.

### Q176. Intermediate

What does this print?

```python
print((1, 2, 3)[0:2])
```

**Answer:**

```text
(1, 2)
```

Slice stop is exclusive.

### Q177. Intermediate

What does this print?

```python
print((1, 2, 3)[2:1])
```

**Answer:**

```text
()
```

Empty when start is after stop with positive step.

### Q178. Intermediate

What does this print?

```python
print((1, 2, 3)[::-2])
```

**Answer:**

```text
(3, 1)
```

Reverse every other element.

### Q179. Intermediate

What does this print?

```python
print((1, 2) + (3,) == (1, 2, 3))
```

**Answer:**

```text
True
```

Concatenation matches literal.

### Q180. Advanced

What does this print?

```python
print((1, 2, 3) <= (1, 2, 3))
```

**Answer:**

```text
True
```

Equal tuples satisfy `<=`.

### Q181. Advanced

What does this print?

```python
print((1, 2, 4) >= (1, 2, 3))
```

**Answer:**

```text
True
```

Greater at third position.

### Q182. Advanced

What does this print?

```python
print((1, 2) != (1, 3))
```

**Answer:**

```text
True
```

Second element differs.

### Q183. Advanced

What does this print?

```python
print(min((('b', 2), ('a', 5)), key=lambda t: t[0]))
```

**Answer:**

```text
('a', 5)
```

Min picks tuple with smallest first element.

### Q184. Advanced

What does this print?

```python
print(max((('b', 2), ('a', 5)), key=lambda t: t[1]))
```

**Answer:**

```text
('a', 5)
```

Max by second element.

### Q185. Advanced

What does this print?

```python
print(sorted(((2, 'y'), (1, 'x'), (1, 'z'))))
```

**Answer:**

```text
[(1, 'x'), (1, 'z'), (2, 'y')]
```

Sort lexicographically by default.

### Q186. Advanced

What does this print?

```python
print(tuple(sorted(((2, 'y'), (1, 'x')), key=lambda t: t[1])))
```

**Answer:**

```text
((1, 'x'), (2, 'y'))
```

Sort by second field only.

### Q187. Advanced

What does this print?

```python
print(len(tuple(c for c in 'hello')))
```

**Answer:**

```text
5
```

Tuple from comprehension over string.

### Q188. Advanced

What does this print?

```python
print((1, 2, 3).count(1) + (1, 2, 3).count(2) + (1, 2, 3).count(3))
```

**Answer:**

```text
3
```

Counts sum to length when all distinct.

### Q189. Advanced

What does this print?

```python
print((1, 2, 3)[-1:-4:-1])
```

**Answer:**

```text
(3, 2, 1)
```

Negative step slice walking backward.

### Q190. Advanced

What does this print?

```python
print((1, 2) * 1 == (1, 2))
```

**Answer:**

```text
True
```

Repetition by 1 equals original values.

### Q191. Advanced

What does this print?

```python
print(tuple(reversed((1, 2, 3))) == (3, 2, 1))
```

**Answer:**

```text
True
```

Reversed materialization.

### Q192. Advanced

What does this print?

```python
print(sum((1, 2, 3), 10))
```

**Answer:**

```text
16
```

`sum` with start adds tuple into start.

### Q193. Advanced

What does this print?

```python
print(any(()) )
```

**Answer:**

```text
False
```

Empty tuple makes `any` false.

### Q194. Advanced

What does this print?

```python
print(all(()) )
```

**Answer:**

```text
True
```

Empty tuple makes `all` true (vacuous).

### Q195. Advanced

What does this print?

```python
print((1, 2, 3).index(2, 0, 2))
```

**Answer:**

```text
1
```

Search limited to indices 0 and 1 finds 2 at 1.

### Q196. Advanced

What happens when this runs?

```python
print((1, 2, 3).index(2, 0, 1))
```

**Answer:**

```text
ValueError: tuple.index(x): x not in tuple
```

Stop index 1 excludes index 1, so 2 is not found.

### Q197. Advanced

What does this print?

```python
print((1, 2, 3) < (1, 2, 3, 0))
```

**Answer:**

```text
True
```

Proper prefix: shorter tuple is less.

### Q198. Advanced

What does this print?

```python
print((1, 2, 3, 0) > (1, 2, 3))
```

**Answer:**

```text
True
```

Longer tuple with same prefix is greater.

### Q199. Advanced

What does this print?

```python
print(tuple(a for a in (1, 2)))
```

**Answer:**

```text
(1, 2)
```

Generator expression inside `tuple()` copies values.

### Q200. Advanced

What does this print?

```python
print((1, 2, 3).index(3, 2, 4))
```

**Answer:**

```text
2
```

Search window `[2:4)` finds 3 at index 2.

*Section size: 200 questions (Basic 70, Intermediate 70, Advanced 60).*

