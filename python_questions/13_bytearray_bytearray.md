## 13. Bytearray (bytearray)

A mutable sequence of integers in 0..255.

### Q1. Basic

What does this print?

```python
print(type(bytearray(b'hi')))
```

**Answer:**

```text
<class 'bytearray'>
```

`bytearray()` is mutable bytes sequence.

### Q2. Basic

What does this print?

```python
print(bytearray([65, 66]))
```

**Answer:**

```text
bytearray(b'AB')
```

Construct from int 0-255.

### Q3. Basic

What does this print?

```python
print(bytearray(3))
```

**Answer:**

```text
bytearray(b'\x00\x00\x00')
```

Length constructor allocates zeros.

### Q4. Basic

What does this print?

```python
print(bytearray(b'abc')[0])
```

**Answer:**

```text
97
```

Index returns int.

### Q5. Basic

What does this print?

```python
ba = bytearray(b'abc')
ba[0] = 65
print(ba)
```

**Answer:**

```text
bytearray(b'Abc')
```

Item assignment mutates.

### Q6. Basic

What does this print?

```python
ba = bytearray(b'abc')
ba.append(33)
print(ba)
```

**Answer:**

```text
bytearray(b'abc!')
```

Append adds int 0-255.

### Q7. Basic

What does this print?

```python
ba = bytearray(b'ab')
ba.extend(b'cd')
print(ba)
```

**Answer:**

```text
bytearray(b'abcd')
```

Extend adds bytes/int iterables.

### Q8. Basic

What does this print?

```python
ba = bytearray(b'hello')
ba[1:3] = b'XX'
print(ba)
```

**Answer:**

```text
bytearray(b'hXXlo')
```

Slice assignment can resize.

### Q9. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(bytes(ba))
```

**Answer:**

```text
b'abc'
```

Bytes snapshot is immutable.

### Q10. Basic

What does this print?

```python
ba = bytearray(b'abc')
ba.reverse()
print(ba)
```

**Answer:**

```text
bytearray(b'cba')
```

Reverse in place.

### Q11. Basic

What does this print?

```python
print(b'abc' == bytearray(b'abc'))
```

**Answer:**

```text
True
```

Equality with bytes value.

### Q12. Basic

What happens when this runs?

```python
print({bytearray(b'x')})
```

**Answer:**

```text
TypeError: unhashable type: 'bytearray'
```

Bytearray unhashable.

### Q13. Basic

What does this print?

```python
ba = bytearray(b'abc')
ba += b'!'
print(ba)
```

**Answer:**

```text
bytearray(b'abc!')
```

+= mutates in place.

### Q14. Basic

What does this print?

```python
print(bytearray(b'abc').decode())
```

**Answer:**

```text
abc
```

Decode like bytes.

### Q15. Basic

What does this print?

```python
print(bytearray('hi', 'utf-8'))
```

**Answer:**

```text
bytearray(b'hi')
```

Encode str to bytearray.

### Q16. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.pop())
```

**Answer:**

```text
99
```

Pop removes last int.

### Q17. Basic

What does this print?

```python
ba = bytearray(b'abc')
ba.insert(1, 88)
print(ba)
```

**Answer:**

```text
bytearray(b'aXbc')
```

Insert at index.

### Q18. Basic

What does this print?

```python
ba = bytearray(b'abcabc')
print(ba.remove(97))
```

**Answer:**

```text
None
```

Remove first matching value.

### Q19. Basic

What does this print?

```python
ba = bytearray(b'abc')
del ba[1]
print(ba)
```

**Answer:**

```text
bytearray(b'ac')
```

del removes index.

### Q20. Basic

What does this print?

```python
ba = bytearray(b'abc')
ba.clear()
print(len(ba))
```

**Answer:**

```text
0
```

Clear empties buffer.

### Q21. Basic

What does this print?

```python
ba = bytearray(b'hello')
print(ba.find(b'll'))
```

**Answer:**

```text
2
```

Find like bytes API.

### Q22. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.replace(b'a', b'z'))
```

**Answer:**

```text
bytearray(b'zbc')
```

Replace returns new bytearray.

### Q23. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.upper())
```

**Answer:**

```text
bytearray(b'ABC')
```

Case methods return new bytearray.

### Q24. Basic

What does this print?

