## 15. None (NoneType)

The singleton used for missing values and for the implicit result of a function.

### Q1. Basic

What does this print?

```python
print(type(None))
```

**Answer:**

```text
<class 'NoneType'>
```

None has type NoneType.

### Q2. Basic

What does this print?

```python
x = None
print(x is None)
```

**Answer:**

```text
True
```

Identity check with None singleton.

### Q3. Basic

What does this print?

```python
print(None == None)
```

**Answer:**

```text
True
```

None equals None.

### Q4. Basic

What does this print?

```python
print(bool(None))
```

**Answer:**

```text
False
```

None is falsy.

### Q5. Basic

What does this print?

```python
def f():
    pass
print(f())
```

**Answer:**

```text
None
```

Implicit return is None.

### Q6. Basic

What does this print?

```python
print(None in [1, None, 2])
```

**Answer:**

```text
True
```

None can be stored in containers.

### Q7. Basic

What does this print?

```python
print([None, None].count(None))
```

**Answer:**

```text
2
```

count finds None entries.

### Q8. Basic

What does this print?

```python
print(None if True else 0)
```

**Answer:**

```text
None
```

Conditional can yield None.

### Q9. Basic

What does this print?

```python
x = print('hi')
print(x)
```

**Answer:**

```text
hi
None
```

print returns None.

### Q10. Basic

What does this print?

```python
print([None][0] is None)
```

**Answer:**

```text
True
```

Stored None is singleton.

### Q11. Basic

What happens when this runs?

```python
print(None + 1)
```

**Answer:**

```text
TypeError: unsupported operand type(s) for +: 'NoneType' and 'int'
```

None does not support addition.

### Q12. Basic

What happens when this runs?

```python
x = None
try:
    x[0]
except Exception as e:
    print(type(e).__name__)
```

**Answer:**

```text
TypeError
```

None not subscriptable.

### Q13. Intermediate

What does this print?

```python
def f(x=[]):
    x.append(1)
    return x
print(f(), f())
```

**Answer:**

```text
[1, 1] [1, 1]
```

Mutable default shared across calls.

### Q14. Intermediate

What does this print?

```python
def g(x=None):
    if x is None:
        x = []
    x.append(1)
    return x
print(g(), g())
```

**Answer:**

```text
[1] [1]
```

None sentinel creates fresh list.

### Q15. Intermediate

What happens when this runs?

```python
print(sorted([1, None, 2]))
```

**Answer:**

```text
TypeError: '<' not supported between instances of 'NoneType' and 'int'
```

Comparing None to int raises TypeError.

### Q16. Intermediate

What does this print?

```python
print(None or 'fallback')
```

**Answer:**

```text
fallback
```

or skips falsy None.

### Q17. Intermediate

What does this print?

```python
print('ok' if None else 'no')
```

**Answer:**

```text
no
```

None branch falsy.

### Q18. Intermediate

What does this print?

```python
d = {}
print(d.get('missing'))
```

**Answer:**

```text
None
```

dict.get default None when absent.

### Q19. Intermediate

What does this print?

```python
d = {'a': None}
print(d.get('a', 'x'))
```

**Answer:**

```text
None
```

Present None value beats default.

### Q20. Advanced

What does this print?

```python
a = None
b = None
print(a is b)
```

**Answer:**

```text
True
```

All None references same object.

### Q21. Basic

What does this print?

```python
print(0 if False else None)
```

**Answer:**

```text
None
```

False branch yields None.

### Q22. Intermediate

What does this print?

```python
print((lambda: None)())
```

**Answer:**

```text
None
```

Lambda without return returns None.

### Q23. Intermediate

What does this print?

```python
print({'a': None}.get('a') is None)
```

**Answer:**

```text
True
```

get returns stored None by identity.

### Q24. Advanced

What does this print?

```python
x = None
print(not x, x is None)
```

**Answer:**

```text
True True
```

