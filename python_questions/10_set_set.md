## 10. Set (set)

An unordered mutable collection of hashable items. Membership is average O(1).

### Q1. Basic

What does this print?

```python
s = {1, 2, 3}
print(1 in s, 4 in s)
```

**Answer:**

```text
True False
```

Membership tests elements.

### Q2. Basic

What does this print?

```python
s = set([1, 2, 2, 3])
print(sorted(s))
```

**Answer:**

```text
[1, 2, 3]
```

Set keeps unique elements; sort to display.

### Q3. Basic

What does this print?

```python
s = {1, 2}
s.add(3)
print(sorted(s))
```

**Answer:**

```text
[1, 2, 3]
```

`add` inserts if absent.

### Q4. Basic

What does this print?

```python
s = {1, 2, 3}
s.remove(2)
print(sorted(s))
```

**Answer:**

```text
[1, 3]
```

`remove` deletes present element.

### Q5. Basic

What happens when this runs?

```python
s = {1}
s.remove(9)
```

**Answer:**

```text
KeyError: 9
```

`remove` on missing element raises `KeyError`.

### Q6. Basic

What does this print?

```python
s = {1, 2}
s.discard(9)
print(sorted(s))
```

**Answer:**

```text
[1, 2]
```

`discard` never raises for absence.

### Q7. Basic

What does this print?

```python
print({1, 2} | {2, 3})
```

**Answer:**

```text
{1, 2, 3}
```

Union via operator.

### Q8. Basic

What does this print?

```python
print({1, 2} & {2, 3})
```

**Answer:**

```text
{2}
```

Intersection via operator.

### Q9. Basic

What does this print?

```python
print({1, 2} - {2, 3})
```

**Answer:**

```text
{1}
```

Difference via operator.

### Q10. Basic

What does this print?

```python
print({1, 2} ^ {2, 3})
```

**Answer:**

```text
{1, 3}
```

Symmetric difference via operator.

### Q11. Basic

What does this print?

```python
a = {1, 2}
a.update({3, 4})
print(sorted(a))
```

**Answer:**

```text
[1, 2, 3, 4]
```

`update` adds from iterable.

### Q12. Basic

What does this print?

```python
a = {1, 2}
a |= {2, 3}
print(sorted(a))
```

**Answer:**

```text
[1, 2, 3]
```

`|=` in-place union.

### Q13. Basic

What does this print?

```python
a = {1, 2, 3}
a &= {2, 3, 4}
print(sorted(a))
```

**Answer:**

```text
[2, 3]
```

`&=` in-place intersection.

### Q14. Basic

What does this print?

```python
a = {1, 2, 3}
a -= {3}
print(sorted(a))
```

**Answer:**

```text
[1, 2]
```

`-=` in-place difference.

### Q15. Basic

What does this print?

```python
a = {1, 2}
a ^= {2, 3}
print(sorted(a))
```

**Answer:**

```text
[1, 3]
```

`^=` in-place symmetric difference.

### Q16. Basic

What does this print?

```python
print({1, 2} <= {1, 2, 3}, {1, 2, 3} >= {1, 2})
```

**Answer:**

```text
True True
```

Subset and superset.

### Q17. Basic

What does this print?

```python
print({1, 2} < {1, 2, 3}, {1, 2} < {1, 2})
```

**Answer:**

```text
True False
```

Proper subset tests.

### Q18. Basic

What does this print?

```python
print({1, 2} == {2, 1})
```

**Answer:**

```text
True
```

Equality ignores insertion order.

### Q19. Basic

What happens when this runs?

```python
s = {1, 2}
print(s[0])
```

**Answer:**

```text
TypeError: 'set' object is not subscriptable
```

Sets are not indexable.

### Q20. Basic

What happens when this runs?

```python
s = set()
s.add([1])
```

**Answer:**

```text
TypeError: unhashable type: 'list'
```

Lists are unhashable set elements.

### Q21. Basic

What does this print?

```python
print(sorted({x for x in 'hello'}))
```

**Answer:**

```text
['e', 'h', 'l', 'o']
```

Set comprehension deduplicates.

### Q22. Basic

What does this print?

```python
print(len({1, 2, 2}))
```

**Answer:**

```text
2
```

Length counts unique elements.

### Q23. Basic

What does this print?

```python
print(bool(set()), bool({0}))
```

**Answer:**

```text
False True
```

Empty set falsy; non-empty truthy.

### Q24. Basic

What does this print?

```python
s = set('aba')
print(sorted(s))
```

**Answer:**

```text
['a', 'b']
```

Constructor deduplicates iterable.

### Q25. Basic

What does this print?

```python
a = {1, 2}
b = a
b.add(3)
print(sorted(a))
```

**Answer:**

```text
[1, 2, 3]
```

Aliasing shares one set object.

### Q26. Basic

What does this print?

```python
print(set())
```

**Answer:**

```text
set()
```

Empty set constructor.

### Q27. Basic

What happens when this runs?

```python
print({})
```

**Answer:**

```text
{}
```

`{}` is empty dict, not set.

### Q28. Basic

What does this print?

```python
print(type(set()), type({}))
```

**Answer:**

```text
<class 'set'> <class 'dict'>
```

Types differ for set vs dict literal.

### Q29. Basic

What does this print?

```python
s = {1, 2}
print(s.pop())
```

**Answer:**