```python
ba = bytearray(b'ABC')
print(ba.lower())
```

**Answer:**

```text
bytearray(b'abc')
```

Lowercase conversion.

### Q25. Basic

What does this print?

```python
ba = bytearray(b' a ')
print(ba.strip())
```

**Answer:**

```text
bytearray(b'a')
```

Strip whitespace.

### Q26. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.startswith(b'ab'), ba.endswith(b'c'))
```

**Answer:**

```text
True True
```

Prefix/suffix tests.

### Q27. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(list(ba))
```

**Answer:**

```text
[97, 98, 99]
```

List materializes ints.

### Q28. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.hex())
```

**Answer:**

```text
616263
```

Hex representation.

### Q29. Basic

What does this print?

```python
print(bytearray.fromhex('616263'))
```

**Answer:**

```text
bytearray(b'abc')
```

Fromhex builds bytearray.

### Q30. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(memoryview(ba).readonly)
```

**Answer:**

```text
False
```

Writable buffer view not readonly.

### Q31. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba * 2)
```

**Answer:**

```text
bytearray(b'abcabc')
```

Repeat concatenates.

### Q32. Basic

What does this print?

```python
ba = bytearray(b'ab')
ba *= 3
print(ba)
```

**Answer:**

```text
bytearray(b'ababab')
```

In-place repeat multiply.

### Q33. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba[::-1])
```

**Answer:**

```text
bytearray(b'cba')
```

Slice reverse copy.

### Q34. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.split(b'b'))
```

**Answer:**

```text
[bytearray(b'a'), bytearray(b'c')]
```

Split returns list of bytearray.

### Q35. Basic

What does this print?

```python
ba = bytearray(b'a,b,c')
print(ba.partition(b','))
```

**Answer:**

```text
(bytearray(b'a'), bytearray(b','), bytearray(b'b,c'))
```

Partition tuple of three parts.

### Q36. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.rfind(b'x'))
```

**Answer:**

```text
-1
```

Rfind missing returns -1.

### Q37. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.index(b'b'))
```

**Answer:**

```text
1
```

Index finds subsequence.

### Q38. Basic

What happens when this runs?

```python
ba = bytearray(b'abc')
print(ba.index(b'z'))
```

**Answer:**

```text
ValueError: subsection not found
```

Index missing raises ValueError.

### Q39. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.count(b'a'))
```

**Answer:**

```text
1
```

Count non-overlapping occurrences.

### Q40. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.capitalize())
```

**Answer:**

```text
bytearray(b'Abc')
```

Capitalize first byte as char.

### Q41. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.title())
```

**Answer:**

```text
bytearray(b'Abc')
```

Title case bytes as chars.

### Q42. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.swapcase())
```

**Answer:**

```text
bytearray(b'ABC')
```

Swap case on bytes.

### Q43. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.center(5, b'-'))
```

**Answer:**

```text
bytearray(b'-abc-')
```

Center with fill byte.

### Q44. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.ljust(5, b'.'))
```

**Answer:**

```text
bytearray(b'abc..')
```

Left justify.

### Q45. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.rjust(5, b'.'))
```

**Answer:**

```text
bytearray(b'..abc')
```

Right justify.

### Q46. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.zfill(5))
```

**Answer:**

```text
bytearray(b'00abc')
```

Zero fill numeric bytes.

### Q47. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.isalpha())
```

**Answer:**

```text
True
```

isalpha on byte values as chars.

### Q48. Basic

What does this print?

```python
ba = bytearray(b'123')
print(ba.isdigit())
```

**Answer:**

```text
True
```

isdigit test.

### Q49. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.islower(), ba.isupper())
```

**Answer:**

```text
True False
```

Case predicates.

### Q50. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.maketrans(b'a', b'x'))
```

**Answer:**