None falsy and identical to None.

### Q25. Intermediate

What happens when this runs?

```python
print(None > 0)
```

**Answer:**

```text
TypeError: '>' not supported between instances of 'NoneType' and 'int'
```

Ordering None vs int raises TypeError.

### Q26. Basic

What does this print?

```python
print(None == 0)
```

**Answer:**

```text
False
```

None only equals None.

### Q27. Basic

What does this print?

```python
print(None == False)
```

**Answer:**

```text
False
```

None does not equal False.

### Q28. Basic

What does this print?

```python
print(None == '')
```

**Answer:**

```text
False
```

None does not equal empty string.

### Q29. Basic

What does this print?

```python
print(None == [])
```

**Answer:**

```text
False
```

None does not equal empty list.

### Q30. Basic

What does this print?

```python
print(None == {})
```

**Answer:**

```text
False
```

None does not equal empty dict.

### Q31. Basic

What does this print?

```python
print(None == 0.0)
```

**Answer:**

```text
False
```

None does not equal float zero.

### Q32. Basic

What does this print?

```python
print(None != 0)
```

**Answer:**

```text
True
```

None != int is True.

### Q33. Basic

What does this print?

```python
print(None != False)
```

**Answer:**

```text
True
```

None != False is True.

### Q34. Basic

What does this print?

```python
print(None != '')
```

**Answer:**

```text
True
```

None != str is True.

### Q35. Basic

What does this print?

```python
print(None != [])
```

**Answer:**

```text
True
```

None != list is True.

### Q36. Basic

What does this print?

```python
print(None != {})
```

**Answer:**

```text
True
```

None != dict is True.

### Q37. Basic

What does this print?

```python
print(None != 0.0)
```

**Answer:**

```text
True
```

None != float is True.

### Q38. Basic

What does this print?

```python
print([None for _ in range(3)].count(None))
```

**Answer:**

```text
3
```

List comprehension of None.

### Q39. Basic

What does this print?

```python
print(tuple([None]*2))
```

**Answer:**

```text
(None, None)
```

Tuple of None values.

### Q40. Basic

What does this print?

```python
print(set([None]) == {None})
```

**Answer:**

```text
True
```

Set containing None.

### Q41. Basic

What does this print?

```python
print({None: 'nil'})
```

**Answer:**

```text
{None: 'nil'}
```

None as dict key.

### Q42. Basic

What does this print?

```python
print({None: None}[None])
```

**Answer:**

```text
None
```

None key maps to None value.

### Q43. Basic

What does this print?

```python
print([None].pop() is None)
```

**Answer:**

```text
True
```

Pop None from list.

### Q44. Basic

What does this print?

```python
print([None].index(None))
```

**Answer:**

```text
0
```

Index None in list.

### Q45. Basic

What does this print?

```python
print([None, None].index(None))
```

**Answer:**

```text
0
```

First None index zero.

### Q46. Basic

What does this print?

```python
print([None, None].count(None))
```

**Answer:**

```text
2
```

Both slots counted.

### Q47. Basic

What does this print?

```python
print([None if i else 0 for i in [0,1,0]])
```

**Answer:**

```text
[0, None, 0]
```

Mixed None and zero list.

### Q48. Basic

What does this print?

```python
print([x for x in [0, None, 1] if x is not None])
```

**Answer:**

```text
[0, 1]
```

Filter out None with identity.

### Q49. Basic

What does this print?

```python
print([x for x in [0, None, 1] if x is None])
```

**Answer:**

```text
[None]
```

Keep only None with identity.

### Q50. Basic

What does this print?

```python
print([x for x in [0, None, 1] if x])
```

**Answer:**

```text
[1]
```

Truthiness filter removes None and zero.

### Q51. Basic

What does this print?

```python
print([x for x in [0, None, 1] if not x])
```

**Answer:**

```text
[0, None]
```

Falsy filter keeps None and zero.