```text
1
```

`pop` removes arbitrary element.

### Q30. Basic

What does this print?

```python
s = {1, 2, 3}
s.clear()
print(len(s))
```

**Answer:**

```text
0
```

`clear` removes all elements.

### Q31. Basic

What does this print?

```python
print(frozenset({1, 2}) == {1, 2})
```

**Answer:**

```text
True
```

Frozenset equals set with same elements.

### Q32. Basic

What does this print?

```python
a = {1, 2}
print(sorted(a.union({3})))
```

**Answer:**

```text
[1, 2, 3]
```

`.union` returns new set.

### Q33. Basic

What does this print?

```python
a = {1, 2}
print(sorted(a.intersection({2, 9})))
```

**Answer:**

```text
[2]
```

`.intersection` accepts iterable.

### Q34. Basic

What does this print?

```python
a = {1, 2, 3}
print(sorted(a.difference({3})))
```

**Answer:**

```text
[1, 2]
```

`.difference` removes elements.

### Q35. Basic

What does this print?

```python
a = {1, 2}
print(sorted(a.symmetric_difference({2, 3})))
```

**Answer:**

```text
[1, 3]
```

`.symmetric_difference` is `^` method form.

### Q36. Basic

What does this print?

```python
a = {1, 2}
print(a.isdisjoint({3, 4}))
```

**Answer:**

```text
True
```

`isdisjoint` checks empty intersection.

### Q37. Basic

What does this print?

```python
s = {1, 2, 3}
print(min(s), max(s))
```

**Answer:**

```text
1 3
```

`min`/`max` work on sets.

### Q38. Basic

What does this print?

```python
s = {3, 1, 2}
print(sorted(s))
```

**Answer:**

```text
[1, 2, 3]
```

Sort for deterministic output.

### Q39. Basic

What does this print?

```python
a = {1, 2}
b = {1, 2}
print(a == b)
```

**Answer:**

```text
True
```

Equal contents compare equal.

### Q40. Basic

What happens when this runs?

```python
s = {{1}, {2}}
```

**Answer:**

```text
TypeError: unhashable type: 'set'
```

Inner sets must be hashable; plain sets are not.

### Q41. Basic

What does this print?

```python
s = {1, 2, 3}
print(len(s))
```

**Answer:**

```text
3
```

Len counts elements.

### Q42. Basic

What does this print?

```python
s = {1, 2}
print(sorted(s | {2, 3}))
```

**Answer:**

```text
[1, 2, 3]
```

Operator union sorts for display.

### Q43. Basic

What does this print?

```python
s = {1, 2, 3}
print(sorted(s & {2, 3, 4}))
```

**Answer:**

```text
[2, 3]
```

Operator intersection.

### Q44. Basic

What does this print?

```python
s = {1, 2, 3}
print(sorted(s - {3}))
```

**Answer:**

```text
[1, 2]
```

Operator difference.

### Q45. Basic

What does this print?

```python
s = {1, 2, 3}
print(sorted(s ^ {2, 3, 4}))
```

**Answer:**

```text
[1, 4]
```

Operator symmetric difference.

### Q46. Basic

What does this print?

```python
s = {1, 2}
s.update('ab')
print(sorted(s))
```

**Answer:**

```text
TypeError: '<' not supported between instances of 'str' and 'int'
```

`update` accepts any hashable iterable.

### Q47. Basic

What does this print?

```python
print({1, 2, 3}.issubset({1, 2, 3, 4}))
```

**Answer:**

```text
True
```

`.issubset` method form.

### Q48. Basic

What does this print?

```python
print({1, 2, 3, 4}.issuperset({1, 2}))
```

**Answer:**

```text
True
```

`.issuperset` method form.

### Q49. Basic

What does this print?

```python
print({1, 2}.isdisjoint({3, 4}))
```

**Answer:**

```text
True
```

`.isdisjoint` method form.

### Q50. Basic

What does this print?

```python
a = {1, 2}
print(a <= a, a >= a)
```

**Answer:**

```text
True True
```

Every set is subset and superset of itself.

### Q51. Basic

What does this print?

```python
print(len(set('mississippi')))
```

**Answer:**

```text
4
```

Count unique letters.

### Q52. Basic

What does this print?

```python
print(sorted(set(['a', 'b', 'a'])))
```

**Answer:**

```text
['a', 'b']
```

List to set deduplicates.

### Q53. Basic

What does this print?

```python
print(sorted(set(('x', 'y', 'x'))))
```

**Answer:**

```text
['x', 'y']
```

Tuple to set deduplicates.

### Q54. Basic

What does this print?

```python
print(sorted(set(range(3))))
```

**Answer:**

```text
[0, 1, 2]
```

Range to set.

### Q55. Basic

What does this print?

```python
print(sorted(set('abc') & set('bcd')))
```

**Answer:**

```text
['b', 'c']
```

Intersection of letter sets.

### Q56. Basic

What does this print?

```python
print(sorted(set('abc') | set('xyz')))
```

**Answer:**

```text
['a', 'b', 'c', 'x', 'y', 'z']
```

Union of letter sets.

### Q57. Basic

What does this print?

```python
print(sorted(set('abc') - set('a')))
```

**Answer:**

```text
['b', 'c']
```

Difference removing vowel/consonant.

### Q58. Basic

What does this print?

