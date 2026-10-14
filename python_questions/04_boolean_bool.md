## 4. Boolean (bool)

`True` and `False` are the only instances. They are the integers 1 and 0, and `and` / `or` return operands.

### Q1. Basic

What does this print?

```python
print(type(True), type(False))
```

**Answer:**

```text
<class 'bool'> <class 'bool'>
```

`True` and `False` are instances of `bool`.

### Q2. Basic

What does this print?

```python
print(True is True, False is False)
```

**Answer:**

```text
True True
```

The two singletons keep stable identity.

### Q3. Basic

What does this print?

```python
print(isinstance(True, bool), isinstance(False, bool))
```

**Answer:**

```text
True True
```

Both literals are `bool`.

### Q4. Basic

What does this print?

```python
print(isinstance(True, int))
```

**Answer:**

```text
True
```

`bool` is a subclass of `int`.

### Q5. Basic

What does this print?

```python
print(True == 1, False == 0)
```

**Answer:**

```text
True True
```

Bools compare equal to their integer values.

### Q6. Basic

What does this print?

```python
a = 1
b = True
print(a == b, a is b)
```

**Answer:**

```text
True False
```

`True` equals 1 but is not the same object as a separate int.

### Q7. Basic

What does this print?

```python
print(True + True, True + False)
```

**Answer:**

```text
2 1
```

Arithmetic treats bools as ints.

### Q8. Basic

What does this print?

```python
print(True - False, False - True)
```

**Answer:**

```text
1 -1
```

Subtraction uses int values.

### Q9. Basic

What does this print?

```python
print(True * 5, False * 100)
```

**Answer:**

```text
5 0
```

Multiplication promotes to int.

### Q10. Basic

What does this print?

```python
print(True / 2)
```

**Answer:**

```text
0.5
```

True division yields a float.

### Q11. Basic

What does this print?

```python
print(True // 2, True % 2)
```

**Answer:**

```text
0 1
```

Floor division and modulo use int semantics.

### Q12. Basic

What does this print?

```python
print(True & True, True | False, True ^ False)
```

**Answer:**

```text
True True True
```

Bitwise ops treat bools as 0/1.

### Q13. Basic

What does this print?

```python
print(~True, ~False)
```

**Answer:**

```text
-2 -1
```

Bitwise NOT on bool returns int.

### Q14. Basic

What does this print?

```python
print(bool(0), bool(1), bool(-3))
```

**Answer:**

```text
False True True
```

Only zero is falsy among ints.

### Q15. Basic

What does this print?

```python
print(bool(''), bool('x'))
```

**Answer:**

```text
False True
```

Empty string is falsy.

### Q16. Basic

What does this print?

```python
print(bool([]), bool([0]))
```

**Answer:**

```text
False True
```

Empty list falsy; non-empty truthy.

### Q17. Basic

What does this print?

```python
print(bool({}), bool({'a': 1}))
```

**Answer:**

```text
False True
```

Empty dict falsy.

### Q18. Basic

What does this print?

```python
print(bool(set()), bool({1}))
```

**Answer:**

```text
False True
```

Empty set falsy.

### Q19. Basic

What does this print?

```python
print(bool(None))
```

**Answer:**

```text
False
```

`None` is falsy.

### Q20. Basic

What does this print?

```python
print(not True, not False, not 0)
```

**Answer:**

```text
False True True
```

`not` coerces to bool then negates.

### Q21. Basic

What does this print?

```python
print(bool(True), bool(False))
```

**Answer:**

```text
True False
```

Bools are already truthy/falsy as themselves.

### Q22. Basic

What does this print?

```python
print(1 < 2 < 3)
```

**Answer:**

```text
True
```

Chained comparisons short-circuit through `and`.

### Q23. Basic

What does this print?

```python
print(1 < 2 > 0)
```

**Answer:**

```text
True
```

Mixed chains still require each link to hold.

### Q24. Basic

What does this print?

```python
print(True and 3)
```

**Answer:**

```text
3
```

`and` returns the last evaluated operand, not necessarily `bool`.

### Q25. Basic

What does this print?

```python
print(False and 3)
```

**Answer:**

```text
False
```

Short-circuit: first falsy operand is returned.

### Q26. Basic

What does this print?

```python
print(0 and 3)
```

**Answer:**

```text
0
```

Zero is falsy, so `and` stops and returns 0.

### Q27. Basic

What does this print?

```python
print(True or 99)
```

**Answer:**

