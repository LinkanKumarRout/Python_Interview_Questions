## 11. Frozenset (frozenset)

An immutable set. It is hashable, so it can be a dict key or a set element.

### Q1. Basic

What does this print?

```python
fs = frozenset([1, 2, 2])
print(sorted(fs))
```

**Answer:**

```text
[1, 2]
```

Frozenset deduplicates on construction.

### Q2. Basic

What does this print?

```python
fs = frozenset({1, 2})
print(fs == {1, 2})
```

**Answer:**

```text
True
```

Equal to set with same elements.

### Q3. Basic

What does this print?

```python
fs = frozenset('ab')
print(len(fs))
```

**Answer:**

```text
2
```

Length counts unique elements.

### Q4. Basic

What happens when this runs?

```python
fs = frozenset([1])
fs.add(2)
```

**Answer:**

```text
AttributeError: 'frozenset' object has no attribute 'add'
```

Frozenset has no mutating add API.

### Q5. Basic

What does this print?

```python
s = {frozenset({1, 2}), frozenset({3})}
print(len(s))
```

**Answer:**

```text
2
```

Hashable frozensets may be set elements.

### Q6. Basic

What does this print?

```python
d = {frozenset({1, 2}): 'ok'}
print(d[frozenset({2, 1})])
```

**Answer:**

```text
ok
```

Frozenset may be dict key; order ignored.

### Q7. Basic

What does this print?

```python
a = frozenset('ab')
b = frozenset('ba')
print(a == b, hash(a) == hash(b))
```

**Answer:**

```text
True True
```

Equal frozensets compare and hash equal.

### Q8. Basic

What does this print?

```python
print(frozenset() == frozenset([]))
```

**Answer:**

```text
True
```

Two empty frozensets equal.

### Q9. Basic

What does this print?

```python
fs = frozenset({1, 2, 3})
print(1 in fs, 9 in fs)
```

**Answer:**

```text
True False
```

Membership like set.

### Q10. Basic

What does this print?

```python
print(frozenset({1, 2}) | frozenset({2, 3}))
```

**Answer:**

```text
frozenset({1, 2, 3})
```

Operators return frozenset.

### Q11. Basic

What does this print?

```python
print(frozenset({1, 2}) & frozenset({2, 3}))
```

**Answer:**

```text
frozenset({2})
```

Intersection returns frozenset.

### Q12. Basic

What does this print?

```python
print(frozenset({1, 2}) - frozenset({2}))
```

**Answer:**

```text
frozenset({1})
```

Difference returns frozenset.

### Q13. Basic

What does this print?

```python
print(frozenset({1, 2}) ^ frozenset({2, 3}))
```

**Answer:**

```text
frozenset({1, 3})
```

Symmetric difference returns frozenset.

### Q14. Basic

What happens when this runs?

```python
frozenset([[1]])
```

**Answer:**

```text
TypeError: unhashable type: 'list'
```

Unhashable elements forbidden.

### Q15. Basic

What does this print?

```python
print(type(frozenset({1})))
```

**Answer:**

```text
<class 'frozenset'>
```

Type name is frozenset.

### Q16. Basic

What does this print?

```python
print(bool(frozenset()), bool(frozenset([0])))
```

**Answer:**

```text
False True
```

Empty falsy; non-empty truthy.

### Q17. Basic

What does this print?

```python
fs = frozenset('aba')
print(sorted(fs))
```

**Answer:**

```text
['a', 'b']
```

Construction deduplicates.

### Q18. Basic

What does this print?

```python
print(frozenset(set([1, 2, 2])))
```

**Answer:**

```text
frozenset({1, 2})
```

Build from set iterable.

### Q19. Basic

What does this print?

```python
print(frozenset({1, 2, 3}).union({3, 4}))
```

**Answer:**

```text
frozenset({1, 2, 3, 4})
```

Union method returns frozenset.

### Q20. Basic

What does this print?

```python
print(frozenset({1, 2, 3}).intersection({2, 3, 4}))
```

**Answer:**

```text
frozenset({2, 3})
```

Intersection method.

### Q21. Basic

What does this print?

```python
print(frozenset({1, 2, 3}).difference({3}))
```

**Answer:**

```text
frozenset({1, 2})
```

Difference method.

### Q22. Basic

What does this print?

```python
print(frozenset({1, 2, 3}).symmetric_difference({3, 4}))
```

**Answer:**

```text
frozenset({1, 2, 4})
```

Symmetric difference method.

### Q23. Basic

What does this print?

```python
print(frozenset({1, 2}) <= frozenset({1, 2, 3}))
```

**Answer:**

```text
True
```

Subset compare.

### Q24. Basic

What does this print?

```python
print(frozenset({1, 2, 3}) >= frozenset({2}))
```

**Answer:**

```text
True
```

Superset compare.

### Q25. Basic

What does this print?

```python
print(frozenset({1, 2}) < frozenset({1, 2, 3}))
```

**Answer:**

```text
True
```

Proper subset.

### Q26. Basic

What does this print?

```python
print(frozenset({1, 2}).isdisjoint(frozenset({3})))
```

**Answer:**

```text
True
```

Disjoint test.

### Q27. Basic