```python
print(sorted(set('ab') ^ set('bc')))
```

**Answer:**

```text
['a', 'c']
```

Symmetric difference on letters.

### Q59. Basic

What does this print?

```python
s = set('cat')
print('c' in s, 'z' in s)
```

**Answer:**

```text
True False
```

Char membership.

### Q60. Basic

What does this print?

```python
s = {True, 1, 2}
print(len(s))
```

**Answer:**

```text
2
```

`True` and `1` collapse to one member.

### Q61. Basic

What does this print?

```python
s = {1, 1.0, 2}
print(len(s))
```

**Answer:**

```text
2
```

`1` and `1.0` are one member.

### Q62. Basic

What does this print?

```python
print(sorted({1, 2, 3}.intersection([2, 3, 4])))
```

**Answer:**

```text
[2, 3]
```

Intersection with list iterable.

### Q63. Basic

What does this print?

```python
print(sorted({1, 2}.union([2, 3])))
```

**Answer:**

```text
[1, 2, 3]
```

Union with list iterable.

### Q64. Basic

What does this print?

```python
print(sorted({1, 2, 3}.difference([3])))
```

**Answer:**

```text
[1, 2]
```

Difference with list iterable.

### Q65. Basic

What does this print?

```python
print(sorted({1, 2}.symmetric_difference([2, 3])))
```

**Answer:**

```text
[1, 3]
```

Symmetric difference with list.

### Q66. Basic

What does this print?

```python
s = {1, 2, 3}
print(sorted(s.copy()))
```

**Answer:**

```text
[1, 2, 3]
```

`.copy()` returns shallow copy of set.

### Q67. Basic

What does this print?

```python
s = {1, 2}
t = s.copy()
t.add(3)
print(sorted(s), sorted(t))
```

**Answer:**

```text
[1, 2] [1, 2, 3]
```

Copy is independent outer set.

### Q68. Basic

What does this print?

```python
print(hash(frozenset({1, 2})))
```

**Answer:**

```text
-1826646154956904602
```

Frozenset is hashable.

### Q69. Basic

What does this print?

```python
print(type({1, 2}.pop()) is int)
```

**Answer:**

```text
True
```

Pop returns an element (int here).

### Q70. Basic

What does this print?

```python
s = {1, 2, 3}
s.intersection_update([2, 3])
print(sorted(s))
```

**Answer:**

```text
[2, 3]
```

`.intersection_update` mutates to intersection.

### Q71. Basic

What does this print?

```python
s = {1, 2, 3}
s &= set([2, 3, 4])
print(sorted(s))
```

**Answer:**

```text
[2, 3]
```

In-place intersection with temporary set.

### Q72. Basic

What does this print?

```python
s = {1, 2, 3}
s |= set([3, 4])
print(sorted(s))
```

**Answer:**

```text
[1, 2, 3, 4]
```

In-place union with temporary set.

### Q73. Basic

What does this print?

```python
s = set()
s.add('alpha')
print('alpha' in s)
```

**Answer:**

```text
True
```

`add` stores `alpha`.

### Q74. Basic

What does this print?

```python
s = set()
s.add('bravo')
print('bravo' in s)
```

**Answer:**

```text
True
```

`add` stores `bravo`.

### Q75. Basic

What does this print?

```python
s = set()
s.add('charlie')
print('charlie' in s)
```

**Answer:**

```text
True
```

`add` stores `charlie`.

### Q76. Basic

What does this print?

```python
s = set()
s.add('delta')
print('delta' in s)
```

**Answer:**

```text
True
```

`add` stores `delta`.

### Q77. Basic

What does this print?

```python
s = set()
s.add('echo')
print('echo' in s)
```

**Answer:**

```text
True
```

`add` stores `echo`.

### Q78. Basic

What does this print?

```python
s = set()
s.add('foxtrot')
print('foxtrot' in s)
```

**Answer:**

```text
True
```

`add` stores `foxtrot`.

### Q79. Intermediate

What does this print?

```python
def jaccard(a, b):
    u = a | b
    return len(a & b) / len(u) if u else 1.0
print(jaccard({1,2},{1,2,3,4}))
```

**Answer:**

```text
0.5
```

Jaccard is |∩|/|∪|; here 2/4.

### Q80. Intermediate

What does this print?

```python
seq = [3, 1, 3, 2, 1]
print(list(dict.fromkeys(seq)))
```

**Answer:**

```text
[3, 1, 2]
```

Sets lack order; `dict.fromkeys` preserves first-seen order.

### Q81. Intermediate

What does this print?

```python
s = {1, 2, 3}
print(2 ** len(s))
```

**Answer:**

```text
8
```

Powerset size is 2**n for n elements.

### Q82. Intermediate

What does this print?

```python
s = {1, 2, 3}
print(sorted(s), sorted(set(sorted(s))))
```

**Answer:**

```text
[1, 2, 3] [1, 2, 3]
```

Sorting before set does not encode order in the set.

### Q83. Intermediate

What does this print?

```python
a = {1, 2, 3}
b = {3, 4}
print(sorted(a & b), sorted(a | b))
```

**Answer:**

```text
[3] [1, 2, 3, 4]
```

Combine intersection and union views.

### Q84. Intermediate

What does this print?

```python
print({1, 2, 3} <= frozenset({1, 2, 3, 4}))
```

**Answer:**

```text
True
```