```text
True
```

First truthy operand wins for `or`.

### Q28. Basic

What does this print?

```python
print(False or 99)
```

**Answer:**

```text
99
```

If left is falsy, `or` returns the right operand.

### Q29. Basic

What does this print?

```python
print(0 or [] or 'ok')
```

**Answer:**

```text
ok
```

Skips falsy values until `'ok'`.

### Q30. Basic

What does this print?

```python
print(not (True and False))
```

**Answer:**

```text
True
```

`not` binds less tightly than `and`.

### Q31. Basic

What does this print?

```python
print(any([False, 0, 3]))
```

**Answer:**

```text
True
```

`any` is True if any element is truthy.

### Q32. Basic

What does this print?

```python
print(all([True, 1, 'a']))
```

**Answer:**

```text
True
```

`all` is True if every element is truthy.

### Q33. Basic

What does this print?

```python
print(any([]))
```

**Answer:**

```text
False
```

Empty iterable: `any` is False.

### Q34. Basic

What does this print?

```python
print(all([]))
```

**Answer:**

```text
True
```

Empty iterable: `all` is True (vacuous).

### Q35. Basic

What does this print?

```python
print(bool())
```

**Answer:**

```text
False
```

`bool()` with no args is False.

### Q36. Basic

What does this print?

```python
print(bool(0.0), bool(0.0+0j))
```

**Answer:**

```text
False False
```

Zero float and zero complex are falsy.

### Q37. Basic

What does this print?

```python
print(int(True), int(False))
```

**Answer:**

```text
1 0
```

Convert bool to int explicitly.

### Q38. Basic

What does this print?

```python
print(float(True), float(False))
```

**Answer:**

```text
1.0 0.0
```

Convert bool to float.

### Q39. Basic

What does this print?

```python
print(True == True, False == False)
```

**Answer:**

```text
True True
```

Bools equal themselves.

### Q40. Basic

What does this print?

```python
print(True != False)
```

**Answer:**

```text
True
```

The two literals differ.

### Q41. Basic

What does this print?

```python
print(True < False)
```

**Answer:**

```text
False
```

As ints, True (1) is not less than False (0).

### Q42. Basic

What does this print?

```python
print(False < True)
```

**Answer:**

```text
True
```

0 < 1 is True.

### Q43. Intermediate

What does this print?

```python
print(True and False or True)
```

**Answer:**

```text
True
```

`and` before `or`: `(True and False) or True`.

### Q44. Intermediate

What does this print?

```python
print(not False and True)
```

**Answer:**

```text
True
```

`not` binds tighter: `(not False) and True`.

### Q45. Intermediate

What does this print?

```python
print(not (False and True))
```

**Answer:**

```text
True
```

Parentheses force inner `and` first.

### Q46. Intermediate

What does this print?

```python
print(1 and 2 and 3)
```

**Answer:**

```text
3
```

All truthy: last value returned.

### Q47. Intermediate

What does this print?

```python
print(1 or 2 or 0)
```

**Answer:**

```text
1
```

First truthy short-circuits to 1.

### Q48. Intermediate

What does this print?

```python
print([] or {} or 0 or 'x')
```

**Answer:**

```text
x
```

Returns first truthy `'x'`.

### Q49. Intermediate

What does this print?

```python
print('' or None or 0)
```

**Answer:**

```text
0
```

All falsy: returns last operand 0.

### Q50. Intermediate

What does this print?

```python
print(True if False else 'no')
```

**Answer:**

```text
no
```

Conditional expression picks `'no'`.

### Q51. Intermediate

What does this print?

```python
print(3 if True else 4)
```

**Answer:**

```text
3
```

Truthy condition picks first branch.

### Q52. Intermediate

What does this print?

```python
print([x for x in [0,1,2] if x])
```

**Answer:**

```text
[1, 2]
```

Comprehension `if x` keeps truthy items.

### Q53. Intermediate

What does this print?

```python
print(list(filter(None, [0,1,False,2,'' ])))
```

**Answer:**

```text
[1, 2]
```

`filter(None, ...)` drops falsy.

### Q54. Intermediate

What does this print?

```python
print(list(filter(bool, [0,1,False,2,'' ])))
```

**Answer:**

```text
[1, 2]
```

`filter(bool, ...)` same idea explicitly.

### Q55. Intermediate

What does this print?

```python
print(sum([True, True, False]))
```

**Answer:**

```text
2
```

Sum treats bools as 0/1.

