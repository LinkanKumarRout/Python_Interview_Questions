## 8. Range (range)

An immutable arithmetic sequence. It stores start, stop, and step. It does not store the expanded values.

### Q1. Basic

What does this print?

```python
print(type(range(3)))
```

**Answer:**

```text
<class 'range'>
```

The built-in `range` constructor returns a `range` object.

### Q2. Basic

What does this print?

```python
print(list(range(3)))
```

**Answer:**

```text
[0, 1, 2]
```

`range(3)` is 0, 1, 2.

### Q3. Basic

What does this print?

```python
print(len(range(3)))
```

**Answer:**

```text
3
```

Length is the number of values generated.

### Q4. Basic

What does this print?

```python
print(range(3).start, range(3).stop, range(3).step)
```

**Answer:**

```text
0 3 1
```

Default start 0, stop 3, step 1.

### Q5. Basic

What does this print?

```python
print(list(range(2, 5)))
```

**Answer:**

```text
[2, 3, 4]
```

Two-argument form: start 2, stop 5 exclusive.

### Q6. Basic

What does this print?

```python
print(range(2, 5).start, range(2, 5).stop)
```

**Answer:**

```text
2 5
```

Attributes reflect the constructor arguments.

### Q7. Basic

What does this print?

```python
print(list(range(0, 10, 2)))
```

**Answer:**

```text
[0, 2, 4, 6, 8]
```

Step 2 yields even numbers below 10.

### Q8. Basic

What does this print?

```python
print(range(0, 10, 2).step)
```

**Answer:**

```text
2
```

Step attribute is 2.

### Q9. Basic

What does this print?

```python
print(list(range(5, 0)))
```

**Answer:**

```text
[]
```

Start >= stop with positive step: empty.

### Q10. Basic

What does this print?

```python
print(len(range(5, 0)))
```

**Answer:**

```text
0
```

Empty range has length 0.

### Q11. Basic

What does this print?

```python
print(list(range(0)))
```

**Answer:**

```text
[]
```

`range(0)` is empty.

### Q12. Basic

What does this print?

```python
print(len(range(0)))
```

**Answer:**

```text
0
```

Length 0.

### Q13. Basic

What does this print?

```python
print(0 in range(3))
```

**Answer:**

```text
True
```

Membership tests without building a list.

### Q14. Basic

What does this print?

```python
print(3 in range(3))
```

**Answer:**

```text
False
```

Stop is exclusive, so 3 is not included.

### Q15. Basic

What does this print?

```python
print(-1 in range(3))
```

**Answer:**

```text
False
```

Negative value not in 0..2.

### Q16. Basic

What does this print?

```python
print(range(3)[0], range(3)[-1])
```

**Answer:**

```text
0 2
```

Indexing works like a sequence.

### Q17. Basic

What does this print?

```python
print(range(3)[1])
```

**Answer:**

```text
1
```

Middle element is 1.

### Q18. Basic

What does this print?

```python
print(list(range(10)[2:5]))
```

**Answer:**

```text
[2, 3, 4]
```

Slicing a range returns another range; list shows 2,3,4.

### Q19. Basic

What does this print?

```python
print(type(range(10)[2:5]))
```

**Answer:**

```text
<class 'range'>
```

Slice of range is still a `range` object.

### Q20. Basic

What does this print?

```python
print(range(10)[2:5].start, range(10)[2:5].stop)
```

**Answer:**

```text
2 5
```

Sliced range has adjusted start/stop.

### Q21. Basic

What does this print?

```python
print(range(3) == range(3))
```

**Answer:**

```text
True
```

Same parameters yield equal ranges.

### Q22. Basic

What does this print?

```python
print(range(3) == range(0, 3))
```

**Answer:**

```text
True
```

Explicit start 0 matches one-argument form.

### Q23. Basic

What does this print?

```python
print(range(0, 5, 2) == range(0, 6, 2))
```

**Answer:**

```text
True
```

Equality compares the generated sequence, not the stop argument alone.

### Q24. Basic

What does this print?

```python
print(list(range(0, 5, 2)), list(range(0, 6, 2)))
```

**Answer:**

```text
[0, 2, 4] [0, 2, 4]
```

Both produce 0, 2, 4.

### Q25. Basic

What does this print?

```python
print(range(3).count(1))
```

**Answer:**

```text
1
```

`count` works on range.

### Q26. Basic

What does this print?

```python
print(range(3).index(1))
```

**Answer:**

```text
1
```

`index` returns position of value.

### Q27. Basic

What does this print?

```python
print(range(3).count(9))
```

**Answer:**

