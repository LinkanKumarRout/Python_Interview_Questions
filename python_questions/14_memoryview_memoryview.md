## 14. Memoryview (memoryview)

A view onto an object that supports the buffer protocol, without copying the bytes.

### Q1. Basic

What does this print?

```python
b = bytearray(b'abc')
v = memoryview(b)
print(v[0])
```

**Answer:**

```text
97
```

Index returns int.

### Q2. Basic

What does this print?

```python
b = bytearray(b'abc')
v = memoryview(b)
v[0] = 65
print(b[0])
```

**Answer:**

```text
65
```

Writable view mutates buffer.

### Q3. Basic

What does this print?

```python
v = memoryview(b'abc')
print(v.readonly)
```

**Answer:**

```text
True
```

Bytes view is readonly.

### Q4. Basic

What does this print?

```python
v = memoryview(b'abc')
print(v[1:3])
```

**Answer:**

```text
<memory at 0x7bc905c90a00>
```

Slice is another memoryview.

### Q5. Basic

What does this print?

```python
v = memoryview(b'abc')
print(type(v[1:3]))
```

**Answer:**

```text
<class 'memoryview'>
```

Sub-view type memoryview.

### Q6. Basic

What does this print?

```python
v = memoryview(b'abc')
print(list(v))
```

**Answer:**

```text
[97, 98, 99]
```

Iteration as ints.

### Q7. Basic

What does this print?

```python
v = memoryview(b'abc')
print(v.tobytes())
```

**Answer:**

```text
b'abc'
```

Copy to bytes.

### Q8. Basic

What does this print?

```python
v = memoryview(b'abc')
print(v.nbytes)
```

**Answer:**

```text
3
```

Byte size of view.

### Q9. Basic

What does this print?

```python
v = memoryview(b'abc')
print(v.itemsize)
```

**Answer:**

```text
1
```

Item size for B format is 1.

### Q10. Basic

What does this print?

```python
v = memoryview(b'abc')
print(v.format)
```

**Answer:**

```text
B
```

Default format unsigned byte.

### Q11. Basic

What does this print?

```python
v = memoryview(b'abc')
print(v.shape)
```

**Answer:**

```text
(3,)
```

1-D shape is length tuple.

### Q12. Basic

What does this print?

```python
v = memoryview(b'abc')
print(v.strides)
```

**Answer:**

```text
(1,)
```

Stride equals itemsize here.

### Q13. Basic

What does this print?

```python
v = memoryview(b'abc')
print(v.contiguous)
```

**Answer:**

```text
True
```

Fresh bytes buffer contiguous.

### Q14. Basic

What does this print?

```python
v = memoryview(b'abc')
print(len(v))
```

**Answer:**

```text
3
```

Len counts elements.

### Q15. Intermediate

What does this print?

```python
ba = bytearray(b'0123456789')
v = memoryview(ba)[2:7]
print(v.tobytes())
```

**Answer:**

```text
b'23456'
```

Slice shares storage.

### Q16. Intermediate

What does this print?

```python
ba = bytearray(b'0123456789')
v = memoryview(ba)[2:7]
v[0] = ord('X')
print(ba[2])
```

**Answer:**

```text
88
```

Mutate through slice view.

### Q17. Intermediate

What does this print?

```python
v = memoryview(b'\x01\x00\x02\x00')
print(list(v.cast('H')))
```

**Answer:**

```text
[1, 2]
```

Cast to unsigned short pairs.

### Q18. Intermediate

What happens when this runs?

```python
v = memoryview(b'abc')
try:
    v[0] = 1
except Exception as e:
    print(type(e).__name__)
```

**Answer:**

```text
TypeError
```

Readonly rejects assignment.

### Q19. Intermediate

What does this print?

```python
v = memoryview(b'abc')
v.release()
print('released')
```

**Answer:**

```text
released
```

Release frees view.

### Q20. Intermediate

What happens when this runs?

```python
v = memoryview(b'abc')
v.release()
try:
    len(v)
except Exception as e:
    print(type(e).__name__)
```

**Answer:**

```text
ValueError
```

Use after release raises.

### Q21. Intermediate

What does this print?

