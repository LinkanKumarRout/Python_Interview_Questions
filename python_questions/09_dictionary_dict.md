## 9. Dictionary (dict)

An insertion-ordered mapping from hashable keys to values.

### Q1. Basic

What does this print?

```python
print(type({}))
```

**Answer:**

```text
<class 'dict'>
```

Curly braces create a `dict`.

### Q2. Basic

What does this print?

```python
print(dict())
```

**Answer:**

```text
{}
```

Empty constructor builds `{}`.

### Q3. Basic

What does this print?

```python
print(dict(alpha=1, bravo=2))
```

**Answer:**

```text
{'alpha': 1, 'bravo': 2}
```

Keywords become string keys in insertion order.

### Q4. Basic

What does this print?

```python
d = {'zulu': 0, 'alpha': 1}
print(list(d))
```

**Answer:**

```text
['zulu', 'alpha']
```

Insertion order is preserved for keys.

### Q5. Basic

What does this print?

```python
print({'xray': 1, 'yankee': 2} == {'yankee': 2, 'xray': 1})
```

**Answer:**

```text
True
```

Equality ignores insertion order.

### Q6. Basic

What does this print?

```python
d = {'key': 'val'}
print(d['key'])
```

**Answer:**

```text
val
```

Bracket lookup returns the value.

### Q7. Basic

What does this print?

```python
d = {}
print(d.get('missing'))
```

**Answer:**

```text
None
```

Missing key returns `None` without raising.

### Q8. Basic

What does this print?

```python
d = {}
print(d.get('missing', 'fallback'))
```

**Answer:**

```text
fallback
```

Default is returned when key is absent.

### Q9. Basic

What happens when this runs?

```python
d = {}
print(d['nope'])
```

**Answer:**

```text
KeyError: 'nope'
```

Bracket access on missing key raises `KeyError`.

### Q10. Basic

What does this print?

```python
d = {'alpha': 1}
print('alpha' in d, 'beta' not in d)
```

**Answer:**

```text
True True
```

Membership tests keys.

### Q11. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(len(d))
```

**Answer:**

```text
2
```

`len` counts key-value pairs.

### Q12. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(list(d.values()))
```

**Answer:**

```text
[1, 2]
```

Values iterate in insertion order.

### Q13. Basic

What does this print?

```python
d = {'solo': 1}
v = d.keys()
d['duo'] = 2
print(list(v))
```

**Answer:**

```text
['solo', 'duo']
```

Keys view reflects mutations.

### Q14. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(list(d.items()))
```

**Answer:**

```text
[('a', 1), ('b', 2)]
```

`.items()` yields pairs in order.

### Q15. Basic

What does this print?

```python
d = {'a': 1}
d['a'] = 9
print(d)
```

**Answer:**

```text
{'a': 9}
```

Reassigning replaces value, not key position.

### Q16. Basic

What does this print?

```python
d = {'a': 1}
d.setdefault('a', 99)
print(d)
```

**Answer:**

```text
{'a': 1}
```

Existing key: `setdefault` does not overwrite.

### Q17. Basic

What does this print?

```python
d = {}
d.setdefault('bag', [])
d['bag'].append('x')
print(d)
```

**Answer:**

```text
{'bag': ['x']}
```

Default object stored when key was missing.

### Q18. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(d.pop('a'), d)
```

**Answer:**

```text
1 {'b': 2}
```

`pop` removes and returns value.

### Q19. Basic

What happens when this runs?

```python
d = {}
print(d.pop('z'))
```

**Answer:**

```text
KeyError: 'z'
```

`pop` without default on missing key raises.

### Q20. Basic

What does this print?

```python
d = {}
print(d.pop('z', 'gone'))
```

**Answer:**

```text
gone
```

Default returned when key missing.

### Q21. Basic

What does this print?

```python
d = {'first': 1, 'second': 2}
print(d.popitem())
```

**Answer:**

```text
('second', 2)
```

LIFO `popitem` removes newest pair.

### Q22. Basic

What happens when this runs?

```python
print({}.popitem())
```

**Answer:**

```text
KeyError: 'popitem(): dictionary is empty'
```

Empty dict `popitem` raises `KeyError`.

### Q23. Basic

What does this print?

```python
a = {'x': 1}
b = {'y': 2}
a.update(b)
print(a)
```

**Answer:**

```text
{'x': 1, 'y': 2}
```

`update` merges mappings.

### Q24. Basic

What does this print?

```python
d = {'a': 1}
d.update([('b', 2)])
print(d)
```

**Answer:**

```text
{'a': 1, 'b': 2}
```

`update` accepts iterable of pairs.

### Q25. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
d.clear()
print(len(d))
```

**Answer:**

```text
0
```

`clear` removes all items.

### Q26. Basic

What does this print?

```python
print(dict.fromkeys(['p', 'q'], 0))
```

**Answer:**

```text
{'p': 0, 'q': 0}
```

`fromkeys` maps keys to one default.

### Q27. Basic

What does this print?

```python
d = {(1, 2): 'pair'}
print(d[(1, 2)])
```

**Answer:**

```text
pair
```

Hashable tuple keys work.

### Q28. Basic

What happens when this runs?

```python
d = {[1]: 'bad'}
```

**Answer:**

```text
TypeError: unhashable type: 'list'
```

Lists are unhashable keys.

### Q29. Basic

What happens when this runs?

```python
d = {{}: 0}
```

**Answer:**

```text
TypeError: unhashable type: 'dict'
```

Dicts are unhashable keys.

### Q30. Basic

What does this print?

```python
print({k: k.upper() for k in 'ab'})
```

**Answer:**

```text
{'a': 'A', 'b': 'B'}
```

Dict comprehension builds a mapping.

### Q31. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
c = d.copy()
c['a'] = 0
print(d, c)
```

**Answer:**