Set compares to frozenset with same elements.

### Q85. Intermediate

What does this print?

```python
s = set('abc')
print(sorted(s.intersection('bcd')))
```

**Answer:**

```text
['b', 'c']
```

Intersection accepts string iterable.

### Q86. Intermediate

What does this print?

```python
s = set('abc')
print(sorted(s.difference('a')))
```

**Answer:**

```text
['b', 'c']
```

Difference with string iterable.

### Q87. Intermediate

What does this print?

```python
s = set('abc')
print(sorted(s.symmetric_difference('bc')))
```

**Answer:**

```text
['a']
```

Symmetric difference with string.

### Q88. Intermediate

What does this print?

```python
s = {1, 2, 3}
print(all(x > 0 for x in s))
```

**Answer:**

```text
True
```

Quantifier over set elements.

### Q89. Intermediate

What does this print?

```python
s = {1, 2, 3}
print(any(x > 2 for x in s))
```

**Answer:**

```text
True
```

`any` over set.

### Q90. Intermediate

What does this print?

```python
s = {1, 2, 3}
print(sum(s))
```

**Answer:**

```text
6
```

Sum elements (ints).

### Q91. Intermediate

What does this print?

```python
s = {1, 2, 3}
print(sorted(s, reverse=True))
```

**Answer:**

```text
[3, 2, 1]
```

Built-in sorted with reverse.

### Q92. Intermediate

What does this print?

```python
s = {3, 1, 2}
print(sorted(s, key=str))
```

**Answer:**

```text
[1, 2, 3]
```

Sorted with key function.

### Q93. Intermediate

What does this print?

```python
a = {1, 2}
b = {2, 3}
print(sorted(a | b), sorted(a & b))
```

**Answer:**

```text
[1, 2, 3] [2]
```

Union and intersection together.

### Q94. Intermediate

What does this print?

```python
a = {1, 2}
b = {2, 3}
print(sorted(a ^ b))
```

**Answer:**

```text
[1, 3]
```

Symmetric difference alone.

### Q95. Intermediate

What does this print?

```python
s = {1, 2, 3}
print(len(s | {3, 4}), len(s & {2, 3}))
```

**Answer:**

```text
4 2
```

Lengths after ops.

### Q96. Intermediate

What does this print?

```python
s = {1, 2}
print(s.issubset({1, 2, 3}), s.issuperset({1}))
```

**Answer:**

```text
True True
```

Method subset/superset.

### Q97. Intermediate

What does this print?

```python
s = {1, 2, 3}
print(s.isdisjoint({4, 5}))
```

**Answer:**

```text
True
```

Disjoint from distant set.

### Q98. Intermediate

What does this print?

```python
print(sorted(set(map(str, [1, 2, 2]))))
```

**Answer:**

```text
['1', '2']
```

Map then set deduplicates.

### Q99. Intermediate

What does this print?

```python
print(sorted(set(filter(None, [0, 1, 0, 2]))))
```

**Answer:**

```text
[1, 2]
```

Filter falsy then unique.

### Q100. Intermediate

What does this print?

```python
print(sorted(set([1, 2]) & set([2, 3])))
```

**Answer:**

```text
[2]
```

Intersection of two set constructors.

### Q101. Intermediate

What does this print?

```python
print(sorted(set('a') | set('b')))
```

**Answer:**

```text
['a', 'b']
```

Union of single-letter sets.

### Q102. Intermediate

What does this print?

```python
print(sorted(set('ab') - set('a')))
```

**Answer:**

```text
['b']
```

Difference removing one letter.

### Q103. Intermediate

What does this print?

```python
print(sorted(set('ab') ^ set('bc')))
```

**Answer:**

```text
['a', 'c']
```

Symmetric diff on small letter sets.

### Q104. Intermediate

What does this print?

```python
s = {1, 2, 3}
for x in s:
    pass
print(len(s))
```

**Answer:**

```text
3
```

Iteration does not change size.

### Q105. Intermediate

What does this print?

```python
s = {1, 2, 3}
print(list(s)[0] in s)
```

**Answer:**

```text
True
```

Materialized list element still in set.

### Q106. Intermediate

What does this print?

```python
print(len(set(range(10)) - set(range(5))))
```

**Answer:**

```text
5
```

Range difference size.

### Q107. Intermediate

What does this print?

```python
print(len(set('hello world'.split())))
```

**Answer:**

```text
2
```

Unique words count.

### Q108. Intermediate

What does this print?

```python
print(sorted(set([1, 2, 3]) ^ set([3, 4, 5])))
```

**Answer:**

```text
[1, 2, 4, 5]
```

Symmetric diff of numeric sets.

### Q109. Intermediate

What does this print?

```python
print(sorted(set([1, 2]) | set([3])))
```

**Answer:**

```text
[1, 2, 3]
```

Union adding disjoint element.

### Q110. Intermediate

What does this print?

```python
print(sorted(set([1, 2, 3]) & set([2, 3, 4])))
```

**Answer:**

```text
[2, 3]
```

Intersection overlap region.

### Q111. Intermediate

What does this print?

```python
print(sorted(set([1, 2, 3]) - set([1])))
```

**Answer:**

```text
[2, 3]
```

Difference removing min element.

### Q112. Intermediate

What does this print?

```python
print(sorted(set('abc') | set('abc')))
```

**Answer:**