```text
0
```

Absent value count is 0.

### Q28. Basic

What does this print?

```python
print(2 in range(0, 10, 2))
```

**Answer:**

```text
True
```

Even membership.

### Q29. Basic

What does this print?

```python
print(3 in range(0, 10, 2))
```

**Answer:**

```text
False
```

Odd value not in even range.

### Q30. Basic

What does this print?

```python
print(list(range(-3, 0)))
```

**Answer:**

```text
[-3, -2, -1]
```

Negative values are allowed.

### Q31. Basic

What does this print?

```python
print(min(range(5)), max(range(5)))
```

**Answer:**

```text
0 4
```

Min 0 max 4 for `range(5)`.

### Q32. Basic

What does this print?

```python
print(sum(range(4)))
```

**Answer:**

```text
6
```

Sum 0+1+2+3 = 6.

### Q33. Basic

What does this print?

```python
print(bool(range(0)))
```

**Answer:**

```text
False
```

Empty range is falsy.

### Q34. Basic

What does this print?

```python
print(bool(range(1)))
```

**Answer:**

```text
True
```

Non-empty range is truthy.

### Q35. Basic

What does this print?

```python
print(list(reversed(range(3))))
```

**Answer:**

```text
[2, 1, 0]
```

Reversed range yields descending list when materialized.

### Q36. Basic

What does this print?

```python
print(tuple(range(3)))
```

**Answer:**

```text
(0, 1, 2)
```

Tuple constructor consumes range.

### Q37. Basic

What does this print?

```python
print(set(range(3)))
```

**Answer:**

```text
{0, 1, 2}
```

Set of values 0,1,2.

### Q38. Basic

What does this print?

```python
print(0 in range(1000000))
```

**Answer:**

```text
True
```

Huge range membership is still cheap (O(1) arithmetic).

### Q39. Basic

What does this print?

```python
print(999999 in range(1000000))
```

**Answer:**

```text
True
```

Last value is stop minus step.

### Q40. Basic

What does this print?

```python
print(list(range(1, 4)))
```

**Answer:**

```text
[1, 2, 3]
```

1, 2, 3.

### Q41. Basic

What does this print?

```python
print(range(1, 4)[-1])
```

**Answer:**

```text
3
```

Last index value 3.

### Q42. Basic

What does this print?

```python
print(len(range(10, 20)))
```

**Answer:**

```text
10
```

Ten values from 10 through 19.

### Q43. Basic

What does this print?

```python
print(list(range(10, 20, 3)))
```

**Answer:**

```text
[10, 13, 16, 19]
```

10, 13, 16, 19.

### Q44. Basic

What does this print?

```python
print(range(5) < range(6))
```

**Answer:**

```text
TypeError: '<' not supported between instances of 'range' and 'range'
```

Ranges compare lexicographically as sequences.

### Q45. Basic

What does this print?

```python
print(range(3) == [0, 1, 2])
```

**Answer:**

```text
False
```

Range equals list with same elements.

### Q46. Basic

What does this print?

```python
print(range(3) == (0, 1, 2))
```

**Answer:**

```text
False
```

Range equals tuple with same elements.

### Q47. Basic

What does this print?

```python
print(iter(range(2)))
print(next(iter(range(2))))
```

**Answer:**

```text
<range_iterator object at 0x7bc905b4b810>
0
```

`range` is iterable but not itself an iterator; `iter` then `next` yields 0.

### Q48. Basic

What does this print?

```python
r = iter(range(2))
print(next(r), next(r))
```

**Answer:**

```text
0 1
```

Two steps exhaust a length-2 range.

### Q49. Basic

What happens when this runs?

```python
r = iter(range(1))
next(r)
next(r)
```

**Answer:**

```text
StopIteration: 
```

Second `next` on exhausted iterator raises `StopIteration`.

### Q50. Basic

What happens when this runs?

```python
print(hash(range(3)))
```

**Answer:**

```text
-8338477496398685190
```

Range is not hashable.

### Q51. Basic

What happens when this runs?

```python
print({range(3): 0})
```

**Answer:**

```text
{range(0, 3): 0}
```

Unhashable range cannot be a dict key.

### Q52. Basic

What does this print?

```python
print(list(range(3, 3)))
```

**Answer:**

```text
[]
```

Equal start and stop: empty.

### Q53. Basic

What does this print?

```python
print(list(range(3, 3, 1)))
```

**Answer:**

```text
[]
```

Same with explicit step.

### Q54. Basic

What does this print?

```python
print(-5 in range(-3, 3))
```

**Answer:**

```text
False
```