```text
{'a': 1, 'b': 2} {'a': 0, 'b': 2}
```

Shallow copy duplicates outer dict.

### Q32. Basic

What does this print?

```python
print(bool({}), bool({'z': 0}))
```

**Answer:**

```text
False True
```

Empty dict falsy; non-empty truthy.

### Q33. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(list(d))
```

**Answer:**

```text
['a', 'b']
```

`list(d)` lists keys.

### Q34. Basic

What does this print?

```python
d = {}
d.update(x=10, y=20)
print(d)
```

**Answer:**

```text
{'x': 10, 'y': 20}
```

`update` accepts keywords.

### Q35. Basic

What does this print?

```python
print({'solo': 1}.items())
```

**Answer:**

```text
dict_items([('solo', 1)])
```

`.items()` returns a view.

### Q36. Basic

What does this print?

```python
d = {'red': 1, 'green': 2, 'blue': 3}
print(sorted(d.values()))
```

**Answer:**

```text
[1, 2, 3]
```

Sort for deterministic display.

### Q37. Basic

What does this print?

```python
print(dict([('k', 'v')]))
```

**Answer:**

```text
{'k': 'v'}
```

Constructor from pair list.

### Q38. Basic

What does this print?

```python
d = dict(zip('ab', range(2)))
print(d)
```

**Answer:**

```text
{'a': 0, 'b': 1}
```

`zip` builds pairs for `dict`.

### Q39. Basic

What does this print?

```python
d = {'a': None}
print(d['a'] is None)
```

**Answer:**

```text
True
```

Retrieved `None` is the singleton.

### Q40. Basic

What does this print?

```python
d = {'a': 1}
print(list(d.keys()))
```

**Answer:**

```text
['a']
```

`.keys()` lists in insertion order.

### Q41. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(list(d.values())[0])
```

**Answer:**

```text
1
```

First value in insertion order.

### Q42. Basic

What does this print?

```python
d = {'a': 1}
print(d.setdefault('b'))
```

**Answer:**

```text
None
```

Omitted default is `None`.

### Q43. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print('a' in d, 1 in d)
```

**Answer:**

```text
True False
```

`in` tests keys only.

### Q44. Basic

What does this print?

```python
d = {'x': 10, 'y': 20}
print(d.get('x'), d.get('z', -1))
```

**Answer:**

```text
10 -1
```

`get` avoids exceptions.

### Q45. Basic

What does this print?

```python
d = {'a': 1, 'b': 2, 'c': 3}
print(d.pop('b'))
```

**Answer:**

```text
2
```

Pop returns removed value.

### Q46. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(d.popitem(), len(d))
```

**Answer:**

```text
('b', 2) 1
```

Popitem reduces length by one.

### Q47. Basic

What does this print?

```python
d = {'a': 1}
print(dict(d))
```

**Answer:**

```text
{'a': 1}
```

`dict(d)` copies mapping.

### Q48. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print({k: v for k, v in d.items() if v > 1})
```

**Answer:**

```text
{'b': 2}
```

Comprehension can filter.

### Q49. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(all(k in d for k in 'ab'))
```

**Answer:**

```text
True
```

Check multiple keys.

### Q50. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(any(k not in d for k in 'xyz'))
```

**Answer:**

```text
True
```

Detect absent keys.

### Q51. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(sum(d.values()))
```

**Answer:**

```text
3
```

Sum values from view.

### Q52. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(min(d), max(d))
```

**Answer:**

```text
a b
```

`min`/`max` use keys.

### Q53. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(sorted(d))
```

**Answer:**

```text
['a', 'b']
```

Sorted keys list.

### Q54. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(list(reversed(d)))
```

**Answer:**

```text
['b', 'a']
```

Reverse key iteration order.

### Q55. Basic

What does this print?

```python
d = {'a': 1}
print(list(d.items()) == list(zip(d.keys(), d.values())))
```

**Answer:**

```text
True
```

Items align keys and values.

### Q56. Basic

What does this print?

```python
d = {'a': 1}
print(list(d.values()) is list(d.values()))
```

**Answer:**

```text
False
```

Each `.values()` creates a new view.

### Q57. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(len(d.keys()), len(d.values()))
```

**Answer:**

```text
2 2
```

View lengths match dict size.

### Q58. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print('a' in d.keys())
```

**Answer:**

```text
True
```

Membership on keys view.

### Q59. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print('a' in d.values())
```

**Answer:**

```text
False
```

Values membership searches values.

### Q60. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(('a', 1) in d.items())
```

**Answer:**

```text
True
```

Items membership tests pairs.

### Q61. Basic

What does this print?

```python
d = {'present': 1}
print(d.get('present', print('never')))
```

**Answer:**

```text
never
1
```

Default expression skipped when key exists.

### Q62. Basic

What does this print?

```python
d = {}
print(d.get('absent', print('ran')))
```

**Answer:**

```text
ran
None
```

Default expression runs when key missing.

### Q63. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
del d['a']
print(d)
```

**Answer:**

```text
{'b': 2}
```

`del` removes a key.

### Q64. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(d | {'b': 9})
```

**Answer:**

```text
{'a': 1, 'b': 9}
```

Preview merge with `|` (non-mutating).

### Q65. Basic

What does this print?

```python
d = {'a': 1}
print({**d, 'b': 2})
```

**Answer:**

```text
{'a': 1, 'b': 2}
```

Unpack merge in literal.

### Q66. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(list(d.items())[0])
```

**Answer:**

```text
('a', 1)
```

First item tuple.

### Q67. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(list(d.items())[-1])
```

**Answer:**

```text
('b', 2)
```

Last item tuple.

### Q68. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(d.get('b'), d.get('c'))
```

**Answer:**

```text
2 None
```

Present and missing without default.