```text
['a', 'b', 'c']
```

Union with equal set is unchanged.

### Q113. Intermediate

What does this print?

```python
print(sorted(set('abc') & set('abc')))
```

**Answer:**

```text
['a', 'b', 'c']
```

Intersection with equal set.

### Q114. Intermediate

What does this print?

```python
print(sorted(set('abc') ^ set('abc')))
```

**Answer:**

```text
[]
```

Symmetric diff with self is empty.

### Q115. Intermediate

What does this print?

```python
print(sorted(set('abc') - set('abc')))
```

**Answer:**

```text
[]
```

Difference with self is empty.

### Q116. Intermediate

What does this print?

```python
s = {1, 2, 3}
print(sorted(s.intersection([1, 2])))
```

**Answer:**

```text
[1, 2]
```

Intersection with list.

### Q117. Intermediate

What does this print?

```python
s = {1, 2, 3}
print(sorted(s.union([4])))
```

**Answer:**

```text
[1, 2, 3, 4]
```

Union adding via list.

### Q118. Intermediate

What does this print?

```python
s = {1, 2, 3}
print(sorted(s.difference([3])))
```

**Answer:**

```text
[1, 2]
```

Difference via list.

### Q119. Intermediate

What does this print?

```python
s = {1, 2, 3}
print(sorted(s.symmetric_difference([3, 4])))
```

**Answer:**

```text
[1, 2, 4]
```

Symmetric diff via list.

### Q120. Intermediate

What does this print?

```python
print(sorted(set([1, 2, 3, 4, 5]) & set([4, 5, 6])))
```

**Answer:**

```text
[4, 5]
```

Overlap tail elements.

### Q121. Intermediate

What does this print?

```python
print(sorted(set([1, 2, 3, 4, 5]) | set([6])))
```

**Answer:**

```text
[1, 2, 3, 4, 5, 6]
```

Union attach new element.

### Q122. Intermediate

What does this print?

```python
print(sorted(set([1, 2, 3, 4, 5]) - set([5])))
```

**Answer:**

```text
[1, 2, 3, 4]
```

Remove max element.

### Q123. Intermediate

What does this print?

```python
print(sorted(set([1, 2, 3, 4, 5]) ^ set([1, 5])))
```

**Answer:**

```text
[2, 3, 4]
```

Symmetric diff endpoints.

### Q124. Intermediate

What does this print?

```python
print(sorted(set('abcde') & set('cdefg')))
```

**Answer:**

```text
['c', 'd', 'e']
```

Letter overlap middle.

### Q125. Intermediate

What does this print?

```python
print(sorted(set('abcde') | set('fghij')))
```

**Answer:**

```text
['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']
```

Disjoint letter union.

### Q126. Intermediate

What does this print?

```python
print(sorted(set('abcde') - set('ae')))
```

**Answer:**

```text
['b', 'c', 'd']
```

Remove endpoints from letters.

### Q127. Intermediate

What does this print?

```python
print(sorted(set('abcde') ^ set('ace')))
```

**Answer:**

```text
['b', 'd']
```

Symmetric diff every other letter.

### Q128. Intermediate

What does this print?

```python
s = set('python')
print('p' in s, 'z' in s)
```

**Answer:**

```text
True False
```

Membership in word set.

### Q129. Intermediate

What does this print?

```python
s = set('unique')
print(len(s))
```

**Answer:**

```text
5
```

Unique letters count.

### Q130. Intermediate

What does this print?

```python
print(sorted(set('aabbcc')))
```

**Answer:**

```text
['a', 'b', 'c']
```

Dedup repeated letters.

### Q131. Intermediate

What does this print?

```python
print(sorted(set(['aa', 'bb', 'aa'])))
```

**Answer:**

```text
['aa', 'bb']
```

Dedup repeated strings.

### Q132. Intermediate

What does this print?

```python
print(sorted(set(frozenset({1, 2}) for _ in range(2))))
```

**Answer:**

```text
[frozenset({1, 2})]
```

Set of equal frozensets collapses.

### Q133. Intermediate

What does this print?

```python
print(sorted({frozenset({1, 2}), frozenset({3})}))
```

**Answer:**

```text
[frozenset({3}), frozenset({1, 2})]
```

Set of distinct frozensets.

### Q134. Intermediate

What does this print?

```python
print(len(set([1, 2, 3]) | set([3, 4])))
```

**Answer:**

```text
4
```

Union size with overlap.

### Q135. Intermediate

What does this print?

```python
print(len(set([1, 2, 3]) & set([2, 3, 4])))
```

**Answer:**

```text
2
```

Intersection size.

### Q136. Intermediate

What does this print?

```python
print(len(set([1, 2, 3]) - set([2])))
```

**Answer:**

```text
2
```

Difference size.

### Q137. Intermediate

What does this print?

```python
print(len(set([1, 2, 3]) ^ set([2, 3])))
```

**Answer:**

```text
1
```

Symmetric diff size.

### Q138. Intermediate

What does this print?

```python
a = set('abc')
b = set('bcd')
print(sorted(a), sorted(b), sorted(a & b))
```

**Answer:**

```text
['a', 'b', 'c'] ['b', 'c', 'd'] ['b', 'c']
```

Three sorted views.

### Q139. Intermediate

What does this print?

```python
print(sorted(set([1, 2, 3, 4]) <= set([1, 2, 3, 4, 5])))
```