```python
import array
a = array.array('i', [1,2,3])
v = memoryview(a)
print(v.format, v.itemsize, list(v))
```

**Answer:**

```text
i 4 [1, 2, 3]
```

Array buffer exposes typed format.

### Q22. Intermediate

What does this print?

```python
import array
a = array.array('H', [1,2,3])
v = memoryview(a)
print(v.shape, v.strides, list(v))
```

**Answer:**

```text
(3,) (2,) [1, 2, 3]
```

H format has itemsize 2.

### Q23. Intermediate

What does this print?

```python
v = memoryview(b'abcd')
print(v.cast('I')[0])
```

**Answer:**

```text
1684234849
```

Cast to unsigned int word.

### Q24. Intermediate

What does this print?

```python
v = memoryview(bytearray(b'xyz'))
print(v.readonly)
```

**Answer:**

```text
False
```

Bytearray view writable.

### Q25. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.obj)
```

**Answer:**

```text
b'abc'
```

Underlying object exposed.

### Q26. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.tolist())
```

**Answer:**

```text
[97, 98, 99]
```

tolist like list(v).

### Q27. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(bytes(v))
```

**Answer:**

```text
b'abc'
```

bytes() copies via buffer protocol.

### Q28. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(bytearray(v))
```

**Answer:**

```text
bytearray(b'abc')
```

bytearray() copies mutable.

### Q29. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.hex())
```

**Answer:**

```text
616263
```

Hex of view bytes.

### Q30. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.nbytes == len(v))
```

**Answer:**

```text
True
```

nbytes equals len for B format.

### Q31. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.ndim)
```

**Answer:**

```text
1
```

Number of dimensions.

### Q32. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.itemsize * v.shape[0] == v.nbytes)
```

**Answer:**

```text
True
```

Size invariant.

### Q33. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.c_contiguous, v.f_contiguous)
```

**Answer:**

```text
True True
```

Contiguity flags.

### Q34. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.readonly, v.contiguous)
```

**Answer:**

```text
True True
```

Readonly and contiguous.

### Q35. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v[0], v[-1])
```

**Answer:**

```text
97 99
```

First and last index.

### Q36. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(list(v[0:2]))
```

**Answer:**

```text
[97, 98]
```

Slice list.

### Q37. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(list(reversed(v)))
```

**Answer:**

```text
[99, 98, 97]
```

Reversed iteration.

### Q38. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(any(x == ord('b') for x in v))
```

**Answer:**

```text
True
```

Any membership via iterate.

### Q39. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(all(x < 256 for x in v))
```

**Answer:**

```text
True
```

All bytes less 256.

### Q40. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(sum(v))
```

**Answer:**

```text
294
```

Sum ints.

### Q41. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(min(v), max(v))
```

**Answer:**

```text
97 99
```

Min max over view.

### Q42. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.tobytes() == b'abc')
```

**Answer:**

```text
True
```

Tobytes equals original bytes.

### Q43. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(memoryview(v).tobytes())
```

**Answer:**

```text
b'abc'
```

View of view copies same data.

### Q44. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('B').tobytes())
```

**Answer:**

```text
b'abc'
```

Cast to same format copies.

### Q45. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('c').tobytes())
```

**Answer:**

```text
b'abc'
```

Cast to signed char format.

### Q46. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('b').tobytes())
```

**Answer:**

```text
b'abc'
```

Cast to signed byte format.

### Q47. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('B').tolist())
```

**Answer:**

```text
[97, 98, 99]
```

Cast B tolist.

### Q48. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('b').tolist())
```

**Answer:**

```text
[97, 98, 99]
```

Cast b tolist.

### Q49. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('c').tolist())
```

**Answer:**

```text
[b'a', b'b', b'c']
```

Cast c tolist.

### Q50. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('B').hex())
```

**Answer:**

```text
616263
```

Cast hex.

### Q51. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('b').hex())
```

**Answer:**

```text
616263
```

Cast b hex.

### Q52. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('c').hex())
```

**Answer:**

```text
616263
```

Cast c hex.

### Q53. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('B').nbytes)
```

**Answer:**

```text
3
```

Cast nbytes.

### Q54. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('b').nbytes)
```

**Answer:**

```text
3
```

Cast b nbytes.