### Q69. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(d.setdefault('c', []), d)
```

**Answer:**

```text
[] {'a': 1, 'b': 2, 'c': []}
```

Insert list default for missing key.

### Q70. Basic

What does this print?

```python
d = {'a': 1}
print(d.pop('a', 'missing'))
```

**Answer:**

```text
1
```

Pop existing ignores default.

### Q71. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(d.popitem()[0])
```

**Answer:**

```text
b
```

Popitem returns `(key, value)`; index key.

### Q72. Basic

What does this print?

```python
d = {'a': 1, 'b': 2}
print(len(d.items()))
```

**Answer:**

```text
2
```

Len of items view equals dict length.

### Q73. Intermediate

What does this print?

```python
d = {'spark': 'payload'}
print(d.get('spark'), d.get('absent_spark', 'default_spark'))
```

**Answer:**

```text
payload default_spark
```

`get` on key `spark` returns the stored value; missing keys use the default.

### Q74. Intermediate

What does this print?

```python
d = {'thorn': 'payload'}
print(d.get('thorn'), d.get('absent_thorn', 'default_thorn'))
```

**Answer:**

```text
payload default_thorn
```

`get` on key `thorn` returns the stored value; missing keys use the default.

### Q75. Intermediate

What does this print?

```python
d = {'upland': 'payload'}
print(d.get('upland'), d.get('absent_upland', 'default_upland'))
```

**Answer:**

```text
payload default_upland
```

`get` on key `upland` returns the stored value; missing keys use the default.

### Q76. Intermediate

What does this print?

```python
d = {'vortex': 'payload'}
print(d.get('vortex'), d.get('absent_vortex', 'default_vortex'))
```

**Answer:**

```text
payload default_vortex
```

`get` on key `vortex` returns the stored value; missing keys use the default.

### Q77. Intermediate

What does this print?

```python
d = {'wisp': 'payload'}
print(d.get('wisp'), d.get('absent_wisp', 'default_wisp'))
```

**Answer:**

```text
payload default_wisp
```

`get` on key `wisp` returns the stored value; missing keys use the default.

### Q78. Intermediate

What does this print?

```python
d = {'yonder': 'payload'}
print(d.get('yonder'), d.get('absent_yonder', 'default_yonder'))
```

**Answer:**

```text
payload default_yonder
```

`get` on key `yonder` returns the stored value; missing keys use the default.

### Q79. Intermediate

What does this print?

```python
d = {'zephyr': 'payload'}
print(d.get('zephyr'), d.get('absent_zephyr', 'default_zephyr'))
```

**Answer:**

```text
payload default_zephyr
```

`get` on key `zephyr` returns the stored value; missing keys use the default.

### Q80. Intermediate

What does this print?

```python
d = {'acorn': 'payload'}
print(d.get('acorn'), d.get('absent_acorn', 'default_acorn'))
```

**Answer:**

```text
payload default_acorn
```

`get` on key `acorn` returns the stored value; missing keys use the default.

### Q81. Intermediate

What does this print?

```python
d = {'bluff': 'payload'}
print(d.get('bluff'), d.get('absent_bluff', 'default_bluff'))
```

**Answer:**

```text
payload default_bluff
```

`get` on key `bluff` returns the stored value; missing keys use the default.

### Q82. Intermediate

What does this print?

```python
d = {'cliff': 'payload'}
print(d.get('cliff'), d.get('absent_cliff', 'default_cliff'))
```

**Answer:**

```text
payload default_cliff
```

`get` on key `cliff` returns the stored value; missing keys use the default.

### Q83. Intermediate

What does this print?

```python
d = {'dune': 'payload'}
print(d.get('dune'), d.get('absent_dune', 'default_dune'))
```

**Answer:**

```text
payload default_dune
```

`get` on key `dune` returns the stored value; missing keys use the default.

### Q84. Intermediate

What does this print?

```python
d = {'elder': 'payload'}
print(d.get('elder'), d.get('absent_elder', 'default_elder'))
```

**Answer:**

```text
payload default_elder
```

`get` on key `elder` returns the stored value; missing keys use the default.

### Q85. Intermediate

What does this print?

```python
d = {'fjord': 'payload'}
print(d.get('fjord'), d.get('absent_fjord', 'default_fjord'))
```

**Answer:**

```text
payload default_fjord
```

`get` on key `fjord` returns the stored value; missing keys use the default.

### Q86. Intermediate

What does this print?

```python
d = {'glade': 'payload'}
print(d.get('glade'), d.get('absent_glade', 'default_glade'))
```

**Answer:**

```text
payload default_glade
```

`get` on key `glade` returns the stored value; missing keys use the default.

### Q87. Intermediate

What does this print?

```python
d = {'harbor': 'payload'}
print(d.get('harbor'), d.get('absent_harbor', 'default_harbor'))
```

**Answer:**

```text
payload default_harbor
```

`get` on key `harbor` returns the stored value; missing keys use the default.

### Q88. Intermediate

What does this print?

```python
d = {'isle': 'payload'}
print(d.get('isle'), d.get('absent_isle', 'default_isle'))
```

**Answer:**

```text
payload default_isle
```

`get` on key `isle` returns the stored value; missing keys use the default.

### Q89. Intermediate

What does this print?

```python
d = {'jungle': 'payload'}
print(d.get('jungle'), d.get('absent_jungle', 'default_jungle'))
```

**Answer:**

```text
payload default_jungle
```

`get` on key `jungle` returns the stored value; missing keys use the default.

### Q90. Intermediate

What does this print?

```python
d = {'knoll': 'payload'}
print(d.get('knoll'), d.get('absent_knoll', 'default_knoll'))
```

**Answer:**

```text
payload default_knoll
```

`get` on key `knoll` returns the stored value; missing keys use the default.

### Q91. Intermediate

What does this print?

```python
d = {'lagoon': 'payload'}
print(d.get('lagoon'), d.get('absent_lagoon', 'default_lagoon'))
```

**Answer:**