What does this print?

```python
fs = frozenset([1])
old = fs
fs |= frozenset([2])
print(sorted(fs), sorted(old))
```

**Answer:**

```text
[1, 2] [1]
```

Augmented op rebinds name to new frozenset.

### Q28. Basic

What does this print?

```python
print(sorted(frozenset('cat') | frozenset('dog')))
```

**Answer:**

```text
['a', 'c', 'd', 'g', 'o', 't']
```

Union of string frozensets.

### Q29. Basic

What does this print?

```python
print(sorted(frozenset('cat') & frozenset('car')))
```

**Answer:**

```text
['a', 'c']
```

Intersection of string frozensets.

### Q30. Basic

What does this print?

```python
print(sorted(frozenset('cat') - frozenset('c')))
```

**Answer:**

```text
['a', 't']
```

Difference removing char.

### Q31. Basic

What does this print?

```python
print(sorted(frozenset('cat') ^ frozenset('act')))
```

**Answer:**

```text
[]
```

Symmetric diff equal elements.

### Q32. Basic

What does this print?

```python
print(len(frozenset(range(5))))
```

**Answer:**

```text
5
```

Range to frozenset length.

### Q33. Basic

What does this print?

```python
print(sorted(frozenset({'a':1,'b':2})))
```

**Answer:**

```text
['a', 'b']
```

Keys of dict become frozenset.

### Q34. Basic

What does this print?

```python
print(sorted(frozenset(['a','b','a'])))
```

**Answer:**

```text
['a', 'b']
```

List with dupes deduped.

### Q35. Basic

What does this print?

```python
print(sorted(frozenset(('x','y','x'))))
```

**Answer:**

```text
['x', 'y']
```

Tuple with dupes deduped.

### Q36. Basic

What does this print?

```python
print(frozenset({1,2}) == frozenset({2,1}))
```

**Answer:**

```text
True
```

Order ignored for equality.

### Q37. Basic

What does this print?

```python
print({frozenset({1}), frozenset({1})})
```

**Answer:**

```text
{frozenset({1})}
```

Equal frozensets collapse in set.

### Q38. Basic

What does this print?

```python
print(len({frozenset({1,2}), frozenset({3})}))
```

**Answer:**

```text
2
```

Two distinct frozenset elements.

### Q39. Basic

What does this print?

```python
print(sorted(frozenset(b'abc')))
```

**Answer:**

```text
[97, 98, 99]
```

Bytes iterable to frozenset of ints.

### Q40. Basic

What does this print?

```python
print(all(x in frozenset('abc') for x in 'abc'))
```

**Answer:**

```text
True
```

All chars present.

### Q41. Basic

What does this print?

```python
print(any(x in frozenset('abc') for x in 'xyz'))
```

**Answer:**

```text
False
```

Any char from other word.

### Q42. Basic

What does this print?

```python
print(min(frozenset('abc')), max(frozenset('abc')))
```

**Answer:**

```text
a c
```

Min/max on frozenset.

### Q43. Basic

What does this print?

```python
print(sum(frozenset({1,2,3})))
```

**Answer:**

```text
6
```

Sum numeric frozenset.

### Q44. Basic

What does this print?

```python
print(sorted(frozenset({True, 1, 2})))
```

**Answer:**

```text
[True, 2]
```

True and 1 collapse.

### Q45. Basic

What does this print?

```python
print(len(frozenset({1, 1.0, 2})))
```

**Answer:**

```text
2
```

1 and 1.0 collapse.

### Q46. Basic

What does this print?

```python
print(frozenset('') == frozenset())
```

**Answer:**

```text
True
```

Empty string and empty frozenset.

### Q47. Basic

What does this print?

```python
print(len(frozenset('a')))
```

**Answer:**

```text
1
```

Single element length.

### Q48. Basic

What does this print?

```python
print(sorted(frozenset('ab') | set('bc')))
```

**Answer:**

```text
['a', 'b', 'c']
```

Mix frozenset and set in union.

### Q49. Basic

What does this print?

```python
print(type(frozenset({1}) | {2}))
```

**Answer:**

```text
<class 'frozenset'>
```

Result type when mixing with set.

### Q50. Basic

What does this print?

```python
print(type(frozenset({1}) & frozenset({1})))
```

**Answer:**

```text
<class 'frozenset'>
```

Both frozenset operands yield frozenset.

### Q51. Basic

What does this print?

```python
print(sorted(frozenset('hello')))
```

**Answer:**

```text
['e', 'h', 'l', 'o']
```

Word letters unique.

### Q52. Basic

What does this print?

```python
print(sorted(frozenset('world')))
```

**Answer:**

```text
['d', 'l', 'o', 'r', 'w']
```

Another word letters.

### Q53. Basic

What does this print?

```python
print(sorted(frozenset('python')))
```

**Answer:**

```text
['h', 'n', 'o', 'p', 't', 'y']
```

Python letters unique.

### Q54. Basic

What does this print?

```python
print(sorted(frozenset('cursor')))
```

**Answer:**

```text
['c', 'o', 'r', 's', 'u']
```

Cursor letters unique.

### Q55. Basic

What does this print?

```python
print(sorted(frozenset('learning')))
```