### Q55. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('c').nbytes)
```

**Answer:**

```text
3
```

Cast c nbytes.

### Q56. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('B').readonly)
```

**Answer:**

```text
True
```

Cast inherits readonly flag.

### Q57. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('b').readonly)
```

**Answer:**

```text
True
```

Cast b readonly.

### Q58. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('c').readonly)
```

**Answer:**

```text
True
```

Cast c readonly.

### Q59. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('B').format)
```

**Answer:**

```text
B
```

Cast format B.

### Q60. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('b').format)
```

**Answer:**

```text
b
```

Cast format b.

### Q61. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('c').format)
```

**Answer:**

```text
c
```

Cast format c.

### Q62. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('B').itemsize)
```

**Answer:**

```text
1
```

Cast itemsize.

### Q63. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('b').itemsize)
```

**Answer:**

```text
1
```

Cast b itemsize.

### Q64. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('c').itemsize)
```

**Answer:**

```text
1
```

Cast c itemsize.

### Q65. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('B').shape)
```

**Answer:**

```text
(3,)
```

Cast shape.

### Q66. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('b').shape)
```

**Answer:**

```text
(3,)
```

Cast b shape.

### Q67. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('c').shape)
```

**Answer:**

```text
(3,)
```

Cast c shape.

### Q68. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('B').strides)
```

**Answer:**

```text
(1,)
```

Cast strides.

### Q69. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('b').strides)
```

**Answer:**

```text
(1,)
```

Cast b strides.

### Q70. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('c').strides)
```

**Answer:**

```text
(1,)
```

Cast c strides.

### Q71. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('B').contiguous)
```

**Answer:**

```text
True
```

Cast contiguous.

### Q72. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('b').contiguous)
```

**Answer:**

```text
True
```

Cast b contiguous.

### Q73. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('c').contiguous)
```

**Answer:**

```text
True
```

Cast c contiguous.

### Q74. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('B').c_contiguous)
```

**Answer:**

```text
True
```

Cast c_contiguous.

### Q75. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('b').c_contiguous)
```

**Answer:**

```text
True
```

Cast b c_contiguous.

### Q76. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('c').c_contiguous)
```

**Answer:**

```text
True
```

Cast c c_contiguous.

### Q77. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('B').f_contiguous)
```

**Answer:**

```text
True
```

Cast f_contiguous.

### Q78. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('b').f_contiguous)
```

**Answer:**

```text
True
```

Cast b f_contiguous.

### Q79. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('c').f_contiguous)
```

**Answer:**

```text
True
```

Cast c f_contiguous.

### Q80. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('B').ndim)
```

**Answer:**

```text
1
```

Cast ndim.