```text
payload default_lagoon
```

`get` on key `lagoon` returns the stored value; missing keys use the default.

### Q92. Intermediate

What does this print?

```python
d = {'meadow': 'payload'}
print(d.get('meadow'), d.get('absent_meadow', 'default_meadow'))
```

**Answer:**

```text
payload default_meadow
```

`get` on key `meadow` returns the stored value; missing keys use the default.

### Q93. Intermediate

What does this print?

```python
d = {'narrows': 'payload'}
print(d.get('narrows'), d.get('absent_narrows', 'default_narrows'))
```

**Answer:**

```text
payload default_narrows
```

`get` on key `narrows` returns the stored value; missing keys use the default.

### Q94. Intermediate

What does this print?

```python
d = {'oasis': 'payload'}
print(d.get('oasis'), d.get('absent_oasis', 'default_oasis'))
```

**Answer:**

```text
payload default_oasis
```

`get` on key `oasis` returns the stored value; missing keys use the default.

### Q95. Intermediate

What does this print?

```python
d = {'plateau': 'payload'}
print(d.get('plateau'), d.get('absent_plateau', 'default_plateau'))
```

**Answer:**

```text
payload default_plateau
```

`get` on key `plateau` returns the stored value; missing keys use the default.

### Q96. Intermediate

What does this print?

```python
d = {'ravine': 'payload'}
print(d.get('ravine'), d.get('absent_ravine', 'default_ravine'))
```

**Answer:**

```text
payload default_ravine
```

`get` on key `ravine` returns the stored value; missing keys use the default.

### Q97. Intermediate

What does this print?

```python
d = {'summit': 'payload'}
print(d.get('summit'), d.get('absent_summit', 'default_summit'))
```

**Answer:**

```text
payload default_summit
```

`get` on key `summit` returns the stored value; missing keys use the default.

### Q98. Intermediate

What does this print?

```python
d = {'tundra': 'payload'}
print(d.get('tundra'), d.get('absent_tundra', 'default_tundra'))
```

**Answer:**

```text
payload default_tundra
```

`get` on key `tundra` returns the stored value; missing keys use the default.

### Q99. Intermediate

What does this print?

```python
d = {'valley': 'payload'}
print(d.get('valley'), d.get('absent_valley', 'default_valley'))
```

**Answer:**

```text
payload default_valley
```

`get` on key `valley` returns the stored value; missing keys use the default.

### Q100. Intermediate

What does this print?

```python
d = {'willow': 'payload'}
print(d.get('willow'), d.get('absent_willow', 'default_willow'))
```

**Answer:**

```text
payload default_willow
```

`get` on key `willow` returns the stored value; missing keys use the default.

### Q101. Intermediate

What does this print?

```python
d = {'yacht': 'payload'}
print(d.get('yacht'), d.get('absent_yacht', 'default_yacht'))
```

**Answer:**

```text
payload default_yacht
```

`get` on key `yacht` returns the stored value; missing keys use the default.

### Q102. Intermediate

What does this print?

```python
d = {'zenith': 'payload'}
print(d.get('zenith'), d.get('absent_zenith', 'default_zenith'))
```

**Answer:**

```text
payload default_zenith
```

`get` on key `zenith` returns the stored value; missing keys use the default.

### Q103. Intermediate

What does this print?

```python
d = {'arc': 'payload'}
print(d.get('arc'), d.get('absent_arc', 'default_arc'))
```

**Answer:**

```text
payload default_arc
```

`get` on key `arc` returns the stored value; missing keys use the default.

### Q104. Intermediate

What does this print?

```python
d = {'bolt': 'payload'}
print(d.get('bolt'), d.get('absent_bolt', 'default_bolt'))
```

**Answer:**

```text
payload default_bolt
```

`get` on key `bolt` returns the stored value; missing keys use the default.

### Q105. Intermediate

What does this print?

```python
d = {'core': 'payload'}
print(d.get('core'), d.get('absent_core', 'default_core'))
```

**Answer:**

```text
payload default_core
```

`get` on key `core` returns the stored value; missing keys use the default.

### Q106. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print(d | {'b': 9, 'c': 3})
```

**Answer:**

```text
{'a': 1, 'b': 9, 'c': 3}
```

`|` returns new dict; right wins collisions.

### Q107. Intermediate

What does this print?

```python
d = {'a': 1}
d |= {'a': 2, 'b': 3}
print(d)
```

**Answer:**

```text
{'a': 2, 'b': 3}
```

`|=` merges in place.

### Q108. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print({**d, 'b': 0, 'c': 4})
```

**Answer:**

```text
{'a': 1, 'b': 0, 'c': 4}
```

Later keys override in unpack merge.

### Q109. Intermediate

What does this print?

```python
base = {'a': 1}
extra = {'b': 2}
print({**base, **extra})
```

**Answer:**

```text
{'a': 1, 'b': 2}
```

Left-to-right unpack merge.

### Q110. Intermediate

What does this print?

```python
d = dict.fromkeys('ab', [])
d['a'].append(1)
print(d['b'])
```

**Answer:**

```text
[1]
```

`fromkeys` mutable default aliasing trap.

### Q111. Intermediate

What does this print?

```python
d = dict.fromkeys('ab')
print(d)
```

**Answer:**

```text
{'a': None, 'b': None}
```

Default value is `None` when omitted.

### Q112. Intermediate

What happens when this runs?

```python
d = {'a': 1}
del d['missing']
```

**Answer:**

```text
KeyError: 'missing'
```

`del` missing key raises `KeyError`.

### Q113. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2, 'c': 3}
for k in list(d):
    if k == 'b':
        del d[k]
print(sorted(d))
```

**Answer:**

```text
['a', 'c']
```

Snapshot keys before delete during loop.

### Q114. Intermediate

What happens when this runs?

```python
d = {'a': 1, 'b': 2}
for k in d:
    del d[k]