```text
b'\x00\x01\x02\x03\x04\x05\x06\x07\x08\t\n\x0b\x0c\r\x0e\x0f\x10\x11\x12\x13\x14\x15\x16\x17\x18\x19\x1a\x1b\x1c\x1d\x1e\x1f !"#$%&\'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\\]^_`xbcdefghijklmnopqrstuvwxyz{|}~\x7f\x80\x81\x82\x83\x84\x85\x86\x87\x88\x89\x8a\x8b\x8c\x8d\x8e\x8f\x90\x91\x92\x93\x94\x95\x96\x97\x98\x99\x9a\x9b\x9c\x9d\x9e\x9f\xa0\xa1\xa2\xa3\xa4\xa5\xa6\xa7\xa8\xa9\xaa\xab\xac\xad\xae\xaf\xb0\xb1\xb2\xb3\xb4\xb5\xb6\xb7\xb8\xb9\xba\xbb\xbc\xbd\xbe\xbf\xc0\xc1\xc2\xc3\xc4\xc5\xc6\xc7\xc8\xc9\xca\xcb\xcc\xcd\xce\xcf\xd0\xd1\xd2\xd3\xd4\xd5\xd6\xd7\xd8\xd9\xda\xdb\xdc\xdd\xde\xdf\xe0\xe1\xe2\xe3\xe4\xe5\xe6\xe7\xe8\xe9\xea\xeb\xec\xed\xee\xef\xf0\xf1\xf2\xf3\xf4\xf5\xf6\xf7\xf8\xf9\xfa\xfb\xfc\xfd\xfe\xff'
```

maketrans builds translation table.

### Q51. Basic

What does this print?

```python
ba = bytearray(b'abc')
print(ba.translate(ba.maketrans(b'a', b'x')))
```

**Answer:**

```text
bytearray(b'xbc')
```

Translate bytes via table.

### Q52. Intermediate

What does this print?

```python
ba = bytearray(b'hello')
print(ba.translate(bytes.maketrans(b'el', b'EL')))
```

**Answer:**

```text
bytearray(b'hELLo')
```

Translate with bytes.maketrans.

### Q53. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.hex(' ', 2))
```

**Answer:**

```text
61 6263
```

Hex with separator and bytes_per_sep.

### Q54. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.join([b'1', b'2']))
```

**Answer:**

```text
bytearray(b'1abc2')
```

Join iterables of bytes-like.

### Q55. Intermediate

What does this print?

```python
ba = bytearray(b'line1\nline2')
print(ba.splitlines())
```

**Answer:**

```text
[bytearray(b'line1'), bytearray(b'line2')]
```

Splitlines keeps pieces as bytearray.

### Q56. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.strip(b'a'))
```

**Answer:**

```text
bytearray(b'bc')
```

Strip specific byte set.

### Q57. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.rstrip(b'c'))
```

**Answer:**

```text
bytearray(b'ab')
```

Right strip subset.

### Q58. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.lstrip(b'a'))
```

**Answer:**

```text
bytearray(b'bc')
```

Left strip subset.

### Q59. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.removeprefix(b'ab'))
```

**Answer:**

```text
bytearray(b'c')
```

Removeprefix if present.

### Q60. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.removesuffix(b'bc'))
```

**Answer:**

```text
bytearray(b'a')
```

Removesuffix if present.

### Q61. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.split(b'a'))
```

**Answer:**

```text
[bytearray(b''), bytearray(b'bc')]
```

Split on delimiter.

### Q62. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.rsplit(b'b', 1))
```

**Answer:**

```text
[bytearray(b'a'), bytearray(b'c')]
```

Right split with maxsplit.

### Q63. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.partition(b'b'))
```

**Answer:**

```text
(bytearray(b'a'), bytearray(b'b'), bytearray(b'c'))
```

Partition on delimiter.

### Q64. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.rpartition(b'b'))
```

**Answer:**

```text
(bytearray(b'a'), bytearray(b'b'), bytearray(b'c'))
```

Rpartition from right.

### Q65. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.find(b'bc', 1))
```

**Answer:**

```text
1
```

Find with start index.

### Q66. Intermediate

What does this print?

```python
ba = bytearray(b'abcabc')
print(ba.rfind(b'bc'))
```

**Answer:**

```text
4
```

Rfind last occurrence.

### Q67. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.startswith((b'a', b'x')))
```

**Answer:**

```text
True
```

Startswith tuple of prefixes.

### Q68. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.endswith((b'c', b'x')))
```

**Answer:**

```text
True
```

Endswith tuple of suffixes.

### Q69. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.replace(b'b', b'B', 1))
```

**Answer:**

```text
bytearray(b'aBc')
```

Replace with count limit.

### Q70. Intermediate

What does this print?

```python
ba = bytearray(b'\xff\xfe')
print(ba.decode('latin-1'))
```