### Q52. Basic

What does this print?

```python
print(any([None, 0, '']))
```

**Answer:**

```text
False
```

any on falsy values.

### Q53. Basic

What does this print?

```python
print(all([None, 1]))
```

**Answer:**

```text
False
```

all short-circuits on falsy None.

### Q54. Basic

What does this print?

```python
print(sum([1, 0, None]) if False else None)
```

**Answer:**

```text
None
```

Guard sum when None present.

### Q55. Basic

What does this print?

```python
print(min([None, 1]) if False else None)
```

**Answer:**

```text
None
```

Avoid min with None.

### Q56. Basic

What does this print?

```python
print(max([None, 1]) if False else None)
```

**Answer:**

```text
None
```

Avoid max with None.

### Q57. Basic

What does this print?

```python
print(str(None))
```

**Answer:**

```text
None
```

str(None) is 'None'.

### Q58. Basic

What does this print?

```python
print(repr(None))
```

**Answer:**

```text
None
```

repr(None) is 'None'.

### Q59. Basic

What does this print?

```python
print(format(None))
```

**Answer:**

```text
None
```

format(None) stringifies.

### Q60. Basic

What does this print?

```python
print(f'{None}')
```

**Answer:**

```text
None
```

f-string None.

### Q61. Basic

What does this print?

```python
print('{}'.format(None))
```

**Answer:**

```text
None
```

format method None.

### Q62. Basic

What does this print?

```python
print('%s' % None)
```

**Answer:**

```text
None
```

Percent format None.

### Q63. Basic

What does this print?

```python
print(None in {None:1})
```

**Answer:**

```text
True
```

None membership as key.

### Q64. Basic

What does this print?

```python
print(None in [None])
```

**Answer:**

```text
True
```

None membership in list.

### Q65. Basic

What does this print?

```python
print(None not in [1,2])
```

**Answer:**

```text
True
```

None not in list without None.

### Q66. Basic

What does this print?

```python
print([None][0] == None)
```

**Answer:**

```text
True
```

Value equality to None.

### Q67. Basic

What does this print?

```python
print([None][0] != 0)
```

**Answer:**

```text
True
```

None is not equal to int zero.

### Q68. Basic

What does this print?

```python
print([None][0] != False)
```

**Answer:**

```text
True
```

None is not equal to False.

### Q69. Basic

What does this print?

```python
print([None][0] != '')
```

**Answer:**

```text
True
```

None is not equal to empty str.

### Q70. Intermediate

What does this print?

```python
def h():
    return
print(h())
```

**Answer:**

```text
None
```

Bare return gives None.

### Q71. Intermediate

What does this print?

```python
print(type(None))
```

**Answer:**

```text
<class 'NoneType'>
```

Use `type(None)`; the None object itself is not callable.

### Q72. Intermediate

What happens when this runs?

```python
print(None())
```

**Answer:**

```text
TypeError: 'NoneType' object is not callable
```

None is not callable.

### Q73. Intermediate

What does this print?

```python
print(getattr(type(None), '__name__'))
```

**Answer:**

```text
NoneType
```

NoneType name.

### Q74. Intermediate

What does this print?

```python
print(None.__class__)
```

**Answer:**

```text
<class 'NoneType'>
```

None class is NoneType.

### Q75. Intermediate

What does this print?

```python
print(None.__class__.__base__)
```

**Answer:**

```text
<class 'object'>
```

NoneType base is object.

### Q76. Intermediate

What does this print?

```python
print(None.__doc__ is not None)
```

**Answer:**

```text
False
```

NoneType has doc attribute.

### Q77. Intermediate

What does this print?

```python
print(hash(None))
```

**Answer:**

```text
4238894112
```

None is hashable.

### Q78. Intermediate

What does this print?

```python
print({None, None})
```

**Answer:**

```text
{None}
```

Set literal dedupes None.

### Q79. Intermediate

What does this print?