**Answer:**

```text
TypeError: 'bool' object is not iterable
```

Subset comparison truth value only.

### Q140. Advanced

What does this print?

```python
a = {'uniform', 'uniform_pair'}
b = {'uniform_pair', 'uniform_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['uniform_pair'] ['uniform', 'uniform_other']
```

Intersection and symmetric difference on `uniform` sets.

### Q141. Advanced

What does this print?

```python
a = {'victor', 'victor_pair'}
b = {'victor_pair', 'victor_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['victor_pair'] ['victor', 'victor_other']
```

Intersection and symmetric difference on `victor` sets.

### Q142. Advanced

What does this print?

```python
a = {'whiskey', 'whiskey_pair'}
b = {'whiskey_pair', 'whiskey_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['whiskey_pair'] ['whiskey', 'whiskey_other']
```

Intersection and symmetric difference on `whiskey` sets.

### Q143. Advanced

What does this print?

```python
a = {'xray', 'xray_pair'}
b = {'xray_pair', 'xray_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['xray_pair'] ['xray', 'xray_other']
```

Intersection and symmetric difference on `xray` sets.

### Q144. Advanced

What does this print?

```python
a = {'yankee', 'yankee_pair'}
b = {'yankee_pair', 'yankee_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['yankee_pair'] ['yankee', 'yankee_other']
```

Intersection and symmetric difference on `yankee` sets.

### Q145. Advanced

What does this print?

```python
a = {'zulu', 'zulu_pair'}
b = {'zulu_pair', 'zulu_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['zulu_pair'] ['zulu', 'zulu_other']
```

Intersection and symmetric difference on `zulu` sets.

### Q146. Advanced

What does this print?

```python
a = {'amber', 'amber_pair'}
b = {'amber_pair', 'amber_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['amber_pair'] ['amber', 'amber_other']
```

Intersection and symmetric difference on `amber` sets.

### Q147. Advanced

What does this print?

```python
a = {'bronze', 'bronze_pair'}
b = {'bronze_pair', 'bronze_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['bronze_pair'] ['bronze', 'bronze_other']
```

Intersection and symmetric difference on `bronze` sets.

### Q148. Advanced

What does this print?

```python
a = {'coral', 'coral_pair'}
b = {'coral_pair', 'coral_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['coral_pair'] ['coral', 'coral_other']
```

Intersection and symmetric difference on `coral` sets.

### Q149. Advanced

What does this print?

```python
a = {'denim', 'denim_pair'}
b = {'denim_pair', 'denim_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['denim_pair'] ['denim', 'denim_other']
```

Intersection and symmetric difference on `denim` sets.

### Q150. Advanced

What does this print?

```python
a = {'ebony', 'ebony_pair'}
b = {'ebony_pair', 'ebony_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['ebony_pair'] ['ebony', 'ebony_other']
```

Intersection and symmetric difference on `ebony` sets.

### Q151. Advanced

What does this print?

```python
a = {'flint', 'flint_pair'}
b = {'flint_pair', 'flint_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['flint_pair'] ['flint', 'flint_other']
```

Intersection and symmetric difference on `flint` sets.

### Q152. Advanced

What does this print?

```python
a = {'granite', 'granite_pair'}
b = {'granite_pair', 'granite_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['granite_pair'] ['granite', 'granite_other']
```

Intersection and symmetric difference on `granite` sets.

### Q153. Advanced

What does this print?

```python
a = {'hazel', 'hazel_pair'}
b = {'hazel_pair', 'hazel_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['hazel_pair'] ['hazel', 'hazel_other']
```

Intersection and symmetric difference on `hazel` sets.

### Q154. Advanced

What does this print?

```python
a = {'ivory', 'ivory_pair'}
b = {'ivory_pair', 'ivory_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['ivory_pair'] ['ivory', 'ivory_other']
```

Intersection and symmetric difference on `ivory` sets.

### Q155. Advanced

What does this print?

```python
a = {'jade', 'jade_pair'}
b = {'jade_pair', 'jade_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['jade_pair'] ['jade', 'jade_other']
```

Intersection and symmetric difference on `jade` sets.

### Q156. Advanced

What does this print?

```python
a = {'khaki', 'khaki_pair'}
b = {'khaki_pair', 'khaki_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['khaki_pair'] ['khaki', 'khaki_other']
```

Intersection and symmetric difference on `khaki` sets.

### Q157. Advanced

What does this print?

```python
a = {'linen', 'linen_pair'}
b = {'linen_pair', 'linen_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['linen_pair'] ['linen', 'linen_other']
```

Intersection and symmetric difference on `linen` sets.

### Q158. Advanced

What does this print?

```python
a = {'maroon', 'maroon_pair'}
b = {'maroon_pair', 'maroon_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['maroon_pair'] ['maroon', 'maroon_other']
```

Intersection and symmetric difference on `maroon` sets.

### Q159. Advanced

What does this print?

```python
a = {'navy', 'navy_pair'}
b = {'navy_pair', 'navy_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['navy_pair'] ['navy', 'navy_other']
```

Intersection and symmetric difference on `navy` sets.

### Q160. Advanced

What does this print?

```python
a = {'olive', 'olive_pair'}
b = {'olive_pair', 'olive_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['olive_pair'] ['olive', 'olive_other']
```