**Answer:**

```text
ÿþ
```

Decode with explicit encoding.

### Q71. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.decode('utf-8', 'ignore'))
```

**Answer:**

```text
abc
```

Decode with error handler.

### Q72. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.decode('utf-8', 'replace'))
```

**Answer:**

```text
abc
```

Replace errors on decode.

### Q73. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.decode('utf-8', 'backslashreplace'))
```

**Answer:**

```text
abc
```

Backslashreplace handler.

### Q74. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.decode('utf-8', 'surrogateescape'))
```

**Answer:**

```text
abc
```

Surrogateescape handler.

### Q75. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.decode('utf-8', 'strict'))
```

**Answer:**

```text
abc
```

Strict handler is default.

### Q76. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.decode('utf-8', 'xmlcharrefreplace'))
```

**Answer:**

```text
abc
```

Xmlcharrefreplace on encode path only; decode strict here.

### Q77. Intermediate

What happens when this runs?

```python
ba = bytearray(b'abc')
print(ba.decode('utf-8', 'invalid'))
```

**Answer:**

```text
abc
```

Invalid error handler name raises LookupError.

### Q78. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.upper().lower() == ba)
```

**Answer:**

```text
True
```

Case round trip for lowercase input.

### Q79. Intermediate

What does this print?

```python
ba = bytearray(b'ABC')
print(ba.lower().upper() == ba)
```

**Answer:**

```text
True
```

Case round trip for uppercase input.

### Q80. Intermediate

What does this print?

```python
ba = bytearray(b'a1')
print(ba.isalnum())
```

**Answer:**

```text
True
```

Alphanumeric test.

### Q81. Intermediate

What does this print?

```python
ba = bytearray(b' \t')
print(ba.isspace())
```

**Answer:**

```text
True
```

Whitespace bytes test.

### Q82. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.isascii())
```

**Answer:**

```text
True
```

All ASCII bytes.

### Q83. Intermediate

What does this print?

```python
ba = bytearray(b'abc\n')
print(ba.isprintable())
```

**Answer:**

```text
AttributeError: 'bytearray' object has no attribute 'isprintable'
```

Printable bytes test.

### Q84. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__sizeof__() > len(ba))
```

**Answer:**

```text
True
```

Object size includes overhead.

### Q85. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.capitalize().decode())
```

**Answer:**

```text
Abc
```

Capitalize then decode to str.

### Q86. Intermediate

What does this print?

```python
ba = bytearray(b'hello world')
print(ba.title().decode())
```

**Answer:**

```text
Hello World
```

Title then decode.

### Q87. Intermediate

What does this print?

```python
ba = bytearray(b'AbC')
print(ba.swapcase().decode())
```

**Answer:**

```text
aBc
```

Swapcase decode.

### Q88. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.maketrans(b'abc', b'xyz'))
```

**Answer:**

```text
b'\x00\x01\x02\x03\x04\x05\x06\x07\x08\t\n\x0b\x0c\r\x0e\x0f\x10\x11\x12\x13\x14\x15\x16\x17\x18\x19\x1a\x1b\x1c\x1d\x1e\x1f !"#$%&\'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\\]^_`xyzdefghijklmnopqrstuvwxyz{|}~\x7f\x80\x81\x82\x83\x84\x85\x86\x87\x88\x89\x8a\x8b\x8c\x8d\x8e\x8f\x90\x91\x92\x93\x94\x95\x96\x97\x98\x99\x9a\x9b\x9c\x9d\x9e\x9f\xa0\xa1\xa2\xa3\xa4\xa5\xa6\xa7\xa8\xa9\xaa\xab\xac\xad\xae\xaf\xb0\xb1\xb2\xb3\xb4\xb5\xb6\xb7\xb8\xb9\xba\xbb\xbc\xbd\xbe\xbf\xc0\xc1\xc2\xc3\xc4\xc5\xc6\xc7\xc8\xc9\xca\xcb\xcc\xcd\xce\xcf\xd0\xd1\xd2\xd3\xd4\xd5\xd6\xd7\xd8\xd9\xda\xdb\xdc\xdd\xde\xdf\xe0\xe1\xe2\xe3\xe4\xe5\xe6\xe7\xe8\xe9\xea\xeb\xec\xed\xee\xef\xf0\xf1\xf2\xf3\xf4\xf5\xf6\xf7\xf8\xf9\xfa\xfb\xfc\xfd\xfe\xff'
```

Three-arg maketrans.

### Q89. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.translate(bytes.maketrans(b'abc', b'123')))
```