### Q81. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('b').ndim)
```

**Answer:**

```text
1
```

Cast b ndim.

### Q82. Intermediate

What does this print?

```python
v = memoryview(b'abc')
print(v.cast('c').ndim)
```

**Answer:**

```text
1
```

Cast c ndim.

### Q83. Advanced

What does this print?

```python
import array
a = array.array('d', [1.5, 2.5])
v = memoryview(a)
print(v.format, list(v))
```

**Answer:**

```text
d [1.5, 2.5]
```

Double array format.

### Q84. Advanced

What does this print?

```python
import array
a = array.array('f', [1.5, 2.5])
v = memoryview(a)
print(v.itemsize, len(v))
```

**Answer:**

```text
4 2
```

Float array itemsize 4.

### Q85. Advanced

What does this print?

```python
import array
a = array.array('q', [1,2,3])
v = memoryview(a)
print(v.itemsize, v.shape)
```

**Answer:**

```text
8 (3,)
```

Long long array view.

### Q86. Advanced

What does this print?

```python
import array
a = array.array('l', [1,2,3])
v = memoryview(a)
print(v.strides, v.nbytes)
```

**Answer:**

```text
(8,) 24
```

Long array strides.

### Q87. Advanced

What does this print?

```python
import array
a = array.array('I', [1,2,3])
v = memoryview(a)
print(list(v.cast('B')))
```

**Answer:**

```text
[1, 0, 0, 0, 2, 0, 0, 0, 3, 0, 0, 0]
```

Unpack unsigned int to bytes.

### Q88. Advanced

What does this print?

```python
import array
a = array.array('h', [-1,0,1])
v = memoryview(a)
print(list(v))
```

**Answer:**

```text
[-1, 0, 1]
```

Signed short array list.

### Q89. Advanced

What does this print?

```python
import array
a = array.array('H', [1,2,3])
v = memoryview(a)
print(list(v))
```

**Answer:**

```text
[1, 2, 3]
```

Unsigned short array list.

### Q90. Advanced

What does this print?

```python
import array
a = array.array('b', [-1,0,1])
v = memoryview(a)
print(list(v))
```

**Answer:**

```text
[-1, 0, 1]
```

Signed char array list.

### Q91. Advanced

What does this print?

```python
import array
a = array.array('B', [1,2,3])
v = memoryview(a)
print(list(v))
```

**Answer:**

```text
[1, 2, 3]
```

Unsigned char array list.

### Q92. Advanced

What does this print?

```python
import array
a = array.array('i', [1,2,3])
v = memoryview(a)
print(v.readonly)
```

**Answer:**

```text
False
```

Array view writable unless exported readonly.

### Q93. Advanced

What does this print?

```python
ba = bytearray(b'abcdef')
v = memoryview(ba)[1:5]
print(v.tobytes(), ba)
```

**Answer:**

```text
b'bcde' bytearray(b'abcdef')
```

Slice view substring.

### Q94. Advanced

What does this print?

```python
ba = bytearray(b'abcdef')
v = memoryview(ba)[::2]
print(list(v))
```

**Answer:**

```text
[97, 99, 101]
```

Strided slice view.

### Q95. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v[::2].tobytes())
```

**Answer:**

```text
b'ace'
```

Strided readonly slice.

### Q96. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v[-3:].tobytes())
```

**Answer:**

```text
b'def'
```

Tail slice tobytes.

### Q97. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v[:3].tobytes())
```

**Answer:**

```text
b'abc'
```

Head slice tobytes.

### Q98. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v[2:4].hex())
```

**Answer:**

```text
6364
```

Mid slice hex.

### Q99. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v[1:-1].hex())
```

**Answer:**

```text
62636465
```

Trim ends hex.

### Q100. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v[::-1].tobytes())
```

**Answer:**

```text
b'fedcba'
```

Reverse slice tobytes.

### Q101. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v[::3].tolist())
```

**Answer:**

```text
[97, 100]
```

Step three tolist.

### Q102. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v[-1::-1].tolist())
```

**Answer:**

```text
[102, 101, 100, 99, 98, 97]
```

Reverse full tolist.

### Q103. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H')[0])
```

**Answer:**

```text
25185
```

First unsigned short from bytes.

### Q104. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(len(v.cast('H')))
```

**Answer:**

```text
3
```

Number of H elements.

### Q105. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').nbytes)
```

**Answer:**

```text
6
```

H cast nbytes.

### Q106. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').itemsize)
```

**Answer:**

```text
2
```

H itemsize two.

### Q107. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').format)
```

**Answer:**

```text
H
```

H format char.

### Q108. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').shape)
```

**Answer:**

```text
(3,)
```

H shape tuple.

### Q109. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').strides)
```

**Answer:**

```text
(2,)
```

H strides tuple.

### Q110. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').readonly)
```

**Answer:**

```text
True
```

H readonly inherits.

### Q111. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').contiguous)
```

**Answer:**

```text
True
```

H contiguous flag.

### Q112. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').c_contiguous)
```

**Answer:**

```text
True
```

H c_contiguous.

### Q113. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').f_contiguous)
```

**Answer:**

```text
True
```

H f_contiguous.

### Q114. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').ndim)
```

**Answer:**

```text
1
```

H ndim.

### Q115. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').tolist())
```

**Answer:**

```text
[25185, 25699, 26213]
```

H tolist.

### Q116. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').hex())
```

**Answer:**

```text
616263646566
```

H hex.

### Q117. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').tobytes())
```

**Answer:**

```text
b'abcdef'
```

H tobytes re-encodes raw bytes of view.

### Q118. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(bytes(v.cast('H')))
```

**Answer:**

```text
b'abcdef'
```

bytes() on H cast.

### Q119. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(bytearray(v.cast('H')))
```