```

**Answer:**

```text
RuntimeError: dictionary changed size during iteration
```

Size change during iteration raises `RuntimeError`.

### Q115. Intermediate

What does this print?

```python
d = {True: 'yes', 1: 'one'}
print(d)
```

**Answer:**

```text
{True: 'one'}
```

`True` and `1` collide as one key.

### Q116. Intermediate

What does this print?

```python
d = {1: 'a', 1.0: 'b'}
print(d)
```

**Answer:**

```text
{1: 'b'}
```

`1` and `1.0` share one key.

### Q117. Intermediate

What does this print?

```python
import copy
inner = ['shared']
d = {'k': inner}
sh = d.copy()
deep = copy.deepcopy(d)
inner.append('x')
print(sh['k'], deep['k'])
```

**Answer:**

```text
['shared', 'x'] ['shared']
```

Shallow vs deep copy of nested objects.

### Q118. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print({v: k for k, v in d.items()})
```

**Answer:**

```text
{1: 'a', 2: 'b'}
```

Invert unique hashable values.

### Q119. Intermediate

What happens when this runs?

```python
d = {'a': 1, 'b': 1}
print({v: k for k, v in d.items()})
```

**Answer:**

```text
{1: 'b'}
```

Duplicate values collide in inversion.

### Q120. Intermediate

What happens when this runs?

```python
print(dict([('only',)]))
```

**Answer:**

```text
ValueError: dictionary update sequence element #0 has length 1; 2 is required
```

Pairs must have length two.

### Q121. Intermediate

What does this print?

```python
d = {'b': 2, 'a': 1}
print(list(d), sorted(d))
```

**Answer:**

```text
['b', 'a'] ['a', 'b']
```

Insertion order differs from sorted keys.

### Q122. Intermediate

What does this print?

```python
a = {'m': 1}
b = a
b['m'] = 9
print(a)
```

**Answer:**

```text
{'m': 9}
```

Names can alias one dict.

### Q123. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print(d.popitem(), d.popitem(), d)
```

**Answer:**

```text
('b', 2) ('a', 1) {}
```

Two LIFO pops.

### Q124. Intermediate

What does this print?

```python
print({i: i for i in []})
```

**Answer:**

```text
{}
```

Empty comprehension yields `{}`.

### Q125. Intermediate

What does this print?

```python
d = {'x': 1, 'y': 2}
print({k: v * 2 for k, v in d.items()})
```

**Answer:**

```text
{'x': 2, 'y': 4}
```

Transform values in comprehension.

### Q126. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print(sorted(d.items()))
```

**Answer:**

```text
[('a', 1), ('b', 2)]
```

Sort items by key.

### Q127. Intermediate

What does this print?

```python
d = {'a': 1}
print(d.keys() | {'b'})
```

**Answer:**

```text
{'b', 'a'}
```

Keys view union with set.

### Q128. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print(d.keys() & {'a', 'c'})
```

**Answer:**

```text
{'a'}
```

Keys view intersection.

### Q129. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print(d.keys() - {'b'})
```

**Answer:**

```text
{'a'}
```

Keys view difference.

### Q130. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print(d.keys() ^ {'a', 'c'})
```

**Answer:**

```text
{'c', 'b'}
```

Keys view symmetric difference.

### Q131. Intermediate

What does this print?

```python
from collections import ChainMap
a = {'x': 1}
b = {'y': 2}
print(dict(ChainMap(a, b)))
```

**Answer:**

```text
{'y': 2, 'x': 1}
```

ChainMap searches maps in order.

### Q132. Intermediate

What does this print?

```python
from collections import ChainMap
m = ChainMap({'a': 1}, {'a': 2})
print(m['a'])
```

**Answer:**

```text
1
```

First mapping wins on lookup.

### Q133. Intermediate

What does this print?

```python
d = {}
d[1] = 'a'
d[1.0] = 'b'
print(list(d.items()))
```

**Answer:**

```text
[(1, 'b')]
```

Equal keys share slot; first order kept.

### Q134. Intermediate

What does this print?

```python
d = {None: 0, False: 1, 0: 2, 1: 3, 1.0: 4}
print(len(d))
```

**Answer:**

```text
3
```

Literals collapse to three keys via equality.

### Q135. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print(set(d.keys()))
```

**Answer:**

```text
{'b', 'a'}
```

Keys view to set.

### Q136. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print(sorted(d.values()))
```

**Answer:**

```text
[1, 2]
```

Sorted values.

### Q137. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print(sorted(d.items(), key=lambda kv: kv[1]))
```

**Answer:**

```text
[('a', 1), ('b', 2)]
```

Sort items by value.

### Q138. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print(sorted(d.items(), key=lambda kv: kv[0], reverse=True))
```

**Answer:**

```text
[('b', 2), ('a', 1)]
```

Sort items by key descending.

### Q139. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print({k: v for k, v in reversed(list(d.items()))})
```

**Answer:**

```text
{'b': 2, 'a': 1}
```

Rebuild from reversed items.

### Q140. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print(all(v > 0 for v in d.values()))
```

**Answer:**

```text
True
```

Truth test on values.

### Q141. Intermediate

What does this print?

```python
d = {'a': 1, 'b': 2}
print(any(v > 1 for v in d.values()))
```

**Answer:**

```text
True
```

`any` on values.

### Q142. Advanced

What does this print?

```python
from collections import defaultdict
dd = defaultdict(int)
for ch in 'aba':
    dd[ch] += 1