### Q56. Intermediate

What does this print?

```python
print(min([True, False]), max([True, False]))
```

**Answer:**

```text
False True
```

Min/max use numeric order of bools.

### Q57. Intermediate

What does this print?

```python
print(sorted([True, False, True]))
```

**Answer:**

```text
[False, True, True]
```

Sorts as False then True.

### Q58. Intermediate

What does this print?

```python
print({True: 't', False: 'f'}[False])
```

**Answer:**

```text
f
```

Bool keys in dict.

### Q59. Intermediate

What does this print?

```python
print({1: 'one', True: 'true'}[1])
```

**Answer:**

```text
true
```

True equals 1, so keys collide; last wins.

### Q60. Intermediate

What does this print?

```python
print(hash(True), hash(1))
```

**Answer:**

```text
1 1
```

Equal values share hash.

### Q61. Intermediate

What happens when this runs?

```python
class MyBool(bool):
    pass
```

**Answer:**

```text
TypeError: type 'bool' is not an acceptable base type
```

Subclassing `bool` raises `TypeError`.

### Q62. Intermediate

What does this print?

```python
print(bool([1,2]))
```

**Answer:**

```text
True
```

Non-empty list is truthy even if elements are truthy.

### Q63. Intermediate

What does this print?

```python
print(bool([0]))
```

**Answer:**

```text
True
```

Non-empty list is truthy even when sole element is 0.

### Q64. Intermediate

What does this print?

```python
print(bool('0'))
```

**Answer:**

```text
True
```

Non-empty string is truthy; `'0'` is not int zero.

### Q65. Intermediate

What does this print?

```python
print(bool('False'))
```

**Answer:**

```text
True
```

The word False as string is still truthy.

### Q66. Intermediate

What does this print?

```python
x = 0
f = False
print(x == f, x is f)
```

**Answer:**

```text
True False
```

Zero equals False but is not the False object.

### Q67. Intermediate

What does this print?

```python
print(None == False, bool(None))
```

**Answer:**

```text
False False
```

`None` is not equal to False; it is falsy.

### Q68. Intermediate

What does this print?

```python
a = 1
t = True
print(a == t, a is t)
```

**Answer:**

```text
True False
```

Same identity lesson for True.

### Q69. Intermediate

What does this print?

```python
print(any(x > 0 for x in [-1, -2]))
```

**Answer:**

```text
False
```

Generator with no truthy: False.

### Q70. Intermediate

What does this print?

```python
print(all(x > 0 for x in [1, 2, 3]))
```

**Answer:**

```text
True
```

All positive: True.

### Q71. Intermediate

What does this print?

```python
print(all(x > 0 for x in [1, -1]))
```

**Answer:**

```text
False
```

One failure: False.

### Q72. Advanced

What does this print?

```python
class Empty:
    def __len__(self):
        return 0
print(bool(Empty()))
```

**Answer:**

```text
False
```

With no `__bool__`, `__len__==0` makes instance falsy.

### Q73. Advanced

What does this print?

```python
class NonEmpty:
    def __len__(self):
        return 3
print(bool(NonEmpty()))
```

**Answer:**

```text
True
```

Non-zero `__len__` is truthy without `__bool__`.

### Q74. Advanced

What does this print?

```python
class Always:
    def __bool__(self):
        return False
    def __len__(self):
        return 99
print(bool(Always()))
```

**Answer:**

```text
False
```

`__bool__` wins over `__len__`.

### Q75. Advanced

What does this print?

```python
class Raising:
    def __bool__(self):
        return True
print(bool(Raising()))
```

**Answer:**

```text
True
```

Custom `__bool__` can force truthiness.

### Q76. Advanced

What does this print?

```python
print(True and True or False)
```

**Answer:**

```text
True
```

Parse as `(True and True) or False`.

### Q77. Advanced

What does this print?

```python
print(False or True and False)
```

**Answer:**

```text
False
```

`and` before `or`: `False or (True and False)`.

### Q78. Advanced

What does this print?

```python
print(not 0 == 0)
```

**Answer:**

```text
False
```

`not` before `==`: `(not 0) == 0` is False.

### Q79. Advanced

What does this print?

```python
print(not (0 == 0))
```

**Answer:**

```text
False
```

Negated equality.

### Q80. Advanced

What does this print?

```python
print(1 < 2 == 2)
```

**Answer:**

```text
True
```

Chained: `1 < 2 and 2 == 2`.