```python
print(frozenset([None, None]))
```

**Answer:**

```text
frozenset({None})
```

Frozenset of None singleton.

### Q80. Intermediate

What does this print?

```python
print([None]*3 == [None, None, None])
```

**Answer:**

```text
True
```

Repeat None list equality.

### Q81. Intermediate

What does this print?

```python
print((None, None)[1] is None)
```

**Answer:**

```text
True
```

Tuple None identity.

### Q82. Intermediate

What does this print?

```python
print({'a': None}.values())
```

**Answer:**

```text
dict_values([None])
```

Values view containing None.

### Q83. Intermediate

What does this print?

```python
print(list({'a': None}.values()))
```

**Answer:**

```text
[None]
```

Listify None value.

### Q84. Intermediate

What does this print?

```python
print({'a': None}.get('a') is None)
```

**Answer:**

```text
True
```

get identity None.

### Q85. Intermediate

What does this print?

```python
print({'a': None}.get('b') is None)
```

**Answer:**

```text
True
```

Missing key get is None.

### Q86. Intermediate

What does this print?

```python
print({'a': None}.setdefault('b') is None)
```

**Answer:**

```text
True
```

setdefault missing returns None.

### Q87. Intermediate

What does this print?

```python
print({'a': None}.setdefault('a') is None)
```

**Answer:**

```text
True
```

setdefault existing None value.

### Q88. Intermediate

What does this print?

```python
print([None].copy()[0] is None)
```

**Answer:**

```text
True
```

Copied list preserves None identity.

### Q89. Intermediate

What does this print?

```python
print([None].clear() or None)
```

**Answer:**

```text
None
```

Clear returns None.

### Q90. Intermediate

What does this print?

```python
print([None].append(None) or None)
```

**Answer:**

```text
None
```

Append returns None.

### Q91. Intermediate

What does this print?

```python
print([None].extend([None]) or None)
```

**Answer:**

```text
None
```

Extend returns None.

### Q92. Intermediate

What does this print?

```python
print([None].insert(0, None) or None)
```

**Answer:**

```text
None
```

Insert returns None.

### Q93. Intermediate

What does this print?

```python
print([None].remove(None) or None)
```

**Answer:**

```text
None
```

Remove returns None.

### Q94. Intermediate

What does this print?

```python
print([None, None].pop() is None)
```

**Answer:**

```text
True
```

Pop returns None.

### Q95. Intermediate

What does this print?

```python
print([None].sort() or None)
```

**Answer:**

```text
None
```

Sort returns None.

### Q96. Intermediate

What does this print?

```python
print([None].reverse() or None)
```

**Answer:**

```text
None
```

Reverse returns None.

### Q97. Intermediate

What does this print?

```python
print([None].__setitem__(0, None) or None)
```

**Answer:**

```text
None
```

setitem returns None.

### Q98. Intermediate

What does this print?

```python
print([None].__delitem__(0) if False else None)
```

**Answer:**

```text
None
```

Avoid deleting only element.

### Q99. Intermediate

What does this print?

```python
print([None].__iadd__([]) or None)
```

**Answer:**

```text
[None]
```

`__iadd__` returns the list itself. The list is truthy, so `or` does not fall through to `None`.

### Q100. Intermediate

What does this print?

```python
print([None].__imul__(1) or None)
```

**Answer:**

```text
[None]
```

`__imul__` returns the list itself, which is truthy, so the `or None` branch is not used.

### Q101. Intermediate

What does this print?

```python
print([None].__contains__(None))
```

**Answer:**

```text
True
```

Dunder contains None.

### Q102. Intermediate

What does this print?

```python
print([None].__len__())
```

**Answer:**

```text
1
```

Len one.

### Q103. Intermediate

What does this print?

```python
print([None].__iter__().__next__() is None)
```

**Answer:**

```text
True
```

Iter yields None.

### Q104. Intermediate

What does this print?