Intersection and symmetric difference on `olive` sets.

### Q161. Advanced

What does this print?

```python
a = {'pearl', 'pearl_pair'}
b = {'pearl_pair', 'pearl_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['pearl_pair'] ['pearl', 'pearl_other']
```

Intersection and symmetric difference on `pearl` sets.

### Q162. Advanced

What does this print?

```python
a = {'quartz', 'quartz_pair'}
b = {'quartz_pair', 'quartz_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['quartz_pair'] ['quartz', 'quartz_other']
```

Intersection and symmetric difference on `quartz` sets.

### Q163. Advanced

What does this print?

```python
a = {'ruby', 'ruby_pair'}
b = {'ruby_pair', 'ruby_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['ruby_pair'] ['ruby', 'ruby_other']
```

Intersection and symmetric difference on `ruby` sets.

### Q164. Advanced

What does this print?

```python
a = {'sage', 'sage_pair'}
b = {'sage_pair', 'sage_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['sage_pair'] ['sage', 'sage_other']
```

Intersection and symmetric difference on `sage` sets.

### Q165. Advanced

What does this print?

```python
a = {'teal', 'teal_pair'}
b = {'teal_pair', 'teal_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['teal_pair'] ['teal', 'teal_other']
```

Intersection and symmetric difference on `teal` sets.

### Q166. Advanced

What does this print?

```python
a = {'umber', 'umber_pair'}
b = {'umber_pair', 'umber_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['umber_pair'] ['umber', 'umber_other']
```

Intersection and symmetric difference on `umber` sets.

### Q167. Advanced

What does this print?

```python
a = {'violet', 'violet_pair'}
b = {'violet_pair', 'violet_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['violet_pair'] ['violet', 'violet_other']
```

Intersection and symmetric difference on `violet` sets.

### Q168. Advanced

What does this print?

```python
a = {'walnut', 'walnut_pair'}
b = {'walnut_pair', 'walnut_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['walnut_pair'] ['walnut', 'walnut_other']
```

Intersection and symmetric difference on `walnut` sets.

### Q169. Advanced

What does this print?

```python
a = {'xenon', 'xenon_pair'}
b = {'xenon_pair', 'xenon_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['xenon_pair'] ['xenon', 'xenon_other']
```

Intersection and symmetric difference on `xenon` sets.

### Q170. Advanced

What does this print?

```python
a = {'yarrow', 'yarrow_pair'}
b = {'yarrow_pair', 'yarrow_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['yarrow_pair'] ['yarrow', 'yarrow_other']
```

Intersection and symmetric difference on `yarrow` sets.

### Q171. Advanced

What does this print?

```python
a = {'zinc', 'zinc_pair'}
b = {'zinc_pair', 'zinc_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['zinc_pair'] ['zinc', 'zinc_other']
```

Intersection and symmetric difference on `zinc` sets.

### Q172. Advanced

What does this print?

```python
a = {'atlas', 'atlas_pair'}
b = {'atlas_pair', 'atlas_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['atlas_pair'] ['atlas', 'atlas_other']
```

Intersection and symmetric difference on `atlas` sets.

### Q173. Advanced

What does this print?

```python
a = {'breeze', 'breeze_pair'}
b = {'breeze_pair', 'breeze_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['breeze_pair'] ['breeze', 'breeze_other']
```

Intersection and symmetric difference on `breeze` sets.

### Q174. Advanced

What does this print?

```python
a = {'cinder', 'cinder_pair'}
b = {'cinder_pair', 'cinder_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['cinder_pair'] ['cinder', 'cinder_other']
```

Intersection and symmetric difference on `cinder` sets.

### Q175. Advanced

What does this print?

```python
a = {'drift', 'drift_pair'}
b = {'drift_pair', 'drift_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['drift_pair'] ['drift', 'drift_other']
```

Intersection and symmetric difference on `drift` sets.

### Q176. Advanced

What does this print?

```python
a = {'ember', 'ember_pair'}
b = {'ember_pair', 'ember_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['ember_pair'] ['ember', 'ember_other']
```

Intersection and symmetric difference on `ember` sets.

### Q177. Advanced

What does this print?

```python
a = {'frost', 'frost_pair'}
b = {'frost_pair', 'frost_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['frost_pair'] ['frost', 'frost_other']
```

Intersection and symmetric difference on `frost` sets.

### Q178. Advanced

What does this print?

```python
a = {'glow', 'glow_pair'}
b = {'glow_pair', 'glow_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['glow_pair'] ['glow', 'glow_other']
```

Intersection and symmetric difference on `glow` sets.

### Q179. Advanced

What does this print?

```python
a = {'haven', 'haven_pair'}
b = {'haven_pair', 'haven_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['haven_pair'] ['haven', 'haven_other']
```

Intersection and symmetric difference on `haven` sets.

### Q180. Advanced

What does this print?

```python
a = {'inlet', 'inlet_pair'}
b = {'inlet_pair', 'inlet_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['inlet_pair'] ['inlet', 'inlet_other']
```

Intersection and symmetric difference on `inlet` sets.

### Q181. Advanced

What does this print?

```python
a = {'jewel', 'jewel_pair'}
b = {'jewel_pair', 'jewel_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['jewel_pair'] ['jewel', 'jewel_other']
```

Intersection and symmetric difference on `jewel` sets.

### Q182. Advanced

What does this print?