print(sorted(dd.items()))
```

**Answer:**

```text
[('a', 2), ('b', 1)]
```

`defaultdict(int)` supplies zero for missing keys.

### Q143. Advanced

What does this print?

```python
from collections import Counter
c = Counter('abracadabra')
print(c['a'], c['z'])
```

**Answer:**

```text
5 0
```

Counter reads missing keys as zero.

### Q144. Advanced

What does this print?

```python
from collections import Counter
c = Counter(a=3, b=1)
d = Counter(a=1, b=2)
print(sorted((c + d).items()))
```

**Answer:**

```text
[('a', 4), ('b', 3)]
```

Counters add counts.

### Q145. Advanced

What does this print?

```python
from collections import Counter
c = Counter('aab')
print(c.most_common(1))
```

**Answer:**

```text
[('a', 2)]
```

`most_common` lists top frequencies.

### Q146. Advanced

What does this print?

```python
from collections import Counter
c = Counter('aab')
print(list(c.elements()))
```

**Answer:**

```text
['a', 'a', 'b']
```

`elements` expands counts.

### Q147. Advanced

What does this print?

```python
from collections import Counter
c = Counter(a=2, b=1)
print(c - Counter(a=1))
```

**Answer:**

```text
Counter({'a': 1, 'b': 1})
```

Counter subtraction drops non-positive counts.

### Q148. Advanced

What does this print?

```python
from collections import ChainMap
m = ChainMap({'a': 1}, {'b': 2})
print(list(m.maps))
```

**Answer:**

```text
[{'a': 1}, {'b': 2}]
```

`.maps` exposes underlying dicts.

### Q149. Advanced

What does this print?

```python
from collections import ChainMap
m = ChainMap({'a': 1}, {'a': 2})
m.maps[0]['a'] = 9
print(m['a'])
```

**Answer:**

```text
9
```

Mutating first map affects lookup.

### Q150. Advanced

What happens when this runs?

```python
d = {(1, [2]): 0}
```

**Answer:**

```text
TypeError: unhashable type: 'list'
```

Tuple with list is unhashable.

### Q151. Advanced

What does this print?

```python
d = {(1, 2): 3, (1, 2): 4}
print(d[(1, 2)])
```

**Answer:**

```text
4
```

Equal tuple keys are one slot.

### Q152. Advanced

What does this print?

```python
from collections import OrderedDict
print(OrderedDict(a=1) == {'a': 1})
```

**Answer:**

```text
True
```

OrderedDict equals dict with same pairs.

### Q153. Advanced

What does this print?

```python
d = {'a': 1}
print(d.popitem() if d else None)
```

**Answer:**

```text
('a', 1)
```

Guard empty dict before popitem.

### Q154. Advanced

What does this print?

```python
d = {'query': 'marker'}
print(list((d | {'query_extra': 'added'}).items()))
```

**Answer:**

```text
[('query', 'marker'), ('query_extra', 'added')]
```

Merge adds `query_extra` and preserves `query`.

### Q155. Advanced

What does this print?

```python
d = {'range': 'marker'}
print(list((d | {'range_extra': 'added'}).items()))
```

**Answer:**

```text
[('range', 'marker'), ('range_extra', 'added')]
```

Merge adds `range_extra` and preserves `range`.

### Q156. Advanced

What does this print?

```python
d = {'scope': 'marker'}
print(list((d | {'scope_extra': 'added'}).items()))
```

**Answer:**

```text
[('scope', 'marker'), ('scope_extra', 'added')]
```

Merge adds `scope_extra` and preserves `scope`.

### Q157. Advanced

What does this print?

```python
d = {'token': 'marker'}
print(list((d | {'token_extra': 'added'}).items()))
```

**Answer:**

```text
[('token', 'marker'), ('token_extra', 'added')]
```

Merge adds `token_extra` and preserves `token`.

### Q158. Advanced

What does this print?

```python
d = {'union': 'marker'}
print(list((d | {'union_extra': 'added'}).items()))
```

**Answer:**

```text
[('union', 'marker'), ('union_extra', 'added')]
```

Merge adds `union_extra` and preserves `union`.

### Q159. Advanced

What does this print?

```python
d = {'value': 'marker'}
print(list((d | {'value_extra': 'added'}).items()))
```

**Answer:**

```text
[('value', 'marker'), ('value_extra', 'added')]
```

Merge adds `value_extra` and preserves `value`.

### Q160. Advanced

What does this print?

```python
d = {'width': 'marker'}
print(list((d | {'width_extra': 'added'}).items()))
```

**Answer:**

```text
[('width', 'marker'), ('width_extra', 'added')]
```

Merge adds `width_extra` and preserves `width`.

### Q161. Advanced

What does this print?

```python
d = {'xform': 'marker'}
print(list((d | {'xform_extra': 'added'}).items()))
```

**Answer:**

```text
[('xform', 'marker'), ('xform_extra', 'added')]
```

Merge adds `xform_extra` and preserves `xform`.

### Q162. Advanced

What does this print?

```python
d = {'yieldy': 'marker'}
print(list((d | {'yieldy_extra': 'added'}).items()))
```

**Answer:**

```text
[('yieldy', 'marker'), ('yieldy_extra', 'added')]
```

Merge adds `yieldy_extra` and preserves `yieldy`.

### Q163. Advanced

What does this print?

```python
d = {'zeta': 'marker'}
print(list((d | {'zeta_extra': 'added'}).items()))
```

**Answer:**

```text
[('zeta', 'marker'), ('zeta_extra', 'added')]
```

Merge adds `zeta_extra` and preserves `zeta`.

### Q164. Advanced

What does this print?

```python
d = {'alga': 'marker'}
print(list((d | {'alga_extra': 'added'}).items()))
```

**Answer:**

```text
[('alga', 'marker'), ('alga_extra', 'added')]
```

Merge adds `alga_extra` and preserves `alga`.

### Q165. Advanced

What does this print?

```python
d = {'birch': 'marker'}
print(list((d | {'birch_extra': 'added'}).items()))
```

**Answer:**

```text
[('birch', 'marker'), ('birch_extra', 'added')]
```

Merge adds `birch_extra` and preserves `birch`.

### Q166. Advanced

What does this print?

```python
d = {'cedar': 'marker'}
print(list((d | {'cedar_extra': 'added'}).items()))
```

**Answer:**

```text
[('cedar', 'marker'), ('cedar_extra', 'added')]
```

Merge adds `cedar_extra` and preserves `cedar`.

### Q167. Advanced

What does this print?

```python
d = {'dusk': 'marker'}
print(list((d | {'dusk_extra': 'added'}).items()))
```

**Answer:**

```text
[('dusk', 'marker'), ('dusk_extra', 'added')]
```

Merge adds `dusk_extra` and preserves `dusk`.

### Q168. Advanced

What does this print?

```python
d = {'eagle': 'marker'}
print(list((d | {'eagle_extra': 'added'}).items()))
```

**Answer:**

```text
[('eagle', 'marker'), ('eagle_extra', 'added')]
```

Merge adds `eagle_extra` and preserves `eagle`.

### Q169. Advanced

What does this print?

```python
d = {'fern': 'marker'}
print(list((d | {'fern_extra': 'added'}).items()))
```

**Answer:**

```text
[('fern', 'marker'), ('fern_extra', 'added')]
```

Merge adds `fern_extra` and preserves `fern`.

### Q170. Advanced

What does this print?

```python
d = {'gull': 'marker'}
print(list((d | {'gull_extra': 'added'}).items()))
```

**Answer:**

```text
[('gull', 'marker'), ('gull_extra', 'added')]
```

Merge adds `gull_extra` and preserves `gull`.

### Q171. Advanced

What does this print?

```python
d = {'hawk': 'marker'}
print(list((d | {'hawk_extra': 'added'}).items()))
```

**Answer:**

```text
[('hawk', 'marker'), ('hawk_extra', 'added')]
```

Merge adds `hawk_extra` and preserves `hawk`.

### Q172. Advanced

What does this print?

```python
d = {'iris': 'marker'}
print(list((d | {'iris_extra': 'added'}).items()))
```

**Answer:**

```text
[('iris', 'marker'), ('iris_extra', 'added')]
```

Merge adds `iris_extra` and preserves `iris`.

### Q173. Advanced

What does this print?

```python
d = {'jay': 'marker'}
print(list((d | {'jay_extra': 'added'}).items()))
```

**Answer:**

```text
[('jay', 'marker'), ('jay_extra', 'added')]
```

Merge adds `jay_extra` and preserves `jay`.

### Q174. Advanced

What does this print?

```python
d = {'koala': 'marker'}
print(list((d | {'koala_extra': 'added'}).items()))
```

**Answer:**

```text
[('koala', 'marker'), ('koala_extra', 'added')]
```

Merge adds `koala_extra` and preserves `koala`.

### Q175. Advanced

What does this print?

```python
d = {'lark': 'marker'}
print(list((d | {'lark_extra': 'added'}).items()))
```

**Answer:**

```text
[('lark', 'marker'), ('lark_extra', 'added')]
```

Merge adds `lark_extra` and preserves `lark`.

### Q176. Advanced

What does this print?

```python
d = {'moth': 'marker'}
print(list((d | {'moth_extra': 'added'}).items()))
```

**Answer:**

```text
[('moth', 'marker'), ('moth_extra', 'added')]
```

Merge adds `moth_extra` and preserves `moth`.

### Q177. Advanced

What does this print?

```python
d = {'newt': 'marker'}
print(list((d | {'newt_extra': 'added'}).items()))
```

**Answer:**

```text
[('newt', 'marker'), ('newt_extra', 'added')]
```

Merge adds `newt_extra` and preserves `newt`.

### Q178. Advanced

What does this print?

```python
d = {'otter': 'marker'}
print(list((d | {'otter_extra': 'added'}).items()))
```

**Answer:**

```text
[('otter', 'marker'), ('otter_extra', 'added')]
```

Merge adds `otter_extra` and preserves `otter`.

### Q179. Advanced

What does this print?

```python
d = {'puma': 'marker'}
print(list((d | {'puma_extra': 'added'}).items()))
```

**Answer:**

```text
[('puma', 'marker'), ('puma_extra', 'added')]
```

Merge adds `puma_extra` and preserves `puma`.

### Q180. Advanced

What does this print?

```python
d = {'quail': 'marker'}
print(list((d | {'quail_extra': 'added'}).items()))
```

**Answer:**

```text
[('quail', 'marker'), ('quail_extra', 'added')]
```

Merge adds `quail_extra` and preserves `quail`.

### Q181. Advanced

What does this print?

```python
d = {'robin': 'marker'}
print(list((d | {'robin_extra': 'added'}).items()))
```

**Answer:**

```text
[('robin', 'marker'), ('robin_extra', 'added')]
```

Merge adds `robin_extra` and preserves `robin`.

### Q182. Advanced

What does this print?

```python
d = {'seal': 'marker'}
print(list((d | {'seal_extra': 'added'}).items()))
```

**Answer:**

```text
[('seal', 'marker'), ('seal_extra', 'added')]
```

Merge adds `seal_extra` and preserves `seal`.

### Q183. Advanced

What does this print?

```python
d = {'toad': 'marker'}
print(list((d | {'toad_extra': 'added'}).items()))
```

**Answer:**

```text
[('toad', 'marker'), ('toad_extra', 'added')]
```

Merge adds `toad_extra` and preserves `toad`.

### Q184. Advanced

What does this print?

```python
d = {'urchin': 'marker'}
print(list((d | {'urchin_extra': 'added'}).items()))
```

**Answer:**

```text
[('urchin', 'marker'), ('urchin_extra', 'added')]
```

Merge adds `urchin_extra` and preserves `urchin`.

### Q185. Advanced

What does this print?

```python
d = {'viper': 'marker'}
print(list((d | {'viper_extra': 'added'}).items()))
```

**Answer:**

```text
[('viper', 'marker'), ('viper_extra', 'added')]
```

Merge adds `viper_extra` and preserves `viper`.

### Q186. Advanced

What does this print?

```python
d = {'wolf': 'marker'}
print(list((d | {'wolf_extra': 'added'}).items()))
```

**Answer:**

```text
[('wolf', 'marker'), ('wolf_extra', 'added')]
```

Merge adds `wolf_extra` and preserves `wolf`.

### Q187. Advanced

What does this print?

```python
d = {'yak': 'marker'}
print(list((d | {'yak_extra': 'added'}).items()))
```

**Answer:**

```text
[('yak', 'marker'), ('yak_extra', 'added')]
```

Merge adds `yak_extra` and preserves `yak`.

### Q188. Advanced

What does this print?

```python
d = {'zebra': 'marker'}
print(list((d | {'zebra_extra': 'added'}).items()))
```

**Answer:**

```text
[('zebra', 'marker'), ('zebra_extra', 'added')]
```

Merge adds `zebra_extra` and preserves `zebra`.

### Q189. Advanced

What does this print?

```python
d = {'apple': 'marker'}
print(list((d | {'apple_extra': 'added'}).items()))
```

**Answer:**

```text
[('apple', 'marker'), ('apple_extra', 'added')]
```

Merge adds `apple_extra` and preserves `apple`.

### Q190. Advanced

What does this print?

```python
d = {'berry': 'marker'}
print(list((d | {'berry_extra': 'added'}).items()))
```

**Answer:**

```text
[('berry', 'marker'), ('berry_extra', 'added')]
```

Merge adds `berry_extra` and preserves `berry`.

### Q191. Advanced

What does this print?

```python
d = {'citrus': 'marker'}
print(list((d | {'citrus_extra': 'added'}).items()))
```

**Answer:**

```text
[('citrus', 'marker'), ('citrus_extra', 'added')]
```

Merge adds `citrus_extra` and preserves `citrus`.

### Q192. Advanced

What does this print?

```python
d = {'dates': 'marker'}
print(list((d | {'dates_extra': 'added'}).items()))
```

**Answer:**

```text
[('dates', 'marker'), ('dates_extra', 'added')]
```

Merge adds `dates_extra` and preserves `dates`.

### Q193. Advanced

What does this print?

```python
d = {'elderberry': 'marker'}
print(list((d | {'elderberry_extra': 'added'}).items()))
```

**Answer:**

```text
[('elderberry', 'marker'), ('elderberry_extra', 'added')]
```

Merge adds `elderberry_extra` and preserves `elderberry`.

### Q194. Advanced

What does this print?

```python
d = {'fig': 'marker'}
print(list((d | {'fig_extra': 'added'}).items()))
```

**Answer:**

```text
[('fig', 'marker'), ('fig_extra', 'added')]
```

Merge adds `fig_extra` and preserves `fig`.

### Q195. Basic

Write `invert_unique(d)` swapping keys and values; values are unique and hashable.

**Answer:**

```python
def invert_unique(d):
    return {v: k for k, v in d.items()}