### Q81. Advanced

What does this print?

```python
print(1 == 1 == True)
```

**Answer:**

```text
True
```

Middle evaluated once; `1 == True` is True.

### Q82. Advanced

What does this print?

```python
print(False is False, True is not False)
```

**Answer:**

```text
True True
```

Identity between singletons.

### Q83. Advanced

What does this print?

```python
print(issubclass(bool, int), issubclass(int, bool))
```

**Answer:**

```text
True False
```

Subclass relation is one-way.

### Q84. Advanced

What does this print?

```python
print(type(True).__mro__)
```

**Answer:**

```text
(<class 'bool'>, <class 'int'>, <class 'object'>)
```

MRO shows `bool` before `int` before `object`.

### Q85. Advanced

What does this print?

```python
print(True.numerator, True.denominator)
```

**Answer:**

```text
1 1
```

As rationals, True is 1/1.

### Q86. Advanced

What does this print?

```python
print(False.bit_length(), True.bit_length())
```

**Answer:**

```text
0 1
```

Int methods work on bool.

### Q87. Advanced

What does this print?

```python
print(format(True, 'b'), format(False, 'b'))
```

**Answer:**

```text
1 0
```

Format bool as binary int.

### Q88. Advanced

What does this print?

```python
print(chr(True), chr(False))
```

**Answer:**

```text
  
```

`chr(1)` is SOH; `chr(0)` is NUL.

### Q89. Advanced

What does this print?

```python
print(divmod(True, True))
```

**Answer:**

```text
(1, 0)
```

Floor division of 1 by 1.

### Q90. Advanced

What does this print?

```python
print(pow(True, 10), pow(False, 0))
```

**Answer:**

```text
1 1
```

Powers follow int rules.

### Q91. Intermediate

What does this print?

```python
log = []
result = log.append('a') or log.append('b')
print(result, log)
```

**Answer:**

```text
None ['a', 'b']
```

First append returns None (falsy), so second runs.

### Q92. Intermediate

What does this print?

```python
log = []
result = log.append('a') and log.append('b')
print(result, log)
```

**Answer:**

```text
None ['a']
```

First falsy stops `and`; only `'a'` logged.

### Q93. Advanced

What does this print?

```python
log = []
(0 or log.append('x'))
print(log)
```

**Answer:**

```text
['x']
```

`or` evaluates append when left is falsy.

### Q94. Advanced

What does this print?

```python
log = []
(1 and log.append('y'))
print(log)
```

**Answer:**

```text
['y']
```

Truthy left lets `and` evaluate append.

### Q95. Basic

What does this print?

```python
print(bool(0))
```

**Answer:**

```text
False
```

Truthiness of 0.

### Q96. Basic

What does this print?

```python
print(bool(1))
```

**Answer:**

```text
True
```

Truthiness of 1.

### Q97. Intermediate

What does this print?

```python
print(bool(2))
```

**Answer:**

```text
True
```

Truthiness of 2.

### Q98. Intermediate

What does this print?

```python
print(bool(-1))
```

**Answer:**

```text
True
```

Truthiness of -1.

### Q99. Basic

What does this print?

```python
print(bool(0.0))
```

**Answer:**

```text
False
```

Truthiness of 0.0.

### Q100. Basic

What does this print?

```python
print(bool(0j))
```

**Answer:**

```text
False
```

Truthiness of 0j.

### Q101. Basic

What does this print?

```python
print(bool(''))
```

**Answer:**

```text
False
```

Truthiness of ''.

### Q102. Intermediate

What does this print?

```python
print(bool('hi'))
```

**Answer:**

```text
True
```

Truthiness of 'hi'.

### Q103. Basic

What does this print?

```python
print(bool([]))
```

**Answer:**

```text
False
```

Truthiness of [].

### Q104. Intermediate

What does this print?

```python
print(bool([0]))
```

**Answer:**

```text
True
```

Truthiness of [0].

### Q105. Basic

What does this print?

```python
print(bool({}))
```

**Answer:**

```text
False
```

Truthiness of {}.

### Q106. Intermediate

What does this print?

```python
print(bool({0: 1}))
```

**Answer:**

```text
True
```

Truthiness of {0: 1}.

### Q107. Basic

What does this print?

```python
print(bool(None))
```

**Answer:**

```text
False
```

Truthiness of None.

### Q108. Basic

What does this print?

```python
print(bool(True))
```

**Answer:**

```text
True
```

Truthiness of True.