**Answer:**

```text
bytearray(b'123')
```

Translate to digits.

### Q90. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.replace(b'a', b'A').replace(b'b', b'B'))
```

**Answer:**

```text
bytearray(b'ABc')
```

Chained replace.

### Q91. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba + b'd')
```

**Answer:**

```text
bytearray(b'abcd')
```

Concat with bytes produces bytes.

### Q92. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba + bytearray(b'd'))
```

**Answer:**

```text
bytearray(b'abcd')
```

Concat two bytearrays yields bytes.

### Q93. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(b'%s' % ba)
```

**Answer:**

```text
b'abc'
```

Percent formatting accepts bytearray.

### Q94. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(format(ba, 's'))
```

**Answer:**

```text
TypeError: unsupported format string passed to bytearray.__format__
```

Format spec on bytearray.

### Q95. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(repr(ba))
```

**Answer:**

```text
bytearray(b'abc')
```

Repr shows bytearray prefix.

### Q96. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(str(ba))
```

**Answer:**

```text
bytearray(b'abc')
```

Str shows decoded ascii where possible.

### Q97. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__len__())
```

**Answer:**

```text
3
```

Dunder len matches len().

### Q98. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__getitem__(1))
```

**Answer:**

```text
98
```

Dunder getitem indexing.

### Q99. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
ba.__setitem__(1, 88)
print(ba)
```

**Answer:**

```text
bytearray(b'aXc')
```

Dunder setitem assignment.

### Q100. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__contains__(97))
```

**Answer:**

```text
True
```

Contains int member.

### Q101. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__contains__(b'a'))
```

**Answer:**

```text
True
```

Contains bytes-like substring.

### Q102. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__iter__().__next__())
```

**Answer:**

```text
97
```

Iterator yields ints.

### Q103. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__reversed__().__next__())
```

**Answer:**

```text
AttributeError: 'bytearray' object has no attribute '__reversed__'
```

Reversed iterator.

### Q104. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__bytes__())
```

**Answer:**

```text
AttributeError: 'bytearray' object has no attribute '__bytes__'
```

Dunder bytes returns bytes copy.

### Q105. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__eq__(b'abc'))
```

**Answer:**

```text
True
```

Compare equal to bytes.

### Q106. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__ne__(b'xyz'))
```

**Answer:**

```text
True
```

Compare not equal.

### Q107. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__lt__(b'abd'))
```

**Answer:**

```text
True
```

Lexicographic less.

### Q108. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__gt__(b'abb'))
```

**Answer:**

```text
True
```

Lexicographic greater.

### Q109. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__add__(b'd'))
```

**Answer:**

```text
bytearray(b'abcd')
```

Dunder add to bytes.

### Q110. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__mul__(2))
```

**Answer:**

```text
bytearray(b'abcabc')
```

Dunder mul repeat.

### Q111. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__mod__(b'%s',))
```

**Answer:**

```text
TypeError: not all arguments converted during bytes formatting
```

Dunder mod formatting.

### Q112. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__str__())
```

**Answer:**

```text
bytearray(b'abc')
```

Dunder str.

### Q113. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__repr__())
```

**Answer:**

```text
bytearray(b'abc')
```

Dunder repr.

### Q114. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__sizeof__())
```

**Answer:**

```text
60
```

Dunder sizeof.

### Q115. Intermediate

What does this print?

```python
ba = bytearray(b'abc')
print(ba.__len__(), len(ba))
```

**Answer:**

```text
3 3
```

Len dunder vs builtin.

### Q116. Advanced

What does this print?

```python
ba = bytearray(b'hello')
print(ba.translate(bytes.maketrans(b'aeiou', b'AEIOU')))
```

**Answer:**

```text
bytearray(b'hEllO')
```

Vowel upper translation.

### Q117. Advanced

What does this print?

```python
ba = bytearray(b'0123456789')
print(ba.translate(bytes.maketrans(b'0123456789', b'9876543210')))
```

**Answer:**

```text
bytearray(b'9876543210')
```

Digit reversal table.

### Q118. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.translate(b' ' * 256).count(0))
```