```

- `invert_unique({'a': 1, 'b': 2})  =>  {1: 'a', 2: 'b'}`

Each value becomes a key in a new dict.

### Q196. Intermediate

Write `group_counts(items)` returning frequencies in a dict.

**Answer:**

```python
def group_counts(items):
    out = {}
    for x in items:
        out[x] = out.get(x, 0) + 1
    return out
```

- `group_counts('aba')  =>  {'a': 2, 'b': 1}`

Use `get` with zero default when incrementing counts.

### Q197. Intermediate

Write `two_sum(nums, target)` returning `(i, j)` with `i < j` or `None`.

**Answer:**

```python
def two_sum(nums, target):
    seen = {}
    for i, x in enumerate(nums):
        need = target - x
        if need in seen:
            return seen[need], i
        seen[x] = i
    return None
```

- `two_sum([2, 7, 11, 15], 9)  =>  (0, 1)`

Store value indices for O(1) complement lookup.

### Q198. Intermediate

Write `first_unique(s)` returning the first character with count one, else `None`.

**Answer:**

```python
def first_unique(s):
    counts = {}
    for ch in s:
        counts[ch] = counts.get(ch, 0) + 1
    for ch in s:
        if counts[ch] == 1:
            return ch
    return None
```

- `first_unique('aabbc')  =>  'c'`

Count first, then scan in original order.

### Q199. Advanced

Write `deep_get(d, keys, default=None)` walking nested dicts along `keys`.

**Answer:**

```python
def deep_get(d, keys, default=None):
    for k in keys:
        if not isinstance(d, dict) or k not in d:
            return default
        d = d[k]
    return d
```

- `deep_get({'a': {'b': 3}}, ['a', 'b'])  =>  3`
- `deep_get({'a': {}}, ['a', 'c'], 0)  =>  0`

Stop at first missing key or non-dict node.

### Q200. Advanced

Implement `LRU(cap)` with `.get` and `.put`; provide `lru_demo_keys()` after a sample sequence.

**Answer:**

```python
class LRU:
    def __init__(self, cap):
        self.cap = cap
        self.data = {}

    def get(self, key):
        if key not in self.data:
            return None
        val = self.data.pop(key)
        self.data[key] = val
        return val

    def put(self, key, value):
        if key in self.data:
            self.data.pop(key)
        elif len(self.data) >= self.cap:
            self.data.pop(next(iter(self.data)))
        self.data[key] = value


def lru_demo_keys():
    c = LRU(2)
    c.put('a', 1)
    c.put('b', 2)
    c.get('a')
    c.put('c', 3)
    return list(c.data.keys())
```

- `lru_demo_keys()  =>  ['a', 'c']`

Move touched keys to end; evict oldest at front via `next(iter(d))`.

*Section size: 200 questions (Basic 73, Intermediate 72, Advanced 55).*