**Answer:**

```text
bytearray(b'abcdef')
```

bytearray() on H cast.

### Q120. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(list(v.cast('H').cast('B')))
```

**Answer:**

```text
[97, 98, 99, 100, 101, 102]
```

H cast back to B list.

### Q121. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').cast('B').tobytes())
```

**Answer:**

```text
b'abcdef'
```

Round cast H to B tobytes.

### Q122. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').cast('B').hex())
```

**Answer:**

```text
616263646566
```

Round cast hex.

### Q123. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').cast('B').tolist())
```

**Answer:**

```text
[97, 98, 99, 100, 101, 102]
```

Round cast tolist.

### Q124. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').cast('B').nbytes)
```

**Answer:**

```text
6
```

Round cast nbytes.

### Q125. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').cast('B').itemsize)
```

**Answer:**

```text
1
```

Round cast itemsize.

### Q126. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').cast('B').format)
```

**Answer:**

```text
B
```

Round cast format.

### Q127. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').cast('B').shape)
```

**Answer:**

```text
(6,)
```

Round cast shape.

### Q128. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').cast('B').strides)
```

**Answer:**

```text
(1,)
```

Round cast strides.

### Q129. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').cast('B').readonly)
```

**Answer:**

```text
True
```

Round cast readonly.

### Q130. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').cast('B').contiguous)
```

**Answer:**

```text
True
```

Round cast contiguous.

### Q131. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').cast('B').c_contiguous)
```

**Answer:**

```text
True
```

Round cast c_contiguous.