**Answer:**

```text
SyntaxError: source code string cannot contain null bytes
```

Delete map using zero table trick.

### Q119. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.hex('.', 1))
```

**Answer:**

```text
61.62.63
```

Hex sep every byte.

### Q120. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.decode('utf-8').encode('utf-16')[:2])
```

**Answer:**

```text
b'\xff\xfe'
```

Round trip through str to utf-16 prefix.

### Q121. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(list(memoryview(ba)))
```

**Answer:**

```text
[97, 98, 99]
```

Memoryview lists underlying ints.

### Q122. Advanced

What does this print?

```python
ba = bytearray(b'abc')
mv = memoryview(ba)
mv[0] = 65
print(ba[0])
```

**Answer:**

```text
65
```

Mutate through memoryview.

### Q123. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.replace(b'abc', b'xyz'))
```

**Answer:**

```text
bytearray(b'xyz')
```

Replace whole buffer.

### Q124. Advanced

What does this print?

```python
ba = bytearray(b'abcabc')
print(ba.replace(b'abc', b'X'))
```

**Answer:**

```text
bytearray(b'XX')
```

Replace all occurrences default.

### Q125. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.strip().strip(b'ab'))
```

**Answer:**

```text
bytearray(b'c')
```

Double strip.

### Q126. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.rjust(10, b'_').decode())
```

**Answer:**

```text
_______abc
```

Wide rjust decode.

### Q127. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.ljust(10, b'_').decode())
```

**Answer:**

```text
abc_______
```

Wide ljust decode.

### Q128. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.center(10, b'_').decode())
```

**Answer:**

```text
___abc____
```

Wide center decode.

### Q129. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.zfill(10).decode())
```

**Answer:**

```text
0000000abc
```

Wide zfill decode.

### Q130. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.upper().hex())
```

**Answer:**

```text
414243
```

Upper then hex.

### Q131. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.lower().hex())
```

**Answer:**

```text
616263
```

Lower then hex.

### Q132. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.capitalize().hex())
```

**Answer:**

```text
416263
```

Capitalize hex.

### Q133. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.title().hex())
```

**Answer:**

```text
416263
```

Title hex.

### Q134. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.swapcase().hex())
```

**Answer:**

```text
414243
```

Swapcase hex.

### Q135. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.replace(b'a', b'A').hex())
```

**Answer:**

```text
416263
```

Replace hex.

### Q136. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.split(b'b')[0].hex())
```

**Answer:**

```text
61
```

Split segment hex.

### Q137. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.partition(b'b')[0].hex())
```

**Answer:**

```text
61
```

Partition head hex.

### Q138. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.partition(b'b')[2].hex())
```

**Answer:**

```text
63
```

Partition tail hex.

### Q139. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.rpartition(b'b')[0].hex())
```

**Answer:**

```text
61
```

Rpartition head hex.

### Q140. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.rpartition(b'b')[2].hex())
```

**Answer:**

```text
63
```

Rpartition tail hex.

### Q141. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.find(b'bc').to_bytes(1,'big'))
```

**Answer:**

```text
b'\x01'
```

Find result as bytes int.

### Q142. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.index(b'b').to_bytes(1,'big'))
```

**Answer:**

```text
b'\x01'
```

Index result as bytes int.

### Q143. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.count(b'a').to_bytes(1,'big'))
```

**Answer:**

```text
b'\x01'
```

Count as byte.

### Q144. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.startswith(b'ab').to_bytes(1,'big'))
```

**Answer:**

```text
b'\x01'
```

Startswith bool as byte.

### Q145. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.endswith(b'bc').to_bytes(1,'big'))
```

**Answer:**

```text
b'\x01'
```

Endswith bool as byte.

### Q146. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.isalpha().to_bytes(1,'big'))
```

**Answer:**

```text
b'\x01'
```

isalpha bool byte.

### Q147. Advanced

What does this print?

```python
ba = bytearray(b'123')
print(ba.isdigit().to_bytes(1,'big'))
```

**Answer:**

```text
b'\x01'
```

isdigit bool byte.