```python
print([None].__reversed__().__next__() is None)
```

**Answer:**

```text
True
```

Reversed iter None.

### Q105. Intermediate

What does this print?

```python
print([None].__getitem__(0) is None)
```

**Answer:**

```text
True
```

Getitem None.

### Q106. Intermediate

What does this print?

```python
print([None].__eq__([None]))
```

**Answer:**

```text
True
```

List equality with None.

### Q107. Intermediate

What does this print?

```python
print([None].__ne__([None]) if False else False)
```

**Answer:**

```text
False
```

Ne equal lists.

### Q108. Intermediate

What does this print?

```python
print([None].__repr__())
```

**Answer:**

```text
[None]
```

Repr of list with None.

### Q109. Intermediate

What does this print?

```python
print([None].__str__())
```

**Answer:**

```text
[None]
```

Str of list with None.

### Q110. Intermediate

What does this print?

```python
print([None].__sizeof__() > 0)
```

**Answer:**

```text
True
```

List with None has size.

### Q111. Intermediate

What does this print?

```python
print([None].__class__.__name__)
```

**Answer:**

```text
list
```

List class name.

### Q112. Intermediate

What does this print?

```python
print([None].__class__.__mro__[0].__name__)
```

**Answer:**

```text
list
```

MRO head list.

### Q113. Intermediate

What does this print?

```python
print([None].__class__.__mro__[1].__name__)
```

**Answer:**

```text
object
```

MRO object.

### Q114. Intermediate

What does this print?

```python
print([None].__class__.__bases__[0].__name__)
```

**Answer:**

```text
object
```

Base object.

### Q115. Intermediate

What does this print?

```python
print([None].__class__.__subclasses__()[0].__name__ if False else 'list')
```

**Answer:**

```text
list
```

Skip huge subclasses scan.

### Q116. Intermediate

What does this print?

```python
print([None].__dir__()[0].isidentifier())
```

**Answer:**

```text
True
```

Dir first name identifier.

### Q117. Intermediate

What does this print?

```python
print(hasattr([None], 'append'))
```

**Answer:**

```text
True
```

Has append.

### Q118. Intermediate

What does this print?

```python
print(getattr([None], 'pop')() is None)
```

**Answer:**

```text
True
```

getattr pop None.

### Q119. Intermediate

What does this print?

```python
print(setattr([None], '__doc__', None) or None)
```

**Answer:**

```text
AttributeError: 'list' object attribute '__doc__' is read-only
```

setattr returns None.

### Q120. Intermediate

What does this print?

```python
print(delattr(type(None), '__doc__') if False else None)
```

**Answer:**

```text
None
```

Avoid delattr on NoneType.

### Q121. Intermediate

What does this print?

```python
print(isinstance(None, type(None)))
```

**Answer:**

```text
True
```

None isinstance NoneType.

### Q122. Intermediate

What does this print?

```python
print(issubclass(type(None), object))
```

**Answer:**

```text
True
```

NoneType subclass object.

### Q123. Intermediate

What does this print?

```python
print(issubclass(type(None), type))
```

**Answer:**

```text
False
```

`type` is the metaclass of classes. `NoneType` is not a subclass of `type`, so this is false.

### Q124. Intermediate

What does this print?

```python
print(issubclass(type(None), type(object)))
```

**Answer:**

```text
False
```

`type(object)` is `type`. `NoneType` is not a subclass of `type`.

### Q125. Intermediate

What does this print?

```python
print(issubclass(type(None), type(None)))
```

**Answer:**

```text
True
```

NoneType subclass of itself.

### Q126. Intermediate

What does this print?

```python
print(isinstance(None, object))
```

**Answer:**

```text
True
```

None is an object instance.

### Q127. Intermediate

What does this print?

```python
print(isinstance(None, type(None)))
```

**Answer:**

```text
True
```

None is instance of NoneType.

### Q128. Intermediate