### Q132. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').cast('B').f_contiguous)
```

**Answer:**

```text
True
```

Round cast f_contiguous.

### Q133. Advanced

What does this print?

```python
v = memoryview(b'abcdef')
print(v.cast('H').cast('B').ndim)
```

**Answer:**

```text
1
```

Round cast ndim.

### Q134. Basic

What does this print?

```python
v = memoryview('json', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `json`.

### Q135. Basic

What does this print?

```python
v = memoryview('keyed', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `keyed`.

### Q136. Basic

What does this print?

```python
v = memoryview('label', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `label`.

### Q137. Basic

What does this print?

```python
v = memoryview('macro', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `macro`.

### Q138. Basic

What does this print?

```python
v = memoryview('nonce', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `nonce`.

### Q139. Basic

What does this print?

```python
v = memoryview('opcode', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `opcode`.

### Q140. Basic

What does this print?

```python
v = memoryview('pixel', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `pixel`.

### Q141. Basic

What does this print?

```python
v = memoryview('query', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `query`.

### Q142. Basic

What does this print?

```python
v = memoryview('range', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `range`.

### Q143. Basic

What does this print?

```python
v = memoryview('scope', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `scope`.

### Q144. Basic

What does this print?

```python
v = memoryview('token', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `token`.

### Q145. Basic

What does this print?

```python
v = memoryview('union', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `union`.

### Q146. Basic

What does this print?

```python
v = memoryview('value', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `value`.

### Q147. Basic

What does this print?

```python
v = memoryview('width', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `width`.

### Q148. Basic

What does this print?

```python
v = memoryview('xform', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `xform`.

### Q149. Basic

What does this print?

```python
v = memoryview('yieldy', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `yieldy`.

### Q150. Basic

What does this print?

```python
v = memoryview('zeta', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `zeta`.

### Q151. Basic

What does this print?

```python
v = memoryview('alga', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `alga`.

### Q152. Basic

What does this print?

```python
v = memoryview('birch', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `birch`.

### Q153. Basic

What does this print?

```python
v = memoryview('cedar', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `cedar`.

### Q154. Basic

What does this print?

```python
v = memoryview('dusk', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `dusk`.

### Q155. Basic

What does this print?

```python
v = memoryview('eagle', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `eagle`.

### Q156. Basic

What does this print?

```python
v = memoryview('fern', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `fern`.

### Q157. Basic

What does this print?

```python
v = memoryview('gull', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `gull`.

### Q158. Basic

What does this print?

```python
v = memoryview('hawk', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `hawk`.

### Q159. Basic

What does this print?

```python
v = memoryview('iris', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `iris`.

### Q160. Basic

What does this print?

```python
v = memoryview('jay', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `jay`.

### Q161. Basic

What does this print?

```python
v = memoryview('koala', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `koala`.

### Q162. Basic

What does this print?

```python
v = memoryview('lark', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `lark`.

### Q163. Basic

What does this print?

```python
v = memoryview('moth', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `moth`.

### Q164. Basic

What does this print?

```python
v = memoryview('newt', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `newt`.

### Q165. Basic

What does this print?

```python
v = memoryview('otter', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `otter`.

### Q166. Basic

What does this print?

```python
v = memoryview('puma', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `puma`.

### Q167. Basic

What does this print?

```python
v = memoryview('quail', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `quail`.

### Q168. Basic

What does this print?

```python
v = memoryview('robin', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `robin`.

### Q169. Basic

What does this print?

```python
v = memoryview('seal', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `seal`.

### Q170. Basic

What does this print?

```python
v = memoryview('toad', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `toad`.

### Q171. Basic

What does this print?

```python
v = memoryview('urchin', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `urchin`.

### Q172. Basic

What does this print?

```python
v = memoryview('viper', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `viper`.

### Q173. Basic

What does this print?

```python
v = memoryview('wolf', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `wolf`.

### Q174. Basic

What does this print?

```python
v = memoryview('yak', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `yak`.

### Q175. Basic

What does this print?

```python
v = memoryview('zebra', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `zebra`.

### Q176. Basic

What does this print?

```python
v = memoryview('apple', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `apple`.

### Q177. Basic

What does this print?

```python
v = memoryview('berry', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `berry`.

### Q178. Basic

What does this print?

```python
v = memoryview('citrus', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `citrus`.

### Q179. Basic

What does this print?

```python
v = memoryview('dates', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `dates`.

### Q180. Basic

What does this print?

```python
v = memoryview('elderberry', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `elderberry`.

### Q181. Basic

What does this print?

```python
v = memoryview('fig', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `fig`.

### Q182. Basic

What does this print?

```python
v = memoryview('grape', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `grape`.

### Q183. Basic

What does this print?

```python
v = memoryview('honey', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `honey`.

### Q184. Basic

What does this print?

```python
v = memoryview('kiwi', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `kiwi`.

### Q185. Basic

What does this print?

```python
v = memoryview('lemon', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `lemon`.

### Q186. Basic

What does this print?

```python
v = memoryview('mango', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `mango`.

### Q187. Basic

What does this print?

```python
v = memoryview('nut', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `nut`.

### Q188. Basic

What does this print?

```python
v = memoryview('oliveoil', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `oliveoil`.

### Q189. Basic

What does this print?

```python
v = memoryview('peach', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `peach`.

### Q190. Basic

What does this print?

```python
v = memoryview('quince', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `quince`.

### Q191. Basic

What does this print?

```python
v = memoryview('raisin', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `raisin`.

### Q192. Basic

What does this print?

```python
v = memoryview('sorbet', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `sorbet`.

### Q193. Basic

What does this print?

```python
v = memoryview('tart', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `tart`.

### Q194. Basic

What does this print?

```python
v = memoryview('udon', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `udon`.

### Q195. Basic

What does this print?

```python
v = memoryview('vanilla', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `vanilla`.

### Q196. Basic

What does this print?

```python
v = memoryview('wheat', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `wheat`.

### Q197. Basic

What does this print?

```python
v = memoryview('yogurt', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `yogurt`.

### Q198. Basic

What does this print?

```python
v = memoryview('zest', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `zest`.

### Q199. Basic

What does this print?

```python
v = memoryview('anise', 'utf-8')
print(v.nbytes)
```

**Answer:**

```text
TypeError: memoryview() takes at most 1 argument (2 given)
```

UTF-8 str buffer view nbytes for `anise`.

### Q200. Advanced

Write `view_sum(buf)` returning sum of memoryview over writable buffer.

**Answer:**

```python
def view_sum(buf):
    return sum(memoryview(buf))
```

- `view_sum(bytearray(b'\x01\x02'))  =>  3`

memoryview iterates byte values as ints.

*Section size: 200 questions (Basic 80, Intermediate 68, Advanced 52).*