### Q109. Basic

What does this print?

```python
print(bool(False))
```

**Answer:**

```text
False
```

Truthiness of False.

### Q110. Basic

What does this print?

```python
print(3 and 4 or 5)
```

**Answer:**

```text
4
```

Left-to-right with precedence.

### Q111. Intermediate

What does this print?

```python
print(0 or 0 or 2)
```

**Answer:**

```text
2
```

Skip falsy until 2.

### Q112. Intermediate

What does this print?

```python
print(True ^ True, True ^ False)
```

**Answer:**

```text
False True
```

XOR on bools as ints.

### Q113. Intermediate

What does this print?

```python
print(bool([False]))
```

**Answer:**

```text
True
```

List containing False is still non-empty.

### Q114. Advanced

What does this print?

```python
print(all([True, True, False]) == False)
```

**Answer:**

```text
True
```

`all` returns bool.

### Q115. Advanced

What does this print?

```python
print(any([False, False, 0]) == False)
```

**Answer:**

```text
True
```

`any` on all falsy.

### Q116. Intermediate

What does this print?

```python
print(not not 0)
```

**Answer:**

```text
False
```

Double not coerces to bool twice.

### Q117. Intermediate

What does this print?

```python
print(not not 'x')
```

**Answer:**

```text
True
```

Double not on truthy string.

### Q118. Advanced

What does this print?

```python
print(1 < 2 < 3 == True)
```

**Answer:**

```text
False
```

Chain mixes operators.

### Q119. Basic

What does this print?

```python
print(False and print('no'))
```

**Answer:**

```text
False
```

Short-circuit prevents print.

### Q120. Basic

What does this print?

```python
print(True or print('no'))
```

**Answer:**

```text
True
```

Short-circuit prevents print on `or`.

### Q121. Basic

What does this print?

```python
print(True << 1)
```

**Answer:**

```text
2
```

Left shift True as int 1 gives 2.

### Q122. Basic

What does this print?

```python
print(False << 3)
```

**Answer:**

```text
0
```

Shift zero stays zero.

### Q123. Intermediate

What does this print?

```python
print(bool(range(0)))
```

**Answer:**

```text
False
```

Empty range is falsy.

### Q124. Intermediate

What does this print?

```python
print(bool(range(1)))
```

**Answer:**

```text
True
```

Non-empty range truthy.

### Q125. Intermediate

What does this print?

```python
print(bool(b''))
```

**Answer:**

```text
False
```

Empty bytes falsy.

### Q126. Intermediate

What does this print?

```python
print(bool(b'0'))
```

**Answer:**

```text
True
```

Non-empty bytes truthy.

### Q127. Intermediate

What does this print?

```python
print(bool(()))
```

**Answer:**

```text
False
```

Empty tuple falsy.

### Q128. Intermediate

What does this print?

```python
print(bool((0,)))
```

**Answer:**

```text
True
```

Non-empty tuple truthy.

### Q129. Intermediate

What does this print?

```python
print(0 and True or False)
```

**Answer:**

```text
False
```

Mix `and`/`or` left-to-right with precedence.

### Q130. Advanced

What does this print?

```python
print(0 if False else 1 if True else 2)
```

**Answer:**

```text
1
```

Nested conditional expressions.

### Q131. Advanced

What does this print?

```python
print([bool(x) for x in range(3)])
```

**Answer:**

```text
[False, True, True]
```

Map bool over ints.

### Q132. Advanced

What does this print?

```python
print({False: 0, True: 1}[True])
```

**Answer:**

```text
1
```

Bool key lookup.

### Q133. Advanced

What does this print?

```python
print(True + True + True == 3)
```

**Answer:**

```text
True
```

Repeated bool sum.

### Q134. Advanced

What does this print?

```python
print(False or False or False or 7)
```

**Answer:**

```text
7
```

Last operand returned when all falsy.

### Q135. Advanced

What does this print?

```python
print(True and True and True and 9)
```

**Answer:**

```text
9
```

Last operand when all truthy.

### Q136. Intermediate

What does this print?

```python
print(not [] )
```

**Answer:**

```text
True
```

not empty list is True.

### Q137. Intermediate

What does this print?

```python
print(not [0])
```

**Answer:**

```text
False
```

not non-empty list is False.

### Q138. Basic

What does this print?

```python
z = bool(0)
f = False
print(z is f)
```

**Answer:**

```text
True
```

`bool(0)` is the False singleton.

### Q139. Basic