What does this print?

```python
print(type(None).__mro__ == (type(None), object))
```

**Answer:**

```text
True
```

NoneType MRO ends at object.

### Q129. Intermediate

What does this print?

```python
print(None.__reduce__())
```

**Answer:**

```text
TypeError: cannot pickle 'NoneType' object
```

Reduce pickle protocol for None.

### Q130. Intermediate

What does this print?

```python
print(None.__reduce_ex__(2))
```

**Answer:**

```text
(<function __newobj__ at 0x7bc905df13a0>, (<class 'NoneType'>,), None, None, None)
```

Reduce_ex for None.

### Q131. Intermediate

What does this print?

```python
print(None.__sizeof__())
```

**Answer:**

```text
16
```

None object size is small positive.

### Q132. Intermediate

What does this print?

```python
print(None.__str__())
```

**Answer:**

```text
None
```

Dunder str on None.

### Q133. Intermediate

What does this print?

```python
print(None.__repr__())
```

**Answer:**

```text
None
```

Dunder repr on None.

### Q134. Advanced

What does this print?

```python
def returns_none():
    return None
print(returns_none() is None)
```

**Answer:**

```text
True
```

Explicit None return identity.

### Q135. Advanced

What does this print?

```python
def default_none(x=None):
    return x
print(default_none() is None)
```

**Answer:**

```text
True
```

Default param None identity.

### Q136. Advanced

What does this print?

```python
def walrus_none():
    if (n := None) is None:
        return 'seen'
    return 'other'
print(walrus_none())
```

**Answer:**

```text
seen
```

Walrus with None sentinel.

### Q137. Advanced

What does this print?

```python
items = [1, None, 2, None, 3]
print([x for x in items if x is not None])
```

**Answer:**

```text
[1, 2, 3]
```

Filter Nones preserving order.

### Q138. Advanced

What does this print?

```python
items = [1, None, 2, None, 3]
print([x for x in items if x is None])
```

**Answer:**

```text
[None, None]
```

Collect only None entries.

### Q139. Advanced

What does this print?

```python
print([None for _ in 'abc'])
```

**Answer:**

```text
[None, None, None]
```

Three None list.

### Q140. Advanced

What does this print?

```python
print({k: None for k in 'abc'})
```

**Answer:**

```text
{'a': None, 'b': None, 'c': None}
```

Dict values all None.

### Q141. Advanced

What does this print?

```python
print(all(v is None for v in {k: None for k in 'abc'}.values()))
```

**Answer:**

```text
True
```

All dict values None identity.

### Q142. Advanced

What does this print?

```python
print(any(v is None for v in [0, None]))
```

**Answer:**

```text
True
```

Any finds None.

### Q143. Advanced

What does this print?

```python
print(not None)
```

**Answer:**

```text
True
```

not None is True.

### Q144. Advanced

What does this print?

```python
print(None and 'x')
```

**Answer:**

```text
None
```

and short-circuit on None.

### Q145. Advanced

What does this print?

```python
print('x' and None)
```

**Answer:**

```text
None
```

and returns last evaluated if truthy left.

### Q146. Advanced

What does this print?

```python
print(None or None or 'z')
```

**Answer:**

```text
z
```

or skips Nones.

### Q147. Advanced

What does this print?

```python
print(('x' if None else None) is None)
```

**Answer:**

```text
True
```

Conditional else None.

### Q148. Advanced

What does this print?

```python
print((None if True else 'x') is None)
```

**Answer:**

```text
True
```

Conditional if None branch.

### Q149. Advanced

What does this print?

```python
print([None][0] if [None] else 'x')
```

**Answer:**

```text
None
```

Subscript in conditional.

### Q150. Advanced

What does this print?

```python
print([None] and None)
```

**Answer:**

```text
None
```

and between list and None.

### Q151. Advanced

What does this print?

```python
print([None] or None)
```

**Answer:**

```text
[None]
```