**Answer:**

```text
['a', 'e', 'g', 'i', 'l', 'n', 'r']
```

Learning letters unique.

### Q56. Basic

What does this print?

```python
print(sorted(frozenset('practice')))
```

**Answer:**

```text
['a', 'c', 'e', 'i', 'p', 'r', 't']
```

Practice letters unique.

### Q57. Basic

What does this print?

```python
print(sorted(frozenset('question')))
```

**Answer:**

```text
['e', 'i', 'n', 'o', 'q', 's', 't', 'u']
```

Question letters unique.

### Q58. Basic

What does this print?

```python
print(sorted(frozenset('answer')))
```

**Answer:**

```text
['a', 'e', 'n', 'r', 's', 'w']
```

Answer letters unique.

### Q59. Basic

What does this print?

```python
print(sorted(frozenset('example')))
```

**Answer:**

```text
['a', 'e', 'l', 'm', 'p', 'x']
```

Example letters unique.

### Q60. Basic

What does this print?

```python
print(sorted(frozenset('snippet')))
```

**Answer:**

```text
['e', 'i', 'n', 'p', 's', 't']
```

Snippet letters unique.

### Q61. Basic

What does this print?

```python
print(sorted(frozenset('hashable')))
```

**Answer:**

```text
['a', 'b', 'e', 'h', 'l', 's']
```

Hashable letters unique.

### Q62. Basic

What does this print?

```python
print(sorted(frozenset('immutable')))
```

**Answer:**

```text
['a', 'b', 'e', 'i', 'l', 'm', 't', 'u']
```

Immutable letters unique.

### Q63. Basic

What does this print?

```python
print(sorted(frozenset('operator')))
```

**Answer:**

```text
['a', 'e', 'o', 'p', 'r', 't']
```

Operator letters unique.

### Q64. Basic

What does this print?

```python
print(sorted(frozenset('element')))
```

**Answer:**

```text
['e', 'l', 'm', 'n', 't']
```

Element letters unique.

### Q65. Basic

What does this print?

```python
print(sorted(frozenset('mapping')))
```

**Answer:**

```text
['a', 'g', 'i', 'm', 'n', 'p']
```

Mapping letters unique.

### Q66. Basic

What does this print?

```python
print(sorted(frozenset('container')))
```

**Answer:**

```text
['a', 'c', 'e', 'i', 'n', 'o', 'r', 't']
```

Container letters unique.

### Q67. Basic

What does this print?

```python
print(sorted(frozenset('sequence')))
```

**Answer:**

```text
['c', 'e', 'n', 'q', 's', 'u']
```

Sequence letters unique.

### Q68. Basic

What does this print?

```python
print(sorted(frozenset('iterable')))
```

**Answer:**

```text
['a', 'b', 'e', 'i', 'l', 'r', 't']
```

Iterable letters unique.

### Q69. Basic

What does this print?

```python
print(sorted(frozenset('collection')))
```

**Answer:**

```text
['c', 'e', 'i', 'l', 'n', 'o', 't']
```

Collection letters unique.

### Q70. Basic

What does this print?

```python
print(sorted(frozenset('singleton')))
```

**Answer:**

```text
['e', 'g', 'i', 'l', 'n', 'o', 's', 't']
```

Singleton letters unique.

### Q71. Basic

What does this print?

```python
print(sorted(frozenset('keyvalue')))
```

**Answer:**

```text
['a', 'e', 'k', 'l', 'u', 'v', 'y']
```

Keyvalue letters unique.

### Q72. Basic

What does this print?

```python
print(sorted(frozenset('membership')))
```

**Answer:**

```text
['b', 'e', 'h', 'i', 'm', 'p', 'r', 's']
```

Membership letters unique.

### Q73. Basic

What does this print?

```python
print(sorted(frozenset('intersection')))
```

**Answer:**

```text
['c', 'e', 'i', 'n', 'o', 'r', 's', 't']
```

Intersection letters unique.

### Q74. Basic

What does this print?

```python
print(sorted(frozenset('union')))
```

**Answer:**

```text
['i', 'n', 'o', 'u']
```

Union letters unique.

### Q75. Basic

What does this print?

```python
print(sorted(frozenset('difference')))
```

**Answer:**

```text
['c', 'd', 'e', 'f', 'i', 'n', 'r']
```

Difference letters unique.

### Q76. Basic

What does this print?

```python
print(sorted(frozenset('symmetric')))
```

**Answer:**

```text
['c', 'e', 'i', 'm', 'r', 's', 't', 'y']
```

Symmetric letters unique.

### Q77. Intermediate

What does this print?

```python
fs = frozenset({1, 2, 3})
print(fs <= {1, 2, 3, 4}, fs >= {1, 2})
```

**Answer:**

```text
True True
```

Compare to plain set.

### Q78. Intermediate

What does this print?

```python
print(frozenset({1, 2}).union([3]))
```

**Answer:**

```text
frozenset({1, 2, 3})
```

Union accepts iterable.

### Q79. Intermediate

What does this print?

```python
print(frozenset({1, 2}).intersection([2, 9]))
```

**Answer:**

```text
frozenset({2})
```

Intersection accepts iterable.