What does this print?

```python
z = bool(1)
t = True
print(z is t)
```

**Answer:**

```text
True
```

`bool(1)` is the True singleton.

### Q140. Intermediate

What does this print?

```python
z = bool(2)
t = True
print(z is t)
```

**Answer:**

```text
True
```

Any truthy int passed through `bool()` returns the `True` singleton.

### Q141. Advanced

What does this print?

```python
z = bool(2)
t = True
print(z == t, z is t)
```

**Answer:**

```text
True True
```

Any non-zero int converts to the True singleton.

### Q142. Intermediate

What does this print?

```python
print(all([bool(0), False]) == False)
```

**Answer:**

```text
True
```

Nested bool in all.

### Q143. Intermediate

What does this print?

```python
print(any([0, '', None, 0.0]) == False)
```

**Answer:**

```text
True
```

Various falsy types.

### Q144. Advanced

What does this print?

```python
class Both:
    def __bool__(self):
        return False
    def __len__(self):
        return 5
print(bool(Both()))
```

**Answer:**

```text
False
```

`__bool__` False beats non-zero len.

### Q145. Advanced

What does this print?

```python
print(1 < 2 == 2 < 3)
```

**Answer:**

```text
True
```

Long chain of comparisons.

### Q146. Advanced

What does this print?

```python
print(5 > 4 > 3 > 2)
```

**Answer:**

```text
True
```

Descending chain.

### Q147. Intermediate

What does this print?

```python
print(True & 1, False | 1)
```

**Answer:**

```text
1 1
```

Mix bool with int bitwise.

### Q148. Intermediate

What does this print?

```python
print(~0 & True)
```

**Answer:**

```text
1
```

Bitwise with True as 1.

### Q149. Basic

What does this print?

```python
print(bool(' \n\t'))
```

**Answer:**

```text
True
```

Whitespace-only string is truthy (non-empty).

### Q150. Basic

What does this print?

```python
print(bool(0.0001))
```

**Answer:**

```text
True
```

Tiny non-zero float truthy.

### Q151. Intermediate

What does this print?

```python
print(bool(0+0.0j))
```

**Answer:**

```text
False
```

Zero complex falsy.

### Q152. Intermediate

What does this print?

```python
print(bool(0+3j))
```

**Answer:**

```text
True
```

Non-zero imag truthy.

### Q153. Advanced

What does this print?

```python
print(sum([True, False, True]))
```

**Answer:**

```text
2
```

Count truthy via sum.

### Q154. Advanced

What does this print?

```python
print(bool(frozenset()))
```

**Answer:**

```text
False
```

Empty frozenset falsy.

### Q155. Advanced

What does this print?

```python
print(bool(frozenset([0])))
```

**Answer:**

```text
True
```

Non-empty frozenset truthy.

### Q156. Advanced

What does this print?

```python
print(bool(memoryview(b'')))
```

**Answer:**

```text
False
```

Empty memoryview falsy.

### Q157. Advanced

What does this print?

```python
print(bool(memoryview(b'x')))
```

**Answer:**

```text
True
```

Non-empty memoryview truthy.

### Q158. Intermediate

What does this print?

```python
print(False == 0 == False)
```

**Answer:**

```text
True
```

Chained equality with False and 0.

### Q159. Intermediate

What does this print?

```python
print(True == 1 == 1.0)
```

**Answer:**

```text
True
```

Chained across numeric types.

### Q160. Basic

What does this print?

```python
print(not None)
```

**Answer:**

```text
True
```

not None is True.

### Q161. Basic

What does this print?

```python
print(not '')
```

**Answer:**

```text
True
```

not empty string is True.

### Q162. Intermediate

What does this print?

```python
print(bool([False, True][0]))
```

**Answer:**

```text
False
```

Index into list of bools.

### Q163. Intermediate

What does this print?

```python
print(bool({False: 1}))
```

**Answer:**

```text
True
```

Dict with False key is non-empty.

### Q164. Advanced

What does this print?

```python
print(bool(type))
```

**Answer:**

```text
True
```

Type objects are truthy.

### Q165. Advanced

What does this print?

```python
print(bool(len))
```

**Answer:**

```text
True
```

Built-in functions are truthy.

### Q166. Advanced

What does this print?

```python
print(bool(lambda: 0))
```

**Answer:**

```text
True
```

Functions are truthy.

### Q167. Intermediate

What does this print?

```python
print(0 or False or None or '')
```

**Answer:**