or with nonempty list.

### Q152. Advanced

What does this print?

```python
print(None if [None] else 'x')
```

**Answer:**

```text
None
```

Truthy list chooses None branch? actually [None] truthy so None if [None] else x -> None.

### Q153. Advanced

What does this print?

```python
print('x' if [None] else None)
```

**Answer:**

```text
x
```

Truthy list picks x.

### Q154. Advanced

What does this print?

```python
print((lambda x=None: x)())
```

**Answer:**

```text
None
```

Lambda default None.

### Q155. Advanced

What does this print?

```python
print((lambda x=None: x is None)())
```

**Answer:**

```text
True
```

Lambda test default None.

### Q156. Advanced

What does this print?

```python
print((lambda: None)() is None)
```

**Answer:**

```text
True
```

Lambda return None identity.

### Q157. Advanced

What does this print?

```python
print((lambda: print('x'))() is None)
```

**Answer:**

```text
x
True
```

Print lambda returns None.

### Q158. Advanced

What does this print?

```python
print((lambda: [].sort())() is None)
```

**Answer:**

```text
True
```

Sort on empty returns None.

### Q159. Advanced

What does this print?

```python
print((lambda: {}.update({}))() is None)
```

**Answer:**

```text
True
```

Update returns None.

### Q160. Advanced

What does this print?

```python
print((lambda: [None].append(None))() is None)
```

**Answer:**

```text
True
```

Append returns None.

### Q161. Advanced

What does this print?

```python
print((lambda: [None].clear())() is None)
```

**Answer:**

```text
True
```

Clear returns None.

### Q162. Advanced

What does this print?

```python
print((lambda: [None].extend([]))() is None)
```

**Answer:**

```text
True
```

Extend empty returns None.

### Q163. Advanced

What does this print?

```python
print((lambda: [None].insert(0, None))() is None)
```

**Answer:**

```text
True
```

Insert returns None.

### Q164. Advanced

What does this print?

```python
print((lambda: [None].remove(None))() is None)
```

**Answer:**

```text
True
```

Remove returns None.

### Q165. Advanced

What does this print?

```python
print((lambda: [None].reverse())() is None)
```

**Answer:**

```text
True
```

Reverse returns None.

### Q166. Advanced

What does this print?

```python
print((lambda: [None].sort())() is None)
```

**Answer:**

```text
True
```

Sort returns None.

### Q167. Basic

What does this print?

```python
print('quail' if None else None)
```

**Answer:**

```text
None
```

Conditional string `quail` vs None.

### Q168. Basic

What does this print?

```python
print('robin' if None else None)
```

**Answer:**

```text
None
```

Conditional string `robin` vs None.

### Q169. Basic

What does this print?

```python
print('seal' if None else None)
```

**Answer:**

```text
None
```

Conditional string `seal` vs None.

### Q170. Basic

What does this print?

```python
print('toad' if None else None)
```

**Answer:**

```text
None
```

Conditional string `toad` vs None.

### Q171. Basic

What does this print?

```python
print('urchin' if None else None)
```

**Answer:**

```text
None
```

Conditional string `urchin` vs None.

### Q172. Basic

What does this print?

```python
print('viper' if None else None)
```

**Answer:**

```text
None
```

Conditional string `viper` vs None.

### Q173. Basic

What does this print?

```python
print('wolf' if None else None)
```

**Answer:**

```text
None
```

Conditional string `wolf` vs None.

### Q174. Basic

What does this print?

```python
print('yak' if None else None)
```

**Answer:**

```text
None
```

Conditional string `yak` vs None.

### Q175. Basic

What does this print?

```python
print('zebra' if None else None)
```

**Answer:**

```text
None
```

Conditional string `zebra` vs None.

### Q176. Basic

What does this print?

```python
print('apple' if None else None)
```

**Answer:**

```text
None
```

Conditional string `apple` vs None.

### Q177. Basic