### Q80. Intermediate

What does this print?

```python
s = {1, 2}
fs = frozenset(s)
print(fs == s, type(fs | {3}))
```

**Answer:**

```text
True <class 'frozenset'>
```

Bridge set/frozenset operations.

### Q81. Intermediate

What does this print?

```python
print({frozenset({1}), frozenset({1})})
```

**Answer:**

```text
{frozenset({1})}
```

Equal frozensets collapse.

### Q82. Intermediate

What does this print?

```python
print(frozenset({1, 2, 3}) - frozenset({3}))
```

**Answer:**

```text
frozenset({1, 2})
```

Difference yields frozenset.

### Q83. Intermediate

What does this print?

```python
print(frozenset({1, 2}) < frozenset({1, 2, 3}))
```

**Answer:**

```text
True
```

Proper subset.

### Q84. Intermediate

What does this print?

```python
print(sorted(frozenset('abc').union('bcd')))
```

**Answer:**

```text
['a', 'b', 'c', 'd']
```

Union with string iterable.

### Q85. Intermediate

What does this print?

```python
print(sorted(frozenset('abc').intersection('bcd')))
```

**Answer:**

```text
['b', 'c']
```

Intersection with string.

### Q86. Intermediate

What does this print?

```python
print(sorted(frozenset('abc').difference('a')))
```

**Answer:**

```text
['b', 'c']
```

Difference with string.

### Q87. Intermediate

What does this print?

```python
print(sorted(frozenset('abc').symmetric_difference('bc')))
```

**Answer:**

```text
['a']
```

Symmetric diff with string.

### Q88. Intermediate

What does this print?

```python
print(len(frozenset('mississippi')))
```

**Answer:**

```text
4
```

Unique letters count.

### Q89. Intermediate

What does this print?

```python
print(sorted(frozenset(map(str, [1, 2, 2]))))
```

**Answer:**

```text
['1', '2']
```

Map then frozenset.

### Q90. Intermediate

What does this print?

```python
print(sorted(frozenset(filter(None, [0, 1, 0, 2]))))
```

**Answer:**

```text
[1, 2]
```

Filter then frozenset.

### Q91. Intermediate

What does this print?

```python
print(sorted(frozenset({1,2}) | frozenset({2,3})))
```

**Answer:**

```text
[1, 2, 3]
```

Operator union sorted.

### Q92. Intermediate

What does this print?

```python
print(sorted(frozenset({1,2}) & frozenset({2,3})))
```

**Answer:**

```text
[2]
```

Operator intersection sorted.

### Q93. Intermediate

What does this print?

```python
print(sorted(frozenset({1,2}) ^ frozenset({2,3})))
```

**Answer:**

```text
[1, 3]
```

Operator symmetric diff sorted.

### Q94. Intermediate

What does this print?

```python
print(sorted(frozenset({1,2,3}) - frozenset({3})))
```

**Answer:**

```text
[1, 2]
```

Operator difference sorted.

### Q95. Intermediate

What does this print?

```python
def freeze(obj):
    if isinstance(obj, dict):
        return frozenset((k, freeze(v)) for k, v in sorted(obj.items()))
    if isinstance(obj, (list, tuple)):
        return frozenset(freeze(x) for x in obj)
    return obj
print(freeze({'b': [1], 'a': 2}))
```

**Answer:**

```text
frozenset({('a', 2), ('b', frozenset({1}))})
```

Recursive freeze for hashable memo keys.

### Q96. Intermediate

What does this print?

```python
cache = {}
def area(w, h):
    key = frozenset((w, h))
    if key not in cache:
        cache[key] = w * h
    return cache[key], len(cache)
print(area(3, 4))
```

**Answer:**

```text
(12, 1)
```

Frozenset memo key ignores pair order.

### Q97. Advanced

What does this print?

```python
print(sorted(frozenset('advanced')))
```

**Answer:**

```text
['a', 'c', 'd', 'e', 'n', 'v']
```

Advanced word letters.

### Q98. Advanced

What does this print?

```python
print(sorted(frozenset('frozenset')))
```

**Answer:**

```text
['e', 'f', 'n', 'o', 'r', 's', 't', 'z']
```

Self-name letters.

### Q99. Advanced

What does this print?

```python
print(sorted(frozenset('hashing')))
```

**Answer:**

```text
['a', 'g', 'h', 'i', 'n', 's']
```

Hashing letters.

### Q100. Advanced

What does this print?

```python
print(sorted(frozenset('memoization')))
```

**Answer:**

```text
['a', 'e', 'i', 'm', 'n', 'o', 't', 'z']
```

Memoization letters.

### Q101. Advanced

What does this print?

```python
print(sorted(frozenset('deduplicate')))
```

**Answer:**

```text
['a', 'c', 'd', 'e', 'i', 'l', 'p', 't', 'u']
```

Deduplicate letters.

### Q102. Advanced

What does this print?

```python
print(sorted(frozenset('subset')))
```

**Answer:**

```text
['b', 'e', 's', 't', 'u']
```

Subset letters.

### Q103. Advanced

What does this print?

```python
print(sorted(frozenset('superset')))
```

**Answer:**