-5 below start.

### Q55. Basic

What does this print?

```python
print(2 in range(-3, 3))
```

**Answer:**

```text
True
```

2 inside interval.

### Q56. Basic

What does this print?

```python
print(list(range(0, 5, 1)))
```

**Answer:**

```text
[0, 1, 2, 3, 4]
```

Step 1 is default.

### Q57. Basic

What does this print?

```python
print(len(range(0, 100, 10)))
```

**Answer:**

```text
10
```

Ten values: 0,10,...,90.

### Q58. Basic

What does this print?

```python
print(range(0, 100, 10)[3])
```

**Answer:**

```text
30
```

Fourth value is 30.

### Q59. Intermediate

What does this print?

```python
print(list(range(2)[0:1]))
```

**Answer:**

```text
[0]
```

Slice length 1.

### Q60. Intermediate

What does this print?

```python
print(list(range(10)[::2]))
```

**Answer:**

```text
[0, 2, 4, 6, 8]
```

Every other value.

### Q61. Intermediate

What does this print?

```python
print(list(range(10)[1::2]))
```

**Answer:**

```text
[1, 3, 5, 7, 9]
```

Odd indices from 1.

### Q62. Intermediate

What does this print?

```python
print(list(range(10)[::-1]))
```

**Answer:**

```text
[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

Reversed via slice.

### Q63. Intermediate

What does this print?

```python
print(list(range(10)[5:2]))
```

**Answer:**

```text
[]
```

Positive step with start > stop: empty.

### Q64. Intermediate

What does this print?

```python
print(list(range(10)[2:10:3]))
```

**Answer:**

```text
[2, 5, 8]
```

Stepped slice.

### Q65. Basic

What does this print?

```python
print(range(4).index(3))
```

**Answer:**

```text
3
```

Last index 3 holds value 3.

### Q66. Basic

What does this print?

```python
print(range(4).count(0))
```

**Answer:**

```text
1
```

0 appears once.

### Q67. Basic

What does this print?

```python
print(0 == range(0))
```

**Answer:**

```text
False
```

Range compares equal to other sequences with same elements.

### Q68. Basic

What does this print?

```python
print(range(2) != range(3))
```

**Answer:**

```text
True
```

Different lengths differ.

### Q69. Basic

What does this print?

```python
print(list(map(lambda x: x * 2, range(3))))
```

**Answer:**

```text
[0, 2, 4]
```

Map over range.

### Q70. Basic

What does this print?

```python
print([x for x in range(3)])
```

**Answer:**

```text
[0, 1, 2]
```

Comprehension over range.

### Q71. Basic

What does this print?

```python
print(len(list(range(1000000))))
```

**Answer:**

```text
1000000
```

Materializing huge range is expensive; `len(range(...))` is not.

### Q72. Basic

What does this print?

```python
print(len(range(1000000)))
```

**Answer:**

```text
1000000
```

Length computed without allocating all ints.

### Q73. Intermediate

What does this print?

```python
print(list(range(5, 0, -1)))
```

**Answer:**

```text
[5, 4, 3, 2, 1]
```

Negative step counts down.

### Q74. Intermediate

What does this print?

```python
print(list(range(5, 0, -2)))
```

**Answer:**

```text
[5, 3, 1]
```

Down by twos.

### Q75. Intermediate

What does this print?

```python
print(len(range(5, 0, -1)))
```

**Answer:**

```text
5
```

Five values 5 down to 1.

### Q76. Intermediate

What does this print?

```python
print(range(5, 0, -1).step)
```

**Answer:**

```text
-1
```

Step is -1.

### Q77. Intermediate

What does this print?

```python
print(list(range(0, 5, -1)))
```

**Answer:**

```text
[]
```

Positive start, negative step, stop below: empty when start < stop.

### Q78. Intermediate

What does this print?

```python
print(list(range(10, 5, -1)))
```

**Answer:**

```text
[10, 9, 8, 7, 6]
```

10, 9, 8, 7, 6.

### Q79. Intermediate

What does this print?

```python
print(6 in range(10, 5, -1))
```

**Answer:**

```text
True
```

6 is included.

### Q80. Intermediate

What does this print?

```python
print(5 in range(10, 5, -1))
```

**Answer:**

```text
False
```

Stop 5 exclusive at bottom.

### Q81. Intermediate

What does this print?

```python
print(range(10, 5, -1)[0])
```

**Answer:**

```text
10
```

First element 10.

### Q82. Intermediate

What does this print?

```python
print(range(10, 5, -1)[-1])
```

**Answer:**

```text
6
```

Last element 6.

### Q83. Intermediate

What does this print?

```python
print(list(range(10, 5, -1)[1:3]))
```

**Answer:**

```text
[9, 8]
```

Slice of descending range.

### Q84. Intermediate

What does this print?

```python
print(type(range(10, 5, -1)[1:3]))
```

**Answer:**

```text
<class 'range'>
```

Still a range object.

### Q85. Intermediate

What does this print?

```python
print(range(10, 5, -1).index(8))
```

**Answer:**

```text
2
```

Index of 8 in descending sequence.

### Q86. Intermediate

What does this print?

```python
print(range(10, 5, -1).count(8))
```

**Answer:**

```text
1
```

Single occurrence.

### Q87. Intermediate

What does this print?

```python
print(range(0, -5, -1) == range(0, -5, -1))
```

**Answer:**

```text
True
```

Negative-bound ranges compare equal to themselves.

### Q88. Intermediate

What does this print?

```python
print(list(range(0, -5, -1)))
```

**Answer:**

```text
[0, -1, -2, -3, -4]
```

0, -1, -2, -3, -4.

### Q89. Intermediate

What does this print?

```python
print(range(0, 5, 2) == range(0, 6, 2))
```

**Answer:**

```text
True
```

Sequence equality: same values even when stop differs.

### Q90. Intermediate

What does this print?

```python
print(range(1, 6, 2) == range(1, 7, 2))
```

**Answer:**

```text
True
```

Sequence equality: same values even when stop differs.

### Q91. Intermediate

What does this print?

```python
print(range(10, 0, -2) == range(10, -1, -2))
```

**Answer:**

```text
False
```

Sequence equality: same values even when stop differs.

### Q92. Intermediate

What does this print?

```python
print(range(3) == range(0, 3, 1))
```

**Answer:**

```text
True
```

Sequence equality: same values even when stop differs.

### Q93. Intermediate

What does this print?

```python
print(range(-2, 2) == range(-2, 2, 1))
```

**Answer:**

```text
True
```

Sequence equality: same values even when stop differs.

### Q94. Intermediate

What does this print?

```python
print(range(0, 5, 2) == range(0, 5, 3))
```

**Answer:**

```text
False
```

Different sequences are unequal.

### Q95. Intermediate

What does this print?

```python
print(range(3) == range(4))
```

**Answer:**

```text
False
```

Different sequences are unequal.

### Q96. Intermediate

What does this print?

```python
print(range(1, 4) == range(1, 5))
```

**Answer:**

```text
False
```

Different sequences are unequal.

### Q97. Intermediate

What does this print?

```python
print(0 in range(0, 10, 2))
```

**Answer:**

```text
True
```

Even start.

### Q98. Intermediate

What does this print?

```python
print(1 in range(0, 10, 2))
```

**Answer:**

```text
False
```

Odd not in even step.

### Q99. Intermediate

What does this print?

```python
print(range(10).index(5))
```

**Answer:**

```text
5
```

Value equals index here.

### Q100. Intermediate

What does this print?

```python
print(range(10).count(5))
```

**Answer:**

```text
1
```

Present exactly once in these examples.

### Q101. Intermediate

What does this print?

```python
print(range(2, 12, 2).index(6))
```

**Answer:**

```text
2
```

Value 6 at index 2: 2,4,6.

### Q102. Intermediate

What does this print?

```python
print(range(2, 12, 2).count(6))
```

**Answer:**

```text
1
```

Present exactly once in these examples.

### Q103. Intermediate

What does this print?

```python
print(range(10, 0, -2).index(6))
```

**Answer:**

```text
2
```

Descending: 10,8,6 at index 2.

### Q104. Intermediate

What does this print?

```python
print(range(10, 0, -2).count(6))
```

**Answer:**

```text
1
```

Present exactly once in these examples.

### Q105. Intermediate

What does this print?

```python
it = iter(range(3))
print(list(it))
```

**Answer:**

```text
[0, 1, 2]
```

Iterator consumes the range once.

### Q106. Intermediate

What does this print?

```python
it = iter(range(3))
print(list(it), list(it))
```

**Answer:**

```text
[0, 1, 2] []
```

Second pass on same iterator is empty.

### Q107. Intermediate

What does this print?

```python
print(type(iter(range(2))))
```

**Answer:**

```text
<class 'range_iterator'>
```

Iterator type is `range_iterator` in CPython.

### Q108. Advanced

What does this print?

```python
r = range(3)
print(hasattr(r, '__next__'))
```

**Answer:**

```text
False
```

Range lacks `__next__`; iterator has it.

### Q109. Advanced

What does this print?

```python
print(next(iter(range(1)), 99))
```

**Answer:**

```text
0
```

Single element: next returns 0.

### Q110. Intermediate

What does this print?

```python
print(list(range(20)[5:15:2]))
```

**Answer:**

```text
[5, 7, 9, 11, 13]
```

Sliced arithmetic progression.

### Q111. Intermediate

What does this print?

```python
print(range(20)[5:15:2].start)
```

**Answer:**

```text
5
```

New start from slice.

### Q112. Intermediate

What does this print?

```python
print(range(20)[5:15:2].step)
```

**Answer:**

```text
2
```

Step preserved.

### Q113. Intermediate

What does this print?

```python
print(list(range(20)[::5]))
```

**Answer:**

```text
[0, 5, 10, 15]
```

Every fifth.

### Q114. Intermediate

What does this print?

```python
print(list(range(20)[::-3]))
```

**Answer:**

```text
[19, 16, 13, 10, 7, 4, 1]
```

Negative step slice on positive range.

### Q115. Advanced

What does this print?

```python
print(list(range(10, 0, -1)[2:8]))
```

**Answer:**

```text
[8, 7, 6, 5, 4, 3]
```

Slice descending range.

### Q116. Advanced

What does this print?

```python
print(range(10, 0, -1)[2:8].step)
```

**Answer:**

```text
-1
```

Slice may flip effective direction.

### Q117. Advanced

What does this print?

```python
print(777777 in range(0, 10**9, 777777))
```

**Answer:**

```text
True
```

Grid membership via division.

### Q118. Advanced

What does this print?

```python
print(len(range(10**9)))
```

**Answer:**

```text
1000000000
```

Length formula, no allocation.

### Q119. Advanced

What does this print?

```python
print(range(10**9)[10**9 - 1])
```

**Answer:**

```text
999999999
```

Last element is stop - step.

### Q120. Advanced

What does this print?

```python
import sys
print(sys.getsizeof(range(10**9)) < 1000)
```

**Answer:**

```text
True
```

Range stores only start/stop/step.

### Q121. Basic

Write `paginate(n, page_size, page)` returning a list of item indices on that zero-based page. Page 0 is the first chunk; empty if page is out of range.

**Answer:**

```python
def paginate(n, page_size, page):
    start = page * page_size
    if start >= n or page_size <= 0:
        return []
    return list(range(start, min(start + page_size, n)))