### Q148. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.islower().to_bytes(1,'big'))
```

**Answer:**

```text
b'\x01'
```

islower bool byte.

### Q149. Advanced

What does this print?

```python
ba = bytearray(b'ABC')
print(ba.isupper().to_bytes(1,'big'))
```

**Answer:**

```text
b'\x01'
```

isupper bool byte.

### Q150. Advanced

What does this print?

```python
ba = bytearray(b'a1')
print(ba.isalnum().to_bytes(1,'big'))
```

**Answer:**

```text
b'\x01'
```

isalnum bool byte.

### Q151. Advanced

What does this print?

```python
ba = bytearray(b' \t')
print(ba.isspace().to_bytes(1,'big'))
```

**Answer:**

```text
b'\x01'
```

isspace bool byte.

### Q152. Advanced

What does this print?

```python
ba = bytearray(b'abc')
print(ba.isascii().to_bytes(1,'big'))
```

**Answer:**

```text
b'\x01'
```

isascii bool byte.

### Q153. Advanced

What does this print?

```python
ba = bytearray(b'abc\n')
print(ba.isprintable().to_bytes(1,'big'))
```

**Answer:**

```text
AttributeError: 'bytearray' object has no attribute 'isprintable'
```

isprintable bool byte.

### Q154. Advanced

What does this print?

```python
ba = bytearray('kilo', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
kilo
```

UTF-8 encode/decode round trip for `kilo`.

### Q155. Advanced

What does this print?

```python
ba = bytearray('lima', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
lima
```

UTF-8 encode/decode round trip for `lima`.

### Q156. Advanced

What does this print?

```python
ba = bytearray('mike', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
mike
```

UTF-8 encode/decode round trip for `mike`.

### Q157. Advanced

What does this print?

```python
ba = bytearray('november', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
november
```

UTF-8 encode/decode round trip for `november`.

### Q158. Advanced

What does this print?

```python
ba = bytearray('oscar', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
oscar
```

UTF-8 encode/decode round trip for `oscar`.

### Q159. Advanced

What does this print?

```python
ba = bytearray('papa', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
papa
```

UTF-8 encode/decode round trip for `papa`.

### Q160. Advanced

What does this print?

```python
ba = bytearray('quebec', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
quebec
```

UTF-8 encode/decode round trip for `quebec`.

### Q161. Advanced

What does this print?

```python
ba = bytearray('romeo', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
romeo
```

UTF-8 encode/decode round trip for `romeo`.

### Q162. Advanced

What does this print?

```python
ba = bytearray('sierra', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
sierra
```

UTF-8 encode/decode round trip for `sierra`.

### Q163. Advanced

What does this print?

```python
ba = bytearray('tango', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
tango
```

UTF-8 encode/decode round trip for `tango`.

### Q164. Advanced

What does this print?

```python
ba = bytearray('uniform', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
uniform
```

UTF-8 encode/decode round trip for `uniform`.

### Q165. Advanced

What does this print?

```python
ba = bytearray('victor', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
victor
```

UTF-8 encode/decode round trip for `victor`.

### Q166. Advanced

What does this print?

```python
ba = bytearray('whiskey', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
whiskey
```

UTF-8 encode/decode round trip for `whiskey`.

### Q167. Advanced

What does this print?

```python
ba = bytearray('xray', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
xray
```

UTF-8 encode/decode round trip for `xray`.

### Q168. Advanced

What does this print?

```python
ba = bytearray('yankee', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
yankee
```

UTF-8 encode/decode round trip for `yankee`.

### Q169. Advanced

What does this print?

```python
ba = bytearray('zulu', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
zulu
```

UTF-8 encode/decode round trip for `zulu`.

### Q170. Advanced

What does this print?

```python
ba = bytearray('amber', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
amber
```

UTF-8 encode/decode round trip for `amber`.

### Q171. Advanced

What does this print?

```python
ba = bytearray('bronze', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
bronze
```

UTF-8 encode/decode round trip for `bronze`.

### Q172. Advanced

What does this print?

```python
ba = bytearray('coral', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
coral
```

UTF-8 encode/decode round trip for `coral`.

### Q173. Advanced

What does this print?

```python
ba = bytearray('denim', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
denim
```

UTF-8 encode/decode round trip for `denim`.

### Q174. Advanced

What does this print?

```python
ba = bytearray('ebony', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
ebony
```

UTF-8 encode/decode round trip for `ebony`.

### Q175. Advanced

What does this print?

```python
ba = bytearray('flint', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
flint
```

UTF-8 encode/decode round trip for `flint`.

### Q176. Advanced

What does this print?

```python
ba = bytearray('granite', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
granite
```

UTF-8 encode/decode round trip for `granite`.

### Q177. Advanced

What does this print?

```python
ba = bytearray('hazel', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
hazel
```

UTF-8 encode/decode round trip for `hazel`.

### Q178. Advanced

What does this print?

```python
ba = bytearray('ivory', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
ivory
```

UTF-8 encode/decode round trip for `ivory`.

### Q179. Advanced

What does this print?

```python
ba = bytearray('jade', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
jade
```

UTF-8 encode/decode round trip for `jade`.

### Q180. Advanced

What does this print?

```python
ba = bytearray('khaki', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
khaki
```

UTF-8 encode/decode round trip for `khaki`.

### Q181. Advanced

What does this print?

```python
ba = bytearray('linen', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
linen
```

UTF-8 encode/decode round trip for `linen`.

### Q182. Advanced

What does this print?

```python
ba = bytearray('maroon', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
maroon
```

UTF-8 encode/decode round trip for `maroon`.

### Q183. Advanced

What does this print?

```python
ba = bytearray('navy', 'utf-8')
print(ba.decode())
```

**Answer:**

```text
navy
```

UTF-8 encode/decode round trip for `navy`.

### Q184. Basic

What does this print?

```python
ba = bytearray('kiwi', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'kiw')
```

First bytes of UTF-8 buffer `kiwi`.

### Q185. Basic

What does this print?

```python
ba = bytearray('lemon', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'lem')
```

First bytes of UTF-8 buffer `lemon`.

### Q186. Basic

What does this print?

```python
ba = bytearray('mango', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'man')
```

First bytes of UTF-8 buffer `mango`.

### Q187. Basic

What does this print?

```python
ba = bytearray('nut', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'nut')
```

First bytes of UTF-8 buffer `nut`.

### Q188. Basic

What does this print?

```python
ba = bytearray('oliveoil', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'oli')
```

First bytes of UTF-8 buffer `oliveoil`.

### Q189. Basic

What does this print?

```python
ba = bytearray('peach', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'pea')
```

First bytes of UTF-8 buffer `peach`.

### Q190. Basic

What does this print?

```python
ba = bytearray('quince', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'qui')
```

First bytes of UTF-8 buffer `quince`.

### Q191. Basic

What does this print?

```python
ba = bytearray('raisin', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'rai')
```

First bytes of UTF-8 buffer `raisin`.

### Q192. Basic

What does this print?

```python
ba = bytearray('sorbet', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'sor')
```

First bytes of UTF-8 buffer `sorbet`.

### Q193. Basic

What does this print?

```python
ba = bytearray('tart', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'tar')
```

First bytes of UTF-8 buffer `tart`.

### Q194. Basic

What does this print?

```python
ba = bytearray('udon', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'udo')
```

First bytes of UTF-8 buffer `udon`.

### Q195. Basic

What does this print?

```python
ba = bytearray('vanilla', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'van')
```

First bytes of UTF-8 buffer `vanilla`.

### Q196. Basic

What does this print?

```python
ba = bytearray('wheat', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'whe')
```

First bytes of UTF-8 buffer `wheat`.

### Q197. Basic

What does this print?

```python
ba = bytearray('yogurt', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'yog')
```

First bytes of UTF-8 buffer `yogurt`.

### Q198. Basic

What does this print?

```python
ba = bytearray('zest', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'zes')
```

First bytes of UTF-8 buffer `zest`.

### Q199. Basic

What does this print?

```python
ba = bytearray('anise', 'utf-8')
print(ba[:3])
```

**Answer:**

```text
bytearray(b'ani')
```

First bytes of UTF-8 buffer `anise`.

### Q200. Intermediate

Write `mutable_upper(b)` returning a new bytearray uppercased (ASCII letters).

**Answer:**

```python
def mutable_upper(b):
    return bytearray(b).upper()
```

- `mutable_upper(b'abc')  =>  bytearray(b'ABC')`

Bytearray exposes bytes-like case methods.

*Section size: 200 questions (Basic 67, Intermediate 65, Advanced 68).*