```text
['e', 'p', 'r', 's', 't', 'u']
```

Superset letters.

### Q104. Advanced

What does this print?

```python
print(sorted(frozenset('disjoint')))
```

**Answer:**

```text
['d', 'i', 'j', 'n', 'o', 's', 't']
```

Disjoint letters.

### Q105. Advanced

What does this print?

```python
print(sorted(frozenset('algebra')))
```

**Answer:**

```text
['a', 'b', 'e', 'g', 'l', 'r']
```

Algebra letters.

### Q106. Advanced

What does this print?

```python
print(sorted(frozenset('immutableset')))
```

**Answer:**

```text
['a', 'b', 'e', 'i', 'l', 'm', 's', 't', 'u']
```

Immutableset letters.

### Q107. Advanced

What does this print?

```python
print(sorted(frozenset('hashablekey')))
```

**Answer:**

```text
['a', 'b', 'e', 'h', 'k', 'l', 's', 'y']
```

Hashablekey letters.

### Q108. Advanced

What does this print?

```python
print(sorted(frozenset('dictkey')))
```

**Answer:**

```text
['c', 'd', 'e', 'i', 'k', 't', 'y']
```

Dictkey letters.

### Q109. Advanced

What does this print?

```python
print(sorted(frozenset('setmember')))
```

**Answer:**

```text
['b', 'e', 'm', 'r', 's', 't']
```

Setmember letters.

### Q110. Advanced

What does this print?

```python
print(sorted(frozenset('uniquechars')))
```

**Answer:**

```text
['a', 'c', 'e', 'h', 'i', 'n', 'q', 'r', 's', 'u']
```

Uniquechars letters.

### Q111. Advanced

What does this print?

```python
print(sorted(frozenset('sortedview')))
```

**Answer:**

```text
['d', 'e', 'i', 'o', 'r', 's', 't', 'v', 'w']
```

Sortedview letters.

### Q112. Advanced

What does this print?

```python
print(sorted(frozenset('comprehension')))
```

**Answer:**

```text
['c', 'e', 'h', 'i', 'm', 'n', 'o', 'p', 'r', 's']
```

Comprehension letters.

### Q113. Advanced

What does this print?

```python
print(sorted(frozenset('constructor')))
```

**Answer:**

```text
['c', 'n', 'o', 'r', 's', 't', 'u']
```

Constructor letters.

### Q114. Advanced

What does this print?

```python
print(sorted(frozenset('iterableinput')))
```

**Answer:**

```text
['a', 'b', 'e', 'i', 'l', 'n', 'p', 'r', 't', 'u']
```

Iterableinput letters.

### Q115. Advanced

What does this print?

```python
print(sorted(frozenset('operatorresult')))
```

**Answer:**

```text
['a', 'e', 'l', 'o', 'p', 'r', 's', 't', 'u']
```

Operatorresult letters.

### Q116. Advanced

What does this print?

```python
print(sorted(frozenset('methodchain')))
```

**Answer:**

```text
['a', 'c', 'd', 'e', 'h', 'i', 'm', 'n', 'o', 't']
```

Methodchain letters.

### Q117. Advanced

What does this print?

```python
print(sorted(frozenset('builtincall')))
```

**Answer:**

```text
['a', 'b', 'c', 'i', 'l', 'n', 't', 'u']
```

Builtincall letters.

### Q118. Advanced

What does this print?

```python
print(sorted(frozenset('typinghint')))
```

**Answer:**

```text
['g', 'h', 'i', 'n', 'p', 't', 'y']
```

Typinghint letters.

### Q119. Advanced

What does this print?

```python
print(sorted(frozenset('python312')))
```

**Answer:**

```text
['1', '2', '3', 'h', 'n', 'o', 'p', 't', 'y']
```

Python312 letters unique.

### Q120. Intermediate

What does this print?

```python
print(sorted(frozenset('yarrow')))
```

**Answer:**

```text
['a', 'o', 'r', 'w', 'y']
```

Unique letters in `yarrow`.

### Q121. Intermediate

What does this print?

```python
print(sorted(frozenset('zinc')))
```

**Answer:**

```text
['c', 'i', 'n', 'z']
```

Unique letters in `zinc`.

### Q122. Intermediate

What does this print?

```python
print(sorted(frozenset('atlas')))
```

**Answer:**

```text
['a', 'l', 's', 't']
```

Unique letters in `atlas`.

### Q123. Intermediate

What does this print?

```python
print(sorted(frozenset('breeze')))
```

**Answer:**

```text
['b', 'e', 'r', 'z']
```

Unique letters in `breeze`.

### Q124. Intermediate

What does this print?

```python
print(sorted(frozenset('cinder')))
```

**Answer:**

```text
['c', 'd', 'e', 'i', 'n', 'r']
```

Unique letters in `cinder`.

### Q125. Intermediate

What does this print?

```python
print(sorted(frozenset('drift')))
```

**Answer:**

```text
['d', 'f', 'i', 'r', 't']
```

Unique letters in `drift`.

### Q126. Intermediate

What does this print?

```python
print(sorted(frozenset('ember')))
```

**Answer:**

```text
['b', 'e', 'm', 'r']
```

Unique letters in `ember`.