What does this print?

```python
print('berry' if None else None)
```

**Answer:**

```text
None
```

Conditional string `berry` vs None.

### Q178. Basic

What does this print?

```python
print('citrus' if None else None)
```

**Answer:**

```text
None
```

Conditional string `citrus` vs None.

### Q179. Basic

What does this print?

```python
print('dates' if None else None)
```

**Answer:**

```text
None
```

Conditional string `dates` vs None.

### Q180. Basic

What does this print?

```python
print('elderberry' if None else None)
```

**Answer:**

```text
None
```

Conditional string `elderberry` vs None.

### Q181. Basic

What does this print?

```python
print('fig' if None else None)
```

**Answer:**

```text
None
```

Conditional string `fig` vs None.

### Q182. Basic

What does this print?

```python
print('grape' if None else None)
```

**Answer:**

```text
None
```

Conditional string `grape` vs None.

### Q183. Basic

What does this print?

```python
print('honey' if None else None)
```

**Answer:**

```text
None
```

Conditional string `honey` vs None.

### Q184. Basic

What does this print?

```python
print('kiwi' if None else None)
```

**Answer:**

```text
None
```

Conditional string `kiwi` vs None.

### Q185. Basic

What does this print?

```python
print('lemon' if None else None)
```

**Answer:**

```text
None
```

Conditional string `lemon` vs None.

### Q186. Basic

What does this print?

```python
print('mango' if None else None)
```

**Answer:**

```text
None
```

Conditional string `mango` vs None.

### Q187. Basic

What does this print?

```python
print('nut' if None else None)
```

**Answer:**

```text
None
```

Conditional string `nut` vs None.

### Q188. Basic

What does this print?

```python
print('oliveoil' if None else None)
```

**Answer:**

```text
None
```

Conditional string `oliveoil` vs None.

### Q189. Basic

What does this print?

```python
print('peach' if None else None)
```

**Answer:**

```text
None
```

Conditional string `peach` vs None.

### Q190. Basic

What does this print?

```python
print('quince' if None else None)
```

**Answer:**

```text
None
```

Conditional string `quince` vs None.

### Q191. Basic

What does this print?

```python
print('raisin' if None else None)
```

**Answer:**

```text
None
```

Conditional string `raisin` vs None.

### Q192. Basic

What does this print?

```python
print('sorbet' if None else None)
```

**Answer:**

```text
None
```

Conditional string `sorbet` vs None.

### Q193. Basic

What does this print?

```python
print('tart' if None else None)
```

**Answer:**

```text
None
```

Conditional string `tart` vs None.

### Q194. Basic

What does this print?

```python
print('udon' if None else None)
```

**Answer:**

```text
None
```

Conditional string `udon` vs None.

### Q195. Basic

What does this print?

```python
print('vanilla' if None else None)
```

**Answer:**

```text
None
```

Conditional string `vanilla` vs None.

### Q196. Basic

What does this print?

```python
print('wheat' if None else None)
```

**Answer:**

```text
None
```

Conditional string `wheat` vs None.

### Q197. Basic

What does this print?

```python
print('yogurt' if None else None)
```

**Answer:**

```text
None
```

Conditional string `yogurt` vs None.

### Q198. Basic

What does this print?

```python
print('zest' if None else None)
```

**Answer:**

```text
None
```

Conditional string `zest` vs None.

### Q199. Basic

What does this print?

```python
print('anise' if None else None)
```

**Answer:**

```text
None
```

Conditional string `anise` vs None.

### Q200. Intermediate

Write `strip_nones(items)` returning a list without None entries (use identity).

**Answer:**

```python
def strip_nones(items):
    return [x for x in items if x is not None]
```

- `strip_nones([1, None, 2, None])  =>  [1, 2]`

Use `is not None` because None is the sentinel to drop.

*Section size: 200 questions (Basic 90, Intermediate 75, Advanced 35).*