```

- `paginate(10, 3, 0)  =>  [0, 1, 2]`
- `paginate(10, 3, 3)  =>  [9]`
- `paginate(10, 3, 4)  =>  []`

Use `range(start, stop)` for index windows.

### Q122. Intermediate

Write `series_sum(n)` returning the sum of integers from 0 through `n` inclusive using `range`.

**Answer:**

```python
def series_sum(n):
    return sum(range(n + 1))
```

- `series_sum(0)  =>  0`
- `series_sum(4)  =>  10`
- `series_sum(10)  =>  55`

Classic arithmetic series; `sum(range(n+1))` is O(n) additions but O(1) memory for the range object.

### Q123. Advanced

Write `in_range(r, value)` that returns whether `value` is in arithmetic progression `r` (a `range`) without converting `r` to a list.

**Answer:**

```python
def in_range(r, value):
    if r.step == 0:
        return False
    if r.step > 0:
        if value < r.start or value >= r.stop:
            return False
    else:
        if value > r.start or value <= r.stop:
            return False
    return (value - r.start) % r.step == 0
```

- `in_range(range(0, 10, 2), 4)  =>  True`
- `in_range(range(0, 10, 2), 5)  =>  False`
- `in_range(range(10, 0, -1), 1)  =>  True`
- `in_range(range(10, 0, -1), 0)  =>  False`

Mirror the logic CPython uses: bounds check then `(value - start) % step == 0` with step sign handled.

### Q124. Basic

What does this print?

```python
print(list(range(-2, 2)))
```

**Answer:**

```text
[-2, -1, 0, 1]
```

Four values crossing zero.

### Q125. Intermediate

What does this print?

```python
print(list(range(100)[90:]))
```

**Answer:**

```text
[90, 91, 92, 93, 94, 95, 96, 97, 98, 99]
```

Tail slice.

### Q126. Intermediate

What does this print?

```python
print(list(range(100)[:5]))
```

**Answer:**

```text
[0, 1, 2, 3, 4]
```

Head slice.

### Q127. Intermediate

What does this print?

```python
print(range(7)[3:3])
```

**Answer:**

```text
range(3, 3)
```

Empty slice object; length 0.

### Q128. Intermediate

What does this print?

```python
print(len(range(7)[3:3]))
```

**Answer:**

```text
0
```

Zero length.

### Q129. Intermediate

What happens when this runs?

```python
print(range(3).index(9))
```

**Answer:**

```text
ValueError: 9 is not in range
```

Missing value raises `ValueError`.

### Q130. Intermediate

What does this print?

```python
print(range(-2, 2)[0])
```

**Answer:**

```text
-2
```

First value -2.

### Q131. Intermediate

What does this print?

```python
print(1 in range(-2, 2))
```

**Answer:**

```text
True
```

1 is between -2 and 2.

### Q132. Intermediate

What does this print?

```python
print(7 in range(4, 8))
```

**Answer:**

```text
True
```

7 is included; stop 8 is not.

### Q133. Intermediate

What does this print?

```python
print(range(4, 8).index(6))
```

**Answer:**

```text
2
```

6 sits at index 2.

### Q134. Intermediate

What does this print?

```python
print(range(4, 8).count(5))
```

**Answer:**

```text
1
```

Single 5.

### Q135. Intermediate

What does this print?

```python
print(list(range(15)[3:12:4]))
```

**Answer:**

```text
[3, 7, 11]
```

3,7,11.

### Q136. Intermediate

What does this print?

```python
print(range(15)[3:12:4].start)
```

**Answer:**

```text
3
```

Sliced start is 3.

### Q137. Intermediate

What does this print?

```python
print(len(range(15)[3:12:4]))
```

**Answer:**

```text
3
```

Three values in the slice.

### Q138. Intermediate

What does this print?

```python
print(7 in range(15)[3:12:4])
```

**Answer:**

```text
True
```

7 is in the sub-range.

### Q139. Intermediate

What does this print?

```python
print(8 in range(15)[3:12:4])
```

**Answer:**

```text
False
```

8 is not on step 4 from 3.

### Q140. Intermediate

What does this print?

```python
print(range(2, 8) == range(2, 9, 1))
```

**Answer:**

```text
False
```

Same 2..7 sequence.

### Q141. Advanced

What happens when this runs?

```python
print(list(range(1, 1, 0)))
```

**Answer:**

```text
ValueError: range() arg 3 must not be zero
```

Zero step raises `ValueError` at construction.

### Q142. Advanced

What does this print?

```python
print(0 in range(0, 0))
```

**Answer:**

```text
False
```

Empty: nothing inside.

### Q143. Advanced

What does this print?

```python
print(bool(range(0, 0)))
```

**Answer:**

```text
False
```

Empty range falsy.

### Q144. Advanced

What does this print?

```python
print(range(5) == range(5, 0))
```

**Answer:**

```text
False
```

Empty vs non-empty false.

### Q145. Advanced

What does this print?

```python
print(list(zip(range(3), 'abc')))
```

**Answer:**

```text
[(0, 'a'), (1, 'b'), (2, 'c')]
```

Zip with range.

### Q146. Advanced

What does this print?

```python
print(list(enumerate(range(3))))
```

**Answer:**

```text
[(0, 0), (1, 1), (2, 2)]
```

Enumerate pairs.

### Q147. Advanced

What does this print?

```python
print(all(x < 3 for x in range(3)))
```

**Answer:**

```text
True
```

All elements below stop.

### Q148. Advanced

What does this print?

```python
print(any(x > 2 for x in range(3)))
```

**Answer:**

```text
False
```

No element above 2.

### Q149. Advanced

What does this print?

```python
print(sorted(range(3), reverse=True))
```

**Answer:**

```text
[2, 1, 0]
```

Sorted descending list.

### Q150. Advanced

What does this print?

```python
print(list(range(10))[::10])
```

**Answer:**

```text
[0]
```

Single element 0.

### Q151. Advanced

What does this print?

```python
print(range(10)[::10].stop)
```

**Answer:**

```text
10
```

Sliced stop for step 10.

### Q152. Advanced

What does this print?

```python
print(range(4, 8, 2).index(6))
```

**Answer:**

```text
1
```

6 at index 1.

### Q153. Advanced

What does this print?

```python
print(len(range(-10, 10, 5)))
```

**Answer:**

```text
4
```

Values -10,-5,0,5 — length 4.

### Q154. Advanced

What does this print?

```python
print(list(range(-10, 10, 5)))
```

**Answer:**

```text
[-10, -5, 0, 5]
```

Confirm values.

### Q155. Advanced

What does this print?

```python
print(2 in range(3) and 3 not in range(3))
```

**Answer:**

```text
True
```

2 included, stop 3 excluded.

### Q156. Advanced

What does this print?

```python
print(list(range(1)[-1:]))
```

**Answer:**

```text
[0]
```

Slice of length-1 range.

### Q157. Advanced

What does this print?

```python
print(range(100)[50] + range(100)[51])
```

**Answer:**

```text
101
```

Two index reads sum to 101.

### Q158. Advanced

What does this print?

```python
print(min(range(5, 10)), max(range(5, 10)))
```

**Answer:**

```text
5 9
```

5 and 9.

### Q159. Advanced

What does this print?

```python
print(sum(range(1, 5)))
```

**Answer:**

```text
10
```

1+2+3+4=10.

### Q160. Advanced

What does this print?

```python
print(len(range(1, 5)))
```

**Answer:**

```text
4
```

Four numbers.

### Q161. Advanced

What does this print?

```python
print(range(0, 1000, 100).index(500))
```

**Answer:**

```text
5
```

Index 5.

### Q162. Advanced

What does this print?

```python
print(range(0, 1000, 100).count(500))
```

**Answer:**

```text
1
```

Count 1.

### Q163. Advanced

What does this print?

```python
print(list(range(0, 1000, 100))[5])
```

**Answer:**

```text
500
```

Same value via list materialization.

### Q164. Advanced

What does this print?

```python
print(10**6 in range(0, 10**7, 10**6))
```

**Answer:**

```text
True
```

Large arithmetic membership.

### Q165. Advanced

What does this print?

```python
print(len(range(0, 10**7, 10**6)))
```

**Answer:**

```text
10
```

Ten values.

### Q166. Advanced

What does this print?

```python
print(range(0, 10**7, 10**6)[-1])
```

**Answer:**

```text
9000000
```

Last grid point.

### Q167. Advanced

What does this print?

```python
print(list(range(3)) + list(range(3, 6)))
```

**Answer:**

```text
[0, 1, 2, 3, 4, 5]
```

Concat lists from ranges.

### Q168. Advanced

What does this print?

```python
print([*range(3), *range(3, 6)])
```

**Answer:**

```text
[0, 1, 2, 3, 4, 5]
```

Unpack ranges into list.

### Q169. Advanced

What does this print?

```python
print(set(range(5)) & set(range(3, 8)))
```

**Answer:**

```text
{3, 4}
```

Intersection 3,4.

### Q170. Advanced

What does this print?

```python
print(set(range(5)) | set(range(3, 8)))
```

**Answer:**

```text
{0, 1, 2, 3, 4, 5, 6, 7}
```

Union 0..7.

### Q171. Advanced

What does this print?

```python
print(all(i == v for i, v in enumerate(range(5))))
```

**Answer:**

```text
True
```

Index equals value for `range(5)`.

### Q172. Advanced

What does this print?

```python
it = iter(range(2))
print(list(it))
print(list(iter(range(2))))
```

**Answer:**

```text
[0, 1]
[0, 1]
```

First iterator exhausts; a new `iter(range(2))` works again.

### Q173. Advanced

What does this print?

```python
print(2 in range(5, 1, -1))
```

**Answer:**

```text
True
```

2 is still included before stop 1.

### Q174. Advanced

What does this print?

```python
print(range(0, 3) == range(0, 4, 1))
```

**Answer:**

```text
False
```

Same 0,1,2 despite different stop.

### Q175. Advanced

What does this print?

```python
print(list(range(10, 20)[5]))
```

**Answer:**

```text
TypeError: 'int' object is not iterable
```

Index 5 yields 15.

### Q176. Advanced

What does this print?

```python
print(1 == range(1))
```

**Answer:**

```text
False
```

A one-element range compares equal to its sole value.

### Q177. Advanced

What does this print?

```python
print(2 == range(2))
```

**Answer:**

```text
False
```

A length-2 range does not equal the int 2.

### Q178. Advanced

What does this print?

```python
print(list(range(5)[3::-1]))
```

**Answer:**

```text
[3, 2, 1, 0]
```

Partial reverse slice of a small range.

### Q179. Advanced

What does this print?

```python
print(7 in range(10, 0, -3))
```

**Answer:**

```text
True
```

7 lies on the downward grid.

### Q180. Advanced

What does this print?

```python
print(range(10, 0, -3).index(4))
```

**Answer:**

```text
2
```

4 is at index 2.

### Q181. Advanced

What does this print?

```python
print(type(range(10, 0, -3)[1:]))
```

**Answer:**

```text
<class 'range'>
```

Slicing a descending range stays a range.

### Q182. Intermediate

What does this print?

```python
r = range(0, 10, 3)
print(r.index(0), r.index(9), r.count(3))
```

**Answer:**

```text
0 3 1
```

`index` and `count` use the arithmetic progression. 3 is not on this grid, so its count is 0. 9 is the last value.

### Q183. Intermediate

What happens when this runs?

```python
print(range(0, 10, 3).index(2))
```

**Answer:**

```text
ValueError: 2 is not in range
```

Values off the grid raise `ValueError` from `index`.

### Q184. Advanced

What does this print?

```python
print(range(10**18)[10**18 - 1])
```

**Answer:**

```text
999999999999999999
```

Indexing a huge range does not build a list. The last value is computed.

### Q185. Advanced

What does this print?

```python
r = range(5, 0, -1)
print(r.start, r.stop, r.step, list(r))
```

**Answer:**

```text
5 0 -1 [5, 4, 3, 2, 1]
```

Attributes keep the original arguments, including a negative step.

### Q186. Advanced

What does this print?

```python
print(range(0, 5, 2) == range(0, 6, 2), range(0, 5, 2) == range(0, 7, 2))
```

**Answer:**

```text
True False
```

Range equality compares the sequence of values. `range(0, 5, 2)` and `range(0, 6, 2)` both yield 0, 2, 4. `range(0, 7, 2)` also yields 6, so it is not equal.

### Q187. Intermediate

What does this print?

```python
print(range(3)[::-1] == range(2, -1, -1))
```

**Answer:**

```text
True
```

A reversed slice is still a range, and it equals the explicit descending range.

### Q188. Basic

What does this print?

```python
it = iter(range(3))
print(next(it), next(it))
```

**Answer:**

```text
0 1
```

`range` is iterable but it is not an iterator. `iter` produces the iterator.

### Q189. Intermediate

What does this print?

```python
r = range(3)
print(list(r), list(r))
```

**Answer:**

```text
[0, 1, 2] [0, 1, 2]
```

A range can be iterated more than once. It does not get exhausted.

### Q190. Advanced

What does this print?

```python
print(range(2**100).count(0))
```

**Answer:**

```text
1
```

`count` is O(1). It does not scan `2**100` values. 0 occurs once.

### Q191. Advanced

What does this print?

```python
import sys
print(sys.getsizeof(range(10**18)) < 200)
```

**Answer:**

```text
True
```

A range object stores three integers, not the expanded sequence. Its size stays small.

### Q192. Intermediate

What happens when this runs?

```python
print(hash(range(3)))
```

**Answer:**

```text
-8338477496398685190
```

`range` is not hashable.

### Q193. Intermediate

What does this print?

```python
print(range(0) == range(5, 5) == range(3, 1))
```

**Answer:**

```text
True
```

Empty ranges compare equal even when their stored endpoints differ.

### Q194. Advanced

What does this print?

```python
r = range(1, 20, 3)
print(10 in r, 4 in r)
```

**Answer:**

```text
True True
```

Membership tests the arithmetic condition in constant time. 10 is not on the grid starting at 1 with step 3. 4 is.

### Q195. Intermediate

What does this print?

```python
print(range(10)[2:8:2])
```

**Answer:**

```text
range(2, 8, 2)
```

Slicing a range returns a range. Printing it shows the computed start, stop, and step.

### Q196. Basic

What does this print?

```python
for i in range(2):
    print(i)
```

**Answer:**

```text
0
1
```

A for-loop consumes the range values.

### Q197. Advanced

What does this print?

```python
print(sum(range(1, 5)) == 10)
```

**Answer:**

```text
True
```

Summing a small range adds 1+2+3+4.

### Q198. Intermediate

What does this print?

```python
a = range(3)
b = range(3)
print(a == b, a is b)
```

**Answer:**

```text
True False
```

Equal ranges need not be the same object.

### Q199. Advanced

What does this print?

```python
print(range(0, 10, 2)[:0] == range(0))
```

**Answer:**

```text
True
```

A zero-length slice is an empty range, and empty ranges compare equal.

### Q200. Intermediate

Write `covers(value, start, stop, step=1)` that reports whether `value` is produced by that range, without building a list.

**Answer:**

```python
def covers(value, start, stop, step=1):
    return value in range(start, stop, step)
```

- `covers(4, 0, 10, 2)  =>  True`
- `covers(3, 0, 10, 2)  =>  False`
- `covers(5, 10, 0, -1)  =>  True`

The `in` operator on a range is an arithmetic test.

*Section size: 200 questions (Basic 70, Intermediate 72, Advanced 58).*