### Q127. Intermediate

What does this print?

```python
print(sorted(frozenset('frost')))
```

**Answer:**

```text
['f', 'o', 'r', 's', 't']
```

Unique letters in `frost`.

### Q128. Intermediate

What does this print?

```python
print(sorted(frozenset('glow')))
```

**Answer:**

```text
['g', 'l', 'o', 'w']
```

Unique letters in `glow`.

### Q129. Intermediate

What does this print?

```python
print(sorted(frozenset('haven')))
```

**Answer:**

```text
['a', 'e', 'h', 'n', 'v']
```

Unique letters in `haven`.

### Q130. Intermediate

What does this print?

```python
print(sorted(frozenset('inlet')))
```

**Answer:**

```text
['e', 'i', 'l', 'n', 't']
```

Unique letters in `inlet`.

### Q131. Intermediate

What does this print?

```python
print(sorted(frozenset('jewel')))
```

**Answer:**

```text
['e', 'j', 'l', 'w']
```

Unique letters in `jewel`.

### Q132. Intermediate

What does this print?

```python
print(sorted(frozenset('knight')))
```

**Answer:**

```text
['g', 'h', 'i', 'k', 'n', 't']
```

Unique letters in `knight`.

### Q133. Intermediate

What does this print?

```python
print(sorted(frozenset('lunar')))
```

**Answer:**

```text
['a', 'l', 'n', 'r', 'u']
```

Unique letters in `lunar`.

### Q134. Intermediate

What does this print?

```python
print(sorted(frozenset('mossy')))
```

**Answer:**

```text
['m', 'o', 's', 'y']
```

Unique letters in `mossy`.

### Q135. Intermediate

What does this print?

```python
print(sorted(frozenset('nebula')))
```

**Answer:**

```text
['a', 'b', 'e', 'l', 'n', 'u']
```

Unique letters in `nebula`.

### Q136. Intermediate

What does this print?

```python
print(sorted(frozenset('orbit')))
```

**Answer:**

```text
['b', 'i', 'o', 'r', 't']
```

Unique letters in `orbit`.

### Q137. Intermediate

What does this print?

```python
print(sorted(frozenset('prism')))
```

**Answer:**

```text
['i', 'm', 'p', 'r', 's']
```

Unique letters in `prism`.

### Q138. Intermediate

What does this print?

```python
print(sorted(frozenset('quill')))
```

**Answer:**

```text
['i', 'l', 'q', 'u']
```

Unique letters in `quill`.

### Q139. Intermediate

What does this print?

```python
print(sorted(frozenset('ridge')))
```

**Answer:**

```text
['d', 'e', 'g', 'i', 'r']
```

Unique letters in `ridge`.

### Q140. Intermediate

What does this print?

```python
print(sorted(frozenset('spark')))
```

**Answer:**

```text
['a', 'k', 'p', 'r', 's']
```

Unique letters in `spark`.

### Q141. Intermediate

What does this print?

```python
print(sorted(frozenset('thorn')))
```

**Answer:**

```text
['h', 'n', 'o', 'r', 't']
```

Unique letters in `thorn`.

### Q142. Intermediate

What does this print?

```python
print(sorted(frozenset('upland')))
```

**Answer:**

```text
['a', 'd', 'l', 'n', 'p', 'u']
```

Unique letters in `upland`.

### Q143. Intermediate

What does this print?

```python
print(sorted(frozenset('vortex')))
```

**Answer:**

```text
['e', 'o', 'r', 't', 'v', 'x']
```

Unique letters in `vortex`.

### Q144. Intermediate

What does this print?

```python
print(sorted(frozenset('wisp')))
```

**Answer:**

```text
['i', 'p', 's', 'w']
```

Unique letters in `wisp`.

### Q145. Intermediate

What does this print?

```python
print(sorted(frozenset('yonder')))
```

**Answer:**

```text
['d', 'e', 'n', 'o', 'r', 'y']
```

Unique letters in `yonder`.

### Q146. Intermediate

What does this print?

```python
print(sorted(frozenset('zephyr')))
```

**Answer:**

```text
['e', 'h', 'p', 'r', 'y', 'z']
```

Unique letters in `zephyr`.

### Q147. Intermediate

What does this print?

```python
print(sorted(frozenset('acorn')))
```

**Answer:**

```text
['a', 'c', 'n', 'o', 'r']
```

Unique letters in `acorn`.

### Q148. Intermediate

What does this print?

```python
print(sorted(frozenset('bluff')))
```

**Answer:**

```text
['b', 'f', 'l', 'u']
```

Unique letters in `bluff`.

### Q149. Intermediate

What does this print?

```python
print(sorted(frozenset('cliff')))
```

**Answer:**

```text
['c', 'f', 'i', 'l']
```

Unique letters in `cliff`.

### Q150. Intermediate

What does this print?

```python
print(sorted(frozenset('dune')))
```

**Answer:**

```text
['d', 'e', 'n', 'u']
```

Unique letters in `dune`.

### Q151. Intermediate

What does this print?

```python
print(sorted(frozenset('elder')))
```

**Answer:**

```text
['d', 'e', 'l', 'r']
```

Unique letters in `elder`.