```python
a = {'knight', 'knight_pair'}
b = {'knight_pair', 'knight_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['knight_pair'] ['knight', 'knight_other']
```

Intersection and symmetric difference on `knight` sets.

### Q183. Advanced

What does this print?

```python
a = {'lunar', 'lunar_pair'}
b = {'lunar_pair', 'lunar_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['lunar_pair'] ['lunar', 'lunar_other']
```

Intersection and symmetric difference on `lunar` sets.

### Q184. Advanced

What does this print?

```python
a = {'mossy', 'mossy_pair'}
b = {'mossy_pair', 'mossy_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['mossy_pair'] ['mossy', 'mossy_other']
```

Intersection and symmetric difference on `mossy` sets.

### Q185. Advanced

What does this print?

```python
a = {'nebula', 'nebula_pair'}
b = {'nebula_pair', 'nebula_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['nebula_pair'] ['nebula', 'nebula_other']
```

Intersection and symmetric difference on `nebula` sets.

### Q186. Advanced

What does this print?

```python
a = {'orbit', 'orbit_pair'}
b = {'orbit_pair', 'orbit_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['orbit_pair'] ['orbit', 'orbit_other']
```

Intersection and symmetric difference on `orbit` sets.

### Q187. Advanced

What does this print?

```python
a = {'prism', 'prism_pair'}
b = {'prism_pair', 'prism_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['prism_pair'] ['prism', 'prism_other']
```

Intersection and symmetric difference on `prism` sets.

### Q188. Advanced

What does this print?

```python
a = {'quill', 'quill_pair'}
b = {'quill_pair', 'quill_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['quill_pair'] ['quill', 'quill_other']
```

Intersection and symmetric difference on `quill` sets.

### Q189. Advanced

What does this print?

```python
a = {'ridge', 'ridge_pair'}
b = {'ridge_pair', 'ridge_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['ridge_pair'] ['ridge', 'ridge_other']
```

Intersection and symmetric difference on `ridge` sets.

### Q190. Advanced

What does this print?

```python
a = {'spark', 'spark_pair'}
b = {'spark_pair', 'spark_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['spark_pair'] ['spark', 'spark_other']
```

Intersection and symmetric difference on `spark` sets.

### Q191. Advanced

What does this print?

```python
a = {'thorn', 'thorn_pair'}
b = {'thorn_pair', 'thorn_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['thorn_pair'] ['thorn', 'thorn_other']
```

Intersection and symmetric difference on `thorn` sets.

### Q192. Advanced

What does this print?

```python
a = {'upland', 'upland_pair'}
b = {'upland_pair', 'upland_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['upland_pair'] ['upland', 'upland_other']
```

Intersection and symmetric difference on `upland` sets.

### Q193. Advanced

What does this print?

```python
a = {'vortex', 'vortex_pair'}
b = {'vortex_pair', 'vortex_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['vortex_pair'] ['vortex', 'vortex_other']
```

Intersection and symmetric difference on `vortex` sets.

### Q194. Advanced

What does this print?

```python
a = {'wisp', 'wisp_pair'}
b = {'wisp_pair', 'wisp_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['wisp_pair'] ['wisp', 'wisp_other']
```

Intersection and symmetric difference on `wisp` sets.

### Q195. Advanced

What does this print?

```python
a = {'yonder', 'yonder_pair'}
b = {'yonder_pair', 'yonder_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['yonder_pair'] ['yonder', 'yonder_other']
```

Intersection and symmetric difference on `yonder` sets.

### Q196. Advanced

What does this print?

```python
a = {'zephyr', 'zephyr_pair'}
b = {'zephyr_pair', 'zephyr_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['zephyr_pair'] ['zephyr', 'zephyr_other']
```

Intersection and symmetric difference on `zephyr` sets.

### Q197. Advanced

What does this print?

```python
a = {'acorn', 'acorn_pair'}
b = {'acorn_pair', 'acorn_other'}
print(sorted(a & b), sorted(a ^ b))
```

**Answer:**

```text
['acorn_pair'] ['acorn', 'acorn_other']
```

Intersection and symmetric difference on `acorn` sets.

### Q198. Basic

Write `unique_sorted(seq)` returning sorted unique hashable elements.

**Answer:**

```python
def unique_sorted(seq):
    return sorted(set(seq))
```

- `unique_sorted([3, 1, 3, 2])  =>  [1, 2, 3]`

Set for uniqueness, sorted for display order.

### Q199. Intermediate

Write `jaccard(a, b)` as |A∩B|/|A∪B|, returning 1.0 when both empty.

**Answer:**

```python
def jaccard(a, b):
    u = a | b
    if not u:
        return 1.0
    return len(a & b) / len(u)
```

- `jaccard({1, 2}, {1, 2, 3, 4})  =>  0.5`
- `jaccard(set(), set())  =>  1.0`

Use set operators for intersection and union sizes.

### Q200. Advanced

Write `dedupe_ordered(seq)` explaining why set alone is insufficient for order.

**Answer:**

```python
def dedupe_ordered(seq):
    return list(dict.fromkeys(seq))
```

- `dedupe_ordered([3, 1, 3, 2, 1])  =>  [3, 1, 2]`

Sets do not preserve order; dict insertion order keeps first-seen sequence.

*Section size: 200 questions (Basic 79, Intermediate 62, Advanced 59).*