```text
(no output)
```

All falsy returns last `''`.

### Q168. Advanced

What does this print?

```python
log=[]
(1 and log.append(1))
print(log)
```

**Answer:**

```text
[1]
```

Side effect only when left truthy.

### Q169. Advanced

What does this print?

```python
log=[]
(0 and log.append(1))
print(log)
```

**Answer:**

```text
[]
```

Falsy left skips side effect.

### Q170. Advanced

What does this print?

```python
log=[]
(0 or log.append(2))
print(log)
```

**Answer:**

```text
[2]
```

Falsy left runs right on `or`.

### Q171. Advanced

What does this print?

```python
log=[]
(1 or log.append(2))
print(log)
```

**Answer:**

```text
[]
```

Truthy left skips right on `or`.

### Q172. Intermediate

What does this print?

```python
print(bool(enumerate([])))
```

**Answer:**

```text
True
```

Enumerate object always truthy (it's an iterator wrapper).

### Q173. Intermediate

What does this print?

```python
print(bool(iter([])))
```

**Answer:**

```text
True
```

Iterator object is truthy even if empty.

### Q174. Advanced

What does this print?

```python
print(all(map(bool, [1,2,3])))
```

**Answer:**

```text
True
```

Map bool then all.

### Q175. Advanced

What does this print?

```python
print(any(map(bool, [0,0,0])))
```

**Answer:**

```text
False
```

Any on mapped falsy.

### Q176. Intermediate

What does this print?

```python
print(True == 1 != False)
```

**Answer:**

```text
True
```

Chained inequality/equality.

### Q177. Basic

What does this print?

```python
print(False and True or True)
```

**Answer:**

```text
True
```

Classic boolean expression.

### Q178. Basic

What does this print?

```python
print(True or False and False)
```

**Answer:**

```text
True
```

`and` binds tighter than `or`.

### Q179. Basic

What does this print?

```python
print(bool(0.0+0.0j))
```

**Answer:**

```text
False
```

Zero complex is falsy.

### Q180. Intermediate

What does this print?

```python
print(1 and 2 or 3 and 4)
```

**Answer:**

```text
2
```

`and` before `or`: `(1 and 2) or (3 and 4)` -> 2.

### Q181. Intermediate

What does this print?

```python
print(0 and 2 or 3 and 4)
```

**Answer:**

```text
4
```

Evaluates to 4.

### Q182. Advanced

What does this print?

```python
print(not (True or False))
```

**Answer:**

```text
False
```

De Morgan on simple literals.

### Q183. Advanced

What does this print?

```python
print((True and False) == False)
```

**Answer:**

```text
True
```

And of opposites is False.

### Q184. Advanced

What does this print?

```python
print((True or False) == True)
```

**Answer:**

```text
True
```

Or of opposites is True.

### Q185. Basic

Write `all_positive(nums)` returning whether every number is > 0.

**Answer:**

```python
def all_positive(nums):
    return all(x > 0 for x in nums)
```

- `all_positive([1,2,3])  =>  True`
- `all_positive([1,0,3])  =>  False`
- `all_positive([])  =>  True`

Empty is vacuously all positive.

### Q186. Basic

Write `xor(a, b)` returning logical XOR without using `^` on bools.

**Answer:**

```python
def xor(a, b):
    return bool(a) != bool(b)
```

- `xor(True, False)  =>  True`
- `xor(1, 1)  =>  False`
- `xor(0, 'x')  =>  True`

Exactly one truthy operand.

### Q187. Intermediate

Write `implies(p, q)` returning `not p or q`.

**Answer:**

```python
def implies(p, q):
    return (not p) or q
```

- `implies(True, True)  =>  True`
- `implies(True, False)  =>  False`
- `implies(False, False)  =>  True`

Material implication.

### Q188. Intermediate

Write `majority(values)` returning True if strictly more than half are truthy.

**Answer:**

```python
def majority(values):
    t = sum(1 for v in values if v)
    return t > len(values) / 2
```

- `majority([1,0,1])  =>  True`
- `majority([1,0,0])  =>  False`
- `majority([1,1,0,0])  =>  False`

Count truthy items.

### Q189. Intermediate

Write `exactly_one(a, b, c)` True iff exactly one argument is truthy.

**Answer:**

```python
def exactly_one(a, b, c):
    return sum(bool(x) for x in (a, b, c)) == 1
```

- `exactly_one(1,0,0)  =>  True`
- `exactly_one(1,1,0)  =>  False`
- `exactly_one(0,0,0)  =>  False`

Count truthy args.

### Q190. Basic

Write `is_truthy(x)` returning `bool(x)`.

**Answer:**

```python
def is_truthy(x):
    return bool(x)
```

- `is_truthy(0)  =>  False`
- `is_truthy('0')  =>  True`
- `is_truthy([])  =>  False`

Delegate to `bool()`.

### Q191. Intermediate

Write `first_truthy(*args)` returning the first truthy argument or the last if none.

**Answer:**

```python
def first_truthy(*args):
    for x in args:
        if x:
            return x
    return args[-1] if args else None
```

- `first_truthy(0, '', 3)  =>  3`
- `first_truthy(0, '', None)  =>  None`
- `first_truthy(5, 9)  =>  5`

Mirrors `or` chain behavior.

### Q192. Advanced

Write `logged_and(a, b, log)` appending `'L'` when starting and `'R'` only if `a` is truthy; return `a and b`.

**Answer:**

```python
def logged_and(a, b, log):
    log.append('L')
    if not a:
        return a
    log.append('R')
    return b


def _log_and_left_falsy():
    log = []
    logged_and(0, 1, log)
    return log


def _log_and_left_truthy():
    log = []
    logged_and(1, 0, log)
    return log
```

- `_log_and_left_falsy()  =>  ['L']`
- `_log_and_left_truthy()  =>  ['L', 'R']`

Demonstrates short-circuit on falsy `a`.

### Q193. Advanced

Write `logged_or(a, b, log)` appending `'L'` always and `'R'` only if `a` is falsy; return `a or b`.

**Answer:**

```python
def logged_or(a, b, log):
    log.append('L')
    if a:
        return a
    log.append('R')
    return b


def _log_or_left_truthy():
    log = []
    logged_or(1, 0, log)
    return log


def _log_or_left_falsy():
    log = []
    logged_or(0, 0, log)
    return log
```

- `_log_or_left_truthy()  =>  ['L']`
- `_log_or_left_falsy()  =>  ['L', 'R']`

Short-circuit `or` when left is truthy.

### Q194. Intermediate

Write `neither(a, b)` True when both are falsy.

**Answer:**

```python
def neither(a, b):
    return not a and not b
```

- `neither(0, '')  =>  True`
- `neither(1, '')  =>  False`
- `neither(0, 1)  =>  False`

De Morgan: not (a or b).

### Q195. Intermediate

Write `both(a, b)` True when both are truthy.

**Answer:**

```python
def both(a, b):
    return bool(a and b)
```

- `both(1, 2)  =>  True`
- `both(0, 2)  =>  False`
- `both(1, 0)  =>  False`

Coerce the `and` result to bool if you need strict bool output.

### Q196. Advanced

Write `count_truthy(items)` returning how many elements are truthy.

**Answer:**

```python
def count_truthy(items):
    return sum(1 for x in items if x)
```

- `count_truthy([0,1,2,''])  =>  2`
- `count_truthy([])  =>  0`

Generator sum pattern.

### Q197. Basic

Write `parity_bool(n)` returning True iff n is odd (bool result).

**Answer:**

```python
def parity_bool(n):
    return bool(n & 1)
```

- `parity_bool(3)  =>  True`
- `parity_bool(4)  =>  False`

Low bit test.

### Q198. Advanced

Write `at_least_two(a, b, c)` True if two or more args are truthy.

**Answer:**

```python
def at_least_two(a, b, c):
    return sum(bool(x) for x in (a, b, c)) >= 2
```

- `at_least_two(1,1,0)  =>  True`
- `at_least_two(1,0,0)  =>  False`
- `at_least_two(1,1,1)  =>  True`

Count truthy values.

### Q199. Intermediate

Write `unless(condition, value)` returning `value` when condition is falsy, else None.

**Answer:**

```python
def unless(condition, value):
    return value if not condition else None
```

- `unless(0, 'ok')  =>  'ok'`
- `unless(1, 'ok')  =>  None`

Guarded default pattern.

### Q200. Advanced

Write `nand(a, b)` returning `not (a and b)`.

**Answer:**

```python
def nand(a, b):
    return not (a and b)
```

- `nand(1,1)  =>  False`
- `nand(1,0)  =>  True`
- `nand(0,0)  =>  True`

Negated conjunction.

*Section size: 200 questions (Basic 70, Intermediate 74, Advanced 56).*