### Q152. Intermediate

What does this print?

```python
print(sorted(frozenset('fjord')))
```

**Answer:**

```text
['d', 'f', 'j', 'o', 'r']
```

Unique letters in `fjord`.

### Q153. Intermediate

What does this print?

```python
print(sorted(frozenset('glade')))
```

**Answer:**

```text
['a', 'd', 'e', 'g', 'l']
```

Unique letters in `glade`.

### Q154. Intermediate

What does this print?

```python
print(sorted(frozenset('harbor')))
```

**Answer:**

```text
['a', 'b', 'h', 'o', 'r']
```

Unique letters in `harbor`.

### Q155. Intermediate

What does this print?

```python
print(sorted(frozenset('isle')))
```

**Answer:**

```text
['e', 'i', 'l', 's']
```

Unique letters in `isle`.

### Q156. Intermediate

What does this print?

```python
print(sorted(frozenset('jungle')))
```

**Answer:**

```text
['e', 'g', 'j', 'l', 'n', 'u']
```

Unique letters in `jungle`.

### Q157. Intermediate

What does this print?

```python
print(sorted(frozenset('knoll')))
```

**Answer:**

```text
['k', 'l', 'n', 'o']
```

Unique letters in `knoll`.

### Q158. Intermediate

What does this print?

```python
print(sorted(frozenset('lagoon')))
```

**Answer:**

```text
['a', 'g', 'l', 'n', 'o']
```

Unique letters in `lagoon`.

### Q159. Intermediate

What does this print?

```python
print(sorted(frozenset('meadow')))
```

**Answer:**

```text
['a', 'd', 'e', 'm', 'o', 'w']
```

Unique letters in `meadow`.

### Q160. Intermediate

What does this print?

```python
print(sorted(frozenset('narrows')))
```

**Answer:**

```text
['a', 'n', 'o', 'r', 's', 'w']
```

Unique letters in `narrows`.

### Q161. Intermediate

What does this print?

```python
print(sorted(frozenset('oasis')))
```

**Answer:**

```text
['a', 'i', 'o', 's']
```

Unique letters in `oasis`.

### Q162. Intermediate

What does this print?

```python
print(sorted(frozenset('plateau')))
```

**Answer:**

```text
['a', 'e', 'l', 'p', 't', 'u']
```

Unique letters in `plateau`.

### Q163. Intermediate

What does this print?

```python
print(sorted(frozenset('ravine')))
```

**Answer:**

```text
['a', 'e', 'i', 'n', 'r', 'v']
```

Unique letters in `ravine`.

### Q164. Intermediate

What does this print?

```python
print(sorted(frozenset('summit')))
```

**Answer:**

```text
['i', 'm', 's', 't', 'u']
```

Unique letters in `summit`.

### Q165. Intermediate

What does this print?

```python
print(sorted(frozenset('tundra')))
```

**Answer:**

```text
['a', 'd', 'n', 'r', 't', 'u']
```

Unique letters in `tundra`.

### Q166. Intermediate

What does this print?

```python
print(sorted(frozenset('valley')))
```

**Answer:**

```text
['a', 'e', 'l', 'v', 'y']
```

Unique letters in `valley`.

### Q167. Intermediate

What does this print?

```python
print(sorted(frozenset('willow')))
```

**Answer:**

```text
['i', 'l', 'o', 'w']
```

Unique letters in `willow`.

### Q168. Intermediate

What does this print?

```python
print(sorted(frozenset('yacht')))
```

**Answer:**

```text
['a', 'c', 'h', 't', 'y']
```

Unique letters in `yacht`.

### Q169. Intermediate

What does this print?

```python
print(sorted(frozenset('zenith')))
```

**Answer:**

```text
['e', 'h', 'i', 'n', 't', 'z']
```

Unique letters in `zenith`.

### Q170. Intermediate

What does this print?

```python
print(sorted(frozenset('arc')))
```

**Answer:**

```text
['a', 'c', 'r']
```

Unique letters in `arc`.

### Q171. Intermediate

What does this print?

```python
print(sorted(frozenset('bolt')))
```

**Answer:**

```text
['b', 'l', 'o', 't']
```

Unique letters in `bolt`.

### Q172. Intermediate

What does this print?

```python
print(sorted(frozenset('core')))
```

**Answer:**

```text
['c', 'e', 'o', 'r']
```

Unique letters in `core`.

### Q173. Intermediate

What does this print?

```python
print(sorted(frozenset('disk')))
```

**Answer:**

```text
['d', 'i', 'k', 's']
```

Unique letters in `disk`.

### Q174. Intermediate

What does this print?

```python
print(sorted(frozenset('edge')))
```

**Answer:**

```text
['d', 'e', 'g']
```

Unique letters in `edge`.

### Q175. Intermediate

What does this print?

```python
print(sorted(frozenset('flux')))
```

**Answer:**

```text
['f', 'l', 'u', 'x']
```

Unique letters in `flux`.

### Q176. Intermediate

What does this print?

```python
print(sorted(frozenset('grid')))
```

**Answer:**

```text
['d', 'g', 'i', 'r']
```

Unique letters in `grid`.

### Q177. Intermediate

What does this print?

```python
print(sorted(frozenset('hook')))
```

**Answer:**

```text
['h', 'k', 'o']
```

Unique letters in `hook`.

### Q178. Intermediate

What does this print?

```python
print(sorted(frozenset('icon')))
```

**Answer:**

```text
['c', 'i', 'n', 'o']
```

Unique letters in `icon`.

### Q179. Intermediate

What does this print?

```python
print(sorted(frozenset('joint')))
```

**Answer:**

```text
['i', 'j', 'n', 'o', 't']
```

Unique letters in `joint`.

### Q180. Intermediate

What does this print?

```python
print(sorted(frozenset('kernel')))
```

**Answer:**

```text
['e', 'k', 'l', 'n', 'r']
```

Unique letters in `kernel`.

### Q181. Intermediate

What does this print?

```python
print(sorted(frozenset('loop')))
```

**Answer:**

```text
['l', 'o', 'p']
```

Unique letters in `loop`.

### Q182. Intermediate

What does this print?

```python
print(sorted(frozenset('mesh')))
```

**Answer:**

```text
['e', 'h', 'm', 's']
```

Unique letters in `mesh`.

### Q183. Intermediate

What does this print?

```python
print(sorted(frozenset('node')))
```

**Answer:**

```text
['d', 'e', 'n', 'o']
```

Unique letters in `node`.

### Q184. Intermediate

What does this print?

```python
print(sorted(frozenset('patch')))
```

**Answer:**

```text
['a', 'c', 'h', 'p', 't']
```

Unique letters in `patch`.

### Q185. Intermediate

What does this print?

```python
print(sorted(frozenset('queue')))
```

**Answer:**

```text
['e', 'q', 'u']
```

Unique letters in `queue`.

### Q186. Intermediate

What does this print?

```python
print(sorted(frozenset('root')))
```

**Answer:**

```text
['o', 'r', 't']
```

Unique letters in `root`.

### Q187. Intermediate

What does this print?

```python
print(sorted(frozenset('slot')))
```

**Answer:**

```text
['l', 'o', 's', 't']
```

Unique letters in `slot`.

### Q188. Intermediate

What does this print?

```python
print(sorted(frozenset('trace')))
```

**Answer:**

```text
['a', 'c', 'e', 'r', 't']
```

Unique letters in `trace`.

### Q189. Intermediate

What does this print?

```python
print(sorted(frozenset('unit')))
```

**Answer:**

```text
['i', 'n', 't', 'u']
```

Unique letters in `unit`.

### Q190. Intermediate

What does this print?

```python
print(sorted(frozenset('vault')))
```

**Answer:**

```text
['a', 'l', 't', 'u', 'v']
```

Unique letters in `vault`.

### Q191. Intermediate

What does this print?

```python
print(sorted(frozenset('wire')))
```

**Answer:**

```text
['e', 'i', 'r', 'w']
```

Unique letters in `wire`.

### Q192. Intermediate

What does this print?

```python
print(sorted(frozenset('yield')))
```

**Answer:**

```text
['d', 'e', 'i', 'l', 'y']
```

Unique letters in `yield`.

### Q193. Intermediate

What does this print?

```python
print(sorted(frozenset('zone')))
```

**Answer:**

```text
['e', 'n', 'o', 'z']
```

Unique letters in `zone`.

### Q194. Intermediate

What does this print?

```python
print(sorted(frozenset('axiom')))
```

**Answer:**

```text
['a', 'i', 'm', 'o', 'x']
```

Unique letters in `axiom`.

### Q195. Intermediate

What does this print?

```python
print(sorted(frozenset('basis')))
```

**Answer:**

```text
['a', 'b', 'i', 's']
```

Unique letters in `basis`.

### Q196. Intermediate

What does this print?

```python
print(sorted(frozenset('cache')))
```

**Answer:**

```text
['a', 'c', 'e', 'h']
```

Unique letters in `cache`.

### Q197. Intermediate

What does this print?

```python
print(sorted(frozenset('datum')))
```

**Answer:**

```text
['a', 'd', 'm', 't', 'u']
```

Unique letters in `datum`.

### Q198. Intermediate

Write `as_frozenset(iterable)` returning a frozenset of elements.

**Answer:**

```python
def as_frozenset(iterable):
    return frozenset(iterable)
```

- `sorted(as_frozenset([2, 1, 2]))  =>  [1, 2]`

Construction deduplicates and freezes.

### Q199. Advanced

Write `memo_key(*args)` returning a frozenset of hashable args for caching.

**Answer:**

```python
def memo_key(*args):
    return frozenset(args)
```

- `memo_key(1, 2) == memo_key(2, 1)  =>  True`

Frozenset ignores order so argument order does not matter.

### Q200. Advanced

Write `freeze_set_of_sets(sets)` returning frozenset of frozensets.

**Answer:**

```python
def freeze_set_of_sets(sets):
    return frozenset(frozenset(s) for s in sets)
```

- `freeze_set_of_sets([[1, 2], [3]]) == frozenset({frozenset({1, 2}), frozenset({3})})  =>  True`

Nested frozensets make the structure hashable.

*Section size: 200 questions (Basic 76, Intermediate 99, Advanced 25).*

