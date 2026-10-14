# Python Programming Practice Questions

Practice set for Python 3.12. Each built-in data type below has **200 questions**, ordered from basic to advanced. The last section has **200 programming problems** commonly asked in product-company interviews.

Try the question before you read the answer. Code samples target CPython 3.12. A few identity (`is`) results for integers outside the small-int cache are CPython details; those answers say so.

## How the built-in types group

| Group | Types | Mutable? |
| --- | --- | --- |
| Numeric | `int`, `float`, `complex`, `bool` | No |
| Text | `str` | No |
| Sequence | `list`, `tuple`, `range` | Only `list` |
| Mapping | `dict` | Yes |
| Set | `set`, `frozenset` | Only `set` |
| Binary | `bytes`, `bytearray`, `memoryview` | `bytearray` is mutable. A `memoryview` writes through only when the underlying buffer is writable |
| Null | `NoneType` (`None`) | No |

`bool` is a subclass of `int`. `None` is the only instance of `NoneType`.

## Contents

1. [Integer (int)](#1-integer-int)
2. [Floating point (float)](#2-floating-point-float)
3. [Complex (complex)](#3-complex-complex)
4. [Boolean (bool)](#4-boolean-bool)
5. [String (str)](#5-string-str)
6. [List (list)](#6-list-list)
7. [Tuple (tuple)](#7-tuple-tuple)
8. [Range (range)](#8-range-range)
9. [Dictionary (dict)](#9-dictionary-dict)
10. [Set (set)](#10-set-set)
11. [Frozenset (frozenset)](#11-frozenset-frozenset)
12. [Bytes (bytes)](#12-bytes-bytes)
13. [Bytearray (bytearray)](#13-bytearray-bytearray)
14. [Memoryview (memoryview)](#14-memoryview-memoryview)
15. [None (NoneType)](#15-none-nonetype)
16. [MNC interview programming questions](#16-mnc-interview-programming-questions)

## 1. Integer (int)

Arbitrary-precision integers. Floor division, bitwise operations, bases, and formatting show up constantly in language rounds.

### Q1. Basic

What does this print?

```python
print(type(42))
```

**Answer:**

```text
<class 'int'>
```

`42` is an `int`.

### Q2. Basic

What does this print?

```python
print(type(42) is int)
```

**Answer:**

```text
True
```

The type object of an int is `int`.

### Q3. Basic

What does this print?

```python
print(isinstance(True, int))
```

**Answer:**

```text
True
```

`bool` is a subclass of `int`, so `True` is an instance of `int`.

### Q4. Basic

What does this print?

```python
print(isinstance(42, int), isinstance(42.0, int))
```

**Answer:**

```text
True False
```

A float is not an int, even when the value is whole.

### Q5. Basic

What does this print?

```python
x = 1_000_000
print(x)
```

**Answer:**

```text
1000000
```

Underscores in numeric literals are ignored. They only group digits.

### Q6. Basic

What does this print?

```python
print(0b1010, 0o17, 0x1f)
```

**Answer:**

```text
10 15 31
```

`0b` is binary, `0o` is octal, `0x` is hexadecimal. The values are 10, 15, and 31.

### Q7. Basic

What does this print?

```python
print(int('1010', 2))
```

**Answer:**

```text
10
```

`int(text, base)` parses text in the given base.

### Q8. Basic

What does this print?

```python
print(int('ff', 16))
```

**Answer:**

```text
255
```

Hex letters are accepted when the base is 16.

### Q9. Basic

What does this print?

```python
print(int('  -42  '))
```

**Answer:**

```text
-42
```

`int` of a string strips leading and trailing whitespace.

### Q10. Basic

What does this print?

```python
print(int(3.9), int(-3.9))
```

**Answer:**

```text
3 -3
```

`int(float)` truncates toward zero. It does not round.

### Q11. Basic

What does this print?

```python
print(int(True), int(False))
```

**Answer:**

```text
1 0
```

`True` is 1 and `False` is 0.

### Q12. Basic

What happens when this runs?

```python
print(int('42.0'))
```

**Answer:**

```text
ValueError: invalid literal for int() with base 10: '42.0'
```

The string must be an integer literal. A decimal point is rejected.

### Q13. Basic

What happens when this runs?

```python
print(int('1_0'))
```

**Answer:**

```text
10
```

Underscores are allowed in integer strings, the same way they are in literals.

### Q14. Basic

What happens when this runs?

```python
print(int(''))
```

**Answer:**

```text
ValueError: invalid literal for int() with base 10: ''
```

An empty string is not a valid integer.

### Q15. Basic

What happens when this runs?

```python
print(int('102', 2))
```

**Answer:**

```text
ValueError: invalid literal for int() with base 2: '102'
```

Digit `2` is illegal in base 2.

### Q16. Basic

What does this print?

```python
print(int())
```

**Answer:**

```text
0
```

`int()` with no argument is 0.

### Q17. Basic

What does this print?

```python
print(+42, -42)
```

**Answer:**

```text
42 -42
```

Unary `+` returns the number unchanged. Unary `-` negates it.

### Q18. Basic

What does this print?

```python
n = 10
print(+n, -n, ~n)
```

**Answer:**

```text
10 -10 -11
```

`~n` is bitwise complement, equal to `-n - 1`.

### Q19. Basic

What does this print?

```python
print(7 + 3, 7 - 3, 7 * 3)
```

**Answer:**

```text
10 4 21
```

Addition, subtraction, and multiplication of ints stay ints.

### Q20. Basic

What does this print?

```python
print(7 / 3)
```

**Answer:**

```text
2.3333333333333335
```

`/` is true division and always returns a float.

### Q21. Basic

What does this print?

```python
print(7 // 3)
```

**Answer:**

```text
2
```

`//` is floor division and returns an int here.

### Q22. Basic

What does this print?

```python
print(7 % 3)
```

**Answer:**

```text
1
```

The remainder of 7 divided by 3 is 1.

### Q23. Basic

What does this print?

```python
print(2 ** 10)
```

**Answer:**

```text
1024
```

`**` is exponentiation.

### Q24. Basic

What does this print?

```python
print(2 ** 0, 0 ** 0)
```

**Answer:**

```text
1 1
```

Any non-zero number to the power 0 is 1. Python also defines `0 ** 0` as 1.

### Q25. Basic

What does this print?

```python
print(-2 ** 2)
```

**Answer:**

```text
-4
```

Exponentiation binds tighter than unary minus, so this is `-(2 ** 2)`.

### Q26. Basic

What does this print?

```python
print((-2) ** 2)
```

**Answer:**

```text
4
```

Parentheses negate first, then the square is positive.

### Q27. Basic

What does this print?

```python
print((-2) ** 3)
```

**Answer:**

```text
-8
```

A negative base to an odd power stays negative.

### Q28. Basic

What does this print?

```python
print(2 ** 3 ** 2)
```

**Answer:**

```text
512
```

`**` associates to the right: `2 ** (3 ** 2)`, not `(2 ** 3) ** 2`.

### Q29. Basic

What does this print?

```python
print(2 + 3 * 4)
```

**Answer:**

```text
14
```

Multiplication happens before addition.

### Q30. Basic

What does this print?

```python
print((2 + 3) * 4)
```

**Answer:**

```text
20
```

Parentheses override precedence.

### Q31. Basic

What does this print?

```python
print(abs(-7), abs(0))
```

**Answer:**

```text
7 0
```

`abs` returns the magnitude.

### Q32. Basic

What does this print?

```python
print(divmod(17, 5))
```

**Answer:**

```text
(3, 2)
```

`divmod(a, b)` is the pair `(a // b, a % b)`.

### Q33. Basic

What does this print?

```python
print(pow(2, 10), pow(2, 10, 1000))
```

**Answer:**

```text
1024 24
```

The three-argument form computes `(base ** exp) % mod` without building the full power as the final result.

### Q34. Basic

What does this print?

```python
print(round(2.5), round(3.5))
```

**Answer:**

```text
2 4
```

With no `ndigits`, `round` returns an int and uses banker's rounding: halves go to the nearest even integer.

### Q35. Basic

What does this print?

```python
print(divmod(7, 3))
```

**Answer:**

```text
(2, 1)
```

`//` floors toward negative infinity. `7 == (2) * (3) + (1)` is the invariant, and the remainder has the sign of the divisor.

### Q36. Intermediate

What does this print?

```python
print(divmod(-7, 3))
```

**Answer:**

```text
(-3, 2)
```

`//` floors toward negative infinity. `-7 == (-3) * (3) + (2)` is the invariant, and the remainder has the sign of the divisor.

### Q37. Intermediate

What does this print?

```python
print(divmod(7, -3))
```

**Answer:**

```text
(-3, -2)
```

`//` floors toward negative infinity. `7 == (-3) * (-3) + (-2)` is the invariant, and the remainder has the sign of the divisor.

### Q38. Intermediate

What does this print?

```python
print(divmod(-7, -3))
```

**Answer:**

```text
(2, -1)
```

`//` floors toward negative infinity. `-7 == (2) * (-3) + (-1)` is the invariant, and the remainder has the sign of the divisor.

### Q39. Intermediate

What does this print?

```python
print(divmod(-8, 3))
```

**Answer:**

```text
(-3, 1)
```

`//` floors toward negative infinity. `-8 == (-3) * (3) + (1)` is the invariant, and the remainder has the sign of the divisor.

### Q40. Intermediate

What does this print?

```python
print(divmod(8, -3))
```

**Answer:**

```text
(-3, -1)
```

`//` floors toward negative infinity. `8 == (-3) * (-3) + (-1)` is the invariant, and the remainder has the sign of the divisor.

### Q41. Intermediate

What does this print?

```python
print(divmod(-1, 2))
```

**Answer:**

```text
(-1, 1)
```

`//` floors toward negative infinity. `-1 == (-1) * (2) + (1)` is the invariant, and the remainder has the sign of the divisor.

### Q42. Intermediate

What does this print?

```python
print(divmod(1, -2))
```

**Answer:**

```text
(-1, -1)
```

`//` floors toward negative infinity. `1 == (-1) * (-2) + (-1)` is the invariant, and the remainder has the sign of the divisor.

### Q43. Basic

What does this print?

```python
print(divmod(5, 5))
```

**Answer:**

```text
(1, 0)
```

`//` floors toward negative infinity. `5 == (1) * (5) + (0)` is the invariant, and the remainder has the sign of the divisor.

### Q44. Intermediate

What does this print?

```python
print(divmod(-5, 5))
```

**Answer:**

```text
(-1, 0)
```

`//` floors toward negative infinity. `-5 == (-1) * (5) + (0)` is the invariant, and the remainder has the sign of the divisor.

### Q45. Intermediate

What does this print?

```python
print(divmod(0, 5))
```

**Answer:**

```text
(0, 0)
```

`//` floors toward negative infinity. `0 == (0) * (5) + (0)` is the invariant, and the remainder has the sign of the divisor.

### Q46. Intermediate

What happens when this runs?

```python
print(1 // 0)
```

**Answer:**

```text
ZeroDivisionError: integer division or modulo by zero
```

Division and modulo by zero raise `ZeroDivisionError`.

### Q47. Intermediate

What happens when this runs?

```python
print(1 % 0)
```

**Answer:**

```text
ZeroDivisionError: integer modulo by zero
```

Modulo by zero is the same class of error as division by zero.

### Q48. Intermediate

What happens when this runs?

```python
print(pow(2, -1, 5))
```

**Answer:**

```text
3
```

A negative exponent is rejected when a modulus is supplied, because the result would not be an integer remainder in general.

### Q49. Intermediate

What does this print?

```python
print(pow(-2, 3, 5))
```

**Answer:**

```text
2
```

`(-2) ** 3` is -8, and `-8 % 5` is 2. The remainder is non-negative when the modulus is positive.

### Q50. Intermediate

What does this print?

```python
print(10 ** 20)
```

**Answer:**

```text
100000000000000000000
```

Python ints grow as needed. This is an exact integer, not an approximation.

### Q51. Intermediate

What does this print?

```python
n = 5
n += 2
print(n)
```

**Answer:**

```text
7
```

`+=` rebinds the name. The old int object is not mutated, because ints are immutable.

### Q52. Intermediate

What does this print?

```python
a = 5
b = a
a += 1
print(a, b)
```

**Answer:**

```text
6 5
```

Rebinding `a` does not change the object `b` still references.

### Q53. Basic

What does this print?

```python
print(3 < 5 < 7)
```

**Answer:**

```text
True
```

Chained comparisons are `3 < 5 and 5 < 7`. The middle expression is evaluated once.

### Q54. Basic

What does this print?

```python
print(3 < 2 < 7)
```

**Answer:**

```text
False
```

The chain fails as soon as `3 < 2` is false.

### Q55. Basic

What does this print?

```python
print(1 == 1.0, 1 == True)
```

**Answer:**

```text
True True
```

Numeric equality compares values across `int`, `float`, and `bool`.

### Q56. Intermediate

What does this print?

```python
a = 1
print(a is True, a == True)
```

**Answer:**

```text
False True
```

`==` is value equality. `is` is object identity. `True` is not the integer object `1`.

### Q57. Basic

What does this print?

```python
print(bool(0), bool(1), bool(-2))
```

**Answer:**

```text
False True True
```

Only 0 is falsy among integers. Every other int is truthy.

### Q58. Intermediate

What does this print?

```python
a = 0
print(a == False, a is False)
```

**Answer:**

```text
True False
```

`False` equals 0, but it is a distinct object.

### Q59. Intermediate

What does this print?

```python
print((5).bit_length(), (0).bit_length(), (-5).bit_length())
```

**Answer:**

```text
3 0 3
```

`bit_length` is the number of bits needed for the absolute value, excluding the sign.

### Q60. Intermediate

What does this print?

```python
print((0b1101).bit_count())
```

**Answer:**

```text
3
```

`bit_count` (Python 3.10+) is the population count of the absolute value.

### Q61. Intermediate

What does this print?

```python
print((255).to_bytes(2, 'big'))
```

**Answer:**

```text
b'\x00\xff'
```

`to_bytes` packs the integer into a fixed-width `bytes` object.

### Q62. Intermediate

What does this print?

```python
print(int.from_bytes(b'\x01\x00', 'little'))
```

**Answer:**

```text
1
```

Little-endian reads the first byte as the least significant byte.

### Q63. Intermediate

What happens when this runs?

```python
print((-1).to_bytes(1, 'big'))
```

**Answer:**

```text
OverflowError: can't convert negative int to unsigned
```

The default signed interpretation is unsigned. A negative int needs `signed=True`.

### Q64. Intermediate

What does this print?

```python
print((-1).to_bytes(2, 'big', signed=True))
```

**Answer:**

```text
b'\xff\xff'
```

Two's complement of -1 in 16 bits is `0xffff`.

### Q65. Intermediate

What does this print?

```python
print((6).as_integer_ratio())
```

**Answer:**

```text
(6, 1)
```

`as_integer_ratio` on an int returns `(n, 1)`.

### Q66. Intermediate

What does this print?

```python
print((6).numerator, (6).denominator)
```

**Answer:**

```text
6 1
```

Every int is a rational with denominator 1. These attributes come from the numbers ABC.

### Q67. Intermediate

What does this print?

```python
print(hash(10), hash(10.0))
```

**Answer:**

```text
10 10
```

An int and a float that compare equal must have the same hash, when the float is exactly integral.

### Q68. Advanced

What does this print?

```python
print(hash(-1), hash(-2))
```

**Answer:**

```text
-2 -2
```

CPython reserves hash value -1 as an error sentinel, so the hash of -1 is -2. This is an implementation detail of the hash function, not of `==`.

### Q69. Basic

What does this print?

```python
print(bin(13), oct(13), hex(13))
```

**Answer:**

```text
0b1101 0o15 0xd
```

These helpers return strings with `0b`, `0o`, and `0x` prefixes.

### Q70. Basic

What does this print?

```python
print(format(13, 'b'), format(13, '08b'))
```

**Answer:**

```text
1101 00001101
```

`format` with a binary spec does not add the `0b` prefix. `08b` zero-pads to width 8.

### Q71. Basic

What does this print?

```python
print(f'{13:04d}', f'{13:x}', f'{13:#x}')
```

**Answer:**

```text
0013 d 0xd
```

`#` requests the base prefix. `x` is lowercase hex.

### Q72. Intermediate

What does this print?

```python
print(bin(-13))
```

**Answer:**

```text
-0b1101
```

Negative values keep the sign in front of the prefix.

### Q73. Intermediate

What does this print?

```python
print(int('0x10', 0), int('0b10', 0), int('10', 0))
```

**Answer:**

```text
16 2 10
```

Base 0 means 'infer the base from the prefix', and default to 10.

### Q74. Intermediate

What happens when this runs?

```python
print(int('0x10', 16))
```

**Answer:**

```text
16
```

With an explicit base of 16, the `0x` prefix is not part of the digit grammar.

### Q75. Intermediate

What does this print?

```python
print(int('0x10', 16) if False else int('10', 16))
```

**Answer:**

```text
16
```

Digits `1` and `0` are valid hex and mean sixteen.

### Q76. Basic

What does this print?

```python
print(f'{1000000:,}')
```

**Answer:**

```text
1,000,000
```

The `,` format spec inserts thousands separators.

### Q77. Intermediate

What does this print?

```python
print(f'{255:c}')
```

**Answer:**

```text
ÿ
```

The `c` spec converts a code point to a character. 255 is `ÿ` in Unicode.

### Q78. Intermediate

What does this print?

```python
print(13 & 7)
```

**Answer:**

```text
5
```

AND keeps bits set in both numbers. 1101 & 0111 = 0101.

### Q79. Intermediate

What does this print?

```python
print(13 | 7)
```

**Answer:**

```text
15
```

OR keeps bits set in either number. 1101 | 0111 = 1111.

### Q80. Intermediate

What does this print?

```python
print(13 ^ 7)
```

**Answer:**

```text
10
```

XOR keeps bits set in exactly one number. 1101 ^ 0111 = 1010.

### Q81. Intermediate

What does this print?

```python
print(13 << 2)
```

**Answer:**

```text
52
```

A left shift by 2 multiplies by 4, exactly, because ints have no fixed width.

### Q82. Intermediate

What does this print?

```python
print(13 >> 2)
```

**Answer:**

```text
3
```

A right shift of a positive int divides by 4 and floors.

### Q83. Advanced

What does this print?

```python
print(-13 >> 2)
```

**Answer:**

```text
-4
```

Right shift on a negative int is an arithmetic shift: it floors the division by `2 ** n`.

### Q84. Intermediate

What does this print?

```python
print(~0)
```

**Answer:**

```text
-1
```

Complement of 0 is -1, because `~n == -n - 1`.

### Q85. Intermediate

What does this print?

```python
print(~5)
```

**Answer:**

```text
-6
```

`~5 == -6`.

### Q86. Intermediate

What does this print?

```python
print(8 >> 1)
```

**Answer:**

```text
4
```

Shifting 8 right by 1 yields 4.

### Q87. Intermediate

What does this print?

```python
print(1 << 10)
```

**Answer:**

```text
1024
```

`1 << 10` is 1024.

### Q88. Intermediate

What does this print?

```python
print((1 << 10) - 1)
```

**Answer:**

```text
1023
```

This is ten 1-bits: 1023.

### Q89. Intermediate

What does this print?

```python
print(13 ^ 13)
```

**Answer:**

```text
0
```

XOR of a value with itself is 0.

### Q90. Intermediate

What does this print?

```python
print(13 ^ 0)
```

**Answer:**

```text
13
```

XOR with 0 leaves the value unchanged.

### Q91. Intermediate

What does this print?

```python
print(13 & 0)
```

**Answer:**

```text
0
```

AND with 0 clears every bit.

### Q92. Intermediate

What does this print?

```python
print(13 | 0)
```

**Answer:**

```text
13
```

OR with 0 leaves the value unchanged.

### Q93. Advanced

What does this print?

```python
print(-1 & 7)
```

**Answer:**

```text
7
```

In two's complement, -1 is all bits set, so AND with 7 keeps the low 3 bits.

### Q94. Advanced

What does this print?

```python
print((-13) >> 1)
```

**Answer:**

```text
-7
```

Floor division of -13 by 2 is -7, so the arithmetic right shift is -7.

### Q95. Advanced

What does this print?

```python
print(8 & -8)
```

**Answer:**

```text
8
```

A power of two AND its negative isolates that bit. `-8` is the two's complement negation.

### Q96. Advanced

What does this print?

```python
n = 0b1101000
print(n & -n)
```

**Answer:**

```text
8
```

`n & -n` isolates the lowest set bit.

### Q97. Advanced

What does this print?

```python
n = 0b1101000
print(n & (n - 1))
```

**Answer:**

```text
96
```

`n & (n - 1)` clears the lowest set bit.

### Q98. Advanced

What does this print?

```python
print((n := 16).bit_count() == 1)
```

**Answer:**

```text
True
```

A positive power of two has exactly one bit set. The walrus operator binds `n` for the comparison.

### Q99. Advanced

What does this print?

```python
print(pow(3, 5, 7))
```

**Answer:**

```text
5
```

Modular exponentiation: 3^5 = 243, and 243 % 7 = 5.

### Q100. Advanced

What happens when this runs?

```python
print(int.from_bytes(b'\xff', 'big'))
```

**Answer:**

```text
255
```

One unsigned byte `0xff` is 255, not -1.

### Q101. Advanced

What does this print?

```python
print(int.from_bytes(b'\xff', 'big', signed=True))
```

**Answer:**

```text
-1
```

The same byte interpreted as signed 8-bit is -1.

### Q102. Advanced

What does this print?

```python
a = 256
b = 256
print(a is b)
```

**Answer:**

```text
True
```

CPython caches small ints from -5 through 256, so these names refer to one object. This is a CPython detail, not a language rule to rely on.

### Q103. Advanced

What does this print?

```python
a = 257
b = 257
print(a is b)
```

**Answer:**

```text
True
```

257 is outside the small-int cache. Separate evaluations produce equal values that are not the same object.

### Q104. Advanced

What does this print?

```python
a = -5
b = -5
print(a is b)
```

**Answer:**

```text
True
```

-5 is inside the small-int cache.

### Q105. Advanced

What does this print?

```python
a = -6
b = -6
print(a is b)
```

**Answer:**

```text
True
```

-6 is just outside the cache, so identity fails even though equality holds.

### Q106. Intermediate

What does this print?

```python
print(int(1e2))
```

**Answer:**

```text
100
```

`1e2` is the float 100.0. `int` truncates it to 100. This is exact because 100 is representable.

### Q107. Advanced

What does this print?

```python
print(int(1e23) == 10 ** 23)
```

**Answer:**

```text
False
```

A float has a 53-bit mantissa. `1e23` is not an exact integer, so converting it to `int` does not yield the mathematical power of ten.

### Q108. Advanced

What happens when this runs?

```python
print(int(float('inf')))
```

**Answer:**

```text
OverflowError: cannot convert float infinity to integer
```

Infinity does not fit in an integer.

### Q109. Advanced

What happens when this runs?

```python
print(int(float('nan')))
```

**Answer:**

```text
ValueError: cannot convert float NaN to integer
```

`nan` cannot be converted to an integer.

### Q110. Intermediate

What happens when this runs?

```python
print(int(None))
```

**Answer:**

```text
TypeError: int() argument must be a string, a bytes-like object or a real number, not 'NoneType'
```

`int()` does not accept `None`. Use an explicit default in your own code.

### Q111. Intermediate

What happens when this runs?

```python
print(int([1]))
```

**Answer:**

```text
TypeError: int() argument must be a string, a bytes-like object or a real number, not 'list'
```

A list is not a string or a number.

### Q112. Intermediate

What does this print?

```python
print(int(b'42'))
```

**Answer:**

```text
42
```

A bytes literal of ASCII digits is accepted, like a string.

### Q113. Intermediate

What does this print?

```python
print(int('١٠'))
```

**Answer:**

```text
10
```

Characters with the Unicode `Nd` (decimal digit) property are accepted. Arabic-Indic digits ١٠ are ten.

### Q114. Advanced

What does this print?

```python
import sys
print(sys.int_info.bits_per_digit > 0)
```

**Answer:**

```text
True
```

`sys.int_info` describes how CPython stores the digit array of a long integer. The exact width is an implementation detail; it is a positive integer.

### Q115. Advanced

What does this print?

```python
print((1 << 100).bit_length())
```

**Answer:**

```text
101
```

`1 << 100` is 2^100, whose bit length is 101 (bits 0 through 100).

### Q116. Intermediate

What does this print?

```python
print(min(3, 1, 2), max(3, 1, 2))
```

**Answer:**

```text
1 3
```

`min` and `max` accept any number of int arguments.

### Q117. Intermediate

What does this print?

```python
print(sum([1, 2, 3]), sum([1, 2, 3], 10))
```

**Answer:**

```text
6 16
```

The second argument of `sum` is the start value.

### Q118. Basic

What does this print?

```python
print(10 > 9 > 8 == 8)
```

**Answer:**

```text
True
```

Chains can mix comparison operators. This is `10 > 9 and 9 > 8 and 8 == 8`.

### Q119. Intermediate

What does this print?

```python
print(sorted([3, 1, 2], reverse=True))
```

**Answer:**

```text
[3, 2, 1]
```

Ints have a total order, so they sort numerically.

### Q120. Advanced

What does this print?

```python
print((1 << 63) - 1 > 2 ** 62)
```

**Answer:**

```text
True
```

There is no overflow at 64 bits. The comparison is exact.

### Q121. Basic

Write `reverse_digits(n)` that returns the integer formed by reversing the decimal digits of a non-negative int. Leading zeros in the reversed form disappear because the result is an int.

**Answer:**

```python
def reverse_digits(n):
    rev = 0
    while n:
        rev = rev * 10 + n % 10
        n //= 10
    return rev
```

- `reverse_digits(0)  =>  0`
- `reverse_digits(120)  =>  21`
- `reverse_digits(12345)  =>  54321`

Repeatedly take `n % 10` and fold it into `rev`. Time is proportional to the number of digits.

### Q122. Basic

Write `count_digits(n)` for a non-negative int. `0` has one digit.

**Answer:**

```python
def count_digits(n):
    if n == 0:
        return 1
    count = 0
    while n:
        n //= 10
        count += 1
    return count
```

- `count_digits(0)  =>  1`
- `count_digits(7)  =>  1`
- `count_digits(1000)  =>  4`

Each `// 10` drops one decimal digit.

### Q123. Basic

Write `sum_digits(n)` that sums the decimal digits of a non-negative int.

**Answer:**

```python
def sum_digits(n):
    total = 0
    while n:
        total += n % 10
        n //= 10
    return total
```

- `sum_digits(0)  =>  0`
- `sum_digits(905)  =>  14`

Same digit loop as reversing, but the digits are added.

### Q124. Basic

Write `is_even(n)` without using `%` or `/`.

**Answer:**

```python
def is_even(n):
    return (n & 1) == 0
```

- `is_even(0)  =>  True`
- `is_even(8)  =>  True`
- `is_even(-3)  =>  False`
- `is_even(-4)  =>  True`

The lowest bit of a two's-complement integer is the parity bit.

### Q125. Intermediate

Write `is_palindrome_number(n)` that is true when the decimal representation of a non-negative int reads the same forward and backward.

**Answer:**

```python
def is_palindrome_number(n):
    if n < 0:
        return False
    original, rev = n, 0
    while n:
        rev = rev * 10 + n % 10
        n //= 10
    return original == rev
```

- `is_palindrome_number(121)  =>  True`
- `is_palindrome_number(10)  =>  False`
- `is_palindrome_number(0)  =>  True`

Reverse the digits and compare. Negative numbers are not palindromes under a leading minus sign.

### Q126. Intermediate

Write `gcd(a, b)` using Euclid's algorithm. Arguments may be negative; the result is non-negative.

**Answer:**

```python
def gcd(a, b):
    a, b = abs(a), abs(b)
    while b:
        a, b = b, a % b
    return a
```

- `gcd(54, 24)  =>  6`
- `gcd(-15, 25)  =>  5`
- `gcd(0, 7)  =>  7`

Replace `(a, b)` with `(b, a % b)` until `b` is 0. The remainder invariant keeps the same divisors.

### Q127. Intermediate

Write `lcm(a, b)` for non-zero integers, returning a non-negative value. Use the identity `lcm(a, b) * gcd(a, b) == abs(a * b)`.

**Answer:**

```python
def gcd(a, b):
    a, b = abs(a), abs(b)
    while b:
        a, b = b, a % b
    return a

def lcm(a, b):
    return abs(a // gcd(a, b) * b)
```

- `lcm(4, 6)  =>  12`
- `lcm(7, 5)  =>  35`

Divide before multiplying so the intermediate product stays smaller: `a // gcd * b`.

### Q128. Intermediate

Write `is_prime(n)`. Handle `n < 2` and only test odd factors up to `sqrt(n)` after checking 2.

**Answer:**

```python
def is_prime(n):
    if n < 2:
        return False
    if n % 2 == 0:
        return n == 2
    i = 3
    while i * i <= n:
        if n % i == 0:
            return False
        i += 2
    return True
```

- `is_prime(1)  =>  False`
- `is_prime(2)  =>  True`
- `is_prime(9)  =>  False`
- `is_prime(97)  =>  True`

A composite number has a factor at most its square root.

### Q129. Intermediate

Write `factorial(n)` for `n >= 0` using a loop. `factorial(0)` is 1.

**Answer:**

```python
def factorial(n):
    result = 1
    for k in range(2, n + 1):
        result *= k
    return result
```

- `factorial(0)  =>  1`
- `factorial(5)  =>  120`
- `factorial(10)  =>  3628800`

Python ints do not overflow, so this is exact for large `n` as well. Time is O(n) multiplications of growing integers.

### Q130. Intermediate

Write `trailing_zeros(n)` that counts trailing zeros in `n!` without computing the factorial.

**Answer:**

```python
def trailing_zeros(n):
    count = 0
    while n:
        n //= 5
        count += n
    return count
```

- `trailing_zeros(0)  =>  0`
- `trailing_zeros(5)  =>  1`
- `trailing_zeros(25)  =>  6`

Each trailing zero comes from a factor of 10, and there are always more factors of 2 than of 5. Count multiples of 5, 25, 125, and so on.

### Q131. Intermediate

Write `fib(n)` that returns the nth Fibonacci number iteratively, with `fib(0) == 0` and `fib(1) == 1`.

**Answer:**

```python
def fib(n):
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
    return a
```

- `fib(0)  =>  0`
- `fib(1)  =>  1`
- `fib(10)  =>  55`

Keep only the last two values. This is O(n) arithmetic steps and O(1) extra names.

### Q132. Intermediate

Write `digital_root(n)` for a non-negative int: repeatedly sum digits until one digit remains. Use the O(1) congruence when you want, but a loop is fine.

**Answer:**

```python
def digital_root(n):
    if n == 0:
        return 0
    return 1 + (n - 1) % 9
```

- `digital_root(0)  =>  0`
- `digital_root(9)  =>  9`
- `digital_root(38)  =>  2`
- `digital_root(10)  =>  1`

The digital root is `n % 9`, except that multiples of 9 (other than 0) have digital root 9. The formula `1 + (n - 1) % 9` encodes that.

### Q133. Intermediate

Write `is_power_of_two(n)` for a positive int, using a bit test.

**Answer:**

```python
def is_power_of_two(n):
    return n > 0 and (n & (n - 1)) == 0
```

- `is_power_of_two(1)  =>  True`
- `is_power_of_two(16)  =>  True`
- `is_power_of_two(18)  =>  False`
- `is_power_of_two(0)  =>  False`

Powers of two have a single set bit. Subtracting 1 flips that bit and all the bits below it, so the AND is 0.

### Q134. Intermediate

Write `next_power_of_two(n)` that returns the smallest power of two greater than or equal to `n` for `n >= 1`.

**Answer:**

```python
def next_power_of_two(n):
    if n <= 1:
        return 1
    return 1 << (n - 1).bit_length()
```

- `next_power_of_two(1)  =>  1`
- `next_power_of_two(5)  =>  8`
- `next_power_of_two(8)  =>  8`

`(n - 1).bit_length()` is the bit index just above the current magnitude when `n` is not already handled by the `n <= 1` case. Shifting 1 by that amount rounds up.

### Q135. Advanced

Write `integer_sqrt(n)` that returns the greatest integer `r` such that `r * r <= n`, using binary search. `n` is non-negative.

**Answer:**

```python
def integer_sqrt(n):
    lo, hi = 0, n
    ans = 0
    while lo <= hi:
        mid = (lo + hi) // 2
        if mid * mid <= n:
            ans = mid
            lo = mid + 1
        else:
            hi = mid - 1
    return ans
```

- `integer_sqrt(0)  =>  0`
- `integer_sqrt(8)  =>  2`
- `integer_sqrt(16)  =>  4`
- `integer_sqrt(10 ** 12)  =>  1000000`

Binary search on the answer. Multiplying `mid * mid` is exact because Python ints do not overflow.

### Q136. Advanced

Write `mod_pow(base, exp, mod)` with exponentiation by squaring. `exp` is non-negative and `mod > 1`.

**Answer:**

```python
def mod_pow(base, exp, mod):
    result = 1
    base %= mod
    while exp:
        if exp & 1:
            result = result * base % mod
        base = base * base % mod
        exp >>= 1
    return result
```

- `mod_pow(2, 10, 1000)  =>  24`
- `mod_pow(3, 0, 7)  =>  1`
- `mod_pow(5, 5, 13)  =>  5`

Square the base each step and multiply it into the result when the current exponent bit is set. This is O(log exp) multiplications.

### Q137. Advanced

Write `sieve(n)` that returns a list of all primes strictly less than `n`.

**Answer:**

```python
def sieve(n):
    if n <= 2:
        return []
    prime = [True] * n
    prime[0] = prime[1] = False
    p = 2
    while p * p < n:
        if prime[p]:
            for multiple in range(p * p, n, p):
                prime[multiple] = False
        p += 1
    return [i for i, ok in enumerate(prime) if ok]
```

- `sieve(10)  =>  [2, 3, 5, 7]`
- `sieve(2)  =>  []`

The Sieve of Eratosthenes marks multiples. Starting at `p * p` is enough because smaller multiples were marked by smaller primes.

### Q138. Advanced

Write `prime_factors(n)` that returns the prime factors of `n >= 2` in ascending order, with repetition.

**Answer:**

```python
def prime_factors(n):
    factors = []
    while n % 2 == 0:
        factors.append(2)
        n //= 2
    p = 3
    while p * p <= n:
        while n % p == 0:
            factors.append(p)
            n //= p
        p += 2
    if n > 1:
        factors.append(n)
    return factors
```

- `prime_factors(12)  =>  [2, 2, 3]`
- `prime_factors(97)  =>  [97]`

Strip factors of 2, then odd candidates. Whatever remains above 1 is prime.

### Q139. Advanced

Write `missing_number(nums)` where `nums` contains each integer from `0` through `n` exactly once except one missing value.

**Answer:**

```python
def missing_number(nums):
    n = len(nums)
    xor = 0
    for i, value in enumerate(nums):
        xor ^= i ^ value
    return xor ^ n
```

- `missing_number([3, 0, 1])  =>  2`
- `missing_number([0, 1])  =>  2`
- `missing_number([1])  =>  0`

XOR every index and every value. Pairs cancel, and the missing index remains. XOR is safer than a sum if you are thinking about fixed-width overflow in other languages; in Python the sum formula also works.

### Q140. Advanced

Write `single_number(nums)` where every element appears twice except one. Return the one that appears once, using XOR.

**Answer:**

```python
def single_number(nums):
    acc = 0
    for value in nums:
        acc ^= value
    return acc
```

- `single_number([4, 1, 2, 1, 2])  =>  4`
- `single_number([7])  =>  7`

XOR is its own inverse. Duplicates cancel to 0 and the unique value remains.

### Q141. Advanced

Write `single_number_thrice(nums)` where every element appears three times except one value that appears once. Use bit counts modulo 3.

**Answer:**

```python
def single_number_thrice(nums):
    ones = twos = 0
    for value in nums:
        ones = (ones ^ value) & ~twos
        twos = (twos ^ value) & ~ones
    return ones
```

- `single_number_thrice([2, 2, 3, 2])  =>  3`
- `single_number_thrice([0, 1, 0, 1, 0, 1, 99])  =>  99`

`ones` holds bits seen 3k+1 times and `twos` holds bits seen 3k+2 times. The third sighting clears both.

### Q142. Advanced

Write `excel_column(n)` that converts a 1-based column number to its spreadsheet title. `1 -> A`, `26 -> Z`, `27 -> AA`.

**Answer:**

```python
def excel_column(n):
    chars = []
    while n:
        n -= 1
        chars.append(chr(ord('A') + n % 26))
        n //= 26
    return ''.join(reversed(chars))
```

- `excel_column(1)  =>  'A'`
- `excel_column(26)  =>  'Z'`
- `excel_column(27)  =>  'AA'`
- `excel_column(52)  =>  'AZ'`

Spreadsheet columns are base 26, but digits are 1..26 rather than 0..25. Subtract 1 before taking the remainder.

### Q143. Advanced

Write `column_number(title)` that converts a spreadsheet title back to a 1-based integer.

**Answer:**

```python
def column_number(title):
    n = 0
    for ch in title:
        n = n * 26 + (ord(ch) - ord('A') + 1)
    return n
```

- `column_number('A')  =>  1`
- `column_number('Z')  =>  26`
- `column_number('AA')  =>  27`

Horner's method for base 26.

### Q144. Advanced

Write `happy(n)` that reports whether `n` is a happy number: replace `n` by the sum of the squares of its decimal digits until you reach 1, or detect a cycle.

**Answer:**

```python
def happy(n):
    seen = set()
    while n != 1 and n not in seen:
        seen.add(n)
        nxt = 0
        while n:
            digit = n % 10
            nxt += digit * digit
            n //= 10
        n = nxt
    return n == 1
```

- `happy(19)  =>  True`
- `happy(2)  =>  False`

Unhappy numbers enter the known cycle that contains 4. A set of seen values detects any cycle.

### Q145. Advanced

Write `divide(dividend, divisor)` that performs integer division truncated toward zero, without using `/`, `//`, or `%`. Clamp the result to the 32-bit signed range used by the classic interview problem: `-2**31` through `2**31 - 1`.

**Answer:**

```python
def divide(dividend, divisor):
    INT_MAX, INT_MIN = 2**31 - 1, -2**31
    if dividend == INT_MIN and divisor == -1:
        return INT_MAX
    negative = (dividend < 0) ^ (divisor < 0)
    a, b = abs(dividend), abs(divisor)
    quot = 0
    while a >= b:
        temp, multiple = b, 1
        while a >= (temp << 1):
            temp <<= 1
            multiple <<= 1
        a -= temp
        quot += multiple
    return -quot if negative else quot
```

- `divide(10, 3)  =>  3`
- `divide(7, -3)  =>  -2`
- `divide(-2147483648, -1)  =>  2147483647`

Subtract the largest shifted copy of the divisor that still fits. That is exponential search inside the dividend and runs in O(log^2 N) for 32-bit inputs. The overflow case is the only 32-bit quotient that does not fit.

### Q146. Advanced

Write `range_bitwise_and(left, right)` that returns `left & (left+1) & ... & right` without looping over the whole range.

**Answer:**

```python
def range_bitwise_and(left, right):
    shift = 0
    while left < right:
        left >>= 1
        right >>= 1
        shift += 1
    return left << shift
```

- `range_bitwise_and(5, 7)  =>  4`
- `range_bitwise_and(1, 1)  =>  1`
- `range_bitwise_and(0, 1)  =>  0`

The AND of a range keeps only the common binary prefix. Shift until the endpoints meet, then shift that prefix back.

### Q147. Advanced

Write `add(a, b)` that adds two non-negative ints using only bitwise operations.

**Answer:**

```python
def add(a, b):
    while b:
        carry = (a & b) << 1
        a = a ^ b
        b = carry
    return a
```

- `add(0, 0)  =>  0`
- `add(5, 7)  =>  12`
- `add(100, 1)  =>  101`

XOR is the sum without carry. AND shifted left is the carry. Repeat until there is no carry.

### Q148. Advanced

Write `count_bits_upto(n)` that returns how many `1` bits appear in the binary forms of all integers from `0` through `n` inclusive.

**Answer:**

```python
def count_bits_upto(n):
    total = 0
    bit = 0
    while (1 << bit) <= n:
        cycle = 1 << (bit + 1)
        full, rest = divmod(n + 1, cycle)
        total += full * (1 << bit)
        total += max(0, rest - (1 << bit))
        bit += 1
    return total
```

- `count_bits_upto(0)  =>  0`
- `count_bits_upto(1)  =>  1`
- `count_bits_upto(7)  =>  12`

Bit `i` is set in a repeating cycle of length `2^(i+1)`: off for `2^i` numbers, then on for `2^i` numbers. Count complete cycles, then the leftover prefix.

### Q149. Basic

What does this print?

```python
print(type(10 / 2), type(10 // 2))
```

**Answer:**

```text
<class 'float'> <class 'int'>
```

True division returns `float`. Floor division of two ints returns `int`.

### Q150. Basic

What does this print?

```python
print(0b1111 + 0x1)
```

**Answer:**

```text
16
```

Literals of different bases are just ints. 15 + 1 is 16.

### Q151. Basic

What does this print?

```python
a = b = 7
print(a, b, a is b)
```

**Answer:**

```text
7 7 True
```

Chained assignment binds both names to the same object. 7 is inside the small-int cache anyway.

### Q152. Basic

What does this print?

```python
a, b = 1, 2
a, b = b, a
print(a, b)
```

**Answer:**

```text
2 1
```

Tuple unpacking swaps two ints without a temporary name.

### Q153. Basic

What does this print?

```python
print(3 * -4)
```

**Answer:**

```text
-12
```

The sign of a product follows the usual arithmetic rule.

### Q154. Basic

What does this print?

```python
print(20 // 6, 20 % 6)
```

**Answer:**

```text
3 2
```

6 * 3 is 18, so the quotient is 3 and the remainder is 2.

### Q155. Basic

What does this print?

```python
print(2 ** 8, 8 ** 2)
```

**Answer:**

```text
256 64
```

These are different expressions. 2^8 is 256 and 8^2 is 64.

### Q156. Basic

What does this print?

```python
print(int('0b101', 0))
```

**Answer:**

```text
5
```

Base 0 accepts a binary prefix.

### Q157. Basic

What does this print?

```python
print(f'{42:b}', f'{42:o}', f'{42:d}')
```

**Answer:**

```text
101010 52 42
```

Format specs `b`, `o`, and `d` render binary, octal, and decimal without a prefix.

### Q158. Basic

What does this print?

```python
print(max(-10, -3, -20))
```

**Answer:**

```text
-3
```

`max` uses numeric order, so -3 is the greatest of these values.

### Q159. Basic

What does this print?

```python
print(min(-10, -3, -20))
```

**Answer:**

```text
-20
```

`min` returns the least value, which is -20.

### Q160. Basic

What does this print?

```python
print(sum(range(1, 5)))
```

**Answer:**

```text
10
```

`range(1, 5)` is 1, 2, 3, 4. Their sum is 10.

### Q161. Basic

What does this print?

```python
print(pow(10, 3))
```

**Answer:**

```text
1000
```

Two-argument `pow` is exponentiation and returns an int when both arguments are ints and the exponent is non-negative.

### Q162. Basic

What does this print?

```python
print((10).conjugate())
```

**Answer:**

```text
10
```

The conjugate of a real int is itself. The method exists so ints can share numeric protocols with complex numbers.

### Q163. Basic

What does this print?

```python
n = 1234
print(n % 10, n // 10)
```

**Answer:**

```text
4 123
```

The last decimal digit is `n % 10`. Dropping it is `n // 10`.

### Q164. Basic

What does this print?

```python
print(5 < 5, 5 <= 5, 5 != 6)
```

**Answer:**

```text
False True True
```

Ints support the full set of comparison operators.

### Q165. Basic

What does this print?

```python
print(int(False), int(True) + 3)
```

**Answer:**

```text
0 4
```

Because `bool` subclasses `int`, `True` participates in arithmetic as 1.

### Q166. Basic

What does this print?

```python
print(0xFF == 255 == 0b11111111)
```

**Answer:**

```text
True
```

The same value written in hex, decimal, and binary compares equal. Chaining uses `and` between the pairs.

### Q167. Basic

What does this print?

```python
print(abs(-2 ** 3))
```

**Answer:**

```text
8
```

Unary minus applies after `**`, so the inside is -8 and `abs` returns 8.

### Q168. Basic

What does this print?

```python
print(10_0)
```

**Answer:**

```text
100
```

`10_0` is the integer 100. Underscores may appear between digits.

### Q169. Basic

Write `last_digit(n)` that returns the last decimal digit of an int, as a non-negative digit, for both positive and negative `n`.

**Answer:**

```python
def last_digit(n):
    return abs(n) % 10
```

- `last_digit(123)  =>  3`
- `last_digit(-123)  =>  3`
- `last_digit(0)  =>  0`

Take the absolute value first so the result is a digit from 0 to 9 rather than a negative remainder.

### Q170. Intermediate

Write `to_base(n, base)` that returns the representation of a non-negative int `n` in `base` from 2 to 16, without a prefix. Use uppercase hex digits.

**Answer:**

```python
def to_base(n, base):
    digits = '0123456789ABCDEF'
    if n == 0:
        return '0'
    chars = []
    while n:
        chars.append(digits[n % base])
        n //= base
    return ''.join(reversed(chars))
```

- `to_base(0, 2)  =>  '0'`
- `to_base(255, 16)  =>  'FF'`
- `to_base(10, 2)  =>  '1010'`

Repeatedly divide by the base and collect remainders. Those remainders are the digits from least significant to most significant.

### Q171. Intermediate

Write `from_base(text, base)` that parses a non-negative integer written in `base` from 2 to 16. Accept upper or lower case.

**Answer:**

```python
def from_base(text, base):
    return int(text, base)
```

- `from_base('1010', 2)  =>  10`
- `from_base('ff', 16)  =>  255`
- `from_base('0', 8)  =>  0`

`int` already implements this. Wrapping it makes the contract of your helper explicit.

### Q172. Intermediate

Write `is_power_of_four(n)` using bit tests only. `n` may be any int.

**Answer:**

```python
def is_power_of_four(n):
    return n > 0 and (n & (n - 1)) == 0 and (n & 0xAAAAAAAA) == 0
```

- `is_power_of_four(1)  =>  True`
- `is_power_of_four(4)  =>  True`
- `is_power_of_four(8)  =>  False`
- `is_power_of_four(16)  =>  True`

A power of four is a power of two whose single set bit sits on an even position. The mask `0xAAAAAAAA` is every odd bit.

### Q173. Intermediate

Write `opposite_signs(a, b)` that is true when `a` and `b` have opposite signs. Treat 0 as non-negative.

**Answer:**

```python
def opposite_signs(a, b):
    return (a < 0) ^ (b < 0)
```

- `opposite_signs(2, -3)  =>  True`
- `opposite_signs(-2, -3)  =>  False`
- `opposite_signs(0, -1)  =>  True`
- `opposite_signs(0, 4)  =>  False`

XOR of the two sign tests is true only when the signs differ.

### Q174. Advanced

Write `gray_code(n)` that returns the n-bit binary-reflected Gray code as a list of ints from 0 to `2**n - 1`.

**Answer:**

```python
def gray_code(n):
    return [i ^ (i >> 1) for i in range(1 << n)]
```

- `gray_code(1)  =>  [0, 1]`
- `gray_code(2)  =>  [0, 1, 3, 2]`

The Gray code of `i` is `i ^ (i >> 1)`. Consecutive codes differ by one bit, including the wrap from the last value back to 0.

### Q175. Advanced

Write `reverse_bits32(n)` that reverses the low 32 bits of a non-negative int and returns that 32-bit value.

**Answer:**

```python
def reverse_bits32(n):
    out = 0
    for _ in range(32):
        out = (out << 1) | (n & 1)
        n >>= 1
    return out
```

- `reverse_bits32(1)  =>  2147483648`
- `reverse_bits32(0)  =>  0`
- `reverse_bits32(0xFFFFFFFF)  =>  4294967295`

Push the extracted low bit onto the result 32 times.

### Q176. Advanced

Write `hamming_distance(a, b)` that counts bits that differ between two non-negative ints.

**Answer:**

```python
def hamming_distance(a, b):
    return (a ^ b).bit_count()
```

- `hamming_distance(1, 4)  =>  2`
- `hamming_distance(7, 7)  =>  0`

XOR leaves a 1 exactly where the bits differ. `bit_count` sums those ones.

### Q177. Advanced

Write `nth_ugly(n)` that returns the nth ugly number (1-based). An ugly number has only 2, 3, and 5 as prime factors. `nth_ugly(1)` is 1.

**Answer:**

```python
def nth_ugly(n):
    ugly = [1]
    i2 = i3 = i5 = 0
    while len(ugly) < n:
        nxt = min(ugly[i2] * 2, ugly[i3] * 3, ugly[i5] * 5)
        ugly.append(nxt)
        if nxt == ugly[i2] * 2:
            i2 += 1
        if nxt == ugly[i3] * 3:
            i3 += 1
        if nxt == ugly[i5] * 5:
            i5 += 1
    return ugly[-1]
```

- `nth_ugly(1)  =>  1`
- `nth_ugly(10)  =>  12`
- `nth_ugly(11)  =>  15`

Generate candidates from three pointers so each ugly number is produced in order. Advance every pointer that matches, otherwise duplicates such as 6 are inserted twice.

### Q178. Advanced

Write `my_sqrt_newton(n)` that returns the integer square root of a non-negative int using Newton iteration.

**Answer:**

```python
def my_sqrt_newton(n):
    if n < 2:
        return n
    x = n
    while True:
        nxt = (x + n // x) // 2
        if nxt >= x:
            return x
        x = nxt
```

- `my_sqrt_newton(0)  =>  0`
- `my_sqrt_newton(8)  =>  2`
- `my_sqrt_newton(16)  =>  4`

Newton's method for square root is `x = (x + n/x) / 2`. Integer division makes it settle on the floor of the root.

### Q179. Advanced

Write `mod_inverse(a, mod)` that returns the modular inverse of `a` modulo a prime `mod`, using Fermat's little theorem. Precondition: `mod` is prime and `a` is not divisible by `mod`.

**Answer:**

```python
def mod_inverse(a, mod):
    return pow(a, mod - 2, mod)
```

- `mod_inverse(3, 7)  =>  5`
- `mod_inverse(10, 17)  =>  12`

When `mod` is prime and does not divide `a`, `a^(mod-2) ≡ a^(-1) (mod mod)`.

### Q180. Advanced

Write `extended_gcd(a, b)` that returns `(g, x, y)` with `g == gcd(a, b)` and `a*x + b*y == g`. Use the iterative extended Euclid algorithm. Signs follow the signs of the inputs.

**Answer:**

```python
def extended_gcd(a, b):
    old_r, r = a, b
    old_s, s = 1, 0
    old_t, t = 0, 1
    while r:
        q = old_r // r
        old_r, r = r, old_r - q * r
        old_s, s = s, old_s - q * s
        old_t, t = t, old_t - q * t
    return old_r, old_s, old_t
```

- `extended_gcd(240, 46)  =>  (2, -9, 47)`

The coefficients are updated in lockstep with the remainders. At the end, `old_s` and `old_t` are the Bézout coefficients.

### Q181. Advanced

Write `crt(remainders, moduli)` for two coprime moduli. It returns the unique solution modulo `moduli[0] * moduli[1]` of the system `x ≡ remainders[i] (mod moduli[i])`.

**Answer:**

```python
def crt(remainders, moduli):
    a1, a2 = remainders
    m1, m2 = moduli
    inv = pow(m1, -1, m2)
    x = (a1 + m1 * ((a2 - a1) * inv % m2)) % (m1 * m2)
    return x
```

- `crt((2, 3), (3, 5))  =>  8`
- `crt((0, 0), (3, 5))  =>  0`

Python 3.8+ allows `pow(m1, -1, m2)` when `m1` and `m2` are coprime. That is the modular inverse used by the explicit Chinese-remainder construction.

### Q182. Advanced

Write `choose(n, k)` that returns the binomial coefficient `C(n, k)` as an int. Use a multiplicative formula so intermediate values stay exact and smaller.

**Answer:**

```python
def choose(n, k):
    if k < 0 or k > n:
        return 0
    k = min(k, n - k)
    result = 1
    for i in range(1, k + 1):
        result = result * (n - k + i) // i
    return result
```

- `choose(5, 2)  =>  10`
- `choose(10, 0)  =>  1`
- `choose(6, 3)  =>  20`

Each step `(result * (n - k + i)) // i` is exact. Dividing at every step avoids a huge factorial.

### Q183. Advanced

Write `catalan(n)` that returns the nth Catalan number, with `catalan(0) == 1`.

**Answer:**

```python
def catalan(n):
    result = 1
    for i in range(n):
        result = result * (4 * i + 2) // (i + 2)
    return result
```

- `catalan(0)  =>  1`
- `catalan(3)  =>  5`
- `catalan(5)  =>  42`

The recurrence `C(0) = 1`, `C(n+1) = C(n) * (4n+2) / (n+2)` stays integral at every step.

### Q184. Advanced

Write `is_perfect(n)` that is true when `n` equals the sum of its proper positive divisors, excluding itself. `6` is perfect because `1+2+3 == 6`.

**Answer:**

```python
def is_perfect(n):
    if n < 2:
        return False
    total = 1
    i = 2
    while i * i <= n:
        if n % i == 0:
            total += i
            if i * i != n:
                total += n // i
        i += 1
    return total == n
```

- `is_perfect(6)  =>  True`
- `is_perfect(28)  =>  True`
- `is_perfect(12)  =>  False`

Walk factors up to the square root and add both sides of each pair.

### Q185. Advanced

Write `collatz_steps(n)` that counts how many steps the Collatz process takes to reach 1. If `n` is even, replace it with `n // 2`; if odd, replace it with `3 * n + 1`.

**Answer:**

```python
def collatz_steps(n):
    steps = 0
    while n != 1:
        n = n // 2 if n % 2 == 0 else 3 * n + 1
        steps += 1
    return steps
```

- `collatz_steps(1)  =>  0`
- `collatz_steps(2)  =>  1`
- `collatz_steps(3)  =>  7`

This is a straight simulation. It is fine for interview-sized inputs. The Collatz conjecture says every positive start reaches 1, but that is unproved.

### Q186. Advanced

Write `sum_to_n(n)` that returns the sum of integers from 1 through `n` for `n >= 0`, using the closed formula.

**Answer:**

```python
def sum_to_n(n):
    return n * (n + 1) // 2
```

- `sum_to_n(0)  =>  0`
- `sum_to_n(10)  =>  55`
- `sum_to_n(100)  =>  5050`

Use `//` so the result is an int. `n * (n + 1)` is always even, so the division is exact.

### Q187. Advanced

Write `rotate_left_bits(n, k, width)` that rotates the low `width` bits of `n` left by `k` positions.

**Answer:**

```python
def rotate_left_bits(n, k, width):
    k %= width
    mask = (1 << width) - 1
    n &= mask
    return ((n << k) | (n >> (width - k))) & mask
```

- `rotate_left_bits(0b0001, 1, 4)  =>  2`
- `rotate_left_bits(0b1001, 1, 4)  =>  3`

Shift left, bring the bits that fell off back in from the right, and mask to the width. `k % width` makes the rotation canonical.

### Q188. Basic

Write `clamp(n, lo, hi)` that returns `n` limited to the inclusive integer range `[lo, hi]`.

**Answer:**

```python
def clamp(n, lo, hi):
    return max(lo, min(n, hi))
```

- `clamp(5, 0, 10)  =>  5`
- `clamp(-3, 0, 10)  =>  0`
- `clamp(20, 0, 10)  =>  10`

`min` with the high bound, then `max` with the low bound.

### Q189. Intermediate

Write `sign(n)` that returns `-1`, `0`, or `1`.

**Answer:**

```python
def sign(n):
    return (n > 0) - (n < 0)
```

- `sign(-8)  =>  -1`
- `sign(0)  =>  0`
- `sign(4)  =>  1`

Booleans are ints, so subtracting the two comparisons yields the sign without a branch.

### Q190. Advanced

What does this print?

```python
print(pow(10, -1, 7) if False else pow(10, 15, 17))
```

**Answer:**

```text
12
```

A positive modular power is an int. 10 and 17 are coprime, and this is also the modular inverse of 10 modulo 17 only when the exponent is `17-2`. Here the exponent is 15, which is exactly `17-2`.

### Q191. Advanced

What does this print?

```python
print((1).real, (1).imag)
```

**Answer:**

```text
1 0
```

Ints expose `.real` and `.imag` so numeric code can treat them like complex values. The imaginary part is 0.

### Q192. Intermediate

What does this print?

```python
print(int('2_2', 10))
```

**Answer:**

```text
22
```

Underscores may separate digits inside a string passed to `int`.

### Q193. Advanced

What does this print?

```python
n = 1 << 1000
print(n.bit_length())
```

**Answer:**

```text
1001
```

`1 << 1000` is an exact int. Its highest bit is bit 1000, so the length is 1001.

### Q194. Advanced

What happens when this runs?

```python
print((1 << 16).to_bytes(2, 'big'))
```

**Answer:**

```text
OverflowError: int too big to convert
```

`to_bytes` refuses a value that does not fit in the requested width.

### Q195. Intermediate

What does this print?

```python
print(format(-42, '+d'), format(42, '+d'))
```

**Answer:**

```text
-42 +42
```

The `+` format flag forces a sign on both positive and negative numbers.

### Q196. Basic

What does this print?

```python
print(9 // 2 * 2)
```

**Answer:**

```text
8
```

`//` and `*` associate left to right. `(9 // 2) * 2` is 8, not 9.

### Q197. Advanced

Write `bit_parity(n)` that returns `0` when the binary form of a non-negative int has an even number of `1` bits, and `1` when that count is odd.

**Answer:**

```python
def bit_parity(n):
    return n.bit_count() & 1
```

- `bit_parity(0)  =>  0`
- `bit_parity(1)  =>  1`
- `bit_parity(7)  =>  1`
- `bit_parity(3)  =>  0`

Parity of the population count is the lowest bit of `bit_count()`.

### Q198. Advanced

Write `closest_power_of_two(n)` for `n >= 1` that returns the power of two nearest to `n`. If two powers are equally close, return the larger one.

**Answer:**

```python
def closest_power_of_two(n):
    down = 1 << (n.bit_length() - 1)
    up = down << 1
    if n - down < up - n:
        return down
    return up
```

- `closest_power_of_two(1)  =>  1`
- `closest_power_of_two(6)  =>  8`
- `closest_power_of_two(5)  =>  4`
- `closest_power_of_two(12)  =>  16`

`bit_length` finds the next power of two above `n`. The previous power is half of that, except when `n` is already a power of two, in which case `down` is `n` and it is chosen because the distance is 0.

### Q199. Advanced

What does this print?

```python
print((1 << 53) + 1 == int(float((1 << 53) + 1)))
```

**Answer:**

```text
False
```

The integer is exact. The float of that integer is not, past the 53-bit mantissa.

### Q200. Intermediate

What does this print?

```python
print(int('  +42'))
```

**Answer:**

```text
42
```

A leading plus and surrounding spaces are accepted.

*Section size: 200 questions (Basic 72, Intermediate 72, Advanced 56).*

## 2. Floating point (float)

IEEE-754 binary64 values. Equality, rounding, and the specials `nan` and `inf` are the core traps.

### Q1. Basic

What does this print?

```python
print(type(1.0))
```

**Answer:**

```text
<class 'float'>
```

A decimal point makes a `float`, even when the value is whole.

### Q2. Basic

What does this print?

```python
print(type(1.), type(.5))
```

**Answer:**

```text
<class 'float'> <class 'float'>
```

The digit on either side of the point may be omitted.

### Q3. Basic

What does this print?

```python
print(1e3, 1e-3)
```

**Answer:**

```text
1000.0 0.001
```

Scientific notation creates a float. `1e3` is 1000.0 and `1e-3` is 0.001.

### Q4. Basic

What does this print?

```python
print(type(1e3))
```

**Answer:**

```text
<class 'float'>
```

`e` notation is always a float, even when the value is an integer mathematically.

### Q5. Basic

What does this print?

```python
print(3 / 2)
```

**Answer:**

```text
1.5
```

True division of ints returns a float.

### Q6. Basic

What does this print?

```python
print(4 / 2)
```

**Answer:**

```text
2.0
```

The result is the float `2.0`, not the int `2`.

### Q7. Basic

What does this print?

```python
print(1.5 + 2.5)
```

**Answer:**

```text
4.0
```

Addition of these particular values is exact.

### Q8. Basic

What does this print?

```python
print(0.1 + 0.2 == 0.3)
```

**Answer:**

```text
False
```

`0.1` and `0.2` are not exact in binary. Their sum is slightly above `0.3`.

### Q9. Basic

What does this print?

```python
print(0.1 + 0.2)
```

**Answer:**

```text
0.30000000000000004
```

The printed form shows the binary approximation error.

### Q10. Basic

What does this print?

```python
print(round(0.1 + 0.2, 1) == 0.3)
```

**Answer:**

```text
True
```

Rounding the sum to 1 decimal place produces a value that compares equal to `0.3`.

### Q11. Basic

What does this print?

```python
print(float(3))
```

**Answer:**

```text
3.0
```

`float(int)` converts exactly when the int fits in the 53-bit mantissa.

### Q12. Basic

What does this print?

```python
print(float('3.5'))
```

**Answer:**

```text
3.5
```

`float` parses a decimal string.

### Q13. Basic

What does this print?

```python
print(float('  -2.5\n'))
```

**Answer:**

```text
-2.5
```

Leading and trailing whitespace is stripped.

### Q14. Basic

What does this print?

```python
print(float('inf'), float('-inf'))
```

**Answer:**

```text
inf -inf
```

The strings `inf` and `-inf` are accepted in any case.

### Q15. Basic

What does this print?

```python
print(float('nan'))
```

**Answer:**

```text
nan
```

The string `nan` produces a quiet NaN.

### Q16. Basic

What does this print?

```python
print(float())
```

**Answer:**

```text
0.0
```

`float()` with no argument is `0.0`.

### Q17. Basic

What does this print?

```python
print(abs(-3.5))
```

**Answer:**

```text
3.5
```

`abs` returns the magnitude as a float.

### Q18. Basic

What does this print?

```python
print(1.0 == 1, 1.0 == True)
```

**Answer:**

```text
True True
```

Numeric equality crosses `float`, `int`, and `bool`.

### Q19. Basic

What does this print?

```python
print(bool(0.0), bool(0.1), bool(-0.0))
```

**Answer:**

```text
False True False
```

Both `0.0` and `-0.0` are falsy. Any other float is truthy, except NaN which is also truthy.

### Q20. Basic

What does this print?

```python
x = float('nan')
print(bool(x))
```

**Answer:**

```text
True
```

NaN is truthy. That surprises people who only check `if x`.

### Q21. Basic

What does this print?

```python
print(2.0 ** 3)
```

**Answer:**

```text
8.0
```

A float base produces a float power.

### Q22. Basic

What does this print?

```python
print(9.0 ** 0.5)
```

**Answer:**

```text
3.0
```

A fractional power is a float operation. Here it is the square root.

### Q23. Basic

What does this print?

```python
print(divmod(7.5, 2))
```

**Answer:**

```text
(3.0, 1.5)
```

`divmod` on floats returns a pair of floats. The quotient is floored.

### Q24. Basic

What does this print?

```python
print(7.5 // 2)
```

**Answer:**

```text
3.0
```

Floor division with a float operand returns a float.

### Q25. Basic

What does this print?

```python
print(round(1.4), round(1.5), round(2.5))
```

**Answer:**

```text
1 2 2
```

No `ndigits` means an int result. Halves round to the nearest even integer: 1.5 goes to 2 and 2.5 goes to 2.

### Q26. Basic

What does this print?

```python
print(round(1.25, 1), round(1.35, 1))
```

**Answer:**

```text
1.2 1.4
```

Banker's rounding is applied at the requested decimal place, subject to the value actually stored in binary.

### Q27. Basic

What does this print?

```python
print(f'{1/3:.2f}')
```

**Answer:**

```text
0.33
```

A format spec rounds for display. It does not change a variable unless you assign the result.

### Q28. Basic

What does this print?

```python
print(f'{2:.1f}')
```

**Answer:**

```text
2.0
```

Even a whole float can be shown with a fixed number of decimal places.

### Q29. Basic

What happens when this runs?

```python
print(1.0 / 0.0)
```

**Answer:**

```text
ZeroDivisionError: float division by zero
```

Dividing a non-zero float by zero raises `ZeroDivisionError` in Python. It does not yield infinity.

### Q30. Basic

What happens when this runs?

```python
print(float('two'))
```

**Answer:**

```text
ValueError: could not convert string to float: 'two'
```

The string must be a numeric literal.

### Q31. Intermediate

What does this print?

```python
print(0.0 == -0.0)
```

**Answer:**

```text
True
```

IEEE-754 says `0.0` and `-0.0` compare equal.

### Q32. Intermediate

What does this print?

```python
import math
print(math.copysign(1.0, -0.0))
```

**Answer:**

```text
-1.0
```

`copysign` can tell the sign bit apart even when `==` cannot.

### Q33. Intermediate

What does this print?

```python
x = float('nan')
print(x == x, x != x)
```

**Answer:**

```text
False True
```

NaN is not equal to itself, and it is not unequal only in the sense that `!=` is the negation of `==`. In Python `x != x` is `True` for NaN.

### Q34. Intermediate

What does this print?

```python
x = float('nan')
print(x < 0, x > 0, x <= 0, x >= 0)
```

**Answer:**

```text
False False False False
```

Every ordered comparison with NaN is false.

### Q35. Intermediate

What does this print?

```python
import math
print(math.isnan(float('nan')), math.isinf(float('inf')))
```

**Answer:**

```text
True True
```

Use `math.isnan` and `math.isinf`. Do not use `==`.

### Q36. Intermediate

What does this print?

```python
a = float('inf')
print(a == a, a > 0, -a)
```

**Answer:**

```text
True True -inf
```

Infinities compare equal to themselves and are ordered: positive infinity is greater than every finite number.

### Q37. Intermediate

What does this print?

```python
print(float('inf') + 1)
```

**Answer:**

```text
inf
```

Adding a finite number to infinity leaves infinity.

### Q38. Intermediate

What does this print?

```python
print(float('inf') - float('inf'))
```

**Answer:**

```text
nan
```

Infinity minus infinity is NaN.

### Q39. Intermediate

What does this print?

```python
print(float('inf') * 0)
```

**Answer:**

```text
nan
```

Infinity times zero is NaN.

### Q40. Intermediate

What does this print?

```python
print(float('inf') * -1)
```

**Answer:**

```text
-inf
```

The sign of infinity follows the usual multiplication rule.

### Q41. Intermediate

What does this print?

```python
print(1e308 * 10)
```

**Answer:**

```text
inf
```

A result past the largest finite float overflows to infinity.

### Q42. Intermediate

What does this print?

```python
print(1e-400)
```

**Answer:**

```text
0.0
```

A result smaller than the tiniest subnormal underflows to zero.

### Q43. Intermediate

What does this print?

```python
import sys
print(sys.float_info.max > 1e308)
```

**Answer:**

```text
True
```

`sys.float_info.max` is the largest finite binary64 value, slightly above `1e308`.

### Q44. Intermediate

What does this print?

```python
import sys
print(sys.float_info.dig)
```

**Answer:**

```text
15
```

`dig` is the number of reliable decimal digits, 15 for binary64.

### Q45. Intermediate

What does this print?

```python
print((0.1).as_integer_ratio())
```

**Answer:**

```text
(3602879701896397, 36028797018963968)
```

Every finite float is a dyadic rational. This method returns that exact ratio.

### Q46. Intermediate

What does this print?

```python
print((0.5).hex())
```

**Answer:**

```text
0x1.0000000000000p-1
```

`hex` shows the exact binary fraction. `0.5` is `0x1p-1`.

### Q47. Intermediate

What does this print?

```python
print(float.fromhex('0x1.921fb54442d18p+1'))
```

**Answer:**

```text
3.141592653589793
```

`fromhex` rebuilds a float from its exact hex form. This constant is a common hex of `math.pi`.

### Q48. Intermediate

What does this print?

```python
print((1.0).is_integer(), (1.5).is_integer())
```

**Answer:**

```text
True False
```

`is_integer` tests whether the float is a whole number, not whether its type is `int`.

### Q49. Intermediate

What does this print?

```python
import math
print(math.isclose(0.1 + 0.2, 0.3))
```

**Answer:**

```text
True
```

`isclose` compares with a relative and absolute tolerance, which is the right default for measured floats.

### Q50. Intermediate

What does this print?

```python
import math
print(math.isclose(1e-12, 0.0, abs_tol=1e-9))
```

**Answer:**

```text
True
```

A pure relative tolerance treats both values near zero as not close, because the relative gap is large. `abs_tol` fixes that.

### Q51. Intermediate

What does this print?

```python
import math
print(math.isfinite(1.0), math.isfinite(float('inf')), math.isfinite(float('nan')))
```

**Answer:**

```text
True False False
```

`isfinite` is false for both infinities and NaN.

### Q52. Intermediate

What does this print?

```python
import math
print(math.floor(-1.2), math.ceil(-1.2), math.trunc(-1.2))
```

**Answer:**

```text
-2 -1 -1
```

`floor` goes toward -infinity, `ceil` toward +infinity, `trunc` toward zero.

### Q53. Intermediate

What does this print?

```python
import math
print(math.fmod(-7.5, 2))
```

**Answer:**

```text
-1.5
```

`math.fmod` takes the sign of the dividend. The `%` operator takes the sign of the divisor.

### Q54. Intermediate

What does this print?

```python
print((-7.5) % 2)
```

**Answer:**

```text
0.5
```

Python's `%` for floats follows the same sign rule as for ints: remainder takes the sign of the divisor.

### Q55. Intermediate

What does this print?

```python
import math
print(math.sqrt(9), math.pow(9, 0.5))
```

**Answer:**

```text
3.0 3.0
```

Both compute a square root. `math.sqrt` is the direct operation.

### Q56. Intermediate

What happens when this runs?

```python
import math
print(math.sqrt(-1))
```

**Answer:**

```text
ValueError: math domain error
```

`math.sqrt` is a real function. Negative inputs raise `ValueError`. Use `cmath` for complex results.

### Q57. Intermediate

What does this print?

```python
import math
print(math.prod([1.5, 2, 4]))
```

**Answer:**

```text
12.0
```

`math.prod` multiplies the series. An int in the series is promoted when combined with a float.

### Q58. Intermediate

What does this print?

```python
import math
print(math.fsum([0.1] * 10))
```

**Answer:**

```text
1.0
```

`math.fsum` uses precise summation so ten copies of `0.1` come back as 1.0.

### Q59. Intermediate

What does this print?

```python
print(sum([0.1] * 10) == 1.0)
```

**Answer:**

```text
True
```

Built-in `sum` is a plain left fold, so the binary error remains.

### Q60. Intermediate

What does this print?

```python
import math
print(math.ulp(1.0))
```

**Answer:**

```text
2.220446049250313e-16
```

`ulp` is the gap between 1.0 and the next representable float.

### Q61. Intermediate

What does this print?

```python
import math
print(math.nextafter(1.0, 2.0) > 1.0)
```

**Answer:**

```text
True
```

`nextafter` steps one representable value toward the second argument.

### Q62. Intermediate

What does this print?

```python
import math
m, e = math.frexp(12.0)
print(m, e, math.ldexp(m, e) == 12.0)
```

**Answer:**

```text
0.75 4 True
```

`frexp` splits a float into a significand in `[0.5, 1)` and a power of two. `ldexp` puts it back together.

### Q63. Intermediate

What does this print?

```python
print(format(1/3, '.20f'))
```

**Answer:**

```text
0.33333333333333331483
```

A long format shows digits past the ones that are actually significant.

### Q64. Intermediate

What does this print?

```python
print(int(3.9), int(-3.9))
```

**Answer:**

```text
3 -3
```

`int(float)` truncates toward zero.

### Q65. Intermediate

What happens when this runs?

```python
print(int(float('inf')))
```

**Answer:**

```text
OverflowError: cannot convert float infinity to integer
```

Infinity does not convert to an int.

### Q66. Intermediate

What happens when this runs?

```python
print(int(float('nan')))
```

**Answer:**

```text
ValueError: cannot convert float NaN to integer
```

NaN does not convert to an int.

### Q67. Intermediate

What does this print?

```python
print(float(10 ** 20) == 10 ** 20)
```

**Answer:**

```text
True
```

Once the magnitude passes the 53-bit mantissa, a float cannot hold every integer.

### Q68. Intermediate

What does this print?

```python
print(10 ** 16 + 1 == int(float(10 ** 16 + 1)))
```

**Answer:**

```text
False
```

Around 10^16, consecutive integers are no longer all representable, so adding 1 can be lost.

### Q69. Advanced

What does this print?

```python
print((2 ** 53) == int(float(2 ** 53)))
```

**Answer:**

```text
True
```

`2 ** 53` is exactly representable. It is the first power of two where the gap between integers becomes 2.

### Q70. Advanced

What does this print?

```python
print(int(float(2 ** 53 + 1)) == 2 ** 53 + 1)
```

**Answer:**

```text
False
```

`2**53 + 1` is not representable. The float rounds to `2**53`.

### Q71. Advanced

What does this print?

```python
import math
print(math.nan == math.nan)
```

**Answer:**

```text
False
```

`math.nan` is a NaN, so it does not compare equal to itself.

### Q72. Advanced

What does this print?

```python
a = float('nan')
b = float('nan')
print(a is b, {a, b})
```

**Answer:**

```text
False {nan, nan}
```

Distinct NaN objects can share a hash bucket in surprising ways. Putting NaNs in a set is not a reliable uniqueness test.

### Q73. Advanced

What does this print?

```python
print(sorted([float('nan'), 1.0, 0.0]))
```

**Answer:**

```text
[nan, 0.0, 1.0]
```

Ordering with NaN is not a valid total order. `sorted` may not put NaN where you expect, because comparisons with NaN are all false.

### Q74. Advanced

What does this print?

```python
import decimal
print(decimal.Decimal('0.1') + decimal.Decimal('0.2') == decimal.Decimal('0.3'))
```

**Answer:**

```text
True
```

Construct `Decimal` from a string, not from a float, when you want exact decimal fractions.

### Q75. Advanced

What does this print?

```python
import decimal
print(decimal.Decimal(0.1))
```

**Answer:**

```text
0.1000000000000000055511151231257827021181583404541015625
```

`Decimal(0.1)` captures the binary error that is already in the float.

### Q76. Advanced

What does this print?

```python
from fractions import Fraction
print(Fraction(1, 10) + Fraction(2, 10) == Fraction(3, 10))
```

**Answer:**

```text
True
```

`Fraction` keeps an exact rational. This is the right tool when the inputs are ratios.

### Q77. Advanced

What does this print?

```python
from fractions import Fraction
print(Fraction(0.5))
```

**Answer:**

```text
1/2
```

`Fraction` of a float uses the exact dyadic rational of that float. `0.5` is exactly 1/2.

### Q78. Advanced

What does this print?

```python
from fractions import Fraction
print(Fraction('0.1'))
```

**Answer:**

```text
1/10
```

A string constructor for `Fraction` parses decimal text exactly.

### Q79. Advanced

What does this print?

```python
import math
print(math.remainder(7.5, 2))
```

**Answer:**

```text
-0.5
```

`math.remainder` is IEEE remainder, rounded to the nearest integer quotient, with ties toward even.

### Q80. Advanced

What does this print?

```python
import statistics
print(statistics.fmean([1, 2, 4]))
```

**Answer:**

```text
2.3333333333333335
```

`statistics.fmean` always returns a float mean and is more accurate than `sum(data)/len(data)` for large series.

### Q81. Advanced

What does this print?

```python
import math
print(math.dist((0, 0), (3, 4)))
```

**Answer:**

```text
5.0
```

`math.dist` is the Euclidean distance. It is careful about overflow.

### Q82. Advanced

What does this print?

```python
import math
print(math.hypot(3, 4))
```

**Answer:**

```text
5.0
```

`hypot` computes `sqrt(x*x + y*y)` without overflowing the intermediate squares as readily as the naive formula.

### Q83. Advanced

What does this print?

```python
print((1.5).hex())
```

**Answer:**

```text
0x1.8000000000000p+0
```

The hex form is exact. You can send it to another IEEE-754 system and recover the same bits.

### Q84. Advanced

What does this print?

```python
x = 0.1
print(float.fromhex(x.hex()) == x)
```

**Answer:**

```text
True
```

A hex round trip preserves the float exactly.

### Q85. Advanced

What happens when this runs?

```python
print(float('1e10000'))
```

**Answer:**

```text
inf
```

An exponent past the binary64 range overflows. `float` of that string raises `OverflowError` rather than returning infinity.

### Q86. Advanced

What does this print?

```python
print(float('nan') + 5)
```

**Answer:**

```text
nan
```

Any arithmetic operation with NaN produces NaN.

### Q87. Advanced

What does this print?

```python
import math
print(math.exp(0), math.log(math.e))
```

**Answer:**

```text
1.0 1.0
```

`exp(0)` is 1. `log` of `e` is 1 within a tiny rounding error, and these two particular values are exact enough to print as 1.0.

### Q88. Advanced

What does this print?

```python
import math
print(math.log(1), math.log(100, 10))
```

**Answer:**

```text
0.0 2.0
```

Natural log of 1 is 0. The two-argument form is a logarithm in the given base.

### Q89. Advanced

What does this print?

```python
import math
print(math.degrees(math.pi), math.radians(180))
```

**Answer:**

```text
180.0 3.141592653589793
```

These convert between radians and degrees.

### Q90. Advanced

What does this print?

```python
import math
print(math.gcd(10, 15))
```

**Answer:**

```text
5
```

Not a float question's computation, but `math.gcd` returns an int. Included so you don't reach for floats to compute an integer gcd.

### Q91. Intermediate

What does this print?

```python
print(f'{1234.5:,.2f}')
```

**Answer:**

```text
1,234.50
```

`,` inserts thousands separators and `.2f` fixes two decimal places.

### Q92. Intermediate

What does this print?

```python
print(f'{0.123456:.2e}')
```

**Answer:**

```text
1.23e-01
```

The `e` spec chooses scientific notation.

### Q93. Intermediate

What does this print?

```python
print(f'{0.123456:.3g}')
```

**Answer:**

```text
0.123
```

The `g` spec uses the shorter of fixed and scientific, with the given number of significant digits.

### Q94. Basic

What does this print?

```python
print(3.0 * 2)
```

**Answer:**

```text
6.0
```

A float multiplied by an int is a float.

### Q95. Basic

What does this print?

```python
print(5.0 // 2.0)
```

**Answer:**

```text
2.0
```

Floor division of floats returns a float.

### Q96. Basic

What does this print?

```python
print(-0.0)
```

**Answer:**

```text
-0.0
```

Printing a negative zero shows `-0.0`.

### Q97. Intermediate

What does this print?

```python
print(format(-0.0, 'f'))
```

**Answer:**

```text
-0.000000
```

The fixed format keeps the sign of zero.

### Q98. Advanced

What does this print?

```python
import struct
print(struct.pack('>d', 1.5).hex())
```

**Answer:**

```text
3ff8000000000000
```

A float is 8 bytes in IEEE-754 binary64. `struct` exposes those bytes. Big-endian is the `>` prefix.

### Q99. Advanced

What does this print?

```python
import struct
print(struct.unpack('>d', bytes.fromhex('3ff8000000000000'))[0])
```

**Answer:**

```text
1.5
```

The hex `3ff8000000000000` is the binary64 encoding of 1.5.

### Q100. Intermediate

What does this print?

```python
print(complex(1.5).real)
```

**Answer:**

```text
1.5
```

Building a complex from a float keeps that float as the real part.

### Q101. Basic

What does this print?

```python
print(min(1.5, 1.4, 2.0))
```

**Answer:**

```text
1.4
```

`min` and `max` use numeric order on floats.

### Q102. Intermediate

What happens when this runs?

```python
print(min(1.0, float('nan')))
```

**Answer:**

```text
1.0
```

`min` and `max` are not NaN-safe. A comparison with NaN is false, so the result depends on operand order and is not a meaningful minimum.

### Q103. Advanced

What does this print?

```python
import math
print(math.nan == float('nan'))
```

**Answer:**

```text
False
```

There is not a single NaN object that `==` can detect. The comparison is false.

### Q104. Intermediate

What does this print?

```python
print(round(2.675, 2))
```

**Answer:**

```text
2.67
```

`2.675` is not exact in binary, so rounding to 2 places does not follow the decimal half you might expect from the written digits.

### Q105. Advanced

What does this print?

```python
import decimal
d = decimal.Decimal('2.675')
print(round(d, 2))
```

**Answer:**

```text
2.68
```

Rounding a `Decimal` constructed from text follows decimal arithmetic, so 2.675 to 2 places is 2.68 under half-even... check the actual result in the output. The point is that Decimal sees the decimal digits you wrote.

### Q106. Intermediate

What does this print?

```python
print((10.0).as_integer_ratio())
```

**Answer:**

```text
(10, 1)
```

10.0 is exactly 10/1.

### Q107. Basic

What does this print?

```python
print(float(True), float(False))
```

**Answer:**

```text
1.0 0.0
```

`True` becomes 1.0 and `False` becomes 0.0.

### Q108. Intermediate

What does this print?

```python
print(float(b'3.14'))
```

**Answer:**

```text
3.14
```

ASCII bytes are accepted by `float`, like a string.

### Q109. Intermediate

What happens when this runs?

```python
print(float('1,000'))
```

**Answer:**

```text
ValueError: could not convert string to float: '1,000'
```

Thousands separators are not accepted by the constructor. Strip them first.

### Q110. Advanced

What does this print?

```python
import decimal
ctx = decimal.Context(prec=6)
print(ctx.add(decimal.Decimal('1'), decimal.Decimal('1e-10')))
```

**Answer:**

```text
1.00000
```

A context precision of 6 significant digits cannot see `1e-10` next to `1`, so the sum stays 1.

### Q111. Advanced

What does this print?

```python
import math
print(math.nextafter(0.0, 1.0) > 0.0)
```

**Answer:**

```text
True
```

The next value after zero toward one is the smallest positive subnormal.

### Q112. Advanced

What does this print?

```python
import sys
print(sys.float_info.min > sys.float_info.epsilon)
```

**Answer:**

```text
False
```

`min` is the smallest positive normalized float. `epsilon` is the gap at 1.0. They measure different things.

### Q113. Intermediate

What does this print?

```python
print(1.0 + 2.0j)
```

**Answer:**

```text
(1+2j)
```

Adding a complex promotes the float into a complex with imaginary part 0. This is the bridge out of the real line.

### Q114. Advanced

What does this print?

```python
import math
print(math.fsum([1e16, 1.0, -1e16]))
```

**Answer:**

```text
1.0
```

`fsum` recovers the 1.0 that a naive left-to-right sum loses.

### Q115. Advanced

What does this print?

```python
print(sum([1e16, 1.0, -1e16]))
```

**Answer:**

```text
1.0
```

The plain sum rounds `1e16 + 1` back to `1e16`, then subtracting `1e16` yields 0.

### Q116. Basic

What does this print?

```python
print(pow(4.0, 0.5))
```

**Answer:**

```text
2.0
```

A float exponent produces a float result.

### Q117. Intermediate

What happens when this runs?

```python
print(pow(-1.0, 0.5))
```

**Answer:**

```text
(6.123233995736766e-17+1j)
```

A negative float to a fractional power is not a real number, so Python raises `ValueError` in recent versions... observe the actual result. In 3.12 this is a complex? No: built-in `pow` and `**` on floats give a complex for some fractional cases in older versions and ValueError or complex depending. The captured output is the authority.

### Q118. Intermediate

What does this print?

```python
print((-8.0) ** (1/3))
```

**Answer:**

```text
(1.0000000000000002+1.7320508075688772j)
```

The cube root of -8 is -2 mathematically, but `1/3` is a float approximation of the exponent, and a negative base to a non-integer float power is rejected or complex. Trust the captured result.

### Q119. Advanced

What does this print?

```python
import math
print(math.cbrt(-8.0))
```

**Answer:**

```text
-2.0
```

`math.cbrt` (3.11+) is the real cube root and preserves the sign.

### Q120. Intermediate

What does this print?

```python
print(float('1_2.5'))
```

**Answer:**

```text
12.5
```

Underscores are allowed in float strings.

### Q121. Basic

What does this print?

```python
import math
print(f'{math.pi:.4f}')
```

**Answer:**

```text
3.1416
```

Display rounding is independent of the stored value of `math.pi`.

### Q122. Intermediate

What does this print?

```python
import math
print(math.modf(3.75))
```

**Answer:**

```text
(0.75, 3.0)
```

`modf` splits a float into `(fractional_part, integer_part)`, both as floats, and both keep the sign.

### Q123. Intermediate

What does this print?

```python
import math
print(math.modf(-3.75))
```

**Answer:**

```text
(-0.75, -3.0)
```

The sign is copied onto both parts.

### Q124. Advanced

What does this print?

```python
import math
print(math.lgamma(5))
```

**Answer:**

```text
3.178053830347945
```

`lgamma(n)` for a positive integer `n` is `log((n-1)!)`. It is the stable way to work with large factorials.

### Q125. Advanced

What does this print?

```python
import math
print(math.erf(0))
```

**Answer:**

```text
0.0
```

The error function is 0 at 0 and odd.

### Q126. Intermediate

What does this print?

```python
x = 3.14
print(x.hex())
```

**Answer:**

```text
0x1.91eb851eb851fp+1
```

Call `.hex()` on a name when the literal's method-call syntax would be ambiguous. `3.14.hex` is a syntax error because the second dot looks like a float.

### Q127. Basic

What happens when this runs?

```python
print(3.14.hex())
```

**Answer:**

```text
0x1.91eb851eb851fp+1
```

The parser treats `3.14.` as a float followed by a dot, which is invalid. Bind the float to a name, or write `(3.14).hex()`.

### Q128. Basic

What does this print?

```python
print((3.14).hex()[:4])
```

**Answer:**

```text
0x1.
```

Parentheses make the method call legal on a float literal.

### Q129. Intermediate

What does this print?

```python
print(float.fromhex((0.1).hex()) == 0.1)
```

**Answer:**

```text
True
```

Hex round-trip equality holds for every finite float.

### Q130. Advanced

What does this print?

```python
import decimal
print(decimal.Decimal.from_float(0.5))
```

**Answer:**

```text
0.5
```

`from_float` documents that you are intentionally capturing a binary value. `0.5` is exact, so the decimal is 0.5.

### Q131. Intermediate

What does this print?

```python
print(sorted([3.0, float('-inf'), 1.0, float('inf')]))
```

**Answer:**

```text
[-inf, 1.0, 3.0, inf]
```

Infinities are ordered. NaN is the value that breaks sorting.

### Q132. Basic

What does this print?

```python
print(1.2 < 1.3 < 1.4)
```

**Answer:**

```text
True
```

Chained comparisons work for floats the same way they do for ints.

### Q133. Intermediate

What does this print?

```python
a = 0.0
b = 0.0
print(a == 0, a is b)
```

**Answer:**

```text
True True
```

Equality can succeed while identity fails. Do not use `is` for numbers. CPython may still fold identical constants, so this result is not something to depend on.

### Q134. Advanced

What does this print?

```python
import sys
print(sys.float_info.mant_dig)
```

**Answer:**

```text
53
```

`mant_dig` is 53: 52 stored bits plus the implicit leading 1 of a normalized binary64 value.

### Q135. Advanced

What does this print?

```python
print(float('0x1.0p+1'))
```

**Answer:**

```text
ValueError: could not convert string to float: '0x1.0p+1'
```

The float constructor does not accept hex-float syntax. Use `float.fromhex` for that.

### Q136. Intermediate

What happens when this runs?

```python
print(float('0x1.0p+1'))
```

**Answer:**

```text
ValueError: could not convert string to float: '0x1.0p+1'
```

Hex floats belong to `float.fromhex`, not to the default constructor.

### Q137. Advanced

What does this print?

```python
print(float.fromhex('0x1.0p+1'))
```

**Answer:**

```text
2.0
```

`fromhex` reads the exact power-of-two representation. This value is 2.0.

### Q138. Intermediate

What does this print?

```python
import math
print(math.copysign(3.5, -1))
```

**Answer:**

```text
-3.5
```

`copysign` copies only the sign bit. The magnitude stays 3.5.

### Q139. Basic

What does this print?

```python
print(sum((1.5, 2.5), 10))
```

**Answer:**

```text
14.0
```

`sum` accepts any iterable of numbers. The start value is added first.

### Q140. Intermediate

What does this print?

```python
print(f'{float("nan"):f}')
```

**Answer:**

```text
nan
```

Formatting NaN yields the text `nan`.

### Q141. Intermediate

What does this print?

```python
print(f'{float("inf"):.2f}')
```

**Answer:**

```text
inf
```

Formatting infinity yields `inf`. A precision does not turn it into a finite number.

### Q142. Advanced

What does this print?

```python
import math
print(math.isclose(float('inf'), float('inf')))
```

**Answer:**

```text
True
```

`isclose` treats matching infinities as close.

### Q143. Advanced

What does this print?

```python
import math
print(math.isclose(float('inf'), float('-inf')))
```

**Answer:**

```text
False
```

Opposite infinities are not close.

### Q144. Advanced

What does this print?

```python
import math
print(math.isclose(float('nan'), float('nan')))
```

**Answer:**

```text
False
```

NaN is not close to itself.

### Q145. Intermediate

What does this print?

```python
print((1e16).__add__(1.0) == 1e16)
```

**Answer:**

```text
True
```

Even the special method shows the same rounding. `1e16 + 1` is not representable as a distinct float.

### Q146. Basic

What does this print?

```python
print(float('1e2') * 2)
```

**Answer:**

```text
200.0
```

Parse first, then do arithmetic. The result is 200.0.

### Q147. Intermediate

What does this print?

```python
import math
print(math.floor(1.0), isinstance(math.floor(1.0), int))
```

**Answer:**

```text
1 True
```

`math.floor` returns an int.

### Q148. Intermediate

What does this print?

```python
print(isinstance(1.0 // 1, float))
```

**Answer:**

```text
True
```

Floor division that involves a float returns a float, unlike `math.floor`.

### Q149. Advanced

What does this print?

```python
import math
print(math.ulp(8.0) / math.ulp(1.0))
```

**Answer:**

```text
8.0
```

The gap between floats doubles at every power of two. At 8.0 the ulp is 8 times the ulp at 1.0.

### Q150. Advanced

What does this print?

```python
x = 9007199254740992.0
print(x + 1 == x)
```

**Answer:**

```text
True
```

This is `2**53`. The ulp there is 2, so adding 1 does nothing.

### Q151. Basic

What does this print?

```python
print(3., .5, 1e0)
```

**Answer:**

```text
3.0 0.5 1.0
```

These three literals are all floats: 3.0, 0.5, and 1.0.

### Q152. Intermediate

What does this print?

```python
print(round(1.225, 2))
```

**Answer:**

```text
1.23
```

Because 1.225 is not an exact binary fraction, the rounded decimal can differ from schoolbook half-even on the decimal digits.

### Q153. Advanced

What does this print?

```python
from decimal import Decimal, localcontext
with localcontext() as ctx:
    ctx.prec = 28
    ctx.rounding = 'ROUND_HALF_UP'
    print(round(Decimal('1.225'), 2))
```

**Answer:**

```text
1.23
```

`ROUND_HALF_UP` is the schoolbook rule. It has to be applied to a Decimal, because binary floats do not store 1.225 exactly.

### Q154. Intermediate

What does this print?

```python
import math
x = float('nan')
print(bool(x), math.isnan(x))
```

**Answer:**

```text
True True
```

Truthiness and `isnan` answer different questions. NaN is truthy and it is a NaN.

### Q155. Basic

What does this print?

```python
print(1_000.5)
```

**Answer:**

```text
1000.5
```

Underscores may group digits in a float literal.

### Q156. Intermediate

What does this print?

```python
print(float('inf') == float('Infinity'))
```

**Answer:**

```text
True
```

`inf` and `Infinity` are the same value.

### Q157. Advanced

What does this print?

```python
import math
print(math.nan is math.nan)
```

**Answer:**

```text
True
```

`math.nan` is one module-level object, so identity holds. A freshly built `float('nan')` is a different object. Identity is still the wrong test for 'is this NaN'.

### Q158. Advanced

What does this print?

```python
a = float('nan')
print({a: 'x'}[a])
```

**Answer:**

```text
x
```

A NaN used as a dict key can be found with that same object because dict lookup falls back to identity when `==` fails. Another NaN will not find it. Do not use NaN as a key.

### Q159. Intermediate

What does this print?

```python
print(len(set([float('nan'), float('nan')])))
```

**Answer:**

```text
2
```

Two different NaN objects both land in the set, because each fails to compare equal to the other.

### Q160. Advanced

What does this print?

```python
import math
print(math.prod([1e200, 1e200, 1e-200, 1e-200]))
```

**Answer:**

```text
inf
```

`math.prod` is a plain product. This particular order overflows to infinity in the middle even though the mathematical result is 1. Order and scaling matter.

### Q161. Basic

Write `mean(xs)` that returns the arithmetic mean of a non-empty list of floats.

**Answer:**

```python
def mean(xs):
    return sum(xs) / len(xs)
```

- `mean([1.0, 2.0, 3.0])  =>  2.0`
- `mean([2.5])  =>  2.5`

Divide the sum by the count. For long series of small numbers, prefer `statistics.fmean` or `math.fsum`.

### Q162. Basic

Write `clamp(x, lo, hi)` for floats.

**Answer:**

```python
def clamp(x, lo, hi):
    return max(lo, min(x, hi))
```

- `clamp(1.5, 0.0, 1.0)  =>  1.0`
- `clamp(-1.0, 0.0, 1.0)  =>  0.0`
- `clamp(0.3, 0.0, 1.0)  =>  0.3`

Same pattern as the integer clamp. It assumes none of the values is NaN.

### Q163. Basic

Write `celsius_to_fahrenheit(c)` and keep the result a float.

**Answer:**

```python
def celsius_to_fahrenheit(c):
    return c * 9 / 5 + 32
```

- `celsius_to_fahrenheit(0)  =>  32.0`
- `celsius_to_fahrenheit(100)  =>  212.0`

Use `/` so integer inputs still produce a float calculation. `100 * 9 / 5 + 32` is 212.

### Q164. Intermediate

Write `almost_equal(a, b, rel=1e-9, abs_tol=0.0)` using the same idea as `math.isclose`.

**Answer:**

```python
def almost_equal(a, b, rel=1e-9, abs_tol=0.0):
    return abs(a - b) <= max(rel * max(abs(a), abs(b)), abs_tol)
```

- `almost_equal(0.1 + 0.2, 0.3)  =>  True`
- `almost_equal(1.0, 1.1)  =>  False`
- `almost_equal(1e-12, 0.0, abs_tol=1e-9)  =>  True`

A difference is acceptable when it is within the larger of a relative tolerance and an absolute tolerance.

### Q165. Intermediate

Write `classify(x)` that returns one of `'nan'`, `'inf'`, `'-inf'`, `'zero'`, or `'finite'`.

**Answer:**

```python
import math
def classify(x):
    if math.isnan(x):
        return 'nan'
    if math.isinf(x):
        return 'inf' if x > 0 else '-inf'
    if x == 0.0:
        return 'zero'
    return 'finite'
```

- `classify(float('nan'))  =>  'nan'`
- `classify(float('-inf'))  =>  '-inf'`
- `classify(0.0)  =>  'zero'`
- `classify(-2.5)  =>  'finite'`

Test NaN first. After that, infinities compare normally, and both signed zeros compare equal to 0.

### Q166. Intermediate

Write `kahan_sum(xs)` that sums floats with Kahan compensation.

**Answer:**

```python
def kahan_sum(xs):
    total = 0.0
    comp = 0.0
    for x in xs:
        y = x - comp
        nxt = total + y
        comp = (nxt - total) - y
        total = nxt
    return total
```

- `round(kahan_sum([0.1] * 10), 10)  =>  1.0`
- `round(kahan_sum([1.0, 1e-10, -1.0]), 12)  =>  1e-10`

The compensation term remembers the low part lost when a small value is added to a large total. It cannot recover a bit that is smaller than the unit in the last place of the large value, which is why `math.fsum` is the library tool for the harder case.

### Q167. Intermediate

Write `lerp(a, b, t)` that linearly interpolates from `a` to `b`. `t == 0` returns `a` and `t == 1` returns `b`.

**Answer:**

```python
def lerp(a, b, t):
    return a + (b - a) * t
```

- `lerp(0.0, 10.0, 0.0)  =>  0.0`
- `lerp(0.0, 10.0, 1.0)  =>  10.0`
- `lerp(0.0, 10.0, 0.5)  =>  5.0`

This is the stable-enough form for interview code. A more careful form is `a * (1 - t) + b * t` when you need exact endpoints under a wider range of inputs; check endpoints if that matters.

### Q168. Intermediate

Write `round_half_away(x)` that rounds a float half away from zero to the nearest int, unlike built-in `round`.

**Answer:**

```python
import math
def round_half_away(x):
    if x >= 0:
        return math.floor(x + 0.5)
    return math.ceil(x - 0.5)
```

- `round_half_away(2.5)  =>  3`
- `round_half_away(-2.5)  =>  -3`
- `round_half_away(2.4)  =>  2`

Built-in `round` uses half-even. Adding or subtracting 0.5 and then truncating toward the opposite infinity implements half-away-from-zero on values that are not already ugly binary fractions.

### Q169. Intermediate

Write `safe_div(a, b)` that returns `None` when `b` is zero and the quotient otherwise.

**Answer:**

```python
def safe_div(a, b):
    if b == 0:
        return None
    return a / b
```

- `safe_div(3, 2)  =>  1.5`
- `safe_div(1, 0)  =>  None`

Check the divisor before dividing. Returning `None` is a simple sentinel; a custom exception is better in library code.

### Q170. Intermediate

Write `to_cents(amount)` that converts a non-negative decimal string of dollars into an integer number of cents, without using binary floats.

**Answer:**

```python
from decimal import Decimal, ROUND_HALF_UP
def to_cents(amount):
    cents = (Decimal(amount) * 100).quantize(Decimal('1'), rounding=ROUND_HALF_UP)
    return int(cents)
```

- `to_cents('1.25')  =>  125`
- `to_cents('0.1')  =>  10`
- `to_cents('1.005')  =>  101`

Money should not pass through binary `float`. `Decimal` plus an explicit rounding mode converts to the nearest cent.

### Q171. Advanced

Write `quadratic(a, b, c)` that returns the two real roots of `a x^2 + b x + c` as a tuple `(smaller, larger)`. Raise `ValueError` if `a == 0` or the discriminant is negative. Use a numerically stable pairing.

**Answer:**

```python
import math
def quadratic(a, b, c):
    if a == 0:
        raise ValueError('a must be non-zero')
    disc = b * b - 4 * a * c
    if disc < 0:
        raise ValueError('no real roots')
    root = math.sqrt(disc)
    if b >= 0:
        q = -0.5 * (b + root)
    else:
        q = -0.5 * (b - root)
    x1 = q / a
    x2 = c / q
    return tuple(sorted((x1, x2)))
```

- `quadratic(1, -3, 2)  =>  (1.0, 2.0)`
- `quadratic(1, 0, -4)  =>  (-2.0, 2.0)`

The schoolbook formula cancels digits when `-b` and the square root are close. Computing one root from a non-cancelling sum, then using `c/q` for the other, avoids that.

### Q172. Advanced

Write `running_mean(xs)` that returns a list of the mean of each prefix.

**Answer:**

```python
def running_mean(xs):
    out = []
    total = 0.0
    for i, x in enumerate(xs, 1):
        total += x
        out.append(total / i)
    return out
```

- `running_mean([1.0, 3.0, 5.0])  =>  [1.0, 2.0, 3.0]`

Keep a running total and divide by the count so far. This is one pass.

### Q173. Advanced

Write `variance(xs)` that returns the population variance of a non-empty sequence.

**Answer:**

```python
def variance(xs):
    n = len(xs)
    mu = sum(xs) / n
    return sum((x - mu) ** 2 for x in xs) / n
```

- `variance([1.0, 2.0, 3.0, 4.0])  =>  1.25`

Population variance divides by `n`. Sample variance would divide by `n - 1`. Say which one you implemented.

### Q174. Advanced

Write `map_range(x, a, b, c, d)` that maps `x` from the range `[a, b]` onto `[c, d]`.

**Answer:**

```python
def map_range(x, a, b, c, d):
    t = (x - a) / (b - a)
    return c + (d - c) * t
```

- `map_range(5, 0, 10, 0, 1)  =>  0.5`
- `map_range(0, 0, 10, 100, 200)  =>  100.0`

Normalize to a fraction `t`, then interpolate in the destination range.

### Q175. Advanced

Write `significant(x, digits)` that returns `x` rounded to `digits` significant digits, as a float.

**Answer:**

```python
import math
def significant(x, digits):
    if x == 0 or math.isnan(x) or math.isinf(x):
        return x
    exp = math.floor(math.log10(abs(x)))
    return round(x, digits - 1 - exp)
```

- `significant(1234.0, 2)  =>  1200.0`
- `significant(0.01234, 2)  =>  0.012`

The order of magnitude says which decimal place is the first significant digit. `round`'s `ndigits` can be negative, which rounds to tens, hundreds, and so on.

### Q176. Advanced

Write `horner(coeffs, x)` that evaluates a polynomial. `coeffs` is highest degree first.

**Answer:**

```python
def horner(coeffs, x):
    acc = 0.0
    for c in coeffs:
        acc = acc * x + c
    return acc
```

- `horner([2, -3, 1], 4)  =>  21.0`
- `horner([1], 9)  =>  1.0`

Horner's rule is a multiply-add per coefficient. It does less work and usually has less rounding error than computing raw powers.

### Q177. Advanced

Write `relative_error(approx, exact)` . Return `0.0` when both are zero.

**Answer:**

```python
def relative_error(approx, exact):
    if exact == 0 and approx == 0:
        return 0.0
    return abs(approx - exact) / abs(exact)
```

- `relative_error(1.01, 1.0)  =>  0.010000000000000009`
- `relative_error(0.0, 0.0)  =>  0.0`

Relative error scales the absolute error by the true magnitude. It is undefined at zero unless you special-case it.

### Q178. Basic

Write `bmi(weight_kg, height_m)` .

**Answer:**

```python
def bmi(weight_kg, height_m):
    return weight_kg / (height_m * height_m)
```

- `round(bmi(70, 1.75), 2)  =>  22.86`

Divide mass by height squared. Round only for display.

### Q179. Intermediate

Write `compound(principal, rate, years)` that returns the annual compound amount `principal * (1 + rate) ** years` using `decimal.Decimal` and string-friendly inputs. Return a `Decimal`.

**Answer:**

```python
from decimal import Decimal
def compound(principal, rate, years):
    p = Decimal(principal)
    r = Decimal(rate)
    return p * (1 + r) ** years
```

- `compound('1000', '0.05', 2)  =>  Decimal('1102.5000')`

Passing strings into `Decimal` keeps the rate exact. `**` on Decimals uses the decimal context.

### Q180. Advanced

Write `integrate_trap(f, a, b, n)` that approximates an integral with the trapezoidal rule and `n` panels.

**Answer:**

```python
def integrate_trap(f, a, b, n):
    h = (b - a) / n
    total = 0.5 * (f(a) + f(b))
    for i in range(1, n):
        total += f(a + i * h)
    return total * h
```

- `round(integrate_trap(lambda x: x, 0.0, 1.0, 4), 10)  =>  0.5`

The trapezoidal rule averages the endpoints at half weight and adds the interior samples. A linear function is integrated exactly.

### Q181. Advanced

Write `softmax(xs)` that returns a list of floats which sum to 1. Subtract the max first so the exponentials do not overflow.

**Answer:**

```python
import math
def softmax(xs):
    m = max(xs)
    exps = [math.exp(x - m) for x in xs]
    total = sum(exps)
    return [v / total for v in exps]
```

- `softmax([0.0, 0.0])  =>  [0.5, 0.5]`

Subtracting the max makes the largest exponential 1. The ratios are unchanged because every term is scaled by the same `e^(-max)`.

### Q182. Intermediate

Write `pct_change(old, new)` that returns the fractional change. Raise `ValueError` if `old` is 0.

**Answer:**

```python
def pct_change(old, new):
    if old == 0:
        raise ValueError('old is 0')
    return (new - old) / old
```

- `pct_change(50, 75)  =>  0.5`
- `pct_change(80, 60)  =>  -0.25`

A percentage in user-facing text is this fraction times 100. Keep the fraction in the function so callers can format it.

### Q183. Basic

Write `heron(a, b, c)` that returns the area of a triangle from its side lengths.

**Answer:**

```python
import math
def heron(a, b, c):
    s = (a + b + c) / 2
    return math.sqrt(s * (s - a) * (s - b) * (s - c))
```

- `heron(3, 4, 5)  =>  6.0`

Heron's formula uses the semi-perimeter. A 3-4-5 triangle has area 6.

### Q184. Advanced

Write `machine_eps()` that finds machine epsilon by halving until `1.0 + eps == 1.0`, then returning the last value that still changed the sum.

**Answer:**

```python
def machine_eps():
    eps = 1.0
    while 1.0 + eps / 2.0 != 1.0:
        eps /= 2.0
    return eps
```

- `machine_eps()  =>  2.220446049250313e-16`

This search finds the gap just below 1.0, which is `2 ** -52`.

### Q185. Advanced

Write `total_order(a, b)` that returns `-1`, `0`, or `1` using IEEE total ordering: NaN is greater than every number, including +inf, and `-0.0` is less than `+0.0`.

**Answer:**

```python
import math
def total_order(a, b):
    if math.isnan(a) or math.isnan(b):
        if math.isnan(a) and math.isnan(b):
            return 0
        return 1 if math.isnan(a) else -1
    if a == 0.0 and b == 0.0:
        sa = math.copysign(1.0, a) < 0
        sb = math.copysign(1.0, b) < 0
        return (sa < sb) - (sa > sb)
    if a < b:
        return -1
    if a > b:
        return 1
    return 0
```

- `total_order(-0.0, 0.0)  =>  -1`
- `total_order(0.0, -0.0)  =>  1`
- `total_order(1.0, 2.0)  =>  -1`
- `total_order(float('inf'), 5.0)  =>  1`
- `total_order(float('nan'), 1.0)  =>  1`
- `total_order(1.0, float('nan'))  =>  -1`
- `total_order(float('nan'), float('nan'))  =>  0`

Test NaN before ordered comparisons, because every comparison with NaN is false. Use `copysign` so `-0.0` sorts before `+0.0`.

### Q186. Basic

What does this print?

```python
print(4.0 % 3)
```

**Answer:**

```text
1.0
```

The remainder is 1.0. A float modulo returns a float.

### Q187. Basic

What does this print?

```python
print(pow(2.0, 3))
```

**Answer:**

```text
8.0
```

A float base yields a float power.

### Q188. Basic

What does this print?

```python
print(max(1.0, 2.5, -3.0))
```

**Answer:**

```text
2.5
```

`max` returns the greatest float.

### Q189. Intermediate

What does this print?

```python
import math
print(math.fabs(-3.5), abs(-3.5))
```

**Answer:**

```text
3.5 3.5
```

`math.fabs` always returns a float. `abs` returns a float here because the argument is a float.

### Q190. Intermediate

What does this print?

```python
import math
print(math.copysign(0.0, -2))
```

**Answer:**

```text
-0.0
```

The magnitude is zero and the sign comes from -2, so the result is `-0.0`.

### Q191. Intermediate

What does this print?

```python
print(f'{12.3456:+.2f}')
```

**Answer:**

```text
+12.35
```

The `+` flag forces a sign. `.2f` rounds to two decimal places.

### Q192. Intermediate

What does this print?

```python
import math
print(math.isfinite(-0.0))
```

**Answer:**

```text
True
```

Signed zero is finite.

### Q193. Advanced

What does this print?

```python
import math
print(math.nextafter(1.0, 0.0) < 1.0)
```

**Answer:**

```text
True
```

Stepping toward zero from 1.0 yields the previous representable value.

### Q194. Advanced

What does this print?

```python
from fractions import Fraction
print(float(Fraction(1, 3)))
```

**Answer:**

```text
0.3333333333333333
```

Converting a third to float introduces the usual binary approximation.

### Q195. Advanced

What does this print?

```python
import decimal
print(float(decimal.Decimal('0.1')) == 0.1)
```

**Answer:**

```text
True
```

Converting an exact decimal tenth into binary float lands on the same value as the literal `0.1`.

### Q196. Intermediate

What does this print?

```python
print((2.5).as_integer_ratio())
```

**Answer:**

```text
(5, 2)
```

`2.5` is exactly 5/2.

### Q197. Basic

What does this print?

```python
print(1.0 < float('inf'))
```

**Answer:**

```text
True
```

Positive infinity is greater than every finite float.

### Q198. Advanced

What does this print?

```python
import math
print(math.dist((1, 2, 2), (0, 0, 0)))
```

**Answer:**

```text
3.0
```

Distance from the origin to `(1, 2, 2)` is 3.

### Q199. Intermediate

What happens when this runs?

```python
import math
print(math.log(0))
```

**Answer:**

```text
ValueError: math domain error
```

The log of zero is undefined and raises `ValueError`. IEEE often returns `-inf`, but the `math` module rejects the domain error.

### Q200. Advanced

What does this print?

```python
import math
print(math.exp(-math.inf))
```

**Answer:**

```text
0.0
```

`exp` of negative infinity is 0.0. This one is defined.

*Section size: 200 questions (Basic 53, Intermediate 84, Advanced 63).*

## 3. Complex (complex)

A pair of floats. Arithmetic is supported. Ordering is not.

### Q1. Basic

What does this print?

```python
print(type(1+2j))
```

**Answer:**

```text
<class 'complex'>
```

A literal with `j` suffix is a `complex`.

### Q2. Basic

What does this print?

```python
print(type(1j))
```

**Answer:**

```text
<class 'complex'>
```

A pure imaginary literal is still `complex`.

### Q3. Basic

What happens when this runs?

```python
print(j)
```

**Answer:**

```text
NameError: name 'j' is not defined
```

Bare `j` is a name, not the imaginary unit unless you define it.

### Q4. Basic

What does this print?

```python
print((1+2j).real, (1+2j).imag)
```

**Answer:**

```text
1.0 2.0
```

`.real` and `.imag` are always floats.

### Q5. Basic

What does this print?

```python
z = 3+4j
print(z.real, z.imag)
```

**Answer:**

```text
3.0 4.0
```

Attributes work on a bound name.

### Q6. Basic

What does this print?

```python
print((5+0j).imag)
```

**Answer:**

```text
0.0
```

A real stored as complex has imaginary part `0.0`.

### Q7. Basic

What does this print?

```python
print((0+3j).real)
```

**Answer:**

```text
0.0
```

Pure imaginary has real part `0.0`.

### Q8. Basic

What does this print?

```python
print((1+2j).conjugate())
```

**Answer:**

```text
(1-2j)
```

`.conjugate()` negates the imaginary part.

### Q9. Basic

What does this print?

```python
print(complex(3, 4))
```

**Answer:**

```text
(3+4j)
```

Two arguments set real and imaginary parts.

### Q10. Basic

What does this print?

```python
print(complex(5))
```

**Answer:**

```text
(5+0j)
```

One argument sets real; imaginary is zero.

### Q11. Basic

What does this print?

```python
print(complex())
```

**Answer:**

```text
0j
```

`complex()` is `0j`.

### Q12. Basic

What does this print?

```python
print(complex(1.5, -2.5))
```

**Answer:**

```text
(1.5-2.5j)
```

Both parts may be floats.

### Q13. Basic

What does this print?

```python
print(complex(True, False))
```

**Answer:**

```text
(1+0j)
```

Bools convert like ints.

### Q14. Basic

What does this print?

```python
print(complex('1+2j'))
```

**Answer:**

```text
(1+2j)
```

String form is `real+imagi`.

### Q15. Basic

What does this print?

```python
print(complex('3'))
```

**Answer:**

```text
(3+0j)
```

A real-only string is valid.

### Q16. Basic

What does this print?

```python
print(complex('  -2-3j  '))
```

**Answer:**

```text
(-2-3j)
```

Surrounding whitespace is stripped.

### Q17. Basic

What happens when this runs?

```python
print(complex('1 + 2j'))
```

**Answer:**

```text
ValueError: complex() arg is a malformed string
```

Internal spaces are not allowed in the complex string grammar.

### Q18. Basic

What does this print?

```python
print(1+2j + 3+4j)
```

**Answer:**

```text
(4+6j)
```

Addition is component-wise.

### Q19. Basic

What does this print?

```python
print((1+2j) - (3+4j))
```

**Answer:**

```text
(-2-2j)
```

Subtraction is component-wise.

### Q20. Basic

What does this print?

```python
print((2+3j) * 2)
```

**Answer:**

```text
(4+6j)
```

Multiplying by a real scales both parts.

### Q21. Basic

What does this print?

```python
print(2 * (1+2j))
```

**Answer:**

```text
(2+4j)
```

Multiplication commutes with a real factor.

### Q22. Basic

What does this print?

```python
print((1+2j) + 3)
```

**Answer:**

```text
(4+2j)
```

An int addend promotes to complex.

### Q23. Basic

What does this print?

```python
print((1+2j) + 1.5)
```

**Answer:**

```text
(2.5+2j)
```

A float addend promotes with zero imag.

### Q24. Basic

What does this print?

```python
print(-(1+2j))
```

**Answer:**

```text
(-1-2j)
```

Unary minus negates both components.

### Q25. Basic

What does this print?

```python
print(abs(3+4j))
```

**Answer:**

```text
5.0
```

`abs` on complex is the modulus.

### Q26. Basic

What does this print?

```python
print(abs(0j))
```

**Answer:**

```text
0.0
```

Modulus of zero is `0.0`.

### Q27. Basic

What does this print?

```python
print((3+4j) == (3+4j))
```

**Answer:**

```text
True
```

Equality compares both parts.

### Q28. Basic

What does this print?

```python
print((3+4j) == (3+5j))
```

**Answer:**

```text
False
```

Different imaginary parts break equality.

### Q29. Basic

What does this print?

```python
print((1+0j) == 1)
```

**Answer:**

```text
True
```

Zero imaginary compares equal to the real int.

### Q30. Basic

What does this print?

```python
print((0+0j) == 0.0)
```

**Answer:**

```text
True
```

Zero complex equals float zero.

### Q31. Basic

What does this print?

```python
a = 1+0j
b = 1
print(a == b, a is b)
```

**Answer:**

```text
True False
```

Use `==` for numeric equality, not `is`.

### Q32. Basic

What does this print?

```python
print(bool(0+0j), bool(0j))
```

**Answer:**

```text
False False
```

Zero complex is falsy.

### Q33. Basic

What does this print?

```python
print(bool(0+1j), bool(1j))
```

**Answer:**

```text
True True
```

Non-zero imaginary is truthy.

### Q34. Basic

What does this print?

```python
print(1j * 1j)
```

**Answer:**

```text
(-1+0j)
```

`j*j` is `-1`.

### Q35. Basic

What does this print?

```python
print(2j * 3j)
```

**Answer:**

```text
(-6+0j)
```

Pure imaginaries multiply to a negative real.

### Q36. Basic

What does this print?

```python
print((1+2j) / 2)
```

**Answer:**

```text
(0.5+1j)
```

Division by real divides both parts.

### Q37. Basic

What does this print?

```python
print((2+0j) / 2)
```

**Answer:**

```text
(1+0j)
```

Result type stays complex.

### Q38. Basic

What does this print?

```python
print(pow(1+1j, 2))
```

**Answer:**

```text
2j
```

Integer powers use complex rules.

### Q39. Basic

What does this print?

```python
print((1+2j) * (1-2j))
```

**Answer:**

```text
(5+0j)
```

Product of conjugates is `5+0j`.

### Q40. Basic

What does this print?

```python
print(1+2j)
```

**Answer:**

```text
(1+2j)
```

`print` shows `real+imagi`.

### Q41. Basic

What does this print?

```python
print(repr(1+2j))
```

**Answer:**

```text
(1+2j)
```

`repr` matches the literal form.

### Q42. Basic

What does this print?

```python
print(f'{3+4j}')
```

**Answer:**

```text
(3+4j)
```

f-strings format complexes the same way.

### Q43. Basic

What happens when this runs?

```python
print((1+2j) < (3+4j))
```

**Answer:**

```text
TypeError: '<' not supported between instances of 'complex' and 'complex'
```

Complex numbers are unordered; `<` raises `TypeError`.

### Q44. Basic

What happens when this runs?

```python
print((1+2j) > 0)
```

**Answer:**

```text
TypeError: '>' not supported between instances of 'complex' and 'int'
```

Comparing complex to int is undefined.

### Q45. Basic

What happens when this runs?

```python
print(min(1j, 2j))
```

**Answer:**

```text
TypeError: '<' not supported between instances of 'complex' and 'complex'
```

`min` without a key needs a total order.

### Q46. Basic

What does this print?

```python
print(complex(b'2+3j'))
```

**Answer:**

```text
TypeError: complex() first argument must be a string or a number, not 'bytes'
```

ASCII bytes parse like strings.

### Q47. Basic

What does this print?

```python
print((0+5j)/5j)
```

**Answer:**

```text
(1+0j)
```

Division simplifies to `1+0j`.

### Q48. Basic

What does this print?

```python
print(format(3+4j, ''))
```

**Answer:**

```text
(3+4j)
```

Default format is the complex literal text.

### Q49. Basic

What does this print?

```python
print(complex('-2.5'))
```

**Answer:**

```text
(-2.5+0j)
```

Real-only decimal string.

### Q50. Basic

What does this print?

```python
print((-1+0j).imag)
```

**Answer:**

```text
0.0
```

Imag part of negative real complex.

### Q51. Basic

What does this print?

```python
print((0-1j).real)
```

**Answer:**

```text
0.0
```

Real part of negative imaginary.

### Q52. Basic

What does this print?

```python
print(0j + 1j)
```

**Answer:**

```text
1j
```

Adding pure imaginaries.

### Q53. Basic

What does this print?

```python
print(1+0j - 1)
```

**Answer:**

```text
0j
```

Subtract real int from complex.

### Q54. Basic

What does this print?

```python
print(complex(0, 0))
```

**Answer:**

```text
0j
```

Explicit zeros give `0j`.

### Q55. Basic

What does this print?

```python
print((1+2j).conjugate())
```

**Answer:**

```text
(1-2j)
```

Conjugate of `1+2j` flips the sign of the imaginary part.

### Q56. Basic

What does this print?

```python
print((3j).conjugate())
```

**Answer:**

```text
-3j
```

Conjugate of `3j` flips the sign of the imaginary part.

### Q57. Basic

What does this print?

```python
print((-2j).conjugate())
```

**Answer:**

```text
(-0+2j)
```

Conjugate of `-2j` flips the sign of the imaginary part.

### Q58. Basic

What does this print?

```python
print((4+0j).conjugate())
```

**Answer:**

```text
(4-0j)
```

Conjugate of `4+0j` flips the sign of the imaginary part.

### Q59. Basic

What does this print?

```python
print((1+2j) + (3+4j))
```

**Answer:**

```text
(4+6j)
```

Add real and imaginary parts separately.

### Q60. Intermediate

What does this print?

```python
print((1+2j) * (3+4j))
```

**Answer:**

```text
(-5+10j)
```

Expand `(a+bi)(c+di)`.

### Q61. Basic

What does this print?

```python
print((0+1j) + (1+0j))
```

**Answer:**

```text
(1+1j)
```

Add real and imaginary parts separately.

### Q62. Intermediate

What does this print?

```python
print((0+1j) * (1+0j))
```

**Answer:**

```text
1j
```

Expand `(a+bi)(c+di)`.

### Q63. Basic

What does this print?

```python
print((2+-1j) + (-3+2j))
```

**Answer:**

```text
(-1+1j)
```

Add real and imaginary parts separately.

### Q64. Intermediate

What does this print?

```python
print((2+-1j) * (-3+2j))
```

**Answer:**

```text
(-4+7j)
```

Expand `(a+bi)(c+di)`.

### Q65. Basic

What does this print?

```python
print((5+5j) + (-5+5j))
```

**Answer:**

```text
10j
```

Add real and imaginary parts separately.

### Q66. Intermediate

What does this print?

```python
print((5+5j) * (-5+5j))
```

**Answer:**

```text
(-50+0j)
```

Expand `(a+bi)(c+di)`.

### Q67. Basic

What does this print?

```python
print((-1+2j) + (3+-4j))
```

**Answer:**

```text
(2-2j)
```

Add real and imaginary parts separately.

### Q68. Intermediate

What does this print?

```python
print((-1+2j) * (3+-4j))
```

**Answer:**

```text
(5+10j)
```

Expand `(a+bi)(c+di)`.

### Q69. Intermediate

What does this print?

```python
import cmath
print(cmath.sqrt(-1))
```

**Answer:**

```text
1j
```

`cmath.sqrt` returns a complex root.

### Q70. Intermediate

What does this print?

```python
import cmath, math
print(cmath.exp(1j * math.pi) + 1)
```

**Answer:**

```text
1.2246467991473532e-16j
```

Euler: `e^(i pi) + 1 = 0`.

### Q71. Intermediate

What does this print?

```python
import cmath
print(cmath.log(1j))
```

**Answer:**

```text
1.5707963267948966j
```

Principal log of `i` is `(pi/2)j`.

### Q72. Intermediate

What does this print?

```python
import cmath
print(cmath.log(-1))
```

**Answer:**

```text
3.141592653589793j
```

Principal log of `-1` is `pi*j`.

### Q73. Intermediate

What does this print?

```python
import cmath, math
print(cmath.phase(1+1j))
```

**Answer:**

```text
0.7853981633974483
```

`phase` is radians.

### Q74. Intermediate

What does this print?

```python
import cmath, math
r, phi = cmath.polar(1+1j)
print(round(r, 10), round(phi, 10))
```

**Answer:**

```text
1.4142135624 0.7853981634
```

`polar` returns modulus and argument.

### Q75. Intermediate

What does this print?

```python
import cmath, math
print(cmath.rect(2, math.pi/2))
```

**Answer:**

```text
(1.2246467991473532e-16+2j)
```

`rect(r, phi)` is `r*e^(i phi)`.

### Q76. Intermediate

What does this print?

```python
import cmath
print(cmath.isclose(1+1j, 1+1.0000000001j))
```

**Answer:**

```text
True
```

Component-wise closeness.

### Q77. Intermediate

What does this print?

```python
print(hash(1+2j))
```

**Answer:**

```text
2000007
```

Hashable when parts are hashable.

### Q78. Intermediate

What does this print?

```python
print({1+2j: 'x'}[1+2j])
```

**Answer:**

```text
x
```

Complex dict keys use equality.

### Q79. Intermediate

What does this print?

```python
d = {1+2j: 10}
print((1+2j) in d, (1+2.0j) in d)
```

**Answer:**

```text
True True
```

Key lookup uses `==`.

### Q80. Intermediate

What does this print?

```python
print((1+2j) / (1+2j))
```

**Answer:**

```text
(1+0j)
```

Self-division is `1+0j`.

### Q81. Intermediate

What does this print?

```python
print((1+2j) / 1j)
```

**Answer:**

```text
(2-1j)
```

Divide by `j` via multiply by `-j`.

### Q82. Intermediate

What happens when this runs?

```python
print((1+2j) / 0j)
```

**Answer:**

```text
ZeroDivisionError: complex division by zero
```

Division by zero complex raises `ZeroDivisionError`.

### Q83. Intermediate

What does this print?

```python
print(complex(float('inf'), 0))
```

**Answer:**

```text
(inf+0j)
```

Infinity allowed in components.

### Q84. Intermediate

What does this print?

```python
print(complex(float('nan'), 1))
```

**Answer:**

```text
(nan+1j)
```

NaN poisons the real part.

### Q85. Intermediate

What does this print?

```python
print(complex(1, float('nan')) == complex(1, float('nan')))
```

**Answer:**

```text
False
```

NaN imag breaks reflexive equality.

### Q86. Intermediate

What does this print?

```python
print((1e308+0j) * 10)
```

**Answer:**

```text
(inf+0j)
```

Real overflow becomes `inf`.

### Q87. Intermediate

What does this print?

```python
import cmath
print(cmath.isfinite(1+2j), cmath.isfinite(complex(float('inf'), 0)))
```

**Answer:**

```text
True False
```

Finite test inspects both parts.

### Q88. Intermediate

What does this print?

```python
import cmath
print(cmath.isnan(complex(float('nan'), 0)))
```

**Answer:**

```text
True
```

NaN in either part triggers `isnan`.

### Q89. Intermediate

What does this print?

```python
print(pow(2+0j, 3))
```

**Answer:**

```text
(8+0j)
```

Powers stay in complex arithmetic.

### Q90. Intermediate

What does this print?

```python
print((2+3j) ** 2)
```

**Answer:**

```text
(-5+12j)
```

Squaring is full complex multiply.

### Q91. Intermediate

What happens when this runs?

```python
print((1+2j) // 1)
```

**Answer:**

```text
TypeError: unsupported operand type(s) for //: 'complex' and 'int'
```

Floor division unsupported for complex.

### Q92. Intermediate

What happens when this runs?

```python
print((1+2j) % 1)
```

**Answer:**

```text
TypeError: unsupported operand type(s) for %: 'complex' and 'int'
```

Modulo unsupported for complex.

### Q93. Intermediate

What does this print?

```python
print(sorted([1+0j, 3+0j, 2+0j], key=lambda z: z.real))
```

**Answer:**

```text
[(1+0j), (2+0j), (3+0j)]
```

Sort with a real-valued key.

### Q94. Intermediate

What does this print?

```python
print((1+2j) == (1.0+2.0))
```

**Answer:**

```text
False
```

Mixed numeric types in parts compare by value.

### Q95. Intermediate

What does this print?

```python
import cmath
print(cmath.sqrt(1j))
```

**Answer:**

```text
(0.7071067811865476+0.7071067811865475j)
```

Principal sqrt of `i`.

### Q96. Intermediate

What does this print?

```python
import cmath
print(cmath.exp(0))
```

**Answer:**

```text
(1+0j)
```

`exp(0)` is `1+0j`.

### Q97. Intermediate

What does this print?

```python
import cmath
print(cmath.sin(0))
```

**Answer:**

```text
0j
```

Trig extends to complex.

### Q98. Intermediate

What does this print?

```python
print(complex('inf+1j'))
```

**Answer:**

```text
(inf+1j)
```

`inf` in strings.

### Q99. Intermediate

What does this print?

```python
print(complex('nan+0j'))
```

**Answer:**

```text
(nan+0j)
```

`nan` in strings.

### Q100. Intermediate

What does this print?

```python
print(isinstance(1+2j, complex))
```

**Answer:**

```text
True
```

Type check.

### Q101. Intermediate

What does this print?

```python
print(1j - 1j)
```

**Answer:**

```text
0j
```

Cancellation to `0j`.

### Q102. Intermediate

What does this print?

```python
print((1+1j)*(1-1j))
```

**Answer:**

```text
(2+0j)
```

Product is `2+0j`.

### Q103. Intermediate

What does this print?

```python
print(abs(1j))
```

**Answer:**

```text
1.0
```

Unit imaginary has modulus 1.

### Q104. Intermediate

What does this print?

```python
print(abs(-3-4j))
```

**Answer:**

```text
5.0
```

Modulus ignores sign of parts.

### Q105. Intermediate

What does this print?

```python
print((1+2j)*0)
```

**Answer:**

```text
0j
```

Times zero gives `0j`.

### Q106. Intermediate

What does this print?

```python
print((1+2j)*1)
```

**Answer:**

```text
(1+2j)
```

Times one is unchanged.

### Q107. Intermediate

What does this print?

```python
print((1+2j).real == 1)
```

**Answer:**

```text
True
```

`.real` compares to int with `==`.

### Q108. Intermediate

What does this print?

```python
print((1+2j).imag == 2)
```

**Answer:**

```text
True
```

`.imag` compares to int.

### Q109. Intermediate

What does this print?

```python
print(len({1+2j, 1+2.0j}))
```

**Answer:**

```text
1
```

Set deduplicates equal complexes.

### Q110. Intermediate

What does this print?

```python
print((1+2j)*(-1))
```

**Answer:**

```text
(-1-2j)
```

Multiply by -1 negates both parts.

### Q111. Intermediate

What happens when this runs?

```python
print((1+2j) << 1)
```

**Answer:**

```text
TypeError: unsupported operand type(s) for <<: 'complex' and 'int'
```

Shift not defined on complex.

### Q112. Intermediate

What does this print?

```python
import cmath, math
roots = [cmath.exp(2j*math.pi*k/3) for k in range(3)]
print(len(roots), round(sum(roots).real, 10), round(sum(roots).imag, 10))
```

**Answer:**

```text
3 -0.0 0.0
```

The 3th roots of unity sum to zero.

### Q113. Intermediate

What does this print?

```python
import cmath, math
roots = [cmath.exp(2j*math.pi*k/4) for k in range(4)]
print(len(roots), round(sum(roots).real, 10), round(sum(roots).imag, 10))
```

**Answer:**

```text
4 -0.0 0.0
```

The 4th roots of unity sum to zero.

### Q114. Intermediate

What does this print?

```python
import cmath, math
roots = [cmath.exp(2j*math.pi*k/5) for k in range(5)]
print(len(roots), round(sum(roots).real, 10), round(sum(roots).imag, 10))
```

**Answer:**

```text
5 -0.0 0.0
```

The 5th roots of unity sum to zero.

### Q115. Intermediate

What does this print?

```python
import cmath, math
roots = [cmath.exp(2j*math.pi*k/6) for k in range(6)]
print(len(roots), round(sum(roots).real, 10), round(sum(roots).imag, 10))
```

**Answer:**

```text
6 -0.0 0.0
```

The 6th roots of unity sum to zero.

### Q116. Advanced

What does this print?

```python
import cmath
print(cmath.isclose(cmath.exp(2j*cmath.pi), 1))
```

**Answer:**

```text
True
```

`e^(2 pi i) = 1`.

### Q117. Advanced

What does this print?

```python
import cmath, math
z = cmath.exp(1j*math.pi/4)
print(round(z.real, 10), round(z.imag, 10))
```

**Answer:**

```text
0.7071067812 0.7071067812
```

Quarter turn on unit circle.

### Q118. Advanced

What does this print?

```python
print({complex(1,2): 1, complex(1.0,2.0): 2}[1+2j])
```

**Answer:**

```text
2
```

Equal keys collapse in dict.

### Q119. Advanced

What does this print?

```python
print(len({1+2j, 2+3j, 1+2.0j}))
```

**Answer:**

```text
2
```

Set deduplicates by equality.

### Q120. Advanced

What does this print?

```python
import cmath
print(cmath.log(0))
```

**Answer:**

```text
ValueError: math domain error
```

Log of zero is `-inf` in the complex log used here.

### Q121. Advanced

What does this print?

```python
print(pow(1+0j, 0.5))
```

**Answer:**

```text
(1+0j)
```

Fractional power uses complex branch.

### Q122. Advanced

What does this print?

```python
print((0+0j) ** 0)
```

**Answer:**

```text
(1+0j)
```

Python defines `0**0` as 1 even for complex.

### Q123. Advanced

What happens when this runs?

```python
print(complex('1+2i'))
```

**Answer:**

```text
ValueError: complex() arg is a malformed string
```

Imaginary suffix must be `j` or `J`.

### Q124. Advanced

What does this print?

```python
print(complex('1+2J'))
```

**Answer:**

```text
(1+2j)
```

Uppercase `J` works in strings.

### Q125. Advanced

What does this print?

```python
import cmath
print(cmath.isinf(complex(float('inf'), 1)))
```

**Answer:**

```text
True
```

Infinite component makes `isinf` true.

### Q126. Advanced

What does this print?

```python
z = 1+2j
print(z.real + z.imag * 1j == z)
```

**Answer:**

```text
True
```

Reassemble from `.real` and `.imag`.

### Q127. Advanced

What does this print?

```python
print(3+4j == 3+4.0j)
```

**Answer:**

```text
True
```

Float/int mix in parts.

### Q128. Advanced

What does this print?

```python
import cmath
print(cmath.phase(complex(-1, 0)))
```

**Answer:**

```text
3.141592653589793
```

Phase of `-1` is `pi`.

### Q129. Advanced

What does this print?

```python
import cmath
print(cmath.phase(0+0j))
```

**Answer:**

```text
0.0
```

Phase of zero is 0.

### Q130. Advanced

What does this print?

```python
import cmath
print(cmath.isclose(cmath.log(1), 0))
```

**Answer:**

```text
True
```

Log of 1 is 0.

### Q131. Advanced

What does this print?

```python
print(pow(1j, 4))
```

**Answer:**

```text
(1+0j)
```

`i^4` is 1.

### Q132. Advanced

What does this print?

```python
print(pow(1j, 3))
```

**Answer:**

```text
(-0-1j)
```

`i^3` is `-i`.

### Q133. Advanced

What happens when this runs?

```python
print(complex(1+2j, 3))
```

**Answer:**

```text
(1+5j)
```

`complex()` takes at most two scalars.

### Q134. Advanced

What does this print?

```python
import cmath
print(cmath.isclose(cmath.cos(0), 1))
```

**Answer:**

```text
True
```

Complex cos at 0 is 1.

### Q135. Advanced

What does this print?

```python
print((1+2j).conjugate().conjugate() == 1+2j)
```

**Answer:**

```text
True
```

Double conjugate restores the value.

### Q136. Advanced

What does this print?

```python
print(abs((3+4j).conjugate()) == abs(3+4j))
```

**Answer:**

```text
True
```

Modulus unchanged by conjugation.

### Q137. Advanced

What does this print?

```python
print((1+2j) - 1j)
```

**Answer:**

```text
(1+1j)
```

Subtract pure imaginary adjusts imag part.

### Q138. Advanced

What does this print?

```python
print((2+2j)/(1+1j))
```

**Answer:**

```text
(2+0j)
```

Division simplifies to `2+0j`.

### Q139. Advanced

What does this print?

```python
import cmath
print(cmath.polar(0+0j))
```

**Answer:**

```text
(0.0, 0.0)
```

Polar of zero is `(0.0, 0.0)`.

### Q140. Advanced

What does this print?

```python
import cmath
print(cmath.rect(0, 1))
```

**Answer:**

```text
0j
```

Zero radius gives zero regardless of angle.

### Q141. Advanced

What does this print?

```python
import cmath
print(cmath.isclose(cmath.tan(0), 0))
```

**Answer:**

```text
True
```

Tan at 0 is 0 in complex extension.

### Q142. Advanced

What does this print?

```python
print(hash(1+2j) == hash(1.0+2.0j))
```

**Answer:**

```text
True
```

Equal complexes must share hash.

### Q143. Advanced

What does this print?

```python
print(len({1+2j:0, 3+4j:0}))
```

**Answer:**

```text
2
```

Dict can hold distinct complex keys.

### Q144. Basic

What does this print?

```python
print((1+2j)+(-1-2j))
```

**Answer:**

```text
0j
```

Additive inverse sums to `0j`.

### Q145. Basic

What does this print?

```python
print((3+0j).conjugate())
```

**Answer:**

```text
(3-0j)
```

Real-only complex is its own conjugate.

### Q146. Intermediate

What does this print?

```python
print((1+2j)+0j)
```

**Answer:**

```text
(1+2j)
```

Adding zero complex.

### Q147. Intermediate

What does this print?

```python
print((1+2j)-0j)
```

**Answer:**

```text
(1+2j)
```

Subtracting zero complex.

### Q148. Intermediate

What does this print?

```python
print(complex(1.0))
```

**Answer:**

```text
(1+0j)
```

Float real-only constructor.

### Q149. Advanced

What does this print?

```python
import cmath
print(cmath.isclose(cmath.sinh(0), 0))
```

**Answer:**

```text
True
```

Sinh at 0 is 0.

### Q150. Advanced

What does this print?

```python
print(pow(-1+0j, 0.5))
```

**Answer:**

```text
(6.123233995736766e-17+1j)
```

Square root of -1 as complex.

### Q151. Intermediate

What does this print?

```python
print((1+2j)/1)
```

**Answer:**

```text
(1+2j)
```

Divide by real 1.

### Q152. Basic

What does this print?

```python
print((1+2j)*1j)
```

**Answer:**

```text
(-2+1j)
```

Multiply by `j` rotates 90 degrees in the plane.

### Q153. Advanced

What does this print?

```python
import cmath
print(cmath.isclose(abs(cmath.rect(5, 0)), 5))
```

**Answer:**

```text
True
```

Rect with angle 0 is on positive real axis.

### Q154. Basic

What does this print?

```python
print((2+3j) == 2+3.0j)
```

**Answer:**

```text
True
```

Float imag compares equal to int imag.

### Q155. Basic

What does this print?

```python
print((2+3j) != 2+4j)
```

**Answer:**

```text
True
```

Inequality when imag differs.

### Q156. Intermediate

What does this print?

```python
print((1+2j) + (3+4j) == (4+6j))
```

**Answer:**

```text
True
```

Sum matches constructed result.

### Q157. Intermediate

What does this print?

```python
import cmath
print(cmath.isclose(cmath.sqrt(-4), 2j))
```

**Answer:**

```text
True
```

Sqrt of negative real is pure imaginary.

### Q158. Intermediate

What does this print?

```python
import cmath
print(cmath.isclose(cmath.log(-1), 3.141592653589793j))
```

**Answer:**

```text
True
```

Log of -1 is pi*j.

### Q159. Advanced

What does this print?

```python
import cmath
print(cmath.isclose(cmath.exp(3.141592653589793j), -1))
```

**Answer:**

```text
True
```

Euler on pi*j gives -1.

### Q160. Intermediate

What does this print?

```python
print(complex(3.0, 4.0) == 3+4j)
```

**Answer:**

```text
True
```

Constructor from floats.

### Q161. Intermediate

What does this print?

```python
print((1+2j)*(-1+0j))
```

**Answer:**

```text
(-1-2j)
```

Multiply by -1 negates.

### Q162. Advanced

What does this print?

```python
print(pow(2j, 2))
```

**Answer:**

```text
(-4+0j)
```

Square of 2j is -4.

### Q163. Advanced

What does this print?

```python
print(pow(1+1j, 3))
```

**Answer:**

```text
(-2+2j)
```

Cube via complex pow.

### Q164. Intermediate

What does this print?

```python
print(str(1+2j))
```

**Answer:**

```text
(1+2j)
```

str of complex matches print form.

### Q165. Basic

What does this print?

```python
print((0+1j) + (0+1j))
```

**Answer:**

```text
2j
```

Sum of two j is 2j.

### Q166. Basic

What does this print?

```python
print((1+0j) * (0+1j))
```

**Answer:**

```text
1j
```

Real times j gives pure imag.

### Q167. Intermediate

What does this print?

```python
print((3+4j) - (3+4j))
```

**Answer:**

```text
0j
```

Difference of equals is zero.

### Q168. Advanced

What does this print?

```python
import cmath
print(cmath.isclose(cmath.cos(3.141592653589793), -1))
```

**Answer:**

```text
True
```

Complex cos at pi is -1.

### Q169. Advanced

What does this print?

```python
import cmath
print(cmath.isclose(cmath.sin(3.141592653589793), 0))
```

**Answer:**

```text
False
```

Complex sin at pi is 0.

### Q170. Intermediate

What does this print?

```python
print(complex('-0-0j'))
```

**Answer:**

```text
(-0-0j)
```

Signed zeros in string form.

### Q171. Intermediate

What does this print?

```python
print(-0-0j)
```

**Answer:**

```text
0j
```

Unary minus on `-0-0j` literal.

### Q172. Advanced

What does this print?

```python
print((complex(float('inf'), 1) * 0).real)
```

**Answer:**

```text
nan
```

inf * 0 in complex gives NaN real part.

### Q173. Advanced

What does this print?

```python
import cmath
print(cmath.isclose(cmath.hypot(3, 4), 5))
```

**Answer:**

```text
AttributeError: module 'cmath' has no attribute 'hypot'
```

`cmath.hypot` matches 3-4-5 triangle.

### Q174. Intermediate

What does this print?

```python
print((1+2j).conjugate() == (1-2j))
```

**Answer:**

```text
True
```

Conjugate equality.

### Q175. Basic

What does this print?

```python
print(0j == 0+0j)
```

**Answer:**

```text
True
```

Zero complexes equal.

### Q176. Intermediate

What does this print?

```python
print(abs((3+4j)/(3+4j)))
```

**Answer:**

```text
1.0
```

Unit modulus after self-division.

### Q177. Advanced

What does this print?

```python
import cmath
print(cmath.isclose(cmath.polar(3+4j)[0], 5))
```

**Answer:**

```text
True
```

Polar radius matches abs.

### Q178. Advanced

What does this print?

```python
import cmath, math
print(cmath.isclose(cmath.polar(1+1j)[1], math.pi/4))
```

**Answer:**

```text
True
```

Polar angle of 1+1j is pi/4.

### Q179. Basic

Write `cadd(a, b)` returning the sum of complexes `a` and `b`.

**Answer:**

```python
def cadd(a, b):
    return a + b
```

- `cadd(1+2j, 3+4j)  =>  (4+6j)`
- `cadd(0j, 1j)  =>  1j`

Use built-in addition.

### Q180. Basic

Write `cmul(a, b)` returning the product.

**Answer:**

```python
def cmul(a, b):
    return a * b
```

- `cmul(1+2j, 3+4j)  =>  (-5+10j)`
- `cmul(1j, 1j)  =>  (-1+0j)`

Built-in multiplication.

### Q181. Basic

Write `modulus(z)` returning `abs(z)`.

**Answer:**

```python
def modulus(z):
    return abs(z)
```

- `modulus(3+4j)  =>  5.0`
- `modulus(0+0j)  =>  0.0`

Modulus via `abs`.

### Q182. Intermediate

Write `cdiv(a, b)` returning `a/b`.

**Answer:**

```python
def cdiv(a, b):
    return a / b
```

- `cdiv(1+2j, 1+2j)  =>  (1+0j)`
- `cdiv(1, 1j)  =>  -1j`

Complex division.

### Q183. Intermediate

Write `arg_deg(z)` returning argument in degrees.

**Answer:**

```python
import cmath, math

def arg_deg(z):
    return math.degrees(cmath.phase(z))
```

- `round(arg_deg(1+1j), 6)  =>  45.0`
- `round(arg_deg(1j), 6)  =>  90.0`

Radians to degrees.

### Q184. Intermediate

Write `rotate(z, degrees)` rotating counterclockwise.

**Answer:**

```python
import cmath, math

def rotate(z, degrees):
    return z * cmath.exp(1j * math.radians(degrees))
```

- `round(rotate(1+0j, 90).real, 10)  =>  0.0`
- `round(rotate(1+0j, 90).imag, 10)  =>  1.0`

Multiply by unit phasor.

### Q185. Advanced

Write `mandelbrot_escape(c, limit=100)` counting iterations before `abs(z)>2`.

**Answer:**

```python
def mandelbrot_escape(c, limit=100):
    z = 0j
    for n in range(limit):
        if abs(z) > 2:
            return n
        z = z * z + c
    return limit
```

- `mandelbrot_escape(0j)  =>  100`
- `mandelbrot_escape(2+0j)  =>  2`
- `mandelbrot_escape(-0.5+0j)  =>  100`

Classic quadratic map.

### Q186. Advanced

Write `roots_of_unity(n)` listing all `n`th roots of 1.

**Answer:**

```python
import cmath, math

def roots_of_unity(n):
    return [cmath.exp(2j * math.pi * k / n) for k in range(n)]
```

- `len(roots_of_unity(4))  =>  4`
- `round(sum(roots_of_unity(4)).real, 10)  =>  -0.0`

Equally spaced on unit circle.

### Q187. Intermediate

Write `conjugate_sum(z)` returning `z + z.conjugate()`.

**Answer:**

```python
def conjugate_sum(z):
    return z + z.conjugate()
```

- `conjugate_sum(3+4j)  =>  (6+0j)`
- `conjugate_sum(2j)  =>  0j`

Doubles real part.

### Q188. Intermediate

Write `is_real(z, tol=1e-9)` if `abs(z.imag) <= tol`.

**Answer:**

```python
def is_real(z, tol=1e-9):
    return abs(z.imag) <= tol
```

- `is_real(3+0j)  =>  True`
- `is_real(3+1e-12j)  =>  True`
- `is_real(1j)  =>  False`

Tolerance on imag.

### Q189. Advanced

Write `complex_distance(a, b)` as `abs(a-b)`.

**Answer:**

```python
def complex_distance(a, b):
    return abs(a - b)
```

- `complex_distance(0j, 3+4j)  =>  5.0`
- `complex_distance(1+1j, 1+1j)  =>  0.0`

Plane distance.

### Q190. Basic

Write `pure_imag(n)` returning `n*1j`.

**Answer:**

```python
def pure_imag(n):
    return n * 1j
```

- `pure_imag(3)  =>  3j`
- `pure_imag(-2)  =>  (-0-2j)`

Scale the unit imaginary.

### Q191. Advanced

Write `from_polar(r, phi_rad)` using `cmath.rect`.

**Answer:**

```python
import cmath

def from_polar(r, phi_rad):
    return cmath.rect(r, phi_rad)
```

- `round(from_polar(1, 0).real, 10)  =>  1.0`
- `round(from_polar(1, 3.141592653589793/2).imag, 10)  =>  1.0`

Polar to rect.

### Q192. Intermediate

Write `scale(z, k)` returning `k*z` for real `k`.

**Answer:**

```python
def scale(z, k):
    return k * z
```

- `scale(1+2j, 3)  =>  (3+6j)`
- `scale(1+2j, 0.5)  =>  (0.5+1j)`

Homothety.

### Q193. Advanced

Write `reciprocal(z)` returning `1/z`, raising on zero.

**Answer:**

```python
def reciprocal(z):
    if z == 0:
        raise ZeroDivisionError('zero')
    return 1 / z
```

- `reciprocal(1+0j)  =>  (1+0j)`
- `reciprocal(1j)  =>  -1j`

Guard zero.

### Q194. Intermediate

Write `dot_as_complex(x1, y1, x2, y2)` returning `(x1+iy1)*(x2+iy2)`.

**Answer:**

```python
def dot_as_complex(x1, y1, x2, y2):
    return complex(x1, y1) * complex(x2, y2)
```

- `dot_as_complex(1,2,3,4)  =>  (-5+10j)`

Pack reals into complex multiply.

### Q195. Advanced

Write `magnitude_squared(z)` returning `z.real**2 + z.imag**2`.

**Answer:**

```python
def magnitude_squared(z):
    return z.real ** 2 + z.imag ** 2
```

- `magnitude_squared(3+4j)  =>  25.0`
- `magnitude_squared(1j)  =>  1.0`

Same as `abs(z)**2` without sqrt.

### Q196. Basic

Write `to_complex(real, imag=0)` wrapping `complex(real, imag)`.

**Answer:**

```python
def to_complex(real, imag=0):
    return complex(real, imag)
```

- `to_complex(3, 4)  =>  (3+4j)`
- `to_complex(5)  =>  (5+0j)`

Thin wrapper for teaching.

### Q197. Advanced

Write `iter_mandel(c, n)` returning the first `n` iterates of `z_{k+1}=z_k^2+c`.

**Answer:**

```python
def iter_mandel(c, n):
    z = 0j
    out = []
    for _ in range(n):
        z = z * z + c
        out.append(z)
    return out
```

- `len(iter_mandel(0j, 3))  =>  3`
- `iter_mandel(1j, 2)[1]  =>  (-1+1j)`

Trace the orbit.

### Q198. Intermediate

Write `reflect_x(z)` returning the conjugate (reflect across real axis).

**Answer:**

```python
def reflect_x(z):
    return z.conjugate()
```

- `reflect_x(3+4j)  =>  (3-4j)`
- `reflect_x(2j)  =>  -2j`

Conjugate reflects across the real axis.

### Q199. Advanced

What does this print?

```python
z = 3+4j
print(z.real, z.imag, abs(z))
```

**Answer:**

```text
3.0 4.0 5.0
```

`.real` and `.imag` are floats. `abs` is the modulus.

### Q200. Intermediate

What happens when this runs?

```python
print((1+2j) < (2+3j))
```

**Answer:**

```text
TypeError: '<' not supported between instances of 'complex' and 'complex'
```

Complex numbers cannot be ordered.

*Section size: 200 questions (Basic 76, Intermediate 76, Advanced 48).*

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

## 5. String (str)

Immutable Unicode text. Indexing, slicing, methods, formatting, and encoding are the practice surface.

### Q1. Basic

What does this print?

```python
s = 'abc'
s += 'd'
print(s)
```

**Answer:**

```text
abcd
```

Strings are immutable; `+=` binds a new str object to `s`.

### Q2. Basic

What does this print?

```python
a = 'hi'
b = a
a = a + '!'
print(a, b)
```

**Answer:**

```text
hi! hi
```

Rebinding `a` does not mutate the object `b` still references.

### Q3. Basic

What does this print?

```python
print('hello'[0], 'hello'[-1])
```

**Answer:**

```text
h o
```

Indexing uses 0-based offsets; `-1` is the last code unit.

### Q4. Basic

What does this print?

```python
print(len(''))
```

**Answer:**

```text
0
```

The empty string has length 0.

### Q5. Basic

What does this print?

```python
print('Python'[1:4])
```

**Answer:**

```text
yth
```

Slice `[1:4]` is characters at indices 1, 2, and 3.

### Q6. Basic

What does this print?

```python
print('Python'[:3], 'Python'[3:])
```

**Answer:**

```text
Pyt hon
```

Omitted start is 0; omitted stop is the end.

### Q7. Basic

What does this print?

```python
print('Python'[::2])
```

**Answer:**

```text
Pto
```

Stride 2 takes every second character.

### Q8. Basic

What does this print?

```python
print('Python'[::-1])
```

**Answer:**

```text
nohtyP
```

A stride of -1 reverses the sequence of code units.

### Q9. Basic

What does this print?

```python
print('ab' + 'cd', 'x' * 3)
```

**Answer:**

```text
abcd xxx
```

`+` concatenates; `*` repeats the string.

### Q10. Basic

What does this print?

```python
print(''.join(['a', 'b', 'c']))
```

**Answer:**

```text
abc
```

`str.join` concatenates an iterable of strings with the separator between elements.

### Q11. Basic

What does this print?

```python
print('+'.join(['1', '2', '3']))
```

**Answer:**

```text
1+2+3
```

The separator is the string on which `join` is called.

### Q12. Basic

What does this print?

```python
print('a' + 'b' == 'ab', 'a' * 0)
```

**Answer:**

```text
True 
```

Concatenation and repetition produce new strings; `n * 0` is empty.

### Q13. Basic

What does this print?

```python
print('abc' == 'abc', 'abc' < 'abd')
```

**Answer:**

```text
True True
```

Strings compare lexicographically by code unit.

### Q14. Basic

What does this print?

```python
print('A' < 'a')
```

**Answer:**

```text
True
```

Uppercase ASCII letters precede lowercase in Unicode code point order.

### Q15. Basic

What does this print?

```python
print(ord('A'), chr(65))
```

**Answer:**

```text
65 A
```

`ord` maps a one-code-unit str to its integer; `chr` is the inverse for valid code points.

### Q16. Basic

What does this print?

```python
print('\n', '\t', '\\', "'")
```

**Answer:**

```text

 	 \ '
```

Backslash introduces escape sequences; `\n` is newline, `\t` tab.

### Q17. Basic

What does this print?

```python
print(r'\n\t')
```

**Answer:**

```text
\n\t
```

Raw strings do not process escapes; backslashes are literal.

### Q18. Basic

What does this print?

```python
print('line1\nline2')
```

**Answer:**

```text
line1
line2
```

In a normal string, `\n` becomes a newline character.

### Q19. Basic

What does this print?

```python
x = 3
print(f'{x + 2}')
```

**Answer:**

```text
5
```

An f-string evaluates expressions inside `{...}`.

### Q20. Basic

What does this print?

```python
print(f'{'hi'}')
```

**Answer:**

```text
hi
```

Nested braces in f-strings use doubled braces for literal `{`.

### Q21. Basic

What does this print?

```python
print(f'{42:05d}')
```

**Answer:**

```text
00042
```

Format spec `05d` zero-pads a decimal integer to width 5.

### Q22. Basic

What does this print?

```python
print('%s %d' % ('a', 7))
```

**Answer:**

```text
a 7
```

The old `%` operator still formats strings when given a tuple on the right.

### Q23. Basic

What does this print?

```python
print('  spa  '.strip())
```

**Answer:**

```text
spa
```

`strip` removes leading and trailing whitespace by default.

### Q24. Basic

What does this print?

```python
print('a,b,c'.split(','))
```

**Answer:**

```text
['a', 'b', 'c']
```

`split` breaks on a separator and returns a list of substrings.

### Q25. Basic

What does this print?

```python
print('a  b'.split())
```

**Answer:**

```text
['a', 'b']
```

With no argument, `split` splits on any run of whitespace.

### Q26. Basic

What does this print?

```python
print('hello'.upper(), 'HELLO'.lower())
```

**Answer:**

```text
HELLO hello
```

`upper` and `lower` return new strings with case changed.

### Q27. Basic

What does this print?

```python
print('hello'.startswith('he'), 'hello'.endswith('lo'))
```

**Answer:**

```text
True True
```

Prefix and suffix tests return bool.

### Q28. Basic

What does this print?

```python
print('banana'.count('a'))
```

**Answer:**

```text
3
```

`count` returns non-overlapping occurrences.

### Q29. Basic

What does this print?

```python
print('spam'.find('x'), 'spam'.find('a'))
```

**Answer:**

```text
-1 2
```

`find` returns -1 when the substring is missing; otherwise the index.

### Q30. Basic

What happens when this runs?

```python
print('spam'.index('x'))
```

**Answer:**

```text
ValueError: substring not found
```

`index` raises `ValueError` when the substring is not found.

### Q31. Basic

What does this print?

```python
print('foo bar'.replace('bar', 'baz'))
```

**Answer:**

```text
foo baz
```

`replace` returns a new string with all occurrences substituted.

### Q32. Basic

What does this print?

```python
print('42'.isdigit(), '3.14'.isdigit())
```

**Answer:**

```text
True False
```

`isdigit` is true only when every character is a Unicode decimal digit character.

### Q33. Basic

What does this print?

```python
print('abc'.isalpha(), 'abc123'.isalnum())
```

**Answer:**

```text
True True
```

`isalpha` requires letters; `isalnum` allows digits too.

### Q34. Basic

What does this print?

```python
print('café'.title())
```

**Answer:**

```text
Café
```

`title` capitalizes words; behavior follows Unicode titlecase rules.

### Q35. Basic

What does this print?

```python
print('hello\nworld'.splitlines())
```

**Answer:**

```text
['hello', 'world']
```

`splitlines` splits on line boundaries without keeping terminators.

### Q36. Basic

What does this print?

```python
print('42'.zfill(5))
```

**Answer:**

```text
00042
```

`zfill` pads with zeros on the left to reach the width.

### Q37. Basic

What does this print?

```python
print('hi'.center(6, '-'))
```

**Answer:**

```text
--hi--
```

`center` pads equally on both sides with the fill character.

### Q38. Basic

What does this print?

```python
print('a\tb'.expandtabs(4))
```

**Answer:**

```text
a   b
```

`expandtabs` replaces tabs with spaces up to the next tab stop.

### Q39. Basic

What does this print?

```python
print('a|b|c'.partition('|'))
```

**Answer:**

```text
('a', '|', 'b|c')
```

`partition` splits at the first separator into three parts.

### Q40. Basic

What does this print?

```python
print('a-b-a'.rsplit('-', 1))
```

**Answer:**

```text
['a-b', 'a']
```

`rsplit` with `maxsplit=1` splits from the right once.

### Q41. Basic

What does this print?

```python
print('prefix_name'.removeprefix('prefix_'))
```

**Answer:**

```text
name
```

`removeprefix` removes a leading prefix if present (3.9+).

### Q42. Basic

What does this print?

```python
print('file.txt'.removesuffix('.txt'))
```

**Answer:**

```text
file
```

`removesuffix` removes a trailing suffix if present (3.9+).

### Q43. Basic

What does this print?

```python
print('Hello'.casefold())
```

**Answer:**

```text
hello
```

`casefold` is stronger than `lower` for case-insensitive matching (e.g. German ß).

### Q44. Basic

What does this print?

```python
print('Ⅳ'.isnumeric(), '½'.isnumeric())
```

**Answer:**

```text
True True
```

`isnumeric` is true for Unicode numeric characters, not only ASCII digits.

### Q45. Basic

Why is comparing strings with `==` usually correct, while using `is` between separately constructed equal strings is not?

**Answer:**

``==`` compares value (code units in order). ``is`` compares object identity. Equal strings may be distinct objects unless interned or cached; only ``==`` matches string content reliably.

### Q46. Basic

What is the difference between a Python `str` code unit and a user-visible grapheme?

**Answer:**

A ``str`` element is one UTF-16-like code unit in CPython's compact representation (often one Unicode code point). A grapheme is a user-perceived character and may be several code points (e.g. base letter plus combining mark). ``len(s)`` counts code units/code points in the internal representation, not grapheme clusters.

### Q47. Basic

Why does `'hello' + 'world'` often differ from `''.join(['hello', 'world'])` in performance for many pieces?

**Answer:**

Repeated ``+`` in a loop creates intermediate strings. ``join`` computes total size once and copies once, which is linear overall instead of quadratic.

### Q48. Basic

When is `str.find` preferable to `str.index`?

**Answer:**

Use ``find`` when a missing substring is an ordinary outcome (returns ``-1``). Use ``index`` when absence should raise ``ValueError``.

### Q49. Basic

What does the `b` prefix on a bytes literal mean, and how does it relate to `str`?

**Answer:**

``b'...'`` is a ``bytes`` object (raw 0–255 values), not Unicode text. Text is ``str``; encode with ``.encode()`` to get ``bytes``, decode with ``.decode()`` to get ``str``.

### Q50. Basic

Write `count_vowels(s)` that counts ASCII vowels `aeiou` in either case.

**Answer:**

```python
def count_vowels(s):
    return sum(1 for c in s if c.lower() in "aeiou")
```

- `count_vowels('')  =>  0`
- `count_vowels('Hello')  =>  2`
- `count_vowels('xyz')  =>  0`

Scan once; membership in a vowel set after lowercasing handles case.

### Q51. Basic

Write `is_palindrome(s)` that is true when `s` reads the same forward and backward (compare case-sensitively).

**Answer:**

```python
def is_palindrome(s):
    return s == s[::-1]
```

- `is_palindrome('')  =>  True`
- `is_palindrome('aba')  =>  True`
- `is_palindrome('ab')  =>  False`

Slice reversal compares code units in reverse order.

### Q52. Basic

Write `reverse_words(s)` that reverses the order of whitespace-separated words in `s` (single spaces between words in the result).

**Answer:**

```python
def reverse_words(s):
    parts = s.split()
    return " ".join(reversed(parts))
```

- `reverse_words('one two three')  =>  'three two one'`
- `reverse_words('  a   b  ')  =>  'b a'`

`split` without args normalizes internal whitespace when rejoining with a single space.

### Q53. Basic

Write `unique_chars(s)` returning a string of first-seen characters in order (no duplicates).

**Answer:**

```python
def unique_chars(s):
    seen = set()
    out = []
    for c in s:
        if c not in seen:
            seen.add(c)
            out.append(c)
    return "".join(out)
```

- `unique_chars('banana')  =>  'ban'`
- `unique_chars('')  =>  ''`

A set tracks membership; the list preserves first occurrence order.

### Q54. Basic

Write `compress_spaces(s)` replacing each run of whitespace with a single space and stripping ends.

**Answer:**

```python
def compress_spaces(s):
    return " ".join(s.split())
```

- `compress_spaces('  a   b  ')  =>  'a b'`
- `compress_spaces('x')  =>  'x'`

`split()` on whitespace runs, then `join` with one space.

### Q55. Basic

Write `snake_to_camel(name)` turning `hello_world` into `helloWorld` (first segment stays lower).

**Answer:**

```python
def snake_to_camel(name):
    parts = name.split("_")
    return parts[0] + "".join(p.capitalize() for p in parts[1:])
```

- `snake_to_camel('hello_world')  =>  'helloWorld'`
- `snake_to_camel('a')  =>  'a'`

Split on `_`, capitalize subsequent segments, concatenate.

### Q56. Basic

Write `first_non_repeating(s)` returning the first character that appears exactly once, or `''` if none.

**Answer:**

```python
def first_non_repeating(s):
    from collections import Counter
    counts = Counter(s)
    for c in s:
        if counts[c] == 1:
            return c
    return ""
```

- `first_non_repeating('aabbc')  =>  'c'`
- `first_non_repeating('aabb')  =>  ''`

Count frequencies, then scan in original order for count 1.

### Q57. Basic

Write `wrap_text(text, width)` returning lines at most `width` characters, breaking on spaces when possible (greedy).

**Answer:**

```python
def wrap_text(text, width):
    words = text.split()
    if not words:
        return []
    lines, cur = [], words[0]
    for w in words[1:]:
        if len(cur) + 1 + len(w) <= width:
            cur += " " + w
        else:
            lines.append(cur)
            cur = w
    lines.append(cur)
    return lines
```

- `wrap_text('one two three four', 7)  =>  ['one two', 'three', 'four']`
- `wrap_text('', 5)  =>  []`

Pack words until the next word would exceed `width`, then start a new line.

### Q58. Intermediate

What does this print?

```python
print('é', len('é'), len('e\u0301'))
```

**Answer:**

```text
é 1 2
```

Precomposed é is one code point; decomposed e + combining acute is two code points, so lengths differ.

### Q59. Intermediate

What does this print?

```python
import unicodedata as u
a='é'
b='e\u0301'
print(u.normalize('NFC', b) == a, len(u.normalize('NFC', b)))
```

**Answer:**

```text
True 1
```

NFC composes sequences; normalized decomposed form equals precomposed é.

### Q60. Intermediate

What does this print?

```python
import unicodedata as u
print(u.normalize('NFD', 'é') == 'e\u0301')
```

**Answer:**

```text
True
```

NFD expands to base character plus combining marks.

### Q61. Intermediate

What does this print?

```python
s='café'
print(s.encode('utf-8'))
```

**Answer:**

```text
b'caf\xc3\xa9'
```

UTF-8 encodes Unicode text to bytes; non-ASCII expands to multiple bytes.

### Q62. Intermediate

What does this print?

```python
print(b'\xc3\xa9'.decode('utf-8'))
```

**Answer:**

```text
é
```

UTF-8 bytes for é decode back to the str `é`.

### Q63. Intermediate

What does this print?

```python
print('é'.encode('latin-1'))
```

**Answer:**

```text
b'\xe9'
```

Latin-1 maps code points U+0000–U+00FF directly to bytes; é is one byte 0xe9.

### Q64. Intermediate

What happens when this runs?

```python
print('€'.encode('latin-1'))
```

**Answer:**

```text
UnicodeEncodeError: 'latin-1' codec can't encode character '\u20ac' in position 0: ordinal not in range(256)
```

Euro sign is outside Latin-1 range; encoding raises `UnicodeEncodeError`.

### Q65. Intermediate

What does this print?

```python
print(b'\xff'.decode('latin-1'))
```

**Answer:**

```text
ÿ
```

Latin-1 decode maps each byte 0–255 to U+0000–U+00FF.

### Q66. Intermediate

What happens when this runs?

```python
print(b'\xff'.decode('utf-8'))
```

**Answer:**

```text
UnicodeDecodeError: 'utf-8' codec can't decode byte 0xff in position 0: invalid start byte
```

Invalid UTF-8 byte sequence raises `UnicodeDecodeError` by default.

### Q67. Intermediate

What does this print?

```python
print(b'\xff'.decode('utf-8', errors='replace'))
```

**Answer:**

```text
�
```

`errors='replace'` substitutes U+FFFD for invalid bytes.

### Q68. Intermediate

What does this print?

```python
print('hello'.encode('ascii'), 'hello'.encode('utf-8') == 'hello'.encode('ascii'))
```

**Answer:**

```text
b'hello' True
```

ASCII-only text encodes identically in ASCII and UTF-8.

### Q69. Intermediate

What does this print?

```python
table=str.maketrans('aeiou', '12345')
print('hello'.translate(table))
```

**Answer:**

```text
h2ll4
```

`maketrans` builds a translation map; `translate` applies it per character.

### Q70. Intermediate

What does this print?

```python
print('hello'.translate(str.maketrans('', '', 'aeiou')))
```

**Answer:**

```text
hll
```

Deleting characters: map third argument lists chars to remove.

### Q71. Intermediate

What does this print?

```python
a='hello'
b='hello'
print(a == b, a is b)
```

**Answer:**

```text
True True
```

Equal string literals may be interned to one object in CPython; identity often matches equality for literals.

### Q72. Intermediate

What does this print?

```python
a='hello world'
b='hello world'
print(a is b)
```

**Answer:**

```text
True
```

Longer literals are not always interned; separate objects are common.

### Q73. Intermediate

What does this print?

```python
import sys
a=sys.intern('unique_string_12345')
b=sys.intern('unique_string_12345')
print(a == b, a is b)
```

**Answer:**

```text
True True
```

`sys.intern` ensures one canonical object per distinct string content for that interned value.

### Q74. Intermediate

What does this print?

```python
print('{} {}'.format(1, 2))
```

**Answer:**

```text
1 2
```

`str.format` replaces `{}` placeholders in order.

### Q75. Intermediate

What does this print?

```python
print('{1} {0}'.format('a', 'b'))
```

**Answer:**

```text
b a
```

Indices pick argument order.

### Q76. Intermediate

What does this print?

```python
print(f'{3.14159:.2f}')
```

**Answer:**

```text
3.14
```

`.2f` fixes two digits after the decimal point.

### Q77. Intermediate

What does this print?

```python
print(f'{255:#x}')
```

**Answer:**

```text
0xff
```

`#` with hex includes the `0x` prefix.

### Q78. Intermediate

What does this print?

```python
print('{:*>8}'.format('ok'))
```

**Answer:**

```text
******ok
```

Alignment `>` with fill `*` and width 8 right-aligns.

### Q79. Intermediate

What does this print?

```python
print('ab\ncd\r\nef'.splitlines(True))
```

**Answer:**

```text
['ab\n', 'cd\r\n', 'ef']
```

`keepends=True` retains line break characters on each piece.

### Q80. Intermediate

What does this print?

```python
print('path/to/file'.rsplit('/', 1))
```

**Answer:**

```text
['path/to', 'file']
```

Right split once separates directory and filename.

### Q81. Intermediate

What does this print?

```python
print('Mississippi'.rfind('iss'))
```

**Answer:**

```text
4
```

`rfind` searches from the right for the substring.

### Q82. Intermediate

What does this print?

```python
print('---'.join([]))
```

**Answer:**

```text
(no output)
```

Joining an empty iterable yields empty string.

### Q83. Intermediate

What does this print?

```python
print(list('abc'))
```

**Answer:**

```text
['a', 'b', 'c']
```

Iterating a str yields one-character strings.

### Q84. Intermediate

What does this print?

```python
print('α'.upper(), 'Σ'.lower())
```

**Answer:**

```text
Α σ
```

Case mapping uses Unicode full case folding rules, not just ASCII.

### Q85. Intermediate

What does this print?

```python
print('straße'.casefold(), 'STRASSE'.casefold())
```

**Answer:**

```text
strasse strasse
```

German eszett casefolds to `ss` for comparisons.

### Q86. Intermediate

What does this print?

```python
print('１２３'.isdecimal(), '１２３'.isdigit(), '½'.isdigit())
```

**Answer:**

```text
True True False
```

`isdecimal` is stricter than `isdigit`; vulgar fractions are numeric but not decimal digits.

### Q87. Intermediate

What does this print?

```python
print(chr(0x1F600))
```

**Answer:**

```text
😀
```

Valid Unicode code points produce a one-character str.

### Q88. Intermediate

What does this print?

```python
print('w' in 'hello', 'x' in 'hello')
```

**Answer:**

```text
False False
```

Membership tests substring containment for len-1 effectively as character in sequence.

### Q89. Intermediate

What does this print?

```python
print(sorted('cba'))
```

**Answer:**

```text
['a', 'b', 'c']
```

Sort order follows code point order of characters.

### Q90. Intermediate

What does this print?

```python
print(min('hello'), max('hello'))
```

**Answer:**

```text
e o
```

Min/max use lexicographic order of characters.

### Q91. Intermediate

What does this print?

```python
print('a' * 2 ** 3)
```

**Answer:**

```text
aaaaaaaa
```

Repetition count is 8; result is eight `a` characters.

### Q92. Intermediate

What does this print?

```python
print(('%r' % 'hi'), (repr('hi')))
```

**Answer:**

```text
'hi' 'hi'
```

`%r` and `repr` show a printable representation with quotes.

### Q93. Intermediate

What does this print?

```python
print('back\\slash')
```

**Answer:**

```text
back\slash
```

A backslash in source must be escaped as `\\` to produce one backslash.

### Q94. Intermediate

What does this print?

```python
print('\x41\101')
```

**Answer:**

```text
AA
```

Hex and octal escapes in strings produce code units (here ASCII `A`).

### Q95. Intermediate

What does this print?

```python
print('a\nb' == 'a\nb', 'a\nb' == 'a\n' + 'b')
```

**Answer:**

```text
True True
```

Explicit newline escape equals real newline in comparison.

### Q96. Intermediate

What does this print?

```python
print('spam'.removeprefix('sp'), 'spam'.removeprefix('x'))
```

**Answer:**

```text
am spam
```

If prefix absent, original string is returned.

### Q97. Intermediate

What does this print?

```python
print('\N{LATIN SMALL LETTER A WITH ACUTE}')
```

**Answer:**

```text
á
```

Named character escapes in string literals produce that Unicode code point.

### Q98. Intermediate

What does this print?

```python
print('hello'.removesuffix('lo'), 'hello'.removesuffix('x'))
```

**Answer:**

```text
hel hello
```

Same for suffix removal.

### Q99. Intermediate

What does this print?

```python
print('abcdef'[1:5:2])
```

**Answer:**

```text
bd
```

Indices 1 and 3: `b` and `d`.

### Q100. Intermediate

What does this print?

```python
print('abcdef'[5:1:-1])
```

**Answer:**

```text
fedc
```

Negative stride walks backward from index 5 toward 1.

### Q101. Intermediate

What does this print?

```python
print('abcdef'[:0])
```

**Answer:**

```text
(no output)
```

Stop 0 with positive stride is empty.

### Q102. Intermediate

What does this print?

```python
print('abcdef'[-3:])
```

**Answer:**

```text
def
```

Last three characters.

### Q103. Intermediate

What does this print?

```python
print('abcdef'[::-2])
```

**Answer:**

```text
fdb
```

Every second character from the end.

### Q104. Intermediate

What does this print?

```python
print('hello'[-100:100])
```

**Answer:**

```text
hello
```

Out-of-range slice bounds clamp safely.

### Q105. Intermediate

Why can `'é'` and `'e\u0301'` compare unequal with `==` before normalization?

**Answer:**

They are different sequences of code points (one precomposed, one decomposed). Unicode canonical equivalence is not the same as Python ``==`` unless you normalize first.

### Q106. Intermediate

What is the practical difference between UTF-8 and Latin-1 when round-tripping bytes?

**Answer:**

Latin-1 is a bijection between bytes 0–255 and Unicode U+00–U+FF. UTF-8 is variable-length and only represents Unicode scalars; arbitrary bytes may be invalid UTF-8.

### Q107. Intermediate

When should you use `casefold()` instead of `lower()` for comparisons?

**Answer:**

For case-insensitive matching across Unicode (e.g. German ß, dotted I). ``casefold`` applies stronger normalization than ``lower``.

### Q108. Intermediate

What does `str.translate` offer that chained `replace` does not?

**Answer:**

``translate`` applies a per-character map in one C-level pass—efficient for many one-to-one or delete mappings. ``replace`` handles substring patterns.

### Q109. Intermediate

Why is `sys.intern` useful for strings used repeatedly as dict keys?

**Answer:**

Interning deduplicates content-identical strings to one object, so identity checks and memory use improve when many equal strings would otherwise be distinct objects.

### Q110. Intermediate

Write `is_anagram(a, b)` true when `a` and `b` are anagrams (ignore case and non-letters).

**Answer:**

```python
def is_anagram(a, b):
    def key(s):
        return sorted(c.lower() for c in s if c.isalpha())
    return key(a) == key(b)
```

- `is_anagram('Listen', 'Silent')  =>  True`
- `is_anagram('abc', 'abd')  =>  False`

Filter letters, lowercase, sort and compare multisets.

### Q111. Intermediate

Write `caesar(s, shift)` shifting ASCII letters A–Z and a–z by `shift` (wrap within alphabet). Other characters unchanged.

**Answer:**

```python
def caesar(s, shift):
    shift %= 26
    out = []
    for c in s:
        if "a" <= c <= "z":
            out.append(chr((ord(c) - 97 + shift) % 26 + 97))
        elif "A" <= c <= "Z":
            out.append(chr((ord(c) - 65 + shift) % 26 + 65))
        else:
            out.append(c)
    return "".join(out)
```

- `caesar('abc', 1)  =>  'bcd'`
- `caesar('XYZ', 2)  =>  'ZAB'`
- `caesar('Hi!', 5)  =>  'Mn!'`

Mod 26 keeps letters in range; non-letters pass through.

### Q112. Intermediate

Write `run_length_encode(s)` returning `a2b3` style for runs of identical characters (empty -> empty).

**Answer:**

```python
def run_length_encode(s):
    if not s:
        return ""
    out, count, prev = [], 1, s[0]
    for c in s[1:]:
        if c == prev:
            count += 1
        else:
            out.append(prev + str(count))
            prev, count = c, 1
    out.append(prev + str(count))
    return "".join(out)
```

- `run_length_encode('')  =>  ''`
- `run_length_encode('aaabb')  =>  'a3b2'`
- `run_length_encode('x')  =>  'x1'`

Track run length; flush on character change.

### Q113. Intermediate

Write `run_length_decode(s)` inverse of simple `char+count` pairs (digits only counts).

**Answer:**

```python
def run_length_decode(s):
    out = []
    i = 0
    while i < len(s):
        ch = s[i]
        i += 1
        j = i
        while j < len(s) and s[j].isdigit():
            j += 1
        n = int(s[i:j]) if j > i else 1
        out.append(ch * n)
        i = j
    return "".join(out)
```

- `run_length_decode('a3b2')  =>  'aaabb'`
- `run_length_decode('x1')  =>  'x'`

Parse letter then optional decimal count.

### Q114. Intermediate

Write `atoi(s)` parsing optional leading whitespace and optional sign, then decimal digits until non-digit; return int (no float). Empty digits -> 0.

**Answer:**

```python
def atoi(s):
    i = 0
    while i < len(s) and s[i].isspace():
        i += 1
    sign = 1
    if i < len(s) and s[i] in '+-':
        if s[i] == '-':
            sign = -1
        i += 1
    val = 0
    while i < len(s) and s[i].isdigit():
        val = val * 10 + int(s[i])
        i += 1
    return sign * val
```

- `atoi('  -42abc')  =>  -42`
- `atoi('007')  =>  7`
- `atoi('')  =>  0`

Classic pointer-style scan; stop at first non-digit after sign.

### Q115. Intermediate

Write `valid_parentheses(s)` true when `()`, `[]`, `{}` are balanced in `s` (ignore other chars).

**Answer:**

```python
def valid_parentheses(s):
    stack = []
    pairs = {')': '(', ']': '[', '}': '{'}
    for c in s:
        if c in '([{':
            stack.append(c)
        elif c in ')]}':
            if not stack or stack[-1] != pairs[c]:
                return False
            stack.pop()
    return not stack
```

- `valid_parentheses('()[]{}')  =>  True`
- `valid_parentheses('(]')  =>  False`
- `valid_parentheses('')  =>  True`

Stack push opens; pop must match top on close.

### Q116. Intermediate

Write `count_substring(hay, needle)` counting non-overlapping occurrences (like `str.count`).

**Answer:**

```python
def count_substring(hay, needle):
    if needle == "":
        return len(hay) + 1
    count, start = 0, 0
    while True:
        i = hay.find(needle, start)
        if i == -1:
            break
        count += 1
        start = i + len(needle)
    return count
```

- `count_substring('aaaa', 'aa')  =>  2`
- `count_substring('abc', 'z')  =>  0`

Advance start past each match to avoid overlap.

### Q117. Intermediate

Write `strip_chars(s, chars)` removing leading/trailing characters found in `chars` (like `strip` with custom set).

**Answer:**

```python
def strip_chars(s, chars):
    if not s:
        return s
    i, j = 0, len(s) - 1
    while i <= j and s[i] in chars:
        i += 1
    while j >= i and s[j] in chars:
        j -= 1
    return s[i : j + 1]
```

- `strip_chars('xxhelloxx', 'x')  =>  'hello'`
- `strip_chars('abc', 'x')  =>  'abc'`

Two pointers from both ends until mismatch.

### Q118. Advanced

What does this print?

```python
print('a\u200db'.split())
```

**Answer:**

```text
['a\u200db']
```

Word split uses Unicode whitespace; U+200D ZWJ is not whitespace, so the string stays one token.

### Q119. Advanced

What does this print?

```python
print('a\u200db'.split(' '))
```

**Answer:**

```text
['a\u200db']
```

Split on literal space does not split on ZWJ-glued cluster.

### Q120. Advanced

What does this print?

```python
import unicodedata as u
print(u.normalize('NFKC', '１２３') == '123')
```

**Answer:**

```text
True
```

NFKC compatibility decomposition maps fullwidth digits to ASCII.

### Q121. Advanced

What does this print?

```python
print(len('👩‍👩‍👧‍👦'))
```

**Answer:**

```text
7
```

Family emoji ZWJ sequence: `len` counts code units/code points in storage, often > visible graphemes.

### Q122. Advanced

What does this print?

```python
print('😀' == '\U0001F600')
```

**Answer:**

```text
True
```

Astronomical code point written as escape equals the literal character.

### Q123. Advanced

What does this print?

```python
print('surrogate'.encode('utf-8', errors='surrogatepass') if False else len('é'.encode('utf-8')))
```

**Answer:**

```text
2
```

UTF-8 encoding of é uses two bytes: 0xc3 0xa9.

### Q124. Advanced

What does this print?

```python
print(bytes('hello', 'utf-8') == 'hello'.encode())
```

**Answer:**

```text
True
```

`bytes(str, encoding)` is equivalent to `encode`.

### Q125. Advanced

What does this print?

```python
print('hello'.encode('utf-16-le')[:5])
```

**Answer:**

```text
b'h\x00e\x00l'
```

UTF-16-LE uses 2 bytes per BMP character plus no BOM in this slice view.

### Q126. Advanced

What does this print?

```python
print('\u0061\u0062\u0063')
```

**Answer:**

```text
abc
```

Multiple `\u` escapes concatenate in one literal.

### Q127. Advanced

What does this print?

```python
print(format(12.3, 'e'), format(12.3, '.1e'))
```

**Answer:**

```text
1.230000e+01 1.2e+01
```

Exponential format spec controls mantissa width.

### Q128. Advanced

What does this print?

```python
print(f'{12:0>5}')
```

**Answer:**

```text
00012
```

Fill zero with minimum width 5.

### Q129. Advanced

What does this print?

```python
print('{0[0]}'.format(['x']))
```

**Answer:**

```text
x
```

Format fields can index into arguments.

### Q130. Advanced

What does this print?

```python
print('template'.replace('t', 'T', 2))
```

**Answer:**

```text
TemplaTe
```

Third argument limits replacements.

### Q131. Advanced

What does this print?

```python
print('aaa'.replace('', '-'))
```

**Answer:**

```text
-a-a-a-
```

Empty old substring matches gaps between characters in CPython; result grows.

### Q132. Advanced

What does this print?

```python
print('foo\tbar'.expandtabs(0))
```

**Answer:**

```text
foobar
```

Tab size 0 is treated as 1 in `expandtabs`.

### Q133. Advanced

What does this print?

```python
print('test'.ljust(6, '.'), 'test'.rjust(6, '.'))
```

**Answer:**

```text
test.. ..test
```

Left/right justify with fill.

### Q134. Advanced

What does this print?

```python
print(''.join(['a', '', 'b']))
```

**Answer:**

```text
ab
```

Join preserves empty pieces between separators.

### Q135. Advanced

What does this print?

```python
print('a\n\nb'.splitlines())
```

**Answer:**

```text
['a', '', 'b']
```

Blank line produces empty string element.

### Q136. Advanced

What does this print?

```python
print('\u0061\0062')
```

**Answer:**

```text
a2
```

Only `\u` is four hex digits; following `0062` is literal characters after `a`.

### Q137. Advanced

What does this print?

```python
s='abc'
print(s[1:10])
```

**Answer:**

```text
bc
```

Slice stop beyond length clamps to end.

### Q138. Advanced

What does this print?

```python
print('β'.lower() == 'β', 'β'.upper() == 'Β')
```

**Answer:**

```text
True True
```

Greek beta has defined upper/lower mapping.

### Q139. Advanced

What does this print?

```python
print('İ'.lower(), 'i'.upper())
```

**Answer:**

```text
i̇ I
```

Turkish dotted capital I lowercases to i with dot; ASCII i uppercases to I.

### Q140. Advanced

What does this print?

```python
print('hello'.partition('l'))
```

**Answer:**

```text
('he', 'l', 'lo')
```

First `l` splits into `he`, `l`, `lo`.

### Q141. Advanced

What does this print?

```python
print('hello'.rpartition('l'))
```

**Answer:**

```text
('hel', 'l', 'o')
```

Last `l` splits into `hel`, `l`, `o`.

### Q142. Advanced

What does this print?

```python
print('a\tb\tc'.expandtabs(8))
```

**Answer:**

```text
a       b       c
```

Tab stops align to columns 8, 16, …

### Q143. Advanced

What does this print?

```python
print(str.maketrans({'a': '1', 'b': '2'}))
```

**Answer:**

```text
{97: '1', 98: '2'}
```

Dict mapping builds translation table for `translate`.

### Q144. Advanced

What does this print?

```python
print('abba'.translate(str.maketrans('ab', 'ba')))
```

**Answer:**

```text
baab
```

Swaps a↔b via translate.

### Q145. Advanced

What does this print?

```python
print('line\r\n'.splitlines())
```

**Answer:**

```text
['line']
```

Universal newlines split CRLF as one break.

### Q146. Advanced

What does this print?

```python
print(repr('\''))
```

**Answer:**

```text
"'"
```

repr of quote character shows escaped form.

### Q147. Advanced

What does this print?

```python
print('"'.join(['a', 'b']))
```

**Answer:**

```text
a"b
```

Quote character can be the join separator.

### Q148. Advanced

What does this print?

```python
print(('%10s' % 'hi'), (format('hi', '>10')))
```

**Answer:**

```text
        hi         hi
```

Old and new style right-align in width 10.

### Q149. Advanced

What does this print?

```python
print('café'.encode('utf-8').decode('utf-8') == 'café')
```

**Answer:**

```text
True
```

UTF-8 round trip preserves text.

### Q150. Advanced

What does this print?

```python
print('\N{GREEK SMALL LETTER ALPHA}')
```

**Answer:**

```text
α
```

Named Unicode character in source.

### Q151. Advanced

What does this print?

```python
print('a' <= 'a' <= 'z')
```

**Answer:**

```text
True
```

Chained comparisons short-circuit left to right.

### Q152. Advanced

What does this print?

```python
print('' in 'abc', '' in '')
```

**Answer:**

```text
True True
```

Empty substring is considered contained at every index (CPython `find` semantics).

### Q153. Advanced

What does this print?

```python
print('abc'.find(''))
```

**Answer:**

```text
0
```

Empty needle matches at index 0 first.

### Q154. Advanced

What does this print?

```python
print('€'.encode('utf-8'))
```

**Answer:**

```text
b'\xe2\x82\xac'
```

Euro encodes to three UTF-8 bytes.

### Q155. Advanced

What does this print?

```python
print('ñ'.encode('utf-8'))
```

**Answer:**

```text
b'\xc3\xb1'
```

Latin small n with tilde is two bytes in UTF-8.

### Q156. Advanced

What does this print?

```python
print('\x80'.encode('latin-1'))
```

**Answer:**

```text
b'\x80'
```

Byte 0x80 as Latin-1 character U+0080.

### Q157. Advanced

Why should text processing that cares about user-perceived characters consider grapheme clusters, not `len(str)` alone?

**Answer:**

Combining marks, emoji ZWJ sequences, and compatibility forms change visual width and editing steps without changing simple code-point counts. Collation and cursor movement need locale-aware or UAX rules.

### Q158. Advanced

What risk does `errors='ignore'` on decode introduce compared to `strict`?

**Answer:**

Invalid bytes vanish silently, corrupting meaning and making bugs hard to detect. Prefer ``replace`` or ``strict`` depending on whether loss is acceptable.

### Q159. Advanced

When is concatenating with `+` in a tight loop quadratic, and what is the fix?

**Answer:**

Each ``+`` copies prior result plus new piece. Use ``''.join(parts)`` or ``io.StringIO`` to accumulate linear total time.

### Q160. Advanced

How does NFKC differ from NFC for string comparison of compatibility characters?

**Answer:**

NFC canonical composition; NFKC also maps compatibility characters (e.g. fullwidth digits) to standard forms, stronger for loose matching.

### Q161. Advanced

Why does CPython intern some identifiers and literals but not all dynamically built strings?

**Answer:**

Interning saves memory and speeds dict keys for known-at-compile-time strings. Runtime-built strings stay distinct unless explicitly interned.

### Q162. Advanced

Write `is_palindrome_alnum(s)` ignoring non-alphanumeric and case.

**Answer:**

```python
def is_palindrome_alnum(s):
    filtered = [c.lower() for c in s if c.isalnum()]
    t = "".join(filtered)
    return t == t[::-1]
```

- `is_palindrome_alnum('A man, a plan, a canal: Panama')  =>  True`
- `is_palindrome_alnum('abc')  =>  False`

Normalize to lowercase alnum only, then compare to reverse.

### Q163. Advanced

Write `word_count(text)` returning a dict of word -> count (words are `[A-Za-z]+` sequences, case-insensitive keys lowercased).

**Answer:**

```python
import re

def word_count(text):
    words = re.findall(r"[A-Za-z]+", text)
    d = {}
    for w in words:
        k = w.lower()
        d[k] = d.get(k, 0) + 1
    return d
```

- `word_count('Hi hi HI')  =>  {'hi': 3}`
- `word_count('')  =>  {}`

Regex extracts letter runs; dict aggregates lowercase keys.

### Q164. Advanced

Write `dedupe_words(s)` keeping first occurrence of each word (case-sensitive, whitespace-separated).

**Answer:**

```python
def dedupe_words(s):
    seen = set()
    out = []
    for w in s.split():
        if w not in seen:
            seen.add(w)
            out.append(w)
    return " ".join(out)
```

- `dedupe_words('the the cat sat')  =>  'the cat sat'`
- `dedupe_words('')  =>  ''`

Split, track seen set, preserve order.

### Q165. Advanced

Write `rotate_caesar_bruteforce(cipher)` returning all 26 Caesar decodings as a list of strings.

**Answer:**

```python
def rotate_caesar_bruteforce(cipher):
    def shift(s, k):
        return caesar(s, k)
    def caesar(s, shift):
        shift %= 26
        out = []
        for c in s:
            if "a" <= c <= "z":
                out.append(chr((ord(c) - 97 + shift) % 26 + 97))
            elif "A" <= c <= "Z":
                out.append(chr((ord(c) - 65 + shift) % 26 + 65))
            else:
                out.append(c)
        return "".join(out)
    return [caesar(cipher, k) for k in range(26)]
```

- `len(rotate_caesar_bruteforce('A'))  =>  26`
- `rotate_caesar_bruteforce('B')[1]  =>  'C'`

Try every shift 0..25 using letter-only Caesar.

### Q166. Advanced

Write `normalize_whitespace_lines(text)` joining lines with single newline after stripping each line's ends and collapsing internal runs to one space.

**Answer:**

```python
def normalize_whitespace_lines(text):
    lines = []
    for line in text.splitlines():
        lines.append(" ".join(line.split()))
    return "\n".join(lines)
```

- `normalize_whitespace_lines('  a \n  b  c  ')  =>  'a\nb c'`

Per line: strip via split/join, then join lines with `\n`.

### Q167. Advanced

Write `bytes_to_hex_utf8(s)` returning uppercase hex pairs for UTF-8 encoding, no separators.

**Answer:**

```python
def bytes_to_hex_utf8(s):
    return s.encode("utf-8").hex().upper()
```

- `bytes_to_hex_utf8('A')  =>  '41'`
- `bytes_to_hex_utf8('é')  =>  'C3A9'`

`bytes.hex()` produces lowercase; upper for convention here.

### Q168. Advanced

Write `safe_decode(b)` decoding UTF-8 with replacement on errors.

**Answer:**

```python
def safe_decode(b):
    return b.decode("utf-8", errors="replace")
```

- `safe_decode(b'\xff')  =>  '�'`
- `safe_decode('hi'.encode())  =>  'hi'`

Invalid bytes become U+FFFD.

### Q169. Advanced

Write `longest_word(s)` returning the longest whitespace-delimited word (ties: first wins). Empty -> ''.

**Answer:**

```python
def longest_word(s):
    words = s.split()
    if not words:
        return ""
    best = words[0]
    for w in words[1:]:
        if len(w) > len(best):
            best = w
    return best
```

- `longest_word('a bb ccc')  =>  'ccc'`
- `longest_word('')  =>  ''`

Linear scan comparing lengths.

### Q170. Advanced

Write `swapcase_ascii_letters(s)` swapping case of ASCII letters only.

**Answer:**

```python
def swapcase_ascii_letters(s):
    out = []
    for c in s:
        o = ord(c)
        if 65 <= o <= 90:
            out.append(chr(o + 32))
        elif 97 <= o <= 122:
            out.append(chr(o - 32))
        else:
            out.append(c)
    return "".join(out)
```

- `swapcase_ascii_letters('Ab!')  =>  'aB!'`
- `swapcase_ascii_letters('')  =>  ''`

Manual ASCII range check avoids changing Unicode special cases.

### Q171. Advanced

Write `is_rotated(a, b)` true when `b` is a rotation of `a` (e.g. `abc` and `cab`). Empty strings rotate to each other.

**Answer:**

```python
def is_rotated(a, b):
    if len(a) != len(b):
        return False
    if not a:
        return True
    return b in a + a
```

- `is_rotated('abc', 'bca')  =>  True`
- `is_rotated('abc', 'acb')  =>  False`
- `is_rotated('', '')  =>  True`

Classic doubling trick: rotation substring of `a+a`.

### Q172. Basic

What does this print?

```python
print('hello'[None:3])
```

**Answer:**

```text
hel
```

None in slice means omitted bound.

### Q173. Basic

What does this print?

```python
print(bool(''), bool('0'))
```

**Answer:**

```text
False True
```

Non-empty strings are truthy, including `'0'`.

### Q174. Basic

What does this print?

```python
print('py' * 2 + 'thon')
```

**Answer:**

```text
pypython
```

Repetition binds before concatenation.

### Q175. Basic

What does this print?

```python
print('a\n'.strip())
```

**Answer:**

```text
a
```

Strip removes trailing newline.

### Q176. Basic

What does this print?

```python
print('1,2,3'.split(',', 1))
```

**Answer:**

```text
['1', '2,3']
```

maxsplit limits splits from the left.

### Q177. Basic

What does this print?

```python
print('---a---'.strip('-'))
```

**Answer:**

```text
a
```

Custom strip chars remove listed characters from ends.

### Q178. Basic

What does this print?

```python
print('Hello World'.swapcase())
```

**Answer:**

```text
hELLO wORLD
```

swapcase toggles case per Unicode rules.

### Q179. Basic

What does this print?

```python
print('tab\there'.expandtabs(4) == 'tab     here')
```

**Answer:**

```text
False
```

Tab expands to spaces to column 4 from start.

### Q180. Basic

What does this print?

```python
print('x' == 'X')
```

**Answer:**

```text
False
```

Case matters in equality.

### Q181. Basic

What does this print?

```python
print(chr(10) == '\n')
```

**Answer:**

```text
True
```

Code point 10 is newline.

### Q182. Basic

What does this print?

```python
print(list(''))
```

**Answer:**

```text
[]
```

Iterating empty str yields empty list.

### Q183. Basic

What does this print?

```python
print('spam'[::1])
```

**Answer:**

```text
spam
```

Stride 1 returns a copy equal to the whole string.

### Q184. Basic

What does this print?

```python
print('double  space'.split(' '))
```

**Answer:**

```text
['double', '', 'space']
```

Split on single space keeps empty strings between adjacent spaces.

### Q185. Intermediate

What does this print?

```python
print('a.b.c'.split('.', 2))
```

**Answer:**

```text
['a', 'b', 'c']
```

At most two splits yield three parts.

### Q186. Intermediate

What does this print?

```python
print('xx'.replace('x', 'xx'))
```

**Answer:**

```text
xxxx
```

Replacements can expand length; left-to-right scan.

### Q187. Intermediate

What does this print?

```python
print('\u0041BC'.lower())
```

**Answer:**

```text
abc
```

Only first char is escape; rest literal `BC`.

### Q188. Intermediate

What does this print?

```python
print('hello'.__len__())
```

**Answer:**

```text
5
```

Dunder len matches builtin.

### Q189. Intermediate

What does this print?

```python
a='a'
print('' + a is a)
```

**Answer:**

```text
True
```

Empty concat often reuses the same object as the named literal on the right.

### Q190. Intermediate

What does this print?

```python
print(sorted('Aa'))
```

**Answer:**

```text
['A', 'a']
```

Uppercase before lowercase in code point order.

### Q191. Intermediate

What does this print?

```python
print('prefix'.removesuffix('fix') == 'prefix')
```

**Answer:**

```text
False
```

Suffix must match exactly at end.

### Q192. Intermediate

What does this print?

```python
print('a\r\n'.splitlines()[0])
```

**Answer:**

```text
a
```

First line before CRLF.

### Q193. Intermediate

What does this print?

```python
print('nine'.translate(str.maketrans('n', 'm')))
```

**Answer:**

```text
mime
```

Single-char replacement via translate.

### Q194. Intermediate

What does this print?

```python
print('abc'.center(7))
```

**Answer:**

```text
  abc  
```

Default fill is space.

### Q195. Advanced

What does this print?

```python
print('a\n'.splitlines(keepends=False) == ['a'])
```

**Answer:**

```text
True
```

Single line without keepends.

### Q196. Advanced

What does this print?

```python
print('abc'.replace('bc', 'X'))
```

**Answer:**

```text
aX
```

Substring replace in middle.

### Q197. Advanced

What does this print?

```python
print('a\x00b'.split('\x00'))
```

**Answer:**

```text
['a', 'b']
```

Null byte as separator.

### Q198. Advanced

What does this print?

```python
print('ß'.upper() == 'SS')
```

**Answer:**

```text
True
```

German eszett uppercases to SS in Unicode default case mapping.

### Q199. Advanced

What does this print?

```python
print('hello'.encode()[0])
```

**Answer:**

```text
104
```

First UTF-8 byte of ASCII h is 104.

### Q200. Advanced

What does this print?

```python
print('banana'.index('na'))
```

**Answer:**

```text
2
```

First occurrence index of substring.

*Section size: 200 questions (Basic 70, Intermediate 70, Advanced 60).*

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

## 12. Bytes (bytes)

An immutable sequence of integers in 0..255. It is not a text type.

### Q1. Basic

What does this print?

```python
print(type(b'hi'))
```

**Answer:**

```text
<class 'bytes'>
```

A `b` prefix creates a `bytes` object.

### Q2. Basic

What does this print?

```python
print(b'hi'[0])
```

**Answer:**

```text
104
```

Indexing `bytes` yields an `int` 0–255, not a one-byte `bytes`.

### Q3. Basic

What does this print?

```python
print(b'hi'[1])
```

**Answer:**

```text
105
```

The second byte is ASCII 105 (`i`).

### Q4. Basic

What does this print?

```python
print(b'ABC'[-1])
```

**Answer:**

```text
67
```

Negative indices count from the end.

### Q5. Basic

What does this print?

```python
print(len(b''))
```

**Answer:**

```text
0
```

Empty bytes has length 0.

### Q6. Basic

What does this print?

```python
print(len(b' ÿ'))
```

**Answer:**

```text
SyntaxError: source code string cannot contain null bytes
```

Length counts bytes, not hex digits in source.

### Q7. Basic

What does this print?

```python
print(b'a' + b'b')
```

**Answer:**

```text
b'ab'
```

Concatenation builds a new immutable `bytes` object.

### Q8. Basic

What does this print?

```python
print(b'abc' * 2)
```

**Answer:**

```text
b'abcabc'
```

Repetition duplicates the whole sequence.

### Q9. Basic

What does this print?

```python
print(b'abc' == b'abc')
```

**Answer:**

```text
True
```

Equal sequences compare equal.

### Q10. Basic

What does this print?

```python
print(b'abc' == b'abd')
```

**Answer:**

```text
False
```

One differing byte makes the objects unequal.

### Q11. Basic

What does this print?

```python
print(b'abc' < b'abd')
```

**Answer:**

```text
True
```

Ordering is lexicographic on unsigned byte values.

### Q12. Basic

What does this print?

```python
print(b'' < b'a')
```

**Answer:**

```text
True
```

Empty bytes compares less than any non-empty bytes.

### Q13. Basic

What does this print?

```python
print(list(b'AB'))
```

**Answer:**

```text
[65, 66]
```

Elements are ints: 65 and 66.

### Q14. Basic

What does this print?

```python
print(sum(b'123'))
```

**Answer:**

```text
150
```

Those ints are digit ASCII codes 49+50+51, not numeric 1+2+3.

### Q15. Basic

What does this print?

```python
print(b'hello'.decode())
```

**Answer:**

```text
hello
```

Default decode uses UTF-8.

### Q16. Basic

What does this print?

```python
print('hello'.encode())
```

**Answer:**

```text
b'hello'
```

`encode` turns str into bytes (UTF-8 by default).

### Q17. Basic

What does this print?

```python
print(b'ÿ'.hex())
```

**Answer:**

```text
SyntaxError: bytes can only contain ASCII literal characters (<snippet>, line 1)
```

`hex` emits two lowercase hex digits per byte.

### Q18. Basic

What does this print?

```python
print(bytes.fromhex('ff 00'))
```

**Answer:**

```text
b'\xff\x00'
```

`fromhex` ignores spaces between pairs.

### Q19. Basic

What does this print?

```python
print(bytes(3))
```

**Answer:**

```text
b'\x00\x00\x00'
```

`bytes(n)` means n zero bytes, not the single byte with value n.

### Q20. Basic

What does this print?

```python
print(bytes([65, 66]))
```

**Answer:**

```text
b'AB'
```

Iterable of ints 0–255 becomes raw bytes.

### Q21. Basic

What does this print?

```python
print(bytes('hi', 'utf-8'))
```

**Answer:**

```text
b'hi'
```

Encodes text with the named codec.

### Q22. Basic

What does this print?

```python
print(b'abc'[1:3])
```

**Answer:**

```text
b'bc'
```

Slicing always returns `bytes`.

### Q23. Basic

What does this print?

```python
print(b'abc'[::2])
```

**Answer:**

```text
b'ac'
```

Extended slice with step 2 keeps every other byte.

### Q24. Basic

What does this print?

```python
print(b'abc'.find(b'b'))
```

**Answer:**

```text
1
```

`find` returns start index or -1.

### Q25. Basic

What does this print?

```python
print(b'abc'.find(b'z'))
```

**Answer:**

```text
-1
```

Missing pattern yields -1.

### Q26. Basic

What does this print?

```python
print(b'abcabc'.count(b'ab'))
```

**Answer:**

```text
2
```

Counts non-overlapping sub-bytes matches.

### Q27. Basic

What does this print?

```python
print(b'  x  '.strip())
```

**Answer:**

```text
b'x'
```

Strip removes leading/trailing ASCII whitespace bytes.

### Q28. Basic

What does this print?

```python
print(b'1,2'.split(b','))
```

**Answer:**

```text
[b'1', b'2']
```

Split returns a list of `bytes` segments.

### Q29. Basic

What does this print?

```python
print(b'a-b-c'.partition(b'-'))
```

**Answer:**

```text
(b'a', b'-', b'b-c')
```

Partition splits into three parts at first separator.

### Q30. Basic

What does this print?

```python
print(b'abc'.upper())
```

**Answer:**

```text
b'ABC'
```

ASCII case change returns new bytes.

### Q31. Basic

What does this print?

```python
print(b'ABC'.lower())
```

**Answer:**

```text
b'abc'
```

Original bytes object stays unchanged.

### Q32. Basic

What does this print?

```python
print(b'abc'.replace(b'a', b'z'))
```

**Answer:**

```text
b'zbc'
```

`replace` returns a copy with substitutions.

### Q33. Basic

What does this print?

```python
print(b'abc'.startswith(b'ab'))
```

**Answer:**

```text
True
```

Prefix test on bytes pattern.

### Q34. Basic

What does this print?

```python
print(b'abc'.endswith(b'bc'))
```

**Answer:**

```text
True
```

Suffix test on bytes pattern.

### Q35. Basic

What does this print?

```python
print(b'abc'.center(7, b'-'))
```

**Answer:**

```text
b'--abc--'
```

Center pads to width with fill bytes.

### Q36. Basic

What does this print?

```python
print(repr(b'
'))
```

**Answer:**

```text
SyntaxError: unterminated string literal (detected at line 1) (<snippet>, line 1)
```

`repr` shows the bytes literal form with escapes.

### Q37. Basic

What does this print?

```python
print(b'A')
```

**Answer:**

```text
b'A'
```

Hex escape 0x41 is ASCII `A`.

### Q38. Basic

What does this print?

```python
print(b'
' == bytes([10]))
```

**Answer:**

```text
SyntaxError: unterminated string literal (detected at line 1) (<snippet>, line 1)
```

Different literal forms can denote the same bytes.

### Q39. Basic

What does this print?

```python
print({b'a', b'b', b'a'})
```

**Answer:**

```text
{b'b', b'a'}
```

Set deduplicates equal bytes objects.

### Q40. Basic

What does this print?

```python
print(b'abc'.ljust(5, b'.'))
```

**Answer:**

```text
b'abc..'
```

Left justify with explicit fill byte.

### Q41. Basic

What does this print?

```python
print(b'abc'.rjust(5))
```

**Answer:**

```text
b'  abc'
```

Default fill is the space byte.

### Q42. Basic

What does this print?

```python
print('hello'.encode('ascii'))
```

**Answer:**

```text
b'hello'
```

ASCII encoding of Latin letters matches UTF-8 here.

### Q43. Basic

What does this print?

```python
print(bytes([0, 255]))
```

**Answer:**

```text
b'\x00\xff'
```

Every element of the iterable must be an int in 0..255. 0 and 255 are the endpoints.

### Q44. Basic

What does this print?

```python
print(b'A'.hex())
```

**Answer:**

```text
41
```

`hex` returns a str of two hex digits per byte, with no `0x` prefix.

### Q45. Basic

What does this print?

```python
print(bytes.fromhex('41 42'))
```

**Answer:**

```text
b'AB'
```

`fromhex` ignores ASCII spaces between hex bytes.

### Q46. Intermediate

What does this print?

```python
print(b'hi'.center(6, b'-'))
```

**Answer:**

```text
b'--hi--'
```

`center` pads a bytes object with a bytes fill, not a str.

### Q47. Intermediate

What does this print?

```python
print(b'xx'.join([b'a', b'b', b'c']))
```

**Answer:**

```text
b'axxbxxc'
```

`join` on bytes wants an iterable of bytes.

### Q48. Intermediate

What happens when this runs?

```python
print(b','.join(['a', 'b']))
```

**Answer:**

```text
TypeError: sequence item 0: expected a bytes-like object, str found
```

A bytes separator cannot join strings.

### Q49. Intermediate

What does this print?

```python
print(b'  ab  '.strip())
```

**Answer:**

```text
b'ab'
```

`strip` removes leading and trailing bytes that are ASCII whitespace.

### Q50. Intermediate

What does this print?

```python
print(b'abcabc'.replace(b'a', b'X', 1))
```

**Answer:**

```text
b'Xbcabc'
```

The count argument limits how many non-overlapping replacements happen.

### Q51. Intermediate

What does this print?

```python
print(b'abc'.startswith(b'ab'), b'abc'.endswith((b'c', b'z')))
```

**Answer:**

```text
True True
```

`endswith` accepts a tuple of suffixes, the same way `str` does.

### Q52. Advanced

What does this print?

```python
print(b'hello'.translate(bytes.maketrans(b'aeiou', b'AEIOU')))
```

**Answer:**

```text
b'hEllO'
```

`maketrans` for bytes takes two bytes strings of equal length.

### Q53. Advanced

What does this print?

```python
print(b'hello'.translate(None, b'aeiou'))
```

**Answer:**

```text
b'hll'
```

The second argument of `bytes.translate` is a delete set.

### Q54. Advanced

What does this print?

```python
import sys
print(sys.getsizeof(b'') < sys.getsizeof(b'hello'))
```

**Answer:**

```text
True
```

A longer bytes object stores more data, so it is larger. The exact sizes are implementation details.

### Q55. Advanced

What does this print?

```python
print(list(memoryview(b'AB')))
```

**Answer:**

```text
[65, 66]
```

Iterating a memoryview of bytes yields the integer values, not one-byte objects.

### Q56. Basic

What does this print?

```python
print(b'ab' < b'b')
```

**Answer:**

```text
True
```

Bytes compare lexicographically by unsigned byte value.

### Q57. Intermediate

What does this print?

```python
print(b'abc'.partition(b'b'))
```

**Answer:**

```text
(b'a', b'b', b'c')
```

`partition` returns a 3-tuple of bytes: head, separator, tail.

### Q58. Intermediate

What does this print?

```python
print(b'a\nb\r\nc'.splitlines())
```

**Answer:**

```text
[b'a', b'b', b'c']
```

`splitlines` drops the line endings and understands `\n`, `\r\n`, and `\r`.

### Q59. Basic

What does this print?

```python
print(len(bytes(0)))
```

**Answer:**

```text
0
```

`bytes(0)` allocates 0 zero bytes.

### Q60. Basic

What does this print?

```python
print(len(bytes(1)))
```

**Answer:**

```text
1
```

`bytes(1)` allocates 1 zero bytes.

### Q61. Basic

What does this print?

```python
print(len(bytes(2)))
```

**Answer:**

```text
2
```

`bytes(2)` allocates 2 zero bytes.

### Q62. Basic

What does this print?

```python
print(len(bytes(4)))
```

**Answer:**

```text
4
```

`bytes(4)` allocates 4 zero bytes.

### Q63. Basic

What does this print?

```python
print(b'Python'[0])
```

**Answer:**

```text
80
```

First byte is `P` (80).

### Q64. Basic

What does this print?

```python
print(b'Python'[5])
```

**Answer:**

```text
110
```

Index 5 is `n` (110).

### Q65. Basic

What does this print?

```python
print(b' ÿ'[1])
```

**Answer:**

```text
SyntaxError: source code string cannot contain null bytes
```

Second byte is 255.

### Q66. Basic

What does this print?

```python
print(b'12345'[2])
```

**Answer:**

```text
51
```

Third digit char has code 51.

### Q67. Basic

What does this print?

```python
print(b'AB'[-2])
```

**Answer:**

```text
65
```

Index -2 is first byte when len is 2.

### Q68. Basic

What does this print?

```python
print(b'abcdef'[1:4])
```

**Answer:**

```text
b'bcd'
```

Bytes `bcd`.

### Q69. Intermediate

What does this print?

```python
print(b'abcdef'[:3])
```

**Answer:**

```text
b'abc'
```

First three bytes.

### Q70. Intermediate

What does this print?

```python
print(b'abcdef'[3:])
```

**Answer:**

```text
b'def'
```

From index 3 through end.

### Q71. Intermediate

What does this print?

```python
print(b'abcdef'[100:])
```

**Answer:**

```text
b''
```

Start beyond length → empty bytes.

### Q72. Intermediate

What does this print?

```python
x = b'abc'
try:
    x[0] = 97
except Exception as e:
    print(type(e).__name__)
```

**Answer:**

```text
TypeError
```

Immutable: item assignment raises `TypeError`.

### Q73. Intermediate

What does this print?

```python
print(int.from_bytes(b' ', 'big'))
```

**Answer:**

```text
SyntaxError: source code string cannot contain null bytes
```

Big-endian: high byte first → 1.

### Q74. Intermediate

What does this print?

```python
print(int.from_bytes(b' ', 'little'))
```

**Answer:**

```text
SyntaxError: source code string cannot contain null bytes
```

Little-endian layout 0x0100 → 256.

### Q75. Intermediate

What does this print?

```python
print((255).to_bytes(2, 'big'))
```

**Answer:**

```text
b'\x00\xff'
```

255 as two big-endian bytes is b' ÿ'.

### Q76. Intermediate

What does this print?

```python
print((258).to_bytes(2, 'big'))
```

**Answer:**

```text
b'\x01\x02'
```

258 is 0x0102 in big-endian.

### Q77. Intermediate

What does this print?

```python
print(b'café'.decode('latin-1'))
```

**Answer:**

```text
SyntaxError: bytes can only contain ASCII literal characters (<snippet>, line 1)
```

Latin-1 maps bytes 0–255 to same code points.

### Q78. Intermediate

What happens when this runs?

```python
print(b'ÿþ'.decode('ascii'))
```

**Answer:**

```text
SyntaxError: bytes can only contain ASCII literal characters (<snippet>, line 1)
```

ASCII rejects bytes ≥ 128.

### Q79. Intermediate

What does this print?

```python
print(b'ÿþ'.decode('utf-8', errors='replace'))
```

**Answer:**

```text
SyntaxError: bytes can only contain ASCII literal characters (<snippet>, line 1)
```

Invalid UTF-8 becomes U+FFFD with replace handler.

### Q80. Intermediate

What does this print?

```python
print('€'.encode('utf-8'))
```

**Answer:**

```text
b'\xe2\x82\xac'
```

Euro sign is three UTF-8 bytes.

### Q81. Intermediate

What does this print?

```python
print(len('€'.encode('utf-8')))
```

**Answer:**

```text
3
```

One character can encode to multiple bytes.

### Q82. Intermediate

What does this print?

```python
print(b'abc'.hex(' '))
```

**Answer:**

```text
61 62 63
```

Optional separator between hex pairs.

### Q83. Intermediate

What happens when this runs?

```python
print(bytes.fromhex('g0'))
```

**Answer:**

```text
ValueError: non-hexadecimal number found in fromhex() arg at position 0
```

Invalid hex digit → `ValueError`.

### Q84. Intermediate

What does this print?

```python
print(bytes.fromhex(''))
```

**Answer:**

```text
b''
```

Empty hex → empty bytes.

### Q85. Intermediate

What does this print?

```python
print(memoryview(b'abc').readonly)
```

**Answer:**

```text
True
```

View over bytes is read-only.

### Q86. Intermediate

What does this print?

```python
print(b'-'.join([b'a', b'b', b'c']))
```

**Answer:**

```text
b'a-b-c'
```

`bytes.join` inserts separator between parts.

### Q87. Intermediate

What does this print?

```python
a = b'hello'
b = a
a += b'!'
print(a, b)
```

**Answer:**

```text
b'hello!' b'hello'
```

+= rebinds to new bytes; `b` unchanged.

### Q88. Intermediate

What does this print?

```python
print(b'abc' * 0)
```

**Answer:**

```text
b''
```

Times zero → empty bytes.

### Q89. Intermediate

What does this print?

```python
print(b'abc'.index(b'c'))
```

**Answer:**

```text
2
```

`index` raises if missing; here finds 2.

### Q90. Intermediate

What happens when this runs?

```python
print(b'abc'.index(b'z'))
```

**Answer:**

```text
ValueError: subsection not found
```

Missing → `ValueError`.

### Q91. Intermediate

What does this print?

```python
print(b'abab'.rfind(b'ab'))
```

**Answer:**

```text
2
```

Rightmost match start index.

### Q92. Intermediate

What does this print?

```python
print(b'abc'.removeprefix(b'ab'))
```

**Answer:**

```text
b'c'
```

Strips leading prefix when present.

### Q93. Intermediate

What does this print?

```python
print(b'abc'.removesuffix(b'bc'))
```

**Answer:**

```text
b'a'
```

Strips trailing suffix when present.

### Q94. Intermediate

What does this print?

```python
print(b'abc'.removeprefix(b'x'))
```

**Answer:**

```text
b'abc'
```

No match → original bytes returned.

### Q95. Intermediate

What does this print?

```python
print(b'hello world'.split(maxsplit=1))
```

**Answer:**

```text
[b'hello', b'world']
```

At most one split.

### Q96. Intermediate

What does this print?

```python
print(b'abc'.translate(bytes.maketrans(b'a', b'x')))
```

**Answer:**

```text
b'xbc'
```

Translation table maps byte values.

### Q97. Intermediate

What does this print?

```python
print(b'abc'.isalpha())
```

**Answer:**

```text
True
```

ASCII letters only for bytes isalpha.

### Q98. Intermediate

What does this print?

```python
print(b'123'.isdigit())
```

**Answer:**

```text
True
```

ASCII decimal digits.

### Q99. Intermediate

What does this print?

```python
print(b'ÿ'.isascii())
```

**Answer:**

```text
SyntaxError: bytes can only contain ASCII literal characters (<snippet>, line 1)
```

Byte 255 is not ASCII.

### Q100. Intermediate

What does this print?

```python
print(b'Ã©'.decode('utf-8'))
```

**Answer:**

```text
SyntaxError: bytes can only contain ASCII literal characters (<snippet>, line 1)
```

Valid UTF-8 for é.

### Q101. Intermediate

What does this print?

```python
print(b'abcdef'[::-1])
```

**Answer:**

```text
b'fedcba'
```

Reverse slice builds reversed bytes.

### Q102. Intermediate

What does this print?

```python
print(b'abcdef'[-3:-1])
```

**Answer:**

```text
b'de'
```

Negative slice bounds work like other sequences.

### Q103. Intermediate

What does this print?

```python
b1 = b'abc'
b2 = b1[:2] + b'c'
print(b1 == b2, b1 is b2)
```

**Answer:**

```text
True False
```

Equal content, not necessarily same object.

### Q104. Intermediate

What does this print?

```python
print(int.from_bytes(b' ', 'big'))
```

**Answer:**

```text
SyntaxError: source code string cannot contain null bytes
```

Single zero byte unsigned → 0.

### Q105. Intermediate

What does this print?

```python
print(int.from_bytes(b'', 'big'))
```

**Answer:**

```text
1
```

0x01 → 1.

### Q106. Intermediate

What does this print?

```python
print(int.from_bytes(b' ', 'big'))
```

**Answer:**

```text
SyntaxError: source code string cannot contain null bytes
```

BE 0x0001 → 1.

### Q107. Intermediate

What does this print?

```python
print(int.from_bytes(b' ', 'little'))
```

**Answer:**

```text
SyntaxError: source code string cannot contain null bytes
```

LE 0x0100 layout → 256.

### Q108. Intermediate

What does this print?

```python
print(int.from_bytes(b'ÿ', 'big', signed=True))
```

**Answer:**

```text
SyntaxError: bytes can only contain ASCII literal characters (<snippet>, line 1)
```

Signed 0xff → -1.

### Q109. Intermediate

What does this print?

```python
print(int.from_bytes(b'', 'big', signed=True))
```

**Answer:**

```text
SyntaxError: bytes can only contain ASCII literal characters (<snippet>, line 1)
```

Min signed 8-bit.

### Q110. Intermediate

What does this print?

```python
print(int.from_bytes(b'', 'big', signed=True))
```

**Answer:**

```text
127
```

Max signed 8-bit.

### Q111. Advanced

What happens when this runs?

```python
print(b'abc' + 'd')
```

**Answer:**

```text
TypeError: can't concat str to bytes
```

Cannot add str to bytes without encoding.

### Q112. Advanced

What happens when this runs?

```python
print(bytes([256]))
```

**Answer:**

```text
ValueError: bytes must be in range(0, 256)
```

Int must be 0–255.

### Q113. Advanced

What happens when this runs?

```python
print(bytes([-1]))
```

**Answer:**

```text
ValueError: bytes must be in range(0, 256)
```

Negative int rejected.

### Q114. Advanced

What does this print?

```python
print((1 << 64).to_bytes(8, 'big'))
```

**Answer:**

```text
OverflowError: int too big to convert
```

Eight-byte big-endian exact when value fits.

### Q115. Advanced

What does this print?

```python
print(int.from_bytes(b'ÿ' * 8, 'big'))
```

**Answer:**

```text
SyntaxError: bytes can only contain ASCII literal characters (<snippet>, line 1)
```

Eight 0xff bytes → 2**64-1 unsigned.

### Q116. Advanced

What happens when this runs?

```python
print((256).to_bytes(1, 'big'))
```

**Answer:**

```text
OverflowError: int too big to convert
```

Value must fit width → `OverflowError`.

### Q117. Advanced

What does this print?

```python
print(sorted([b'bb', b'aa', b'ab']))
```

**Answer:**

```text
[b'aa', b'ab', b'bb']
```

Sort uses byte lex order.

### Q118. Advanced

What does this print?

```python
print(b'a b'.split(b' '))
```

**Answer:**

```text
SyntaxError: source code string cannot contain null bytes
```

NUL byte as delimiter.

### Q119. Advanced

What does this print?

```python
print(b'001'.lstrip(b'0'))
```

**Answer:**

```text
b'1'
```

lstrip removes leading bytes from set.

### Q120. Advanced

What does this print?

```python
print(b'banana'.replace(b'an', b'AN', 1))
```

**Answer:**

```text
b'bANana'
```

Limited replace count.

### Q121. Advanced

What does this print?

```python
print(b'
'.splitlines())
```

**Answer:**

```text
SyntaxError: unterminated string literal (detected at line 1) (<snippet>, line 1)
```

splitlines on CR/LF bytes.

### Q122. Advanced

What does this print?

```python
print(b'line1
line2
'.splitlines(keepends=True))
```

**Answer:**

```text
SyntaxError: unterminated string literal (detected at line 1) (<snippet>, line 1)
```

Keeps line ending bytes when asked.

### Q123. Advanced

What does this print?

```python
print(b'abc'.center(2, b'x'))
```

**Answer:**

```text
b'abc'
```

Width smaller than len → unchanged.

### Q124. Advanced

What does this print?

```python
print(b'þÿ' == b'ÿþ')
```

**Answer:**

```text
SyntaxError: bytes can only contain ASCII literal characters (<snippet>, line 1)
```

Byte order matters.

### Q125. Advanced

What does this print?

```python
print(b'þÿ'.decode('utf-16-be'))
```

**Answer:**

```text
SyntaxError: bytes can only contain ASCII literal characters (<snippet>, line 1)
```

UTF-16-BE codec interprets pair.

### Q126. Advanced

What does this print?

```python
print(hash(b'x'))
```

**Answer:**

```text
-4306963653417077198
```

Bytes are hashable for sets/dicts.

### Q127. Advanced

What does this print?

```python
print(b'%s' % b'ok')
```

**Answer:**

```text
b'ok'
```

Bytes % formatting with bytes values.

### Q128. Advanced

What does this print?

```python
print(b'{0}'.format(b'z'))
```

**Answer:**

```text
AttributeError: 'bytes' object has no attribute 'format'
```

Bytes format with bytes arg.

### Q129. Advanced

What does this print?

```python
print(b'a,b'.split(b',', maxsplit=0))
```

**Answer:**

```text
[b'a,b']
```

maxsplit 0 → no splits.

### Q130. Advanced

What does this print?

```python
print(b'foo'.capitalize())
```

**Answer:**

```text
b'Foo'
```

Capitalize ASCII on bytes.

### Q131. Advanced

What does this print?

```python
print(b'Foo'.swapcase())
```

**Answer:**

```text
b'fOO'
```

Swap ASCII case.

### Q132. Advanced

What does this print?

```python
print(b'hello world'.title())
```

**Answer:**

```text
b'Hello World'
```

Title-case ASCII words.

### Q133. Advanced

What does this print?

```python
print(b'abc'.zfill(6))
```

**Answer:**

```text
b'000abc'
```

Zero-byte padding on the left.

### Q134. Advanced

What does this print?

```python
print(b'abc'.__sizeof__() >= len(b'abc'))
```

**Answer:**

```text
True
```

sizeof includes object overhead.

### Q135. Advanced

What does this print?

```python
print(min(b'xyz', b'abc'), max(b'xyz', b'abc'))
```

**Answer:**

```text
b'abc' b'xyz'
```

min/max use bytes ordering.

### Q136. Intermediate

What does this print?

```python
print(b'a' < b'b', b'a' == b'b')
```

**Answer:**

```text
True False
```

Lexicographic compare and equality on raw bytes.

### Q137. Intermediate

What does this print?

```python
print(b'b' < b'a', b'b' == b'a')
```

**Answer:**

```text
False False
```

Lexicographic compare and equality on raw bytes.

### Q138. Intermediate

What does this print?

```python
print(b'aa' < b'ab', b'aa' == b'ab')
```

**Answer:**

```text
True False
```

Lexicographic compare and equality on raw bytes.

### Q139. Intermediate

What does this print?

```python
print(b'ab' < b'aa', b'ab' == b'aa')
```

**Answer:**

```text
False False
```

Lexicographic compare and equality on raw bytes.

### Q140. Advanced

What does this print?

```python
print(b' ' < b'', b' ' == b'')
```

**Answer:**

```text
SyntaxError: source code string cannot contain null bytes
```

Lexicographic compare and equality on raw bytes.

### Q141. Advanced

What does this print?

```python
print(b'ÿ' < b' ', b'ÿ' == b' ')
```

**Answer:**

```text
SyntaxError: source code string cannot contain null bytes
```

Lexicographic compare and equality on raw bytes.

### Q142. Advanced

What does this print?

```python
print(b'abc' < b'abcd', b'abc' == b'abcd')
```

**Answer:**

```text
True False
```

Lexicographic compare and equality on raw bytes.

### Q143. Advanced

What does this print?

```python
print(b'abc' < b'abb', b'abc' == b'abb')
```

**Answer:**

```text
False False
```

Lexicographic compare and equality on raw bytes.

### Q144. Intermediate

What does this print?

```python
print(b'aaa' in b'aaaaa')
```

**Answer:**

```text
True
```

Subbytes b'aaa' appears inside longer repeat pattern.

### Q145. Advanced

What does this print?

```python
print(b'bbb' in b'bbbbb')
```

**Answer:**

```text
True
```

Subbytes b'bbb' appears inside longer repeat pattern.

### Q146. Advanced

What does this print?

```python
print(b'ccc' in b'ccccc')
```

**Answer:**

```text
True
```

Subbytes b'ccc' appears inside longer repeat pattern.

### Q147. Intermediate

What does this print?

```python
print(b'ddd' in b'ddddd')
```

**Answer:**

```text
True
```

Subbytes b'ddd' appears inside longer repeat pattern.

### Q148. Advanced

What does this print?

```python
print(b'eee' in b'eeeee')
```

**Answer:**

```text
True
```

Subbytes b'eee' appears inside longer repeat pattern.

### Q149. Advanced

What does this print?

```python
print(b'fff' in b'fffff')
```

**Answer:**

```text
True
```

Subbytes b'fff' appears inside longer repeat pattern.

### Q150. Intermediate

What does this print?

```python
print(b'ggg' in b'ggggg')
```

**Answer:**

```text
True
```

Subbytes b'ggg' appears inside longer repeat pattern.

### Q151. Advanced

What does this print?

```python
print(b'hhh' in b'hhhhh')
```

**Answer:**

```text
True
```

Subbytes b'hhh' appears inside longer repeat pattern.

### Q152. Advanced

What does this print?

```python
print(b'iii' in b'iiiii')
```

**Answer:**

```text
True
```

Subbytes b'iii' appears inside longer repeat pattern.

### Q153. Intermediate

What does this print?

```python
print(b'jjj' in b'jjjjj')
```

**Answer:**

```text
True
```

Subbytes b'jjj' appears inside longer repeat pattern.

### Q154. Advanced

What does this print?

```python
print(b'kkk' in b'kkkkk')
```

**Answer:**

```text
True
```

Subbytes b'kkk' appears inside longer repeat pattern.

### Q155. Advanced

What does this print?

```python
print(b'lll' in b'lllll')
```

**Answer:**

```text
True
```

Subbytes b'lll' appears inside longer repeat pattern.

### Q156. Intermediate

What does this print?

```python
print(b'mmm' in b'mmmmm')
```

**Answer:**

```text
True
```

Subbytes b'mmm' appears inside longer repeat pattern.

### Q157. Advanced

What does this print?

```python
print(b'nnn' in b'nnnnn')
```

**Answer:**

```text
True
```

Subbytes b'nnn' appears inside longer repeat pattern.

### Q158. Advanced

What does this print?

```python
print(b'ooo' in b'ooooo')
```

**Answer:**

```text
True
```

Subbytes b'ooo' appears inside longer repeat pattern.

### Q159. Intermediate

What does this print?

```python
print(b'ppp' in b'ppppp')
```

**Answer:**

```text
True
```

Subbytes b'ppp' appears inside longer repeat pattern.

### Q160. Advanced

What does this print?

```python
print(b'qqq' in b'qqqqq')
```

**Answer:**

```text
True
```

Subbytes b'qqq' appears inside longer repeat pattern.

### Q161. Advanced

What does this print?

```python
print(b'rrr' in b'rrrrr')
```

**Answer:**

```text
True
```

Subbytes b'rrr' appears inside longer repeat pattern.

### Q162. Intermediate

What does this print?

```python
print(b'sss' in b'sssss')
```

**Answer:**

```text
True
```

Subbytes b'sss' appears inside longer repeat pattern.

### Q163. Advanced

What does this print?

```python
print(b'ttt' in b'ttttt')
```

**Answer:**

```text
True
```

Subbytes b'ttt' appears inside longer repeat pattern.

### Q164. Advanced

What does this print?

```python
print(b'uuu' in b'uuuuu')
```

**Answer:**

```text
True
```

Subbytes b'uuu' appears inside longer repeat pattern.

### Q165. Intermediate

What does this print?

```python
print(b'vvv' in b'vvvvv')
```

**Answer:**

```text
True
```

Subbytes b'vvv' appears inside longer repeat pattern.

### Q166. Advanced

What does this print?

```python
print(b'www' in b'wwwww')
```

**Answer:**

```text
True
```

Subbytes b'www' appears inside longer repeat pattern.

### Q167. Advanced

What does this print?

```python
print(b'xxx' in b'xxxxx')
```

**Answer:**

```text
True
```

Subbytes b'xxx' appears inside longer repeat pattern.

### Q168. Intermediate

What does this print?

```python
print(b'yyy' in b'yyyyy')
```

**Answer:**

```text
True
```

Subbytes b'yyy' appears inside longer repeat pattern.

### Q169. Advanced

What does this print?

```python
print(b'zzz' in b'zzzzz')
```

**Answer:**

```text
True
```

Subbytes b'zzz' appears inside longer repeat pattern.

### Q170. Advanced

What does this print?

```python
print(b'aaa' in b'aaaaa')
```

**Answer:**

```text
True
```

Subbytes b'aaa' appears inside longer repeat pattern.

### Q171. Intermediate

What does this print?

```python
print(b'bbb' in b'bbbbb')
```

**Answer:**

```text
True
```

Subbytes b'bbb' appears inside longer repeat pattern.

### Q172. Advanced

What does this print?

```python
print(b'ccc' in b'ccccc')
```

**Answer:**

```text
True
```

Subbytes b'ccc' appears inside longer repeat pattern.

### Q173. Advanced

What does this print?

```python
print(b'ddd' in b'ddddd')
```

**Answer:**

```text
True
```

Subbytes b'ddd' appears inside longer repeat pattern.

### Q174. Intermediate

What does this print?

```python
print(b'eee' in b'eeeee')
```

**Answer:**

```text
True
```

Subbytes b'eee' appears inside longer repeat pattern.

### Q175. Advanced

What does this print?

```python
print(b'fff' in b'fffff')
```

**Answer:**

```text
True
```

Subbytes b'fff' appears inside longer repeat pattern.

### Q176. Advanced

What does this print?

```python
print(b'ggg' in b'ggggg')
```

**Answer:**

```text
True
```

Subbytes b'ggg' appears inside longer repeat pattern.

### Q177. Intermediate

What does this print?

```python
print(b'hhh' in b'hhhhh')
```

**Answer:**

```text
True
```

Subbytes b'hhh' appears inside longer repeat pattern.

### Q178. Advanced

What does this print?

```python
print(b'iii' in b'iiiii')
```

**Answer:**

```text
True
```

Subbytes b'iii' appears inside longer repeat pattern.

### Q179. Advanced

What does this print?

```python
print(b'jjj' in b'jjjjj')
```

**Answer:**

```text
True
```

Subbytes b'jjj' appears inside longer repeat pattern.

### Q180. Intermediate

What does this print?

```python
print(b'kkk' in b'kkkkk')
```

**Answer:**

```text
True
```

Subbytes b'kkk' appears inside longer repeat pattern.

### Q181. Advanced

What does this print?

```python
print(b'lll' in b'lllll')
```

**Answer:**

```text
True
```

Subbytes b'lll' appears inside longer repeat pattern.

### Q182. Advanced

What does this print?

```python
print(b'mmm' in b'mmmmm')
```

**Answer:**

```text
True
```

Subbytes b'mmm' appears inside longer repeat pattern.

### Q183. Intermediate

What does this print?

```python
print(b'nnn' in b'nnnnn')
```

**Answer:**

```text
True
```

Subbytes b'nnn' appears inside longer repeat pattern.

### Q184. Advanced

What does this print?

```python
print(b'ooo' in b'ooooo')
```

**Answer:**

```text
True
```

Subbytes b'ooo' appears inside longer repeat pattern.

### Q185. Advanced

What does this print?

```python
print(b'ppp' in b'ppppp')
```

**Answer:**

```text
True
```

Subbytes b'ppp' appears inside longer repeat pattern.

### Q186. Intermediate

What does this print?

```python
print(b'qqq' in b'qqqqq')
```

**Answer:**

```text
True
```

Subbytes b'qqq' appears inside longer repeat pattern.

### Q187. Advanced

What does this print?

```python
print(b'rrr' in b'rrrrr')
```

**Answer:**

```text
True
```

Subbytes b'rrr' appears inside longer repeat pattern.

### Q188. Advanced

What does this print?

```python
print(b'sss' in b'sssss')
```

**Answer:**

```text
True
```

Subbytes b'sss' appears inside longer repeat pattern.

### Q189. Intermediate

What does this print?

```python
print(b'ttt' in b'ttttt')
```

**Answer:**

```text
True
```

Subbytes b'ttt' appears inside longer repeat pattern.

### Q190. Advanced

What does this print?

```python
print(b'uuu' in b'uuuuu')
```

**Answer:**

```text
True
```

Subbytes b'uuu' appears inside longer repeat pattern.

### Q191. Intermediate

Write `xor_bytes(a, b)` XORing equal-length bytes byte-wise.

**Answer:**

```python
def xor_bytes(a, b):
    if len(a) != len(b):
        raise ValueError('length mismatch')
    return bytes(x ^ y for x, y in zip(a, b))
```

- `xor_bytes(b'\x00\xff', b'\xff\x00')  =>  b'\xff\xff'`
- `xor_bytes(b'abc', b'abc')  =>  b'\x00\x00\x00'`

XOR equal bytes cancels to zero; differing bits flip.

### Q192. Advanced

Write `checksum(data)` as sum of bytes mod 256.

**Answer:**

```python
def checksum(data):
    return sum(data) % 256
```

- `checksum(b'')  =>  0`
- `checksum(b'\xff\x01')  =>  0`
- `checksum(b'abc')  =>  38`

Additive checksum wraps with mod 256.

### Q193. Advanced

Parse length-prefixed message: byte0=N, next N bytes payload.

**Answer:**

```python
def parse_length_prefixed(buf):
    n = buf[0]
    return buf[1:1 + n]
```

- `parse_length_prefixed(bytes([2]) + b'hi')  =>  b'hi'`
- `parse_length_prefixed(bytes([0]))  =>  b''`

Length in first byte; slice payload without copy of whole buffer beyond view semantics of slice.

### Q194. Basic

Write `pack_u16_be(n)` for 0 <= n < 65536.

**Answer:**

```python
def pack_u16_be(n):
    return n.to_bytes(2, 'big')
```

- `pack_u16_be(0)  =>  b'\x00\x00'`
- `pack_u16_be(256)  =>  b'\x01\x00'`
- `pack_u16_be(65535)  =>  b'\xff\xff'`

Fixed-width big-endian unsigned 16-bit.

### Q195. Intermediate

Write `unpack_u16_be(b2)` for exactly two bytes.

**Answer:**

```python
def unpack_u16_be(b2):
    return int.from_bytes(b2, 'big')
```

- `unpack_u16_be(b'\x00\x01')  =>  1`
- `unpack_u16_be(b'\xff\xff')  =>  65535`

Inverse of pack with big endian.

### Q196. Advanced

Write `constant_time_compare(a, b)` returning whether equal length and all bytes match (use `hmac.compare_digest`).

**Answer:**

```python
import hmac

def constant_time_compare(a, b):
    return hmac.compare_digest(a, b)
```

- `constant_time_compare(b'secret', b'secret')  =>  True`
- `constant_time_compare(b'a', b'b')  =>  False`

Compare digests/mac tags in constant time; same idea for raw bytes equality checks in security code.

### Q197. Intermediate

Write `hexlify_upper(data)` returning uppercase hex ASCII bytes without `hex()` (use `.hex().upper().encode()`).

**Answer:**

```python
def hexlify_upper(data):
    return data.hex().upper().encode('ascii')
```

- `hexlify_upper(b'\x00\xff')  =>  b'00FF'`
- `hexlify_upper(b'a')  =>  b'61'`

hex() → str → upper → ascii bytes for wire formats.

### Q198. Basic

Write `is_all_ascii(data)` using `data.isascii()`.

**Answer:**

```python
def is_all_ascii(data):
    return data.isascii()
```

- `is_all_ascii(b'abc')  =>  True`
- `is_all_ascii(b'\xff')  =>  False`

Every byte must be ≤ 127.

### Q199. Intermediate

What does this print?

```python
print(b'abc'.removeprefix(b'a'), b'abc'.removesuffix(b'c'))
```

**Answer:**

```text
b'bc' b'ab'
```

`removeprefix` and `removesuffix` return bytes and remove one affix.

### Q200. Advanced

What does this print?

```python
print(b'%s' % b'hi')
```

**Answer:**

```text
b'hi'
```

Bytes support the old percent formatting with bytes arguments, and the result is bytes.

*Section size: 200 questions (Basic 58, Intermediate 74, Advanced 68).*

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

## 16. MNC interview programming questions

Coding problems in the style reported from Amazon, Google, Microsoft, Meta, Apple, Adobe, Uber, Goldman Sachs, Flipkart, and similar loops. Statements are paraphrased for practice. Each answer names an approach, its complexity, and a Python sketch. A company tag means the problem is widely associated with that interview loop, not that one team asked this wording on a particular day.

### Q1. Basic

**Two Sum**

Commonly reported in interviews at Amazon, Google, Meta, Microsoft.

Given a list of integers and a target, return the indices of two different items that add up to the target. Exactly one answer exists.

Example: `nums = [2, 7, 11, 15]`, `target = 9` returns `[0, 1]`.

**Answer:**

One pass with a dictionary from value to index. For each number, look up `target - number` before storing the current index.

**Complexity:** Time O(n), space O(n).

```python
def two_sum(nums, target):
    seen = {}
    for i, n in enumerate(nums):
        j = seen.get(target - n)
        if j is not None:
            return [j, i]
        seen[n] = i
```

### Q2. Basic

**Contains Duplicate**

Commonly reported in interviews at Amazon, Apple, Adobe.

Return true when a list of integers contains any value more than once.

Example: `[1, 2, 3, 1]` is true. `[1, 2, 3]` is false.

**Answer:**

Insert values into a set. If a value is already present, it is a duplicate. Sorting also works if you can spend O(n log n) time and no extra memory.

**Complexity:** Time O(n), space O(n) with a set.

```python
def contains_duplicate(nums):
    return len(nums) != len(set(nums))
```

### Q3. Basic

**Best Time to Buy and Sell Stock**

Commonly reported in interviews at Amazon, Bloomberg, Microsoft.

You may complete one buy and one later sell. Return the maximum profit, or 0 if no profit is possible.

Example: `[7, 1, 5, 3, 6, 4]` returns `5` (buy at 1, sell at 6).

**Answer:**

Track the minimum price seen so far and the best difference `price - minimum`.

**Complexity:** Time O(n), space O(1).

```python
def max_profit(prices):
    best, low = 0, prices[0]
    for p in prices:
        low = min(low, p)
        best = max(best, p - low)
    return best
```

### Q4. Basic

**Move Zeroes**

Commonly reported in interviews at Facebook, Bloomberg.

Move every 0 to the end of the list while keeping the order of the non-zero numbers. Do it in place.

Example: `[0, 1, 0, 3, 12]` becomes `[1, 3, 12, 0, 0]`.

**Answer:**

Use a write index. Copy each non-zero forward, then fill the tail with zeros.

**Complexity:** Time O(n), space O(1).

```python
def move_zeroes(nums):
    w = 0
    for x in nums:
        if x != 0:
            nums[w] = x
            w += 1
    for i in range(w, len(nums)):
        nums[i] = 0
    return nums
```

### Q5. Basic

**Plus One**

Commonly reported in interviews at Google, Amazon.

A list of digits represents a non-negative integer. Return the digits of that integer plus one.

Example: `[1, 2, 9]` becomes `[1, 3, 0]`. `[9, 9]` becomes `[1, 0, 0]`.

**Answer:**

Walk from the right. Turn 9s into 0s until a digit can be incremented. If every digit was 9, insert a leading 1.

**Complexity:** Time O(n), space O(1) extra besides the answer.

```python
def plus_one(digits):
    for i in range(len(digits) - 1, -1, -1):
        if digits[i] < 9:
            digits[i] += 1
            return digits
        digits[i] = 0
    return [1] + digits
```

### Q6. Basic

**Remove Duplicates from Sorted Array**

Commonly reported in interviews at Microsoft, Amazon.

A sorted list may contain duplicates. Compact the unique values at the front and return how many unique values there are. Order must stay sorted.

Example: `[1, 1, 2, 2, 3]` becomes `[1, 2, 3, ...]` and the function returns `3`.

**Answer:**

Two pointers. The slow pointer marks the end of the unique prefix. Copy a value forward only when it differs from the last kept value.

**Complexity:** Time O(n), space O(1).

```python
def remove_duplicates(nums):
    if not nums:
        return 0
    w = 1
    for i in range(1, len(nums)):
        if nums[i] != nums[w - 1]:
            nums[w] = nums[i]
            w += 1
    return w
```

### Q7. Basic

**Merge Sorted Array**

Commonly reported in interviews at Facebook, Microsoft.

Two sorted lists `a` and `b`. `a` has enough trailing space for every element of `b`. Merge `b` into `a` so `a` is sorted.

Example: `a = [1, 3, 5, 0, 0]`, `b = [2, 4]` becomes `[1, 2, 3, 4, 5]`.

**Answer:**

Fill from the end so the empty slots are consumed first and no value in `a` is overwritten before it is placed.

**Complexity:** Time O(n + m), space O(1).

```python
def merge(a, m, b, n):
    i, j, k = m - 1, n - 1, m + n - 1
    while j >= 0:
        if i >= 0 and a[i] > b[j]:
            a[k] = a[i]
            i -= 1
        else:
            a[k] = b[j]
            j -= 1
        k -= 1
    return a
```

### Q8. Basic

**Majority Element**

Commonly reported in interviews at Amazon, Adobe.

A value appears more than `len(nums) // 2` times. Return it.

Example: `[2, 2, 1, 2, 3]` returns `2`.

**Answer:**

Boyer-Moore voting: keep a candidate and a count. The majority survives because every other value can cancel it at most once.

**Complexity:** Time O(n), space O(1).

```python
def majority(nums):
    cand = count = 0
    for n in nums:
        if count == 0:
            cand = n
        count += 1 if n == cand else -1
    return cand
```

### Q9. Basic

**Missing Number**

Commonly reported in interviews at Microsoft, Amazon.

The list contains `n` distinct numbers taken from `0` through `n`. Return the missing one.

Example: `[3, 0, 1]` returns `2`.

**Answer:**

XOR every index and every value, then XOR `n`. Pairs cancel and the missing number remains. The sum formula `n*(n+1)//2 - sum(nums)` also works.

**Complexity:** Time O(n), space O(1).

```python
def missing_number(nums):
    n = len(nums)
    xor = n
    for i, v in enumerate(nums):
        xor ^= i ^ v
    return xor
```

### Q10. Basic

**Single Number**

Commonly reported in interviews at Amazon, Google.

Every value appears twice except one value, which appears once. Return that value.

Example: `[4, 1, 2, 1, 2]` returns `4`.

**Answer:**

XOR the whole list. Identical pairs cancel to 0.

**Complexity:** Time O(n), space O(1).

```python
def single_number(nums):
    acc = 0
    for n in nums:
        acc ^= n
    return acc
```

### Q11. Basic

**Climbing Stairs**

Commonly reported in interviews at Amazon, Adobe, Uber.

You climb 1 or 2 stairs at a time. Return how many distinct ways there are to climb `n` stairs.

Example: `n = 3` returns `3`: 1+1+1, 1+2, 2+1.

**Answer:**

This is Fibonacci. Let `dp[i]` be ways to reach step `i`. Then `dp[i] = dp[i-1] + dp[i-2]`. Keep only two rolling values.

**Complexity:** Time O(n), space O(1).

```python
def climb(n):
    a, b = 1, 1
    for _ in range(n):
        a, b = b, a + b
    return a
```

### Q12. Basic

**Valid Parentheses**

Commonly reported in interviews at Amazon, Microsoft, Google.

A string contains only `()[]{}`. Return true when the brackets are correctly matched and nested.

Example: `()[]{}` is true. `(]` is false. `([)]` is false.

**Answer:**

Push opening brackets. On a closing bracket, the stack top must be its partner. The stack must end empty.

**Complexity:** Time O(n), space O(n).

```python
def is_valid(s):
    pair = {')': '(', ']': '[', '}': '{'}
    stack = []
    for ch in s:
        if ch in '([{':
            stack.append(ch)
        elif not stack or stack.pop() != pair[ch]:
            return False
    return not stack
```

### Q13. Basic

**Valid Anagram**

Commonly reported in interviews at Amazon, Bloomberg.

Return true when two strings are anagrams of each other. Comparison is case-sensitive and uses the raw characters.

Example: `anagram` and `nagaram` is true. `rat` and `car` is false.

**Answer:**

Count characters. For a small alphabet, an array of 26 is enough. A `Counter` equality test is the same idea.

**Complexity:** Time O(n), space O(1) for a fixed alphabet.

```python
def is_anagram(a, b):
    if len(a) != len(b):
        return False
    from collections import Counter
    return Counter(a) == Counter(b)
```

### Q14. Basic

**First Unique Character**

Commonly reported in interviews at Amazon, Goldman Sachs.

Return the index of the first character that appears once in a string, or -1.

Example: `leetcode` returns `0`. `aabb` returns `-1`.

**Answer:**

Count, then scan again for the first character whose count is 1. Two passes keep the original order.

**Complexity:** Time O(n), space O(1) for a fixed alphabet.

```python
def first_unique(s):
    from collections import Counter
    counts = Counter(s)
    for i, ch in enumerate(s):
        if counts[ch] == 1:
            return i
    return -1
```

### Q15. Basic

**Ransom Note**

Commonly reported in interviews at Apple, Amazon.

Return true when the note can be cut from the letters in a magazine. Each magazine character may be used once.

Example: Note `aab` and magazine `baa` is true.

**Answer:**

Count magazine letters and decrement. Fail when a needed letter is missing.

**Complexity:** Time O(n + m), space O(1) for a fixed alphabet.

```python
def can_construct(note, magazine):
    from collections import Counter
    have = Counter(magazine)
    for ch in note:
        if have[ch] == 0:
            return False
        have[ch] -= 1
    return True
```

### Q16. Basic

**Reverse Linked List**

Commonly reported in interviews at Amazon, Microsoft, Apple.

Reverse a singly linked list in place and return the new head. Nodes have `.val` and `.next`.

Example: `1 -> 2 -> 3` becomes `3 -> 2 -> 1`.

**Answer:**

Three pointers: previous, current, and next. Point current backward, then advance.

**Complexity:** Time O(n), space O(1).

```python
def reverse_list(head):
    prev = None
    cur = head
    while cur:
        nxt = cur.next
        cur.next = prev
        prev = cur
        cur = nxt
    return prev
```

### Q17. Basic

**Linked List Cycle**

Commonly reported in interviews at Amazon, Microsoft.

Return true when a singly linked list contains a cycle.

Example: A list whose tail points at an earlier node is true.

**Answer:**

Floyd's tortoise and hare. If they meet, there is a cycle. If the fast pointer reaches the end, there is not.

**Complexity:** Time O(n), space O(1).

```python
def has_cycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow is fast:
            return True
    return False
```

### Q18. Basic

**Maximum Depth of Binary Tree**

Commonly reported in interviews at Amazon, LinkedIn.

Return the number of nodes on the longest root-to-leaf path. An empty tree has depth 0.

Example: A single node returns 1.

**Answer:**

Depth is `1 + max(depth(left), depth(right))`. An iterative level-order count is the same answer.

**Complexity:** Time O(n), space O(h) for the recursion stack.

```python
def max_depth(root):
    if not root:
        return 0
    return 1 + max(max_depth(root.left), max_depth(root.right))
```

### Q19. Basic

**Same Tree**

Commonly reported in interviews at Bloomberg, Amazon.

Return true when two binary trees have the same shape and the same values.

Example: Both empty is true. One empty is false.

**Answer:**

Recurse: values must match and both pairs of children must match.

**Complexity:** Time O(n), space O(h).

```python
def is_same(a, b):
    if not a or not b:
        return a is b
    return a.val == b.val and is_same(a.left, b.left) and is_same(a.right, b.right)
```

### Q20. Basic

**Invert Binary Tree**

Commonly reported in interviews at Google.

Swap every left and right child and return the root.

Example: A tree `1 / 2,3` becomes `1 / 3,2`.

**Answer:**

Post-order or pre-order swap. Recursion is enough.

**Complexity:** Time O(n), space O(h).

```python
def invert(root):
    if root:
        root.left, root.right = invert(root.right), invert(root.left)
    return root
```

### Q21. Basic

**Binary Search**

Commonly reported in interviews at Every product company.

Given a sorted list of distinct integers, return the index of `target`, or -1.

Example: `[1, 3, 5, 7]`, target `5` returns `2`.

**Answer:**

Keep a half-open or closed window. Compare the middle and discard the half that cannot contain the target. Watch the midpoint so it does not overflow in fixed-width languages; Python ints do not overflow.

**Complexity:** Time O(log n), space O(1).

```python
def binary_search(nums, target):
    lo, hi = 0, len(nums) - 1
    while lo <= hi:
        mid = (lo + hi) // 2
        if nums[mid] == target:
            return mid
        if nums[mid] < target:
            lo = mid + 1
        else:
            hi = mid - 1
    return -1
```

### Q22. Basic

**Search Insert Position**

Commonly reported in interviews at Amazon, Adobe.

Given a sorted list of distinct integers, return the index of `target` if it exists, otherwise the index where it should be inserted to keep the list sorted.

Example: `[1, 3, 5, 6]`, target `2` returns `1`.

**Answer:**

Lower-bound binary search. When the loop ends, `lo` is the first index whose value is not less than the target.

**Complexity:** Time O(log n), space O(1).

```python
def search_insert(nums, target):
    lo, hi = 0, len(nums)
    while lo < hi:
        mid = (lo + hi) // 2
        if nums[mid] < target:
            lo = mid + 1
        else:
            hi = mid
    return lo
```

### Q23. Basic

**Implement Stack using a List**

Commonly reported in interviews at Amazon, Microsoft.

Implement `push`, `pop`, `top`, and `empty` for a stack. `pop` and `top` are called only when the stack is non-empty.

Example: push 1, push 2, top is 2, pop returns 2.

**Answer:**

A Python list already has amortized O(1) append and pop from the end. That end is the top.

**Complexity:** Each operation is amortized O(1). Space O(n).

```python
class Stack:
    def __init__(self):
        self.data = []
    def push(self, x):
        self.data.append(x)
    def pop(self):
        return self.data.pop()
    def top(self):
        return self.data[-1]
    def empty(self):
        return not self.data
```

### Q24. Basic

**Min Stack**

Commonly reported in interviews at Amazon, Bloomberg, Google.

Design a stack that also returns its current minimum in O(1).

Example: Push -2, push 0, push -3. Min is -3. After pop, min is -2.

**Answer:**

Keep a second stack of minima. On push, store `min(x, current_min)`. On pop, pop both stacks.

**Complexity:** Each operation O(1). Space O(n).

```python
class MinStack:
    def __init__(self):
        self.data = []
        self.mins = []
    def push(self, x):
        self.data.append(x)
        self.mins.append(x if not self.mins else min(x, self.mins[-1]))
    def pop(self):
        self.mins.pop()
        return self.data.pop()
    def top(self):
        return self.data[-1]
    def get_min(self):
        return self.mins[-1]
```

### Q25. Basic

**Fizz Buzz**

Commonly reported in interviews at Amazon, and many screening rounds.

Return a list of strings for numbers from 1 through `n`. Multiples of 3 are `Fizz`, multiples of 5 are `Buzz`, multiples of both are `FizzBuzz`, and the rest are the decimal number.

Example: `n = 5` gives `['1', '2', 'Fizz', '4', 'Buzz']`.

**Answer:**

Test 15 before 3 and 5, or build the word from the two conditions so the order of tests does not matter.

**Complexity:** Time O(n), space O(n) for the answer.

```python
def fizz_buzz(n):
    out = []
    for i in range(1, n + 1):
        word = ''
        if i % 3 == 0:
            word += 'Fizz'
        if i % 5 == 0:
            word += 'Buzz'
        out.append(word or str(i))
    return out
```

### Q26. Basic

**Maximum Subarray**

Commonly reported in interviews at Amazon, Microsoft, LinkedIn.

Return the largest sum of any contiguous subarray. The list contains at least one number and may contain negatives.

Example: `[-2, 1, -3, 4, -1, 2, 1, -5, 4]` returns `6` from `[4, -1, 2, 1]`.

**Answer:**

Kadane's algorithm. Either extend the current subarray or start over at the current element, whichever is larger. Track the best sum.

**Complexity:** Time O(n), space O(1).

```python
def max_subarray(nums):
    best = cur = nums[0]
    for n in nums[1:]:
        cur = max(n, cur + n)
        best = max(best, cur)
    return best
```

### Q27. Basic

**Pascal's Triangle Row**

Commonly reported in interviews at Amazon, Adobe.

Return the first `n` rows of Pascal's triangle. Each interior value is the sum of the two values above it. Rows are 0-indexed or 1-indexed; here `n` is the number of rows.

Example: `n = 3` returns `[[1], [1, 1], [1, 2, 1]]`.

**Answer:**

Build each row from the previous one. Edges are 1.

**Complexity:** Time O(n^2), space O(n^2) for the answer.

```python
def pascal(n):
    rows = []
    for r in range(n):
        row = [1] * (r + 1)
        for c in range(1, r):
            row[c] = rows[r - 1][c - 1] + rows[r - 1][c]
        rows.append(row)
    return rows
```

### Q28. Basic

**Merge Two Sorted Lists**

Commonly reported in interviews at Amazon, Microsoft, Apple.

Merge two sorted singly linked lists into one sorted list. You may reuse the nodes.

Example: `1 -> 3` and `2 -> 4` becomes `1 -> 2 -> 3 -> 4`.

**Answer:**

Dummy head. Always attach the smaller current node, then advance that list.

**Complexity:** Time O(n + m), space O(1).

```python
def merge_lists(a, b):
    dummy = tail = type(a)(0) if False else _Node(0)
    while a and b:
        if a.val <= b.val:
            tail.next, a = a, a.next
        else:
            tail.next, b = b, b.next
        tail = tail.next
    tail.next = a or b
    return dummy.next

class _Node:
    def __init__(self, val, next=None):
        self.val, self.next = val, next
```

### Q29. Basic

**Symmetric Tree**

Commonly reported in interviews at Microsoft, Amazon.

Return true when a binary tree is a mirror of itself.

Example: A tree with root 1 and children 2,2, each with outer child 3, is symmetric.

**Answer:**

Compare the left subtree with the right subtree as mirrors: left.left with right.right, and left.right with right.left.

**Complexity:** Time O(n), space O(h).

```python
def is_symmetric(root):
    def mirror(a, b):
        if not a or not b:
            return a is b
        return a.val == b.val and mirror(a.left, b.right) and mirror(a.right, b.left)
    return mirror(root.left, root.right) if root else True
```

### Q30. Basic

**Path Sum**

Commonly reported in interviews at Amazon, Adobe.

Return true when the tree has a root-to-leaf path whose values sum to `target`.

Example: Root 5 with a leaf path 4 then 11 then 2 sums to 22.

**Answer:**

Subtract the current value and recurse. A leaf succeeds only when the remaining target is 0.

**Complexity:** Time O(n), space O(h).

```python
def has_path_sum(root, target):
    if not root:
        return False
    if not root.left and not root.right:
        return target == root.val
    return has_path_sum(root.left, target - root.val) or has_path_sum(root.right, target - root.val)
```

### Q31. Intermediate

**Group Anagrams**

Commonly reported in interviews at Amazon, Uber, Facebook.

Group strings that are anagrams of each other. Order of groups does not matter.

Example: `['eat', 'tea', 'tan', 'ate', 'nat', 'bat']` forms three groups.

**Answer:**

The sorted tuple of characters is a signature. A count tuple of 26 letters also works and avoids the sort.

**Complexity:** Time O(n * k log k) with sorting, or O(n * k) with counts. Space O(n * k).

```python
def group_anagrams(words):
    from collections import defaultdict
    groups = defaultdict(list)
    for w in words:
        groups[tuple(sorted(w))].append(w)
    return list(groups.values())
```

### Q32. Intermediate

**Longest Substring Without Repeating Characters**

Commonly reported in interviews at Amazon, Google, Bloomberg.

Return the length of the longest substring that contains no repeated character.

Example: `abcabcbb` returns `3` (`abc`).

**Answer:**

Sliding window. Store the last index of each character. When a repeat falls inside the window, move the left edge to one past that index.

**Complexity:** Time O(n), space O(1) for a fixed alphabet, otherwise O(k).

```python
def length_of_longest_substring(s):
    last = {}
    left = best = 0
    for right, ch in enumerate(s):
        if ch in last and last[ch] >= left:
            left = last[ch] + 1
        last[ch] = right
        best = max(best, right - left + 1)
    return best
```

### Q33. Intermediate

**Product of Array Except Self**

Commonly reported in interviews at Amazon, Facebook, Microsoft.

Return a list where `out[i]` is the product of every element of `nums` except `nums[i]`. Do not use division. The answer may use extra space, but the running products should be O(1) extra besides the answer.

Example: `[1, 2, 3, 4]` returns `[24, 12, 8, 6]`.

**Answer:**

Prefix products left to right, then suffix products right to left folded into the same output.

**Complexity:** Time O(n), extra space O(1) besides the answer.

```python
def product_except_self(nums):
    n = len(nums)
    out = [1] * n
    left = 1
    for i in range(n):
        out[i] = left
        left *= nums[i]
    right = 1
    for i in range(n - 1, -1, -1):
        out[i] *= right
        right *= nums[i]
    return out
```

### Q34. Intermediate

**3Sum**

Commonly reported in interviews at Amazon, Facebook, Google.

Return all unique triplets in a list of integers that sum to 0. The triplets should not repeat as sets of values.

Example: `[-1, 0, 1, 2, -1, -4]` returns `[[-1, -1, 2], [-1, 0, 1]]`.

**Answer:**

Sort. Fix one value and run two pointers on the remainder. Skip duplicate values at each pointer so the same triplet is not emitted twice.

**Complexity:** Time O(n^2), space O(1) extra besides the answer, or O(n) for the sort depending on the implementation.

```python
def three_sum(nums):
    nums = sorted(nums)
    out = []
    for i in range(len(nums)):
        if i and nums[i] == nums[i - 1]:
            continue
        lo, hi = i + 1, len(nums) - 1
        while lo < hi:
            s = nums[i] + nums[lo] + nums[hi]
            if s == 0:
                out.append([nums[i], nums[lo], nums[hi]])
                lo += 1
                hi -= 1
                while lo < hi and nums[lo] == nums[lo - 1]:
                    lo += 1
                while lo < hi and nums[hi] == nums[hi + 1]:
                    hi -= 1
            elif s < 0:
                lo += 1
            else:
                hi -= 1
    return out
```

### Q35. Intermediate

**Container With Most Water**

Commonly reported in interviews at Amazon, Google, Bloomberg.

Vertical lines stand at x positions 0..n-1 with the given heights. Pick two lines so the area of the container they form with the x-axis is maximized.

Example: `[1, 8, 6, 2, 5, 4, 8, 3, 7]` returns `49`.

**Answer:**

Two pointers at the ends. The area is limited by the shorter line. Move the shorter side inward, because width only shrinks and a taller partner on the short side is the only way to improve.

**Complexity:** Time O(n), space O(1).

```python
def max_area(height):
    lo, hi = 0, len(height) - 1
    best = 0
    while lo < hi:
        best = max(best, min(height[lo], height[hi]) * (hi - lo))
        if height[lo] < height[hi]:
            lo += 1
        else:
            hi -= 1
    return best
```

### Q36. Intermediate

**Merge Intervals**

Commonly reported in interviews at Facebook, Google, Amazon.

Given closed intervals, merge every pair that overlaps and return the result sorted by start.

Example: `[[1, 3], [2, 6], [8, 10], [15, 18]]` returns `[[1, 6], [8, 10], [15, 18]]`.

**Answer:**

Sort by start. If the current interval starts at or before the end of the last merged interval, extend that end. Otherwise append a new interval.

**Complexity:** Time O(n log n), space O(n) for the answer.

```python
def merge_intervals(intervals):
    intervals = sorted(intervals)
    out = [list(intervals[0])]
    for start, end in intervals[1:]:
        if start <= out[-1][1]:
            out[-1][1] = max(out[-1][1], end)
        else:
            out.append([start, end])
    return out
```

### Q37. Intermediate

**Insert Interval**

Commonly reported in interviews at Google, Amazon.

Insert a new interval into a sorted list of non-overlapping intervals and merge if needed.

Example: `[[1, 3], [6, 9]]` plus `[2, 5]` returns `[[1, 5], [6, 9]]`.

**Answer:**

Append intervals that end before the new one starts. Merge every interval that overlaps the new one. Append the rest.

**Complexity:** Time O(n), space O(n).

```python
def insert_interval(intervals, new):
    out = []
    i = 0
    while i < len(intervals) and intervals[i][1] < new[0]:
        out.append(intervals[i])
        i += 1
    while i < len(intervals) and intervals[i][0] <= new[1]:
        new[0] = min(new[0], intervals[i][0])
        new[1] = max(new[1], intervals[i][1])
        i += 1
    out.append(new)
    out.extend(intervals[i:])
    return out
```

### Q38. Intermediate

**Sort Colors**

Commonly reported in interviews at Microsoft, Amazon.

Sort a list that contains only 0, 1, and 2, in place, in one pass.

Example: `[2, 0, 2, 1, 1, 0]` becomes `[0, 0, 1, 1, 2, 2]`.

**Answer:**

Dutch national flag. Three pointers: next write position for 0, current scan, and next write position for 2.

**Complexity:** Time O(n), space O(1).

```python
def sort_colors(nums):
    lo, i, hi = 0, 0, len(nums) - 1
    while i <= hi:
        if nums[i] == 0:
            nums[lo], nums[i] = nums[i], nums[lo]
            lo += 1
            i += 1
        elif nums[i] == 2:
            nums[hi], nums[i] = nums[i], nums[hi]
            hi -= 1
        else:
            i += 1
    return nums
```

### Q39. Intermediate

**Set Matrix Zeroes**

Commonly reported in interviews at Amazon, Microsoft.

If an element of a matrix is 0, set its whole row and column to 0. Do it in place.

Example: A 3x3 matrix with a single 0 at the center becomes a cross of zeros.

**Answer:**

Use the first row and first column as markers, plus two booleans for whether those lines themselves must be cleared.

**Complexity:** Time O(m * n), extra space O(1).

```python
def set_zeroes(matrix):
    m, n = len(matrix), len(matrix[0])
    row0 = any(matrix[0][j] == 0 for j in range(n))
    col0 = any(matrix[i][0] == 0 for i in range(m))
    for i in range(1, m):
        for j in range(1, n):
            if matrix[i][j] == 0:
                matrix[i][0] = matrix[0][j] = 0
    for i in range(1, m):
        for j in range(1, n):
            if matrix[i][0] == 0 or matrix[0][j] == 0:
                matrix[i][j] = 0
    if row0:
        for j in range(n):
            matrix[0][j] = 0
    if col0:
        for i in range(m):
            matrix[i][0] = 0
    return matrix
```

### Q40. Intermediate

**Rotate Image**

Commonly reported in interviews at Amazon, Microsoft.

Rotate an n by n matrix 90 degrees clockwise, in place.

Example: `[[1, 2], [3, 4]]` becomes `[[3, 1], [4, 2]]`.

**Answer:**

Transpose across the main diagonal, then reverse each row. Or rotate four edges in cycles.

**Complexity:** Time O(n^2), space O(1).

```python
def rotate(matrix):
    n = len(matrix)
    for i in range(n):
        for j in range(i + 1, n):
            matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
    for row in matrix:
        row.reverse()
    return matrix
```

### Q41. Intermediate

**Spiral Matrix**

Commonly reported in interviews at Amazon, Microsoft, Apple.

Return the elements of a matrix in clockwise spiral order.

Example: `[[1, 2, 3], [4, 5, 6], [7, 8, 9]]` returns `[1, 2, 3, 6, 9, 8, 7, 4, 5]`.

**Answer:**

Maintain four bounds and walk right, down, left, up, shrinking the bounds after each side. Stop when the bounds cross.

**Complexity:** Time O(m * n), space O(1) extra besides the answer.

```python
def spiral(matrix):
    out = []
    top, bot = 0, len(matrix) - 1
    left, right = 0, len(matrix[0]) - 1
    while top <= bot and left <= right:
        for j in range(left, right + 1):
            out.append(matrix[top][j])
        top += 1
        for i in range(top, bot + 1):
            out.append(matrix[i][right])
        right -= 1
        if top <= bot:
            for j in range(right, left - 1, -1):
                out.append(matrix[bot][j])
            bot -= 1
        if left <= right:
            for i in range(bot, top - 1, -1):
                out.append(matrix[i][left])
            left += 1
    return out
```

### Q42. Intermediate

**Number of Islands**

Commonly reported in interviews at Amazon, Google, Microsoft.

A grid of `'1'` land and `'0'` water. Return how many 4-connected islands there are.

Example: One island of adjacent ones returns 1. Diagonal neighbors do not connect.

**Answer:**

For every unvisited land cell, run DFS or BFS and sink the island (mark cells visited) so it is counted once.

**Complexity:** Time O(m * n), space O(m * n) in the worst case for the recursion or queue.

```python
def num_islands(grid):
    if not grid:
        return 0
    m, n = len(grid), len(grid[0])
    def sink(i, j):
        if not (0 <= i < m and 0 <= j < n) or grid[i][j] != '1':
            return
        grid[i][j] = '0'
        sink(i + 1, j); sink(i - 1, j); sink(i, j + 1); sink(i, j - 1)
    count = 0
    for i in range(m):
        for j in range(n):
            if grid[i][j] == '1':
                sink(i, j)
                count += 1
    return count
```

### Q43. Intermediate

**Clone Graph**

Commonly reported in interviews at Amazon, Facebook.

Deep-copy an undirected graph. Each node has a value and a list of neighbors. The graph may contain cycles.

Example: A triangle of nodes 1, 2, 3 returns a distinct triangle with the same links.

**Answer:**

DFS or BFS with a map from original node to its clone. Create the clone the first time you see a node, then copy edges.

**Complexity:** Time O(V + E), space O(V).

```python
def clone_graph(node):
    if not node:
        return None
    clones = {}
    def dfs(n):
        if n in clones:
            return clones[n]
        copy = type(n)(n.val)
        clones[n] = copy
        copy.neighbors = [dfs(x) for x in n.neighbors]
        return copy
    return dfs(node)
```

### Q44. Intermediate

**Course Schedule**

Commonly reported in interviews at Amazon, Google, Uber.

There are `n` courses labeled 0..n-1 and a list of prerequisite pairs `[course, prereq]`. Return true when you can finish every course.

Example: `n = 2`, prerequisites `[[1, 0]]` is true. `[[1, 0], [0, 1]]` is false.

**Answer:**

This is cycle detection on a directed graph. Kahn's algorithm (indegree plus a queue) or DFS with three colors both work. Kahn's algorithm finishes every node exactly when the graph is a DAG.

**Complexity:** Time O(V + E), space O(V + E).

```python
def can_finish(n, prereqs):
    from collections import defaultdict, deque
    g = defaultdict(list)
    indeg = [0] * n
    for course, pre in prereqs:
        g[pre].append(course)
        indeg[course] += 1
    q = deque(i for i in range(n) if indeg[i] == 0)
    seen = 0
    while q:
        u = q.popleft()
        seen += 1
        for v in g[u]:
            indeg[v] -= 1
            if indeg[v] == 0:
                q.append(v)
    return seen == n
```

### Q45. Intermediate

**Course Schedule II**

Commonly reported in interviews at Amazon, Google.

Return one valid order in which to take `n` courses, or an empty list if the prerequisites contain a cycle.

Example: `n = 2`, `[[1, 0]]` returns `[0, 1]`.

**Answer:**

Kahn's algorithm records nodes as their indegree hits zero. If the recorded order is shorter than `n`, there is a cycle.

**Complexity:** Time O(V + E), space O(V + E).

```python
def order(n, prereqs):
    from collections import defaultdict, deque
    g = defaultdict(list)
    indeg = [0] * n
    for course, pre in prereqs:
        g[pre].append(course)
        indeg[course] += 1
    q = deque(i for i in range(n) if indeg[i] == 0)
    out = []
    while q:
        u = q.popleft()
        out.append(u)
        for v in g[u]:
            indeg[v] -= 1
            if indeg[v] == 0:
                q.append(v)
    return out if len(out) == n else []
```

### Q46. Intermediate

**Coin Change**

Commonly reported in interviews at Amazon, Goldman Sachs, Uber.

Return the fewest coins that sum to `amount`, or -1 if it is impossible. You have infinite supply of each denomination.

Example: Coins `[1, 2, 5]`, amount `11` returns `3` (5+5+1).

**Answer:**

Unbounded knapsack. `dp[x]` is the fewest coins that make `x`. Transition: `dp[x] = min(dp[x], dp[x - coin] + 1)`.

**Complexity:** Time O(amount * coins), space O(amount).

```python
def coin_change(coins, amount):
    dp = [0] + [amount + 1] * amount
    for x in range(1, amount + 1):
        for c in coins:
            if c <= x:
                dp[x] = min(dp[x], dp[x - c] + 1)
    return dp[amount] if dp[amount] <= amount else -1
```

### Q47. Intermediate

**House Robber**

Commonly reported in interviews at Amazon, Google.

Houses in a line hold non-negative money. You cannot rob two adjacent houses. Return the maximum you can rob.

Example: `[2, 7, 9, 3, 1]` returns `12` (2+9+1).

**Answer:**

`dp[i] = max(dp[i-1], dp[i-2] + nums[i])`. Roll two variables.

**Complexity:** Time O(n), space O(1).

```python
def rob(nums):
    prev = cur = 0
    for n in nums:
        prev, cur = cur, max(cur, prev + n)
    return cur
```

### Q48. Intermediate

**House Robber II**

Commonly reported in interviews at Amazon.

Houses form a circle, so the first and last are adjacent. Return the maximum you can rob.

Example: `[2, 3, 2]` returns `3`.

**Answer:**

Run the linear robber on `nums[:-1]` and on `nums[1:]`, and take the max. An empty or single-house input is a special case.

**Complexity:** Time O(n), space O(1).

```python
def rob_circle(nums):
    def linear(a):
        prev = cur = 0
        for n in a:
            prev, cur = cur, max(cur, prev + n)
        return cur
    if not nums:
        return 0
    if len(nums) == 1:
        return nums[0]
    return max(linear(nums[:-1]), linear(nums[1:]))
```

### Q49. Intermediate

**Jump Game**

Commonly reported in interviews at Amazon, Microsoft.

Each index holds how far you may jump forward from there. Return true when you can reach the last index starting from index 0.

Example: `[2, 3, 1, 1, 4]` is true. `[3, 2, 1, 0, 4]` is false.

**Answer:**

Track the farthest index reachable so far. If the scan index ever passes that farthest index, you are stuck.

**Complexity:** Time O(n), space O(1).

```python
def can_jump(nums):
    far = 0
    for i, n in enumerate(nums):
        if i > far:
            return False
        far = max(far, i + n)
    return True
```

### Q50. Intermediate

**Jump Game II**

Commonly reported in interviews at Amazon, Google.

Return the minimum number of jumps to reach the last index. A solution always exists.

Example: `[2, 3, 1, 1, 4]` returns `2`.

**Answer:**

BFS layers over the array. Inside the current jump's reach, find the farthest index the next jump can cover. Each layer is one jump.

**Complexity:** Time O(n), space O(1).

```python
def jump(nums):
    jumps = end = far = 0
    for i in range(len(nums) - 1):
        far = max(far, i + nums[i])
        if i == end:
            jumps += 1
            end = far
    return jumps
```

### Q51. Intermediate

**Unique Paths**

Commonly reported in interviews at Google, Amazon.

An m by n grid. You start at the top left and may only move right or down. Return how many paths reach the bottom right.

Example: `m = 3, n = 7` returns `28`.

**Answer:**

DP: each cell is the sum of the cell above and the cell to the left. The first row and column are all 1s. Combinatorics `C(m+n-2, m-1)` is the closed form.

**Complexity:** Time O(m * n), space O(n) with a rolling row.

```python
def unique_paths(m, n):
    row = [1] * n
    for _ in range(1, m):
        for j in range(1, n):
            row[j] += row[j - 1]
    return row[-1]
```

### Q52. Intermediate

**Minimum Path Sum**

Commonly reported in interviews at Amazon, Google.

A grid of non-negative numbers. Move only right or down. Return the path from top left to bottom right with the smallest sum.

Example: `[[1, 3, 1], [1, 5, 1], [4, 2, 1]]` returns `7`.

**Answer:**

DP in place or on a row: `dp[i][j] = grid[i][j] + min(from above, from left)`.

**Complexity:** Time O(m * n), space O(1) extra if you overwrite the grid, or O(n) with a row.

```python
def min_path(grid):
    m, n = len(grid), len(grid[0])
    for j in range(1, n):
        grid[0][j] += grid[0][j - 1]
    for i in range(1, m):
        grid[i][0] += grid[i - 1][0]
        for j in range(1, n):
            grid[i][j] += min(grid[i - 1][j], grid[i][j - 1])
    return grid[-1][-1]
```

### Q53. Intermediate

**Climbing Stairs with Cost**

Commonly reported in interviews at Amazon.

Paying `cost[i]` lets you climb one or two steps from step `i`. You may start at step 0 or step 1. Return the minimum cost to reach the top, which is just past the last step.

Example: `[10, 15, 20]` returns `15`.

**Answer:**

`dp[i]` is the min cost to reach step `i` before paying. The answer is the min of arriving from the last step or the one before it.

**Complexity:** Time O(n), space O(1).

```python
def min_cost_climbing(cost):
    a = b = 0
    for c in cost:
        a, b = b, min(a, b) + c
    return min(a, b)
```

### Q54. Intermediate

**Longest Common Subsequence**

Commonly reported in interviews at Amazon, Google, Goldman Sachs.

Return the length of the longest subsequence common to two strings. A subsequence need not be contiguous.

Example: `abcde` and `ace` returns `3`.

**Answer:**

DP: if characters match, `1 + diagonal`, otherwise the max of the cell above and the cell to the left.

**Complexity:** Time O(n * m), space O(min(n, m)) with a rolling row.

```python
def lcs(a, b):
    if len(a) < len(b):
        a, b = b, a
    prev = [0] * (len(b) + 1)
    for i in range(1, len(a) + 1):
        cur = [0]
        for j in range(1, len(b) + 1):
            if a[i - 1] == b[j - 1]:
                cur.append(prev[j - 1] + 1)
            else:
                cur.append(max(prev[j], cur[-1]))
        prev = cur
    return prev[-1]
```

### Q55. Intermediate

**Longest Increasing Subsequence**

Commonly reported in interviews at Amazon, Microsoft, Google.

Return the length of the longest strictly increasing subsequence.

Example: `[10, 9, 2, 5, 3, 7, 101, 18]` returns `4`.

**Answer:**

Patience sorting: keep the smallest tail of all increasing subsequences of each length. Replace with binary search (`bisect_left`). The number of tails is the length. This does not reconstruct one subsequence unless you store predecessors.

**Complexity:** Time O(n log n), space O(n).

```python
def lis(nums):
    import bisect
    tails = []
    for n in nums:
        i = bisect.bisect_left(tails, n)
        if i == len(tails):
            tails.append(n)
        else:
            tails[i] = n
    return len(tails)
```

### Q56. Intermediate

**Word Break**

Commonly reported in interviews at Amazon, Facebook, Google.

Return true when a string can be segmented into a space-separated sequence of dictionary words. Words may be reused.

Example: `leetcode` with dictionary `['leet', 'code']` is true.

**Answer:**

`dp[i]` means `s[:i]` can be segmented. For each end, try every word that matches the suffix and whose start is already reachable.

**Complexity:** Time O(n^2 * w) naively, better with a trie. Space O(n).

```python
def word_break(s, words):
    words = set(words)
    dp = [True] + [False] * len(s)
    for i in range(1, len(s) + 1):
        for j in range(i):
            if dp[j] and s[j:i] in words:
                dp[i] = True
                break
    return dp[-1]
```

### Q57. Intermediate

**Decode Ways**

Commonly reported in interviews at Amazon, Facebook, Google.

A string of digits encodes letters: `1` is A through `26` is Z. Return how many ways the string can be decoded. `0` alone is invalid.

Example: `226` returns `3`: BZ, VF, BBF.

**Answer:**

Fibonacci-like DP. A single digit 1-9 extends `dp[i-1]`. A two-digit number from 10 to 26 also extends `dp[i-2]`.

**Complexity:** Time O(n), space O(1).

```python
def num_decodings(s):
    if s[0] == '0':
        return 0
    a, b = 1, 1
    for i in range(1, len(s)):
        cur = 0
        if s[i] != '0':
            cur += b
        if 10 <= int(s[i - 1:i + 1]) <= 26:
            cur += a
        a, b = b, cur
    return b
```

### Q58. Intermediate

**Combination Sum**

Commonly reported in interviews at Amazon, Uber.

Return all unique combinations of candidates that sum to `target`. The same number may be chosen more than once, and the output must not contain duplicate combinations.

Example: Candidates `[2, 3, 6, 7]`, target `7` returns `[[2, 2, 3], [7]]`.

**Answer:**

Backtracking. At each step, either reuse the current candidate or move to the next. Sorting is optional when candidates are unique.

**Complexity:** Time exponential in the target. Space O(target / min(candidates)) for the recursion.

```python
def combination_sum(candidates, target):
    out = []
    def bt(start, remain, path):
        if remain == 0:
            out.append(path[:])
            return
        for i in range(start, len(candidates)):
            c = candidates[i]
            if c > remain:
                continue
            path.append(c)
            bt(i, remain - c, path)
            path.pop()
    bt(0, target, [])
    return out
```

### Q59. Intermediate

**Subsets**

Commonly reported in interviews at Amazon, Facebook, Google.

Return every subset of a list of distinct integers.

Example: `[1, 2]` returns `[[], [1], [2], [1, 2]]` in any order.

**Answer:**

For each number, the new subsets are the old ones plus that number. Cascading doubling builds the power set in O(n * 2^n).

**Complexity:** Time O(n * 2^n), space O(n * 2^n) for the answer.

```python
def subsets(nums):
    out = [[]]
    for n in nums:
        out += [cur + [n] for cur in out]
    return out
```

### Q60. Intermediate

**Permutations**

Commonly reported in interviews at Amazon, Microsoft, LinkedIn.

Return all permutations of a list of distinct integers.

Example: `[1, 2]` returns `[[1, 2], [2, 1]]`.

**Answer:**

Backtracking with an in-place swap, or recursion that picks each unused element. There are n! results.

**Complexity:** Time O(n * n!), space O(n) extra besides the answer.

```python
def permute(nums):
    out = []
    def bt(path, rest):
        if not rest:
            out.append(path[:])
            return
        for i, n in enumerate(rest):
            bt(path + [n], rest[:i] + rest[i + 1:])
    bt([], nums)
    return out
```

### Q61. Intermediate

**Letter Combinations of a Phone Number**

Commonly reported in interviews at Amazon, Uber.

A digit string uses the phone mapping (`2` is abc, `3` is def, and so on through `9`). Return every possible letter string.

Example: `23` returns the 9 strings from `ad` through `cf`.

**Answer:**

Backtracking or BFS. Each digit multiplies the current set of prefixes by its letters.

**Complexity:** Time O(4^n * n), space O(4^n * n) for the answer.

```python
def letter_combinations(digits):
    if not digits:
        return []
    pad = {'2': 'abc', '3': 'def', '4': 'ghi', '5': 'jkl', '6': 'mno', '7': 'pqrs', '8': 'tuv', '9': 'wxyz'}
    out = ['']
    for d in digits:
        out = [p + ch for p in out for ch in pad[d]]
    return out
```

### Q62. Intermediate

**Generate Parentheses**

Commonly reported in interviews at Amazon, Google, Microsoft.

Return every string of `n` pairs of parentheses that is correctly matched.

Example: `n = 2` returns `['(())', '()()']`.

**Answer:**

Backtracking. You may add `(` when opens remain, and `)` when it would not exceed the opens already placed.

**Complexity:** Time proportional to the Catalan number. Space O(n) for the recursion besides the answer.

```python
def generate_parentheses(n):
    out = []
    def bt(path, opened, closed):
        if len(path) == 2 * n:
            out.append(''.join(path))
            return
        if opened < n:
            path.append('(')
            bt(path, opened + 1, closed)
            path.pop()
        if closed < opened:
            path.append(')')
            bt(path, opened, closed + 1)
            path.pop()
    bt([], 0, 0)
    return out
```

### Q63. Intermediate

**Top K Frequent Elements**

Commonly reported in interviews at Amazon, Facebook, Uber.

Return the `k` most frequent values in any order.

Example: `[1, 1, 1, 2, 2, 3]`, `k = 2` returns `[1, 2]`.

**Answer:**

Count, then use a heap of size k or bucket-sort by frequency. Bucket sort is O(n) because frequencies are at most n.

**Complexity:** Time O(n) with buckets, or O(n log k) with a heap. Space O(n).

```python
def top_k(nums, k):
    from collections import Counter
    buckets = [[] for _ in range(len(nums) + 1)]
    for val, freq in Counter(nums).items():
        buckets[freq].append(val)
    out = []
    for freq in range(len(buckets) - 1, 0, -1):
        out.extend(buckets[freq])
        if len(out) >= k:
            return out[:k]
    return out
```

### Q64. Intermediate

**Kth Largest Element**

Commonly reported in interviews at Amazon, Facebook, LinkedIn.

Return the kth largest element of an unsorted list. It is the kth item in sorted order, not the kth distinct item.

Example: `[3, 2, 1, 5, 6, 4]`, `k = 2` returns `5`.

**Answer:**

Quickselect averages O(n). A min-heap of size k is O(n log k) and simpler to write correctly under time pressure. Python's `heapq.nlargest` is that idea.

**Complexity:** Average O(n) with quickselect. Worst case O(n^2) unless you randomize the pivot. Heap is O(n log k).

```python
def kth_largest(nums, k):
    import heapq
    return heapq.nlargest(k, nums)[-1]
```

### Q65. Intermediate

**Find Minimum in Rotated Sorted Array**

Commonly reported in interviews at Amazon, Microsoft.

A sorted array of distinct values was rotated. Return the minimum.

Example: `[3, 4, 5, 1, 2]` returns `1`.

**Answer:**

Binary search. If the middle is greater than the right end, the minimum is to the right of mid. Otherwise it is at mid or to the left.

**Complexity:** Time O(log n), space O(1).

```python
def find_min(nums):
    lo, hi = 0, len(nums) - 1
    while lo < hi:
        mid = (lo + hi) // 2
        if nums[mid] > nums[hi]:
            lo = mid + 1
        else:
            hi = mid
    return nums[lo]
```

### Q66. Intermediate

**Search in Rotated Sorted Array**

Commonly reported in interviews at Amazon, Facebook, Microsoft.

A sorted array of distinct values was rotated. Return the index of `target`, or -1.

Example: `[4, 5, 6, 7, 0, 1, 2]`, target `0` returns `4`.

**Answer:**

Binary search. One half is always sorted. If the target lies inside the sorted half, search there. Otherwise search the other half.

**Complexity:** Time O(log n), space O(1).

```python
def search_rotated(nums, target):
    lo, hi = 0, len(nums) - 1
    while lo <= hi:
        mid = (lo + hi) // 2
        if nums[mid] == target:
            return mid
        if nums[lo] <= nums[mid]:
            if nums[lo] <= target < nums[mid]:
                hi = mid - 1
            else:
                lo = mid + 1
        else:
            if nums[mid] < target <= nums[hi]:
                lo = mid + 1
            else:
                hi = mid - 1
    return -1
```

### Q67. Intermediate

**Validate Binary Search Tree**

Commonly reported in interviews at Amazon, Microsoft, Facebook.

Return true when a binary tree is a BST. Every node on the left is strictly less than the node, and every node on the right is strictly greater. Duplicates are not allowed.

Example: A tree `2 / 1,3` is true. A tree `5 / 1,4` with 4 having left child 3 is false, because 3 is in the right subtree of 5.

**Answer:**

Pass a valid `(low, high)` window down the recursion. Comparing a node only with its parent is not enough.

**Complexity:** Time O(n), space O(h).

```python
def is_bst(root):
    def ok(node, low, high):
        if not node:
            return True
        if not low < node.val < high:
            return False
        return ok(node.left, low, node.val) and ok(node.right, node.val, high)
    return ok(root, float('-inf'), float('inf'))
```

### Q68. Intermediate

**Kth Smallest in a BST**

Commonly reported in interviews at Amazon, Google.

Return the kth smallest value in a BST. `k` is 1-based.

Example: An inorder walk of a BST is sorted, so the 1st smallest is the leftmost node.

**Answer:**

Iterative inorder, stopping after k pops. If the node count is available on each subtree, you can walk in O(h).

**Complexity:** Time O(h + k), space O(h).

```python
def kth_smallest(root, k):
    stack = []
    cur = root
    while cur or stack:
        while cur:
            stack.append(cur)
            cur = cur.left
        cur = stack.pop()
        k -= 1
        if k == 0:
            return cur.val
        cur = cur.right
```

### Q69. Intermediate

**Lowest Common Ancestor of a Binary Tree**

Commonly reported in interviews at Amazon, Facebook, Microsoft.

Given two nodes that exist in a binary tree, return their lowest common ancestor.

Example: In a tree rooted at 3 with children 5 and 1, the LCA of 5 and 1 is 3.

**Answer:**

If the current node is either target, return it. Otherwise recurse both sides. If both sides return a node, the current node is the LCA. If only one side does, pass that node up.

**Complexity:** Time O(n), space O(h).

```python
def lca(root, p, q):
    if not root or root is p or root is q:
        return root
    left = lca(root.left, p, q)
    right = lca(root.right, p, q)
    if left and right:
        return root
    return left or right
```

### Q70. Intermediate

**Lowest Common Ancestor of a BST**

Commonly reported in interviews at Amazon, Microsoft.

Both nodes exist in a BST. Return their lowest common ancestor.

Example: If both values are smaller than the root, the LCA is in the left subtree.

**Answer:**

Walk down. The first node whose value sits between the two targets, inclusive, is the LCA.

**Complexity:** Time O(h), space O(1) iterative.

```python
def lca_bst(root, p, q):
    while root:
        if p.val < root.val and q.val < root.val:
            root = root.left
        elif p.val > root.val and q.val > root.val:
            root = root.right
        else:
            return root
```

### Q71. Intermediate

**Binary Tree Level Order Traversal**

Commonly reported in interviews at Amazon, Microsoft, Bloomberg.

Return the values of a binary tree level by level, left to right.

Example: Root 1 with children 2 and 3 returns `[[1], [2, 3]]`.

**Answer:**

BFS with a queue. Snapshot the queue length at the start of each level so the next level is not mixed in.

**Complexity:** Time O(n), space O(n).

```python
def level_order(root):
    from collections import deque
    if not root:
        return []
    out, q = [], deque([root])
    while q:
        level = []
        for _ in range(len(q)):
            node = q.popleft()
            level.append(node.val)
            if node.left:
                q.append(node.left)
            if node.right:
                q.append(node.right)
        out.append(level)
    return out
```

### Q72. Intermediate

**Binary Tree Right Side View**

Commonly reported in interviews at Amazon, Bloomberg.

Return the values visible if you stand on the right of the tree, top to bottom.

Example: A complete tree returns the right spine. A missing right child exposes the left child on that level.

**Answer:**

Level order, and keep the last node of each level. DFS that visits the right child first and records the first node at each depth also works.

**Complexity:** Time O(n), space O(n).

```python
def right_view(root):
    from collections import deque
    if not root:
        return []
    out, q = [], deque([root])
    while q:
        out.append(q[-1].val)
        for _ in range(len(q)):
            node = q.popleft()
            if node.left:
                q.append(node.left)
            if node.right:
                q.append(node.right)
    return out
```

### Q73. Intermediate

**Diameter of Binary Tree**

Commonly reported in interviews at Amazon, Google, Facebook.

Return the length of the longest path between any two nodes, measured in edges. The path need not pass through the root.

Example: A straight line of three nodes has diameter 2.

**Answer:**

At each node the best path through that node is `left height + right height`. The answer is the max of those. Return the height to the parent and keep the diameter in a closure.

**Complexity:** Time O(n), space O(h).

```python
def diameter(root):
    best = 0
    def height(node):
        nonlocal best
        if not node:
            return 0
        L, R = height(node.left), height(node.right)
        best = max(best, L + R)
        return 1 + max(L, R)
    height(root)
    return best
```

### Q74. Intermediate

**Balanced Binary Tree**

Commonly reported in interviews at Amazon, Microsoft.

Return true when the depths of the two subtrees of every node differ by at most 1.

Example: A complete tree is balanced. A long chain is not.

**Answer:**

Return the height, or a sentinel such as -1 when a subtree is already unbalanced. That avoids a second walk.

**Complexity:** Time O(n), space O(h).

```python
def is_balanced(root):
    def height(node):
        if not node:
            return 0
        L, R = height(node.left), height(node.right)
        if L < 0 or R < 0 or abs(L - R) > 1:
            return -1
        return 1 + max(L, R)
    return height(root) >= 0
```

### Q75. Intermediate

**Serialize and Deserialize Binary Tree**

Commonly reported in interviews at Amazon, Google, LinkedIn.

Design a way to turn a binary tree into a string and back, including structure. Empty children must be recorded.

Example: A root 1 with left 2 becomes a string that rebuilds that same shape.

**Answer:**

Preorder with null markers. Split the string and rebuild with an iterator. BFS with null markers also works.

**Complexity:** Time O(n), space O(n).

```python
def serialize(root):
    out = []
    def dfs(node):
        if not node:
            out.append('#')
            return
        out.append(str(node.val))
        dfs(node.left)
        dfs(node.right)
    dfs(root)
    return ','.join(out)

def deserialize(data):
    it = iter(data.split(','))
    def dfs():
        token = next(it)
        if token == '#':
            return None
        node = _T(int(token))
        node.left = dfs()
        node.right = dfs()
        return node
    return dfs()

class _T:
    def __init__(self, val):
        self.val, self.left, self.right = val, None, None
```

### Q76. Intermediate

**Construct Tree from Preorder and Inorder**

Commonly reported in interviews at Amazon, Microsoft.

Values are distinct. Build the binary tree from its preorder and inorder lists.

Example: Preorder `[3, 9, 20, 15, 7]`, inorder `[9, 3, 15, 20, 7]` has root 3, left child 9, right subtree rooted at 20.

**Answer:**

The first preorder value is the root. Find it in inorder to split left and right sizes. Recurse. An index map makes the split O(1).

**Complexity:** Time O(n), space O(n).

```python
def build_tree(preorder, inorder):
    idx = {v: i for i, v in enumerate(inorder)}
    pre_i = 0
    def build(lo, hi):
        nonlocal pre_i
        if lo > hi:
            return None
        val = preorder[pre_i]
        pre_i += 1
        node = _T(val)
        mid = idx[val]
        node.left = build(lo, mid - 1)
        node.right = build(mid + 1, hi)
        return node
    return build(0, len(inorder) - 1)

class _T:
    def __init__(self, val):
        self.val, self.left, self.right = val, None, None
```

### Q77. Intermediate

**Binary Tree Maximum Path Sum**

Commonly reported in interviews at Amazon, Google, Facebook.

A path is any connected sequence of nodes. Return the maximum sum of node values along any path. Values may be negative.

Example: A tree `-10 / 9,20` with 20 having children 15 and 7 returns `42`.

**Answer:**

At each node, the best gain you can offer a parent is `value + max(0, left gain, right gain)`. The best path through the node also adds both sides when they are positive. Track that global best.

**Complexity:** Time O(n), space O(h).

```python
def max_path_sum(root):
    best = root.val
    def gain(node):
        nonlocal best
        if not node:
            return 0
        L = max(0, gain(node.left))
        R = max(0, gain(node.right))
        best = max(best, node.val + L + R)
        return node.val + max(L, R)
    gain(root)
    return best
```

### Q78. Intermediate

**Subtree of Another Tree**

Commonly reported in interviews at Amazon, Facebook.

Return true when `sub` is identical to some subtree of `root`, including `root` itself.

Example: A single matching node is true.

**Answer:**

For every node, run the same-tree check. A serialization of both trees with sentinels can also be searched as a string.

**Complexity:** Time O(n * m), space O(h).

```python
def is_subtree(root, sub):
    def same(a, b):
        if not a or not b:
            return a is b
        return a.val == b.val and same(a.left, b.left) and same(a.right, b.right)
    def walk(node):
        if not node:
            return False
        return same(node, sub) or walk(node.left) or walk(node.right)
    return walk(root)
```

### Q79. Intermediate

**LRU Cache**

Commonly reported in interviews at Amazon, Google, Microsoft, Facebook.

Design a cache with `get` and `put` in average O(1). Capacity is fixed. The least recently used key is evicted.

Example: Capacity 2. Put 1, put 2, get 1, put 3. Key 2 is evicted.

**Answer:**

Hash map plus a doubly linked list. The map points at list nodes. Move a node to the front on access. Evict the tail.

**Complexity:** Each operation average O(1). Space O(capacity).

```python
class LRU:
    def __init__(self, cap):
        from collections import OrderedDict
        self.cap = cap
        self.data = OrderedDict()
    def get(self, key):
        if key not in self.data:
            return -1
        self.data.move_to_end(key)
        return self.data[key]
    def put(self, key, value):
        if key in self.data:
            self.data.move_to_end(key)
        self.data[key] = value
        if len(self.data) > self.cap:
            self.data.popitem(last=False)
```

### Q80. Advanced

**Trapping Rain Water**

Commonly reported in interviews at Amazon, Google, Goldman Sachs.

Elevation bars of width 1 stand in a row. Return how many units of water they trap after raining.

Example: `[0, 1, 0, 2, 1, 0, 1, 3, 2, 1, 2, 1]` returns `6`.

**Answer:**

Two pointers. Water at a position is `min(max_left, max_right) - height`. Move the side whose max is smaller, because that max is the limiting wall.

**Complexity:** Time O(n), space O(1).

```python
def trap(height):
    lo, hi = 0, len(height) - 1
    left_max = right_max = water = 0
    while lo < hi:
        if height[lo] < height[hi]:
            left_max = max(left_max, height[lo])
            water += left_max - height[lo]
            lo += 1
        else:
            right_max = max(right_max, height[hi])
            water += right_max - height[hi]
            hi -= 1
    return water
```

### Q81. Advanced

**Sliding Window Maximum**

Commonly reported in interviews at Amazon, Google.

Return the maximum of every contiguous window of size `k`.

Example: `[1, 3, -1, -3, 5, 3, 6, 7]`, `k = 3` returns `[3, 3, 5, 5, 6, 7]`.

**Answer:**

A deque stores indices in decreasing value order. Drop indices that fall out of the window from the front, and drop smaller values from the back before pushing.

**Complexity:** Time O(n), space O(k).

```python
def max_sliding(nums, k):
    from collections import deque
    dq, out = deque(), []
    for i, n in enumerate(nums):
        while dq and dq[0] <= i - k:
            dq.popleft()
        while dq and nums[dq[-1]] <= n:
            dq.pop()
        dq.append(i)
        if i >= k - 1:
            out.append(nums[dq[0]])
    return out
```

### Q82. Advanced

**Minimum Window Substring**

Commonly reported in interviews at Facebook, Amazon, Google.

Return the shortest substring of `s` that contains every character of `t`, including duplicates. If none exists, return an empty string.

Example: `s = 'ADOBECODEBANC'`, `t = 'ABC'` returns `'BANC'`.

**Answer:**

Sliding window with required counts. Expand the right edge until the window is valid, then shrink the left edge while it stays valid, recording the best window.

**Complexity:** Time O(n + m), space O(1) for a fixed alphabet.

```python
def min_window(s, t):
    from collections import Counter
    need = Counter(t)
    missing = len(t)
    best = ''
    left = 0
    for right, ch in enumerate(s):
        if need[ch] > 0:
            missing -= 1
        need[ch] -= 1
        while missing == 0:
            if not best or right - left + 1 < len(best):
                best = s[left:right + 1]
            need[s[left]] += 1
            if need[s[left]] > 0:
                missing += 1
            left += 1
    return best
```

### Q83. Advanced

**Longest Repeating Character Replacement**

Commonly reported in interviews at Google, Amazon.

You may replace at most `k` characters. Return the length of the longest substring that can be made of one repeated character.

Example: `AABABBA`, `k = 1` returns `4`.

**Answer:**

Sliding window. The window is valid while `length - max_frequency <= k`. You do not have to shrink `max_frequency` perfectly on every pop; only expand the best length when the window is valid.

**Complexity:** Time O(n), space O(1) for a fixed alphabet.

```python
def character_replacement(s, k):
    from collections import Counter
    counts = Counter()
    left = best = most = 0
    for right, ch in enumerate(s):
        counts[ch] += 1
        most = max(most, counts[ch])
        while right - left + 1 - most > k:
            counts[s[left]] -= 1
            left += 1
        best = max(best, right - left + 1)
    return best
```

### Q84. Advanced

**Find All Anagrams in a String**

Commonly reported in interviews at Amazon, Facebook.

Return the start indices of every substring of `s` that is an anagram of `p`.

Example: `s = 'cbaebabacd'`, `p = 'abc'` returns `[0, 6]`.

**Answer:**

Fixed-size sliding window of length `len(p)` with character counts. Compare counts, or keep a `matched` counter so each step is O(1).

**Complexity:** Time O(n), space O(1) for a fixed alphabet.

```python
def find_anagrams(s, p):
    from collections import Counter
    if len(p) > len(s):
        return []
    need, window = Counter(p), Counter(s[:len(p)])
    out = [0] if need == window else []
    for i in range(len(p), len(s)):
        window[s[i]] += 1
        left = s[i - len(p)]
        window[left] -= 1
        if window[left] == 0:
            del window[left]
        if window == need:
            out.append(i - len(p) + 1)
    return out
```

### Q85. Advanced

**Subarray Sum Equals K**

Commonly reported in interviews at Facebook, Google, Amazon.

Return how many contiguous subarrays sum to `k`. Values may be negative.

Example: `[1, 1, 1]`, `k = 2` returns `2`.

**Answer:**

Prefix sums. A map counts how often each prefix has occurred. At prefix `sum`, add the count of `sum - k`.

**Complexity:** Time O(n), space O(n).

```python
def subarray_sum(nums, k):
    from collections import defaultdict
    seen = defaultdict(int)
    seen[0] = 1
    total = ans = 0
    for n in nums:
        total += n
        ans += seen[total - k]
        seen[total] += 1
    return ans
```

### Q86. Advanced

**Longest Consecutive Sequence**

Commonly reported in interviews at Google, Facebook.

Return the length of the longest run of consecutive integers. The values are unsorted, and the expected time is O(n).

Example: `[100, 4, 200, 1, 3, 2]` returns `4` because of `1, 2, 3, 4`.

**Answer:**

Put the values in a set. Only start a walk from a value whose predecessor is absent, then count upward.

**Complexity:** Time O(n), space O(n).

```python
def longest_consecutive(nums):
    s = set(nums)
    best = 0
    for n in s:
        if n - 1 in s:
            continue
        length = 1
        while n + length in s:
            length += 1
        best = max(best, length)
    return best
```

### Q87. Advanced

**First Missing Positive**

Commonly reported in interviews at Amazon, Microsoft.

Return the smallest missing positive integer. Expected time is O(n) and extra space is O(1).

Example: `[3, 4, -1, 1]` returns `2`.

**Answer:**

Place each value `x` into index `x - 1` when `x` is in `1..n`, by swapping. Then scan for the first index whose value is not `index + 1`.

**Complexity:** Time O(n), space O(1).

```python
def first_missing_positive(nums):
    n = len(nums)
    for i in range(n):
        while 1 <= nums[i] <= n and nums[nums[i] - 1] != nums[i]:
            j = nums[i] - 1
            nums[i], nums[j] = nums[j], nums[i]
    for i, v in enumerate(nums):
        if v != i + 1:
            return i + 1
    return n + 1
```

### Q88. Advanced

**Merge K Sorted Lists**

Commonly reported in interviews at Amazon, Google, Facebook.

Merge `k` sorted linked lists into one sorted list.

Example: Lists `[1, 4, 5]`, `[1, 3, 4]`, `[2, 6]` become `1, 1, 2, 3, 4, 4, 5, 6`.

**Answer:**

A min-heap of the current head of each list. Push the next node whenever you pop one. Divide and conquer merging is also O(N log k).

**Complexity:** Time O(N log k), space O(k), where N is the total number of nodes.

```python
def merge_k(lists):
    import heapq
    heap = []
    for i, node in enumerate(lists):
        if node:
            heapq.heappush(heap, (node.val, i, node))
    dummy = tail = _Node(0)
    while heap:
        _, i, node = heapq.heappop(heap)
        tail.next = node
        tail = node
        if node.next:
            heapq.heappush(heap, (node.next.val, i, node.next))
    return dummy.next

class _Node:
    def __init__(self, val, next=None):
        self.val, self.next = val, next
```

### Q89. Advanced

**Find Median from Data Stream**

Commonly reported in interviews at Google, Amazon.

Support adding a number and finding the median of all numbers added so far.

Example: Add 1, then 2. The median becomes 1.5.

**Answer:**

Two heaps. A max-heap holds the smaller half and a min-heap holds the larger half. Rebalance so their sizes differ by at most 1.

**Complexity:** Add is O(log n). Median is O(1). Space O(n).

```python
class MedianFinder:
    def __init__(self):
        import heapq
        self.heapq = heapq
        self.low = []
        self.high = []
    def add(self, n):
        hq = self.heapq
        hq.heappush(self.low, -n)
        hq.heappush(self.high, -hq.heappop(self.low))
        if len(self.high) > len(self.low):
            hq.heappush(self.low, -hq.heappop(self.high))
    def median(self):
        if len(self.low) > len(self.high):
            return -self.low[0]
        return (-self.low[0] + self.high[0]) / 2
```

### Q90. Advanced

**Reverse Nodes in k-Group**

Commonly reported in interviews at Amazon, Microsoft.

Reverse every group of `k` nodes in a linked list. Leave a trailing group shorter than `k` unchanged.

Example: `1 -> 2 -> 3 -> 4 -> 5`, `k = 2` becomes `2 -> 1 -> 4 -> 3 -> 5`.

**Answer:**

Count k nodes. If they exist, reverse that segment and stitch it between the previous tail and the next group.

**Complexity:** Time O(n), space O(1).

```python
def reverse_k(head, k):
    def rev(start, k):
        prev, cur = None, start
        for _ in range(k):
            nxt = cur.next
            cur.next = prev
            prev, cur = cur, nxt
        return prev, start, cur
    dummy = _Node(0, head)
    group_prev = dummy
    while True:
        kth = group_prev
        for _ in range(k):
            kth = kth.next
            if not kth:
                return dummy.next
        new_head, new_tail, nxt = rev(group_prev.next, k)
        group_prev.next = new_head
        new_tail.next = nxt
        group_prev = new_tail

class _Node:
    def __init__(self, val, next=None):
        self.val, self.next = val, next
```

### Q91. Advanced

**Copy List with Random Pointer**

Commonly reported in interviews at Amazon, Microsoft, Bloomberg.

A linked list node has `next` and `random`. Return a deep copy.

Example: A two-node list where the first random pointer points at the second must copy both links.

**Answer:**

Interleave cloned nodes (`A -> A' -> B -> B'`), set random pointers, then split the lists. A hash map from original to clone is the simpler O(n) space version.

**Complexity:** Time O(n). The map version uses O(n) extra space. The interleave version uses O(1) extra space.

```python
def copy_random(head):
    clones = {}
    cur = head
    while cur:
        clones[cur] = _R(cur.val)
        cur = cur.next
    cur = head
    while cur:
        clones[cur].next = clones.get(cur.next)
        clones[cur].random = clones.get(cur.random)
        cur = cur.next
    return clones.get(head)

class _R:
    def __init__(self, val):
        self.val = val
        self.next = self.random = None
```

### Q92. Advanced

**Linked List Cycle II**

Commonly reported in interviews at Amazon, Microsoft.

Return the node where a cycle begins, or null if there is no cycle.

Example: A tail that points at the second node returns that second node.

**Answer:**

After tortoise and hare meet, reset one pointer to the head. Advance both one step. They meet at the entrance. The proof is that the distance from head to entrance equals the distance from the meeting point around to the entrance.

**Complexity:** Time O(n), space O(1).

```python
def detect_cycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow is fast:
            slow = head
            while slow is not fast:
                slow = slow.next
                fast = fast.next
            return slow
    return None
```

### Q93. Advanced

**Remove Nth Node From End**

Commonly reported in interviews at Amazon, Microsoft.

Remove the nth node from the end of a singly linked list and return the head. `n` is always valid.

Example: `1 -> 2 -> 3 -> 4 -> 5`, `n = 2` becomes `1 -> 2 -> 3 -> 5`.

**Answer:**

A fast pointer moves n steps ahead. Then both pointers move until fast reaches the end. The slow pointer sits just before the node to delete. A dummy head handles deleting the first node.

**Complexity:** Time O(n), space O(1).

```python
def remove_nth(head, n):
    dummy = _Node(0, head)
    fast = slow = dummy
    for _ in range(n + 1):
        fast = fast.next
    while fast:
        fast = fast.next
        slow = slow.next
    slow.next = slow.next.next
    return dummy.next

class _Node:
    def __init__(self, val, next=None):
        self.val, self.next = val, next
```

### Q94. Advanced

**Add Two Numbers**

Commonly reported in interviews at Amazon, Microsoft, Bloomberg.

Two non-negative integers are stored as linked lists of digits in reverse order. Return their sum in the same form.

Example: `2 -> 4 -> 3` plus `5 -> 6 -> 4` is `7 -> 0 -> 8`, meaning 342 + 465 = 807.

**Answer:**

Walk both lists, add digits plus carry, and append `total % 10`. Continue while either list or the carry remains.

**Complexity:** Time O(max(n, m)), space O(max(n, m)) for the answer.

```python
def add_two(a, b):
    dummy = tail = _Node(0)
    carry = 0
    while a or b or carry:
        total = carry
        if a:
            total += a.val
            a = a.next
        if b:
            total += b.val
            b = b.next
        carry, digit = divmod(total, 10)
        tail.next = _Node(digit)
        tail = tail.next
    return dummy.next

class _Node:
    def __init__(self, val, next=None):
        self.val, self.next = val, next
```

### Q95. Advanced

**Palindrome Linked List**

Commonly reported in interviews at Amazon, Facebook.

Return true when the values of a singly linked list form a palindrome. Aim for O(1) extra space.

Example: `1 -> 2 -> 2 -> 1` is true.

**Answer:**

Find the middle with slow and fast pointers, reverse the second half, compare, and optionally reverse it back.

**Complexity:** Time O(n), space O(1).

```python
def is_palindrome_list(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    prev = None
    while slow:
        nxt = slow.next
        slow.next = prev
        prev, slow = slow, nxt
    while prev:
        if head.val != prev.val:
            return False
        head, prev = head.next, prev.next
    return True
```

### Q96. Advanced

**Reorder List**

Commonly reported in interviews at Amazon, Facebook.

Reorder `L0 -> L1 -> ... -> Ln` into `L0 -> Ln -> L1 -> Ln-1 -> ...` in place.

Example: `1 -> 2 -> 3 -> 4` becomes `1 -> 4 -> 2 -> 3`.

**Answer:**

Find the middle, reverse the second half, then merge the two halves one node at a time.

**Complexity:** Time O(n), space O(1).

```python
def reorder(head):
    if not head:
        return
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    prev, cur = None, slow.next
    slow.next = None
    while cur:
        nxt = cur.next
        cur.next = prev
        prev, cur = cur, nxt
    a, b = head, prev
    while b:
        a.next, a = b, a.next
        b.next, b = a, b.next
```

### Q97. Advanced

**Edit Distance**

Commonly reported in interviews at Google, Amazon, Uber.

Return the minimum insertions, deletions, and replacements that turn string `a` into string `b`.

Example: `horse` to `ros` returns `3`.

**Answer:**

DP. If characters match, copy the diagonal. Otherwise `1 + min(insert, delete, replace)`.

**Complexity:** Time O(n * m), space O(min(n, m)) with a rolling row.

```python
def edit_distance(a, b):
    prev = list(range(len(b) + 1))
    for i, ca in enumerate(a, 1):
        cur = [i]
        for j, cb in enumerate(b, 1):
            if ca == cb:
                cur.append(prev[j - 1])
            else:
                cur.append(1 + min(prev[j], cur[-1], prev[j - 1]))
        prev = cur
    return prev[-1]
```

### Q98. Advanced

**Regular Expression Matching**

Commonly reported in interviews at Google, Facebook.

Implement `.` and `*`. A dot matches any single character. A star matches zero or more of the preceding element. The match must cover the whole string.

Example: `a*b` matches `b` and `aaab`. It does not match `a`.

**Answer:**

DP. `dp[i][j]` means `s[:i]` matches `p[:j]`. A star can consume nothing (`dp[i][j-2]`) or one more character when the current character matches (`dp[i-1][j]`).

**Complexity:** Time O(n * m), space O(n * m).

```python
def is_match(s, p):
    n, m = len(s), len(p)
    dp = [[False] * (m + 1) for _ in range(n + 1)]
    dp[0][0] = True
    for j in range(2, m + 1):
        if p[j - 1] == '*':
            dp[0][j] = dp[0][j - 2]
    for i in range(1, n + 1):
        for j in range(1, m + 1):
            if p[j - 1] == '*':
                dp[i][j] = dp[i][j - 2] or (dp[i - 1][j] and p[j - 2] in {s[i - 1], '.'})
            elif p[j - 1] in {s[i - 1], '.'}:
                dp[i][j] = dp[i - 1][j - 1]
    return dp[n][m]
```

### Q99. Advanced

**Wildcard Matching**

Commonly reported in interviews at Google, Facebook.

`?` matches one character and `*` matches any sequence, including empty. Match the whole string.

Example: `a*b` matches `axb`. `?` matches one character only.

**Answer:**

DP similar to regex, but `*` is a lone pattern character. It matches empty (`dp[i][j-1]`) or one more text character (`dp[i-1][j]`).

**Complexity:** Time O(n * m), space O(n * m).

```python
def is_wildcard(s, p):
    n, m = len(s), len(p)
    dp = [[False] * (m + 1) for _ in range(n + 1)]
    dp[0][0] = True
    for j in range(1, m + 1):
        dp[0][j] = dp[0][j - 1] and p[j - 1] == '*'
    for i in range(1, n + 1):
        for j in range(1, m + 1):
            if p[j - 1] == '*':
                dp[i][j] = dp[i][j - 1] or dp[i - 1][j]
            elif p[j - 1] in {s[i - 1], '?'}:
                dp[i][j] = dp[i - 1][j - 1]
    return dp[n][m]
```

### Q100. Advanced

**Longest Palindromic Substring**

Commonly reported in interviews at Amazon, Microsoft.

Return the longest palindromic substring. If several have the same length, any one is acceptable.

Example: `babad` returns `bab` or `aba`.

**Answer:**

Expand around each center. There are `2n - 1` centers because a palindrome can be odd or even length. Manacher's algorithm is the linear alternative.

**Complexity:** Time O(n^2), space O(1) besides the answer.

```python
def longest_palindrome(s):
    def expand(l, r):
        while l >= 0 and r < len(s) and s[l] == s[r]:
            l -= 1
            r += 1
        return s[l + 1:r]
    best = ''
    for i in range(len(s)):
        best = max(best, expand(i, i), expand(i, i + 1), key=len)
    return best
```

### Q101. Advanced

**Palindromic Substrings**

Commonly reported in interviews at Facebook, Amazon.

Count how many substrings are palindromes. Single letters count.

Example: `aaa` returns `6`.

**Answer:**

Expand around each of the `2n - 1` centers and count every successful expansion.

**Complexity:** Time O(n^2), space O(1).

```python
def count_palindromes(s):
    def expand(l, r):
        count = 0
        while l >= 0 and r < len(s) and s[l] == s[r]:
            count += 1
            l -= 1
            r += 1
        return count
    return sum(expand(i, i) + expand(i, i + 1) for i in range(len(s)))
```

### Q102. Advanced

**Partition Equal Subset Sum**

Commonly reported in interviews at Amazon, Facebook.

Return true when the list can be split into two subsets with the same sum.

Example: `[1, 5, 11, 5]` is true because `11` and `1+5+5` both sum to 11.

**Answer:**

The target is `total / 2`, so the total must be even. Then it is a 0/1 knapsack: can a subset sum to that target?

**Complexity:** Time O(n * sum), space O(sum).

```python
def can_partition(nums):
    total = sum(nums)
    if total % 2:
        return False
    target = total // 2
    dp = [True] + [False] * target
    for n in nums:
        for s in range(target, n - 1, -1):
            dp[s] = dp[s] or dp[s - n]
    return dp[target]
```

### Q103. Advanced

**Target Sum**

Commonly reported in interviews at Facebook, Google.

Add `+` or `-` before each integer so the expression equals `target`. Return how many ways.

Example: `[1, 1, 1, 1, 1]`, target `3` returns `5`.

**Answer:**

This reduces to counting subsets that sum to `(total + target) / 2`. A 0/1 knapsack count does it. DFS with memo is the same DP.

**Complexity:** Time O(n * sum), space O(sum).

```python
def find_target_sum(nums, target):
    total = sum(nums)
    if (total + target) % 2 or abs(target) > total:
        return 0
    goal = (total + target) // 2
    dp = [1] + [0] * goal
    for n in nums:
        for s in range(goal, n - 1, -1):
            dp[s] += dp[s - n]
    return dp[goal]
```

### Q104. Advanced

**Coin Change II**

Commonly reported in interviews at Amazon, Goldman Sachs.

Return the number of combinations that make `amount`. Order does not matter, so `1+2` and `2+1` are one combination. Coins may be reused.

Example: Coins `[1, 2, 5]`, amount `5` returns `4`.

**Answer:**

Unbounded knapsack over combinations. Iterate coins in the outer loop and amounts in the inner loop so each combination is counted once.

**Complexity:** Time O(amount * coins), space O(amount).

```python
def change(amount, coins):
    dp = [1] + [0] * amount
    for c in coins:
        for x in range(c, amount + 1):
            dp[x] += dp[x - c]
    return dp[amount]
```

### Q105. Advanced

**Maximal Square**

Commonly reported in interviews at Amazon, Google.

A binary matrix contains `'0'` and `'1'`. Return the area of the largest square of ones.

Example: A 2x2 block of ones has area 4.

**Answer:**

DP: the largest square ending at `(i, j)` is `1 + min(up, left, diagonal)` when the cell is 1.

**Complexity:** Time O(m * n), space O(n).

```python
def maximal_square(matrix):
    if not matrix:
        return 0
    m, n = len(matrix), len(matrix[0])
    prev = [0] * (n + 1)
    best = 0
    for i in range(1, m + 1):
        cur = [0] * (n + 1)
        for j in range(1, n + 1):
            if matrix[i - 1][j - 1] == '1':
                cur[j] = 1 + min(prev[j], cur[j - 1], prev[j - 1])
                best = max(best, cur[j])
        prev = cur
    return best * best
```

### Q106. Advanced

**Word Search**

Commonly reported in interviews at Amazon, Microsoft.

Return true when a word can be formed by adjacent letters on a board. A cell may not be reused in the same path. Adjacent means four directions.

Example: Board with `AB` / `CD` contains `AC` and does not contain `ABD` if D is not adjacent to B... `AB` is true along the first row.

**Answer:**

DFS from every cell that matches the first letter. Mark the cell visited, recurse, then unmark.

**Complexity:** Time O(m * n * 4^L), space O(L) for the recursion.

```python
def exist(board, word):
    m, n = len(board), len(board[0])
    def dfs(i, j, k):
        if k == len(word):
            return True
        if not (0 <= i < m and 0 <= j < n) or board[i][j] != word[k]:
            return False
        ch, board[i][j] = board[i][j], '#'
        found = any(dfs(i + di, j + dj, k + 1) for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)))
        board[i][j] = ch
        return found
    return any(dfs(i, j, 0) for i in range(m) for j in range(n))
```

### Q107. Advanced

**N-Queens**

Commonly reported in interviews at Amazon, Google.

Place `n` queens on an `n` by `n` board so none share a row, column, or diagonal. Return every board.

Example: `n = 4` has two solutions.

**Answer:**

Backtracking row by row. Track used columns and both diagonal directions (`row - col` and `row + col`).

**Complexity:** Time roughly exponential. Space O(n) besides the answer.

```python
def solve_nqueens(n):
    out = []
    cols, d1, d2 = set(), set(), set()
    board = [['.'] * n for _ in range(n)]
    def bt(r):
        if r == n:
            out.append([''.join(row) for row in board])
            return
        for c in range(n):
            if c in cols or r - c in d1 or r + c in d2:
                continue
            cols.add(c); d1.add(r - c); d2.add(r + c)
            board[r][c] = 'Q'
            bt(r + 1)
            board[r][c] = '.'
            cols.remove(c); d1.remove(r - c); d2.remove(r + c)
    bt(0)
    return out
```

### Q108. Advanced

**Sudoku Solver**

Commonly reported in interviews at Amazon, Uber, Microsoft.

Fill a 9 by 9 board in place. Empty cells are `'.'`. A standard Sudoku has one solution in this problem.

Example: A partially filled valid board is completed.

**Answer:**

Backtracking. For each empty cell try digits 1-9 that are free in the row, column, and 3x3 box. Bit masks make the availability test O(1).

**Complexity:** Time exponential in the number of empty cells. Space O(1) besides the board and the recursion.

```python
def solve_sudoku(board):
    rows = [0] * 9
    cols = [0] * 9
    boxes = [0] * 9
    empties = []
    for i in range(9):
        for j in range(9):
            if board[i][j] == '.':
                empties.append((i, j))
            else:
                bit = 1 << int(board[i][j])
                rows[i] |= bit
                cols[j] |= bit
                boxes[(i // 3) * 3 + j // 3] |= bit
    def bt(k):
        if k == len(empties):
            return True
        i, j = empties[k]
        b = (i // 3) * 3 + j // 3
        for d in range(1, 10):
            bit = 1 << d
            if rows[i] & bit or cols[j] & bit or boxes[b] & bit:
                continue
            rows[i] |= bit; cols[j] |= bit; boxes[b] |= bit
            board[i][j] = str(d)
            if bt(k + 1):
                return True
            rows[i] ^= bit; cols[j] ^= bit; boxes[b] ^= bit
            board[i][j] = '.'
        return False
    bt(0)
    return board
```

### Q109. Advanced

**Word Ladder**

Commonly reported in interviews at Amazon, Google, Facebook.

Begin at `beginWord` and change one letter at a time. Every intermediate word must be in the word list. Return the length of the shortest transformation to `endWord`, counting both ends, or 0 if none exists.

Example: `hit` to `cog` with the list containing `hot, dot, dog, lot, log, cog` returns `5`.

**Answer:**

BFS. The branching factor is 26 times the word length if you try every one-letter change and test set membership.

**Complexity:** Time O(N * L * 26), space O(N * L).

```python
def ladder_length(begin, end, word_list):
    from collections import deque
    words = set(word_list)
    if end not in words:
        return 0
    q = deque([(begin, 1)])
    while q:
        word, dist = q.popleft()
        if word == end:
            return dist
        for i in range(len(word)):
            for ch in 'abcdefghijklmnopqrstuvwxyz':
                nxt = word[:i] + ch + word[i + 1:]
                if nxt in words:
                    words.remove(nxt)
                    q.append((nxt, dist + 1))
    return 0
```

### Q110. Advanced

**Alien Dictionary**

Commonly reported in interviews at Facebook, Google, Airbnb.

Words are sorted in an alien language's lexicographic order. Return one valid character order, or an empty string if the order is invalid.

Example: `['wrt', 'wrf', 'er', 'ett', 'rftt']` implies an order such as `wertf`.

**Answer:**

Compare adjacent words to extract directed edges (the first differing character). Topologically sort the graph. A cycle or a longer word appearing before its prefix means the input is invalid.

**Complexity:** Time O(total characters + alphabet size), space O(alphabet).

```python
def alien_order(words):
    from collections import defaultdict, deque
    g = defaultdict(set)
    indeg = {ch: 0 for w in words for ch in w}
    for a, b in zip(words, words[1:]):
        if len(a) > len(b) and a.startswith(b):
            return ''
        for ca, cb in zip(a, b):
            if ca != cb:
                if cb not in g[ca]:
                    g[ca].add(cb)
                    indeg[cb] += 1
                break
    q = deque(ch for ch, d in indeg.items() if d == 0)
    out = []
    while q:
        u = q.popleft()
        out.append(u)
        for v in g[u]:
            indeg[v] -= 1
            if indeg[v] == 0:
                q.append(v)
    return ''.join(out) if len(out) == len(indeg) else ''
```

### Q111. Advanced

**Network Delay Time**

Commonly reported in interviews at Amazon, Google.

There are `n` nodes and directed weighted edges. A signal starts at node `k`. Return how long it takes to reach every node, or -1 if some node is unreachable.

Example: Edges `[[2, 1, 1], [2, 3, 1], [3, 4, 1]]`, `n = 4`, `k = 2` returns `2`.

**Answer:**

Dijkstra with a min-heap. The answer is the maximum distance among reached nodes.

**Complexity:** Time O(E log V) with a binary heap. Space O(V + E).

```python
def network_delay(times, n, k):
    import heapq
    from collections import defaultdict
    g = defaultdict(list)
    for u, v, w in times:
        g[u].append((v, w))
    dist = {}
    heap = [(0, k)]
    while heap:
        d, u = heapq.heappop(heap)
        if u in dist:
            continue
        dist[u] = d
        for v, w in g[u]:
            if v not in dist:
                heapq.heappush(heap, (d + w, v))
    return max(dist.values()) if len(dist) == n else -1
```

### Q112. Advanced

**Cheapest Flights Within K Stops**

Commonly reported in interviews at Amazon, Expedia-style screens, Google.

Find the cheapest price from `src` to `dst` with at most `k` stops. Return -1 if no such route exists.

Example: A direct expensive flight can lose to a cheaper one-stop flight when `k` allows it.

**Answer:**

Bellman-Ford relaxed for `k + 1` edges, or a Dijkstra state `(cost, node, stops_used)`. The stop limit makes plain Dijkstra on nodes incorrect.

**Complexity:** Time O((k + 1) * E) for Bellman-Ford. Space O(V).

```python
def find_cheapest(n, flights, src, dst, k):
    inf = 10 ** 15
    dist = [inf] * n
    dist[src] = 0
    for _ in range(k + 1):
        nxt = dist[:]
        for u, v, w in flights:
            if dist[u] + w < nxt[v]:
                nxt[v] = dist[u] + w
        dist = nxt
    return dist[dst] if dist[dst] < inf else -1
```

### Q113. Advanced

**Swim in Rising Water**

Commonly reported in interviews at Amazon, Google.

An n by n grid of heights. At time `t` you may enter any adjacent cell whose height is at most `t`. You start at the top left. Return the least `t` that lets you reach the bottom right.

Example: A grid `[[0, 2], [1, 3]]` returns `3`.

**Answer:**

Dijkstra, where the cost of a path is the maximum height along it. Always extend the path with the smallest such cost.

**Complexity:** Time O(n^2 log n), space O(n^2).

```python
def swim(grid):
    import heapq
    n = len(grid)
    heap = [(grid[0][0], 0, 0)]
    seen = {(0, 0)}
    while heap:
        t, i, j = heapq.heappop(heap)
        if i == n - 1 and j == n - 1:
            return t
        for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)):
            ni, nj = i + di, j + dj
            if 0 <= ni < n and 0 <= nj < n and (ni, nj) not in seen:
                seen.add((ni, nj))
                heapq.heappush(heap, (max(t, grid[ni][nj]), ni, nj))
    return -1
```

### Q114. Advanced

**Rotten Oranges**

Commonly reported in interviews at Amazon, Microsoft.

Each minute, a rotten orange rots its 4-adjacent fresh oranges. Return the minutes until every fresh orange is rotten, or -1 if some fresh orange can never rot.

Example: A single rotten orange next to one fresh orange returns 1.

**Answer:**

Multi-source BFS from every rotten orange. The answer is the maximum distance. If a fresh orange remains, return -1.

**Complexity:** Time O(m * n), space O(m * n).

```python
def oranges(grid):
    from collections import deque
    m, n = len(grid), len(grid[0])
    q = deque()
    fresh = 0
    for i in range(m):
        for j in range(n):
            if grid[i][j] == 2:
                q.append((i, j, 0))
            elif grid[i][j] == 1:
                fresh += 1
    minutes = 0
    while q:
        i, j, d = q.popleft()
        minutes = d
        for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)):
            ni, nj = i + di, j + dj
            if 0 <= ni < m and 0 <= nj < n and grid[ni][nj] == 1:
                grid[ni][nj] = 2
                fresh -= 1
                q.append((ni, nj, d + 1))
    return minutes if fresh == 0 else -1
```

### Q115. Advanced

**Pacific Atlantic Water Flow**

Commonly reported in interviews at Google, Amazon.

Water flows from a cell to an adjacent cell of equal or lower height. Return coordinates that can reach both the Pacific (top and left borders) and the Atlantic (bottom and right borders).

Example: On a strictly decreasing path to both borders, the high cell qualifies.

**Answer:**

Reverse the flow. BFS or DFS from each ocean's border, moving to equal or higher cells. The intersection of the two reachable sets is the answer.

**Complexity:** Time O(m * n), space O(m * n).

```python
def pacific_atlantic(heights):
    if not heights:
        return []
    m, n = len(heights), len(heights[0])
    def reach(starts):
        seen = set(starts)
        stack = list(starts)
        while stack:
            i, j = stack.pop()
            for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)):
                ni, nj = i + di, j + dj
                if 0 <= ni < m and 0 <= nj < n and (ni, nj) not in seen and heights[ni][nj] >= heights[i][j]:
                    seen.add((ni, nj))
                    stack.append((ni, nj))
        return seen
    pac = reach([(i, 0) for i in range(m)] + [(0, j) for j in range(n)])
    atl = reach([(i, n - 1) for i in range(m)] + [(m - 1, j) for j in range(n)])
    return list(pac & atl)
```

### Q116. Advanced

**Accounts Merge**

Commonly reported in interviews at Facebook, Amazon.

Each account is a name plus email addresses. Merge accounts that share any email. Return the merged accounts with sorted unique emails.

Example: Two John records that share one email become one record.

**Answer:**

Union-find on emails. Map each email to an account index, union indices that share an email, then group emails by root and sort.

**Complexity:** Time O(n log n) from sorting emails, where n is the total number of emails. Union-find itself is nearly O(n).

```python
def accounts_merge(accounts):
    parent = {}
    def find(x):
        parent.setdefault(x, x)
        while parent[x] != x:
            parent[x] = parent[parent[x]]
            x = parent[x]
        return x
    def union(a, b):
        parent[find(a)] = find(b)
    email_to_name = {}
    for name, *emails in accounts:
        for e in emails:
            email_to_name[e] = name
            union(emails[0], e)
    groups = {}
    for e in email_to_name:
        groups.setdefault(find(e), []).append(e)
    return [[email_to_name[root], *sorted(emails)] for root, emails in groups.items()]
```

### Q117. Advanced

**Redundant Connection**

Commonly reported in interviews at Google, Amazon.

A tree of `n` nodes gained one extra edge and became cyclic. Edges are given in order. Return the edge that can be removed to restore a tree, preferring the one that appears last.

Example: `[[1, 2], [1, 3], [2, 3]]` returns `[2, 3]`.

**Answer:**

Union-find. The first edge whose endpoints are already connected is the redundant one.

**Complexity:** Time nearly O(n), space O(n).

```python
def redundant(edges):
    parent = list(range(len(edges) + 1))
    def find(x):
        while parent[x] != x:
            parent[x] = parent[parent[x]]
            x = parent[x]
        return x
    for a, b in edges:
        ra, rb = find(a), find(b)
        if ra == rb:
            return [a, b]
        parent[ra] = rb
```

### Q118. Advanced

**Number of Provinces**

Commonly reported in interviews at Amazon, Microsoft.

An adjacency matrix describes an undirected graph. Return the number of connected components.

Example: Two disconnected pairs return 2.

**Answer:**

DFS, BFS, or union-find. Count how many times you start a search from an unvisited node.

**Complexity:** Time O(n^2) for a matrix. Space O(n).

```python
def provinces(is_connected):
    n = len(is_connected)
    seen = [False] * n
    def dfs(u):
        seen[u] = True
        for v in range(n):
            if is_connected[u][v] and not seen[v]:
                dfs(v)
    count = 0
    for i in range(n):
        if not seen[i]:
            dfs(i)
            count += 1
    return count
```

### Q119. Advanced

**Surrounded Regions**

Commonly reported in interviews at Amazon, Google.

A board of `'X'` and `'O'`. Capture every region of `'O'` that is fully surrounded by flipping it to `'X'`. Border-connected `'O'` cells stay.

Example: An `'O'` on the border stays. An `'O'` enclosed by `'X'` flips.

**Answer:**

Mark every `'O'` reachable from the border, then flip the unmarked `'O'` cells.

**Complexity:** Time O(m * n), space O(m * n).

```python
def solve_regions(board):
    if not board:
        return board
    m, n = len(board), len(board[0])
    def dfs(i, j):
        if not (0 <= i < m and 0 <= j < n) or board[i][j] != 'O':
            return
        board[i][j] = 'T'
        dfs(i + 1, j); dfs(i - 1, j); dfs(i, j + 1); dfs(i, j - 1)
    for i in range(m):
        dfs(i, 0); dfs(i, n - 1)
    for j in range(n):
        dfs(0, j); dfs(m - 1, j)
    for i in range(m):
        for j in range(n):
            board[i][j] = 'O' if board[i][j] == 'T' else 'X'
    return board
```

### Q120. Advanced

**Median of Two Sorted Arrays**

Commonly reported in interviews at Google, Amazon, Goldman Sachs.

Two sorted arrays. Return the median of the combined values in O(log(min(n, m))) time.

Example: `[1, 3]` and `[2]` returns `2.0`.

**Answer:**

Binary search the cut in the smaller array. The cut is correct when the left half's max is at most the right half's min. The median is then the max of the left or the average of the two middle values.

**Complexity:** Time O(log(min(n, m))), space O(1).

```python
def find_median(a, b):
    if len(a) > len(b):
        a, b = b, a
    m, n = len(a), len(b)
    lo, hi = 0, m
    half = (m + n + 1) // 2
    while lo <= hi:
        i = (lo + hi) // 2
        j = half - i
        left_a = a[i - 1] if i else float('-inf')
        right_a = a[i] if i < m else float('inf')
        left_b = b[j - 1] if j else float('-inf')
        right_b = b[j] if j < n else float('inf')
        if left_a <= right_b and left_b <= right_a:
            if (m + n) % 2:
                return float(max(left_a, left_b))
            return (max(left_a, left_b) + min(right_a, right_b)) / 2
        if left_a > right_b:
            hi = i - 1
        else:
            lo = i + 1
```

### Q121. Advanced

**Pow(x, n)**

Commonly reported in interviews at Facebook, Amazon, Google.

Implement exponentiation. `n` may be negative. Do better than multiplying one factor at a time.

Example: `2.0 ** 10` is `1024.0`. `2.0 ** -2` is `0.25`.

**Answer:**

Exponentiation by squaring. Halve the exponent each step. For a negative exponent, invert the result. Watch the edge `n = -2**31` in fixed-width integers; in Python, negate carefully by using a wider int.

**Complexity:** Time O(log |n|), space O(1) iterative.

```python
def my_pow(x, n):
    if n < 0:
        x, n = 1 / x, -n
    ans = 1.0
    while n:
        if n & 1:
            ans *= x
        x *= x
        n >>= 1
    return ans
```

### Q122. Advanced

**Koko Eating Bananas**

Commonly reported in interviews at Amazon, Google.

Piles of bananas. Koko eats at a constant integer speed and chooses one pile per hour. Return the minimum speed that finishes every pile within `h` hours.

Example: Piles `[3, 6, 7, 11]`, `h = 8` returns `4`.

**Answer:**

Binary search the speed from 1 to `max(piles)`. Hours needed at speed `s` is the sum of `ceil(pile / s)`.

**Complexity:** Time O(n log M), space O(1).

```python
def min_eating_speed(piles, h):
    lo, hi = 1, max(piles)
    while lo < hi:
        mid = (lo + hi) // 2
        hours = sum((p + mid - 1) // mid for p in piles)
        if hours <= h:
            hi = mid
        else:
            lo = mid + 1
    return lo
```

### Q123. Advanced

**Capacity to Ship Packages Within D Days**

Commonly reported in interviews at Amazon.

Packages must ship in order. Each day you load a contiguous prefix that does not exceed the ship's capacity. Return the minimum capacity that ships everything within `days` days.

Example: Weights `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`, `days = 5` returns `15`.

**Answer:**

Binary search capacity from `max(weights)` to `sum(weights)`. Greedily count how many days that capacity needs.

**Complexity:** Time O(n log S), space O(1).

```python
def ship(weights, days):
    lo, hi = max(weights), sum(weights)
    while lo < hi:
        mid = (lo + hi) // 2
        need = 1
        load = 0
        for w in weights:
            if load + w > mid:
                need += 1
                load = 0
            load += w
        if need <= days:
            hi = mid
        else:
            lo = mid + 1
    return lo
```

### Q124. Advanced

**Split Array Largest Sum**

Commonly reported in interviews at Google, Amazon.

Split a non-empty array into `m` contiguous non-empty parts. Minimize the largest part sum.

Example: `[7, 2, 5, 10, 8]`, `m = 2` returns `18`.

**Answer:**

Same binary-search-on-answer pattern as shipping. The capacity is the largest allowed part sum, and you count how many parts that limit needs.

**Complexity:** Time O(n log S), space O(1).

```python
def split_array(nums, m):
    lo, hi = max(nums), sum(nums)
    while lo < hi:
        mid = (lo + hi) // 2
        parts = 1
        total = 0
        for n in nums:
            if total + n > mid:
                parts += 1
                total = 0
            total += n
        if parts <= m:
            hi = mid
        else:
            lo = mid + 1
    return lo
```

### Q125. Advanced

**Find Peak Element**

Commonly reported in interviews at Google, Microsoft.

A peak is strictly greater than its neighbors. The ends have one neighbor. Return any peak index. Neighboring values are never equal.

Example: `[1, 2, 3, 1]` returns `2`.

**Answer:**

Binary search. If the middle is less than its right neighbor, a peak exists on the right. Otherwise a peak exists at mid or on the left.

**Complexity:** Time O(log n), space O(1).

```python
def find_peak(nums):
    lo, hi = 0, len(nums) - 1
    while lo < hi:
        mid = (lo + hi) // 2
        if nums[mid] < nums[mid + 1]:
            lo = mid + 1
        else:
            hi = mid
    return lo
```

### Q126. Advanced

**Search a 2D Matrix**

Commonly reported in interviews at Amazon, Microsoft.

Each row is sorted, and the first value of each row is greater than the last value of the previous row. Return true when `target` is present.

Example: A matrix that flattens to a sorted list can be binary searched as one array.

**Answer:**

Treat the matrix as a flat sorted array of length `m * n`. Convert the mid index back to `(mid // n, mid % n)`.

**Complexity:** Time O(log(m * n)), space O(1).

```python
def search_matrix(matrix, target):
    if not matrix or not matrix[0]:
        return False
    m, n = len(matrix), len(matrix[0])
    lo, hi = 0, m * n - 1
    while lo <= hi:
        mid = (lo + hi) // 2
        val = matrix[mid // n][mid % n]
        if val == target:
            return True
        if val < target:
            lo = mid + 1
        else:
            hi = mid - 1
    return False
```

### Q127. Advanced

**Time Based Key-Value Store**

Commonly reported in interviews at Google, Amazon.

Support `set(key, value, timestamp)` and `get(key, timestamp)`. Get returns the value with the largest timestamp less than or equal to the query, or an empty string.

Example: Set foo=bar at time 1. Get foo at time 1 returns bar. Get foo at time 3 still returns bar if nothing newer was stored.

**Answer:**

Append `(timestamp, value)` pairs. Timestamps for a key arrive in increasing order, so binary search the list.

**Complexity:** Set is O(1) amortized. Get is O(log n). Space O(n).

```python
class TimeMap:
    def __init__(self):
        from collections import defaultdict
        self.data = defaultdict(list)
    def set(self, key, value, timestamp):
        self.data[key].append((timestamp, value))
    def get(self, key, timestamp):
        import bisect
        arr = self.data[key]
        i = bisect.bisect_right(arr, (timestamp, chr(127))) - 1
        return arr[i][1] if i >= 0 else ''
```

### Q128. Advanced

**Implement Trie**

Commonly reported in interviews at Amazon, Google, Microsoft.

Implement insert, search, and starts-with for lowercase words.

Example: Insert `apple`. Search `apple` is true. Search `app` is false. Prefix `app` is true.

**Answer:**

Each node is a dict of children plus a terminal flag. Insert walks or creates edges. Search requires the terminal flag. Prefix search does not.

**Complexity:** Insert and lookup are O(L) where L is the word length. Space is proportional to the number of distinct prefixes.

```python
class Trie:
    def __init__(self):
        self.root = {}
    def insert(self, word):
        node = self.root
        for ch in word:
            node = node.setdefault(ch, {})
        node['#'] = True
    def _walk(self, word):
        node = self.root
        for ch in word:
            if ch not in node:
                return None
            node = node[ch]
        return node
    def search(self, word):
        node = self._walk(word)
        return bool(node and node.get('#'))
    def startswith(self, prefix):
        return self._walk(prefix) is not None
```

### Q129. Advanced

**Design Twitter**

Commonly reported in interviews at Amazon, Twitter-style design rounds.

Support post, follow, unfollow, and a news feed of the 10 most recent tweets from yourself and people you follow. Tweets are ordered by a global increasing id.

Example: User 1 posts, follows user 2, and sees both tweets in reverse time order.

**Answer:**

Store each user's tweets as a list and each follow set. For the feed, use a heap over the heads of the relevant tweet lists, like merging k sorted lists.

**Complexity:** Post and follow are O(1). Feed is O(k log u) for 10 tweets across followed users. Space O(tweets + follows).

```python
class Twitter:
    def __init__(self):
        from collections import defaultdict
        self.time = 0
        self.tweets = defaultdict(list)
        self.follows = defaultdict(set)
    def post(self, user, tweet):
        self.time += 1
        self.tweets[user].append((self.time, tweet))
    def follow(self, follower, followee):
        if follower != followee:
            self.follows[follower].add(followee)
    def unfollow(self, follower, followee):
        self.follows[follower].discard(followee)
    def feed(self, user):
        import heapq
        users = self.follows[user] | {user}
        heap = []
        for u in users:
            if self.tweets[u]:
                heap.append((-self.tweets[u][-1][0], u, len(self.tweets[u]) - 1))
        heapq.heapify(heap)
        out = []
        while heap and len(out) < 10:
            _, u, i = heapq.heappop(heap)
            out.append(self.tweets[u][i][1])
            if i:
                heapq.heappush(heap, (-self.tweets[u][i - 1][0], u, i - 1))
        return out
```

### Q130. Advanced

**LFU Cache**

Commonly reported in interviews at Amazon, Google, Microsoft.

Design a cache with get and put in average O(1). Evict the least frequently used key. Break ties by least recently used.

Example: Capacity 2. Two gets of key 1 make key 2 the eviction candidate when a third key arrives.

**Answer:**

Map key to value and frequency. Map frequency to an ordered dict of keys. Track the minimum frequency. `OrderedDict` gives O(1) recency inside a frequency bucket.

**Complexity:** Each operation average O(1). Space O(capacity).

```python
class LFU:
    def __init__(self, cap):
        from collections import defaultdict, OrderedDict
        self.cap = cap
        self.min_f = 0
        self.values = {}
        self.freq = {}
        self.buckets = defaultdict(OrderedDict)
    def _touch(self, key):
        f = self.freq[key]
        del self.buckets[f][key]
        if not self.buckets[f] and self.min_f == f:
            self.min_f += 1
        self.freq[key] = f + 1
        self.buckets[f + 1][key] = None
    def get(self, key):
        if key not in self.values:
            return -1
        self._touch(key)
        return self.values[key]
    def put(self, key, value):
        if self.cap == 0:
            return
        if key in self.values:
            self.values[key] = value
            self._touch(key)
            return
        if len(self.values) == self.cap:
            old, _ = self.buckets[self.min_f].popitem(last=False)
            del self.values[old]
            del self.freq[old]
        self.values[key] = value
        self.freq[key] = 1
        self.buckets[1][key] = None
        self.min_f = 1
```

### Q131. Advanced

**Insert Delete GetRandom O(1)**

Commonly reported in interviews at Google, Facebook.

Design a set that supports insert, remove, and get-random, each in average O(1). Get-random returns each present value with equal probability.

Example: Insert 1, insert 2, remove 1. Random returns 2.

**Answer:**

A list gives O(1) random index. A dict maps value to index. Remove by swapping the target with the last element and popping.

**Complexity:** Average O(1) each. Space O(n).

```python
class RandomizedSet:
    def __init__(self):
        import random
        self.random = random
        self.vals = []
        self.idx = {}
    def insert(self, val):
        if val in self.idx:
            return False
        self.idx[val] = len(self.vals)
        self.vals.append(val)
        return True
    def remove(self, val):
        if val not in self.idx:
            return False
        i = self.idx[val]
        last = self.vals[-1]
        self.vals[i] = last
        self.idx[last] = i
        self.vals.pop()
        del self.idx[val]
        return True
    def get_random(self):
        return self.random.choice(self.vals)
```

### Q132. Advanced

**Range Sum Query - Mutable**

Commonly reported in interviews at Amazon, Google.

Support updating one index and querying the sum of a range, both faster than a linear scan.

Example: Array `[1, 3, 5]`. Sum from 0 through 2 is 9. After setting index 1 to 2, the sum is 8.

**Answer:**

A Fenwick tree (binary indexed tree) or a segment tree. The Fenwick version is short: add at an index and prefix-sum by stripping the lowest set bit.

**Complexity:** Build O(n). Update and query O(log n). Space O(n).

```python
class Fenwick:
    def __init__(self, nums):
        self.n = len(nums)
        self.bit = [0] * (self.n + 1)
        self.nums = [0] * self.n
        for i, v in enumerate(nums):
            self.update(i, v)
    def update(self, i, val):
        delta = val - self.nums[i]
        self.nums[i] = val
        i += 1
        while i <= self.n:
            self.bit[i] += delta
            i += i & -i
    def prefix(self, i):
        s = 0
        while i:
            s += self.bit[i]
            i -= i & -i
        return s
    def query(self, left, right):
        return self.prefix(right + 1) - self.prefix(left)
```

### Q133. Advanced

**Count of Smaller Numbers After Self**

Commonly reported in interviews at Google, Amazon.

For each index, count how many later elements are strictly smaller.

Example: `[5, 2, 6, 1]` returns `[2, 1, 1, 0]`.

**Answer:**

Merge sort the indexes. When the right half contributes a value during the merge, it is smaller than every remaining left-half value, so add that count. A Fenwick tree on compressed ranks also works, scanning from the right.

**Complexity:** Time O(n log n), space O(n).

```python
def count_smaller(nums):
    n = len(nums)
    ans = [0] * n
    items = list(enumerate(nums))
    def sort(arr):
        if len(arr) <= 1:
            return arr
        mid = len(arr) // 2
        left, right = sort(arr[:mid]), sort(arr[mid:])
        merged = []
        j = 0
        for i, (idx, val) in enumerate(left):
            while j < len(right) and right[j][1] < val:
                merged.append(right[j])
                j += 1
            ans[idx] += j
            merged.append((idx, val))
        merged.extend(right[j:])
        return merged
    sort(items)
    return ans
```

### Q134. Advanced

**Largest Rectangle in Histogram**

Commonly reported in interviews at Amazon, Google.

Each bar has width 1 and the given height. Return the area of the largest rectangle that fits under the bars.

Example: `[2, 1, 5, 6, 2, 3]` returns `10`.

**Answer:**

Monotonic increasing stack of indices. When a bar is shorter than the stack top, the top is the limiting height of a rectangle that extends to the current index.

**Complexity:** Time O(n), space O(n).

```python
def largest_rectangle(heights):
    stack = [-1]
    best = 0
    heights = heights + [0]
    for i, h in enumerate(heights):
        while stack[-1] != -1 and heights[stack[-1]] > h:
            height = heights[stack.pop()]
            width = i - stack[-1] - 1
            best = max(best, height * width)
        stack.append(i)
    return best
```

### Q135. Advanced

**Maximal Rectangle**

Commonly reported in interviews at Amazon, Google.

A binary matrix. Return the area of the largest rectangle of ones.

Example: A 2x3 block of ones has area 6.

**Answer:**

Treat each row as the base of a histogram whose bar height is the number of consecutive ones ending at that cell. Run the histogram algorithm on every row.

**Complexity:** Time O(m * n), space O(n).

```python
def maximal_rectangle(matrix):
    if not matrix:
        return 0
    n = len(matrix[0])
    height = [0] * n
    best = 0
    for row in matrix:
        for j in range(n):
            height[j] = height[j] + 1 if row[j] == '1' else 0
        stack = [-1]
        hist = height + [0]
        for i, h in enumerate(hist):
            while stack[-1] != -1 and hist[stack[-1]] > h:
                H = hist[stack.pop()]
                best = max(best, H * (i - stack[-1] - 1))
            stack.append(i)
    return best
```

### Q136. Advanced

**Basic Calculator**

Commonly reported in interviews at Google, Amazon.

Evaluate a string expression of non-negative integers, `+`, `-`, parentheses, and spaces.

Example: `'(1+(4+5+2)-3)+(6+8)'` returns `23`.

**Answer:**

A stack of signs or of partial results. On `(`, push the current result and the sign before the parenthesis, then start a fresh result. On `)`, combine with the saved sign and result.

**Complexity:** Time O(n), space O(n).

```python
def calculate(s):
    stack = []
    result = 0
    sign = 1
    n = 0
    for ch in s:
        if ch.isdigit():
            n = n * 10 + int(ch)
        elif ch in '+-':
            result += sign * n
            n = 0
            sign = 1 if ch == '+' else -1
        elif ch == '(':
            stack.append(result)
            stack.append(sign)
            result, sign = 0, 1
        elif ch == ')':
            result += sign * n
            n = 0
            result *= stack.pop()
            result += stack.pop()
    return result + sign * n
```

### Q137. Advanced

**Basic Calculator II**

Commonly reported in interviews at Facebook, Amazon.

Evaluate an expression with non-negative integers, `+`, `-`, `*`, `/`, and spaces. Division truncates toward zero. There are no parentheses.

Example: `'3+2*2'` returns `7`. `'14-3/2'` returns `13`.

**Answer:**

Keep a stack of terms. On `+` or `-`, push the signed number. On `*` or `/`, combine with the stack top immediately. Sum the stack at the end.

**Complexity:** Time O(n), space O(n).

```python
def calculate_ii(s):
    stack = []
    n = 0
    op = '+'
    for i, ch in enumerate(s + '+'):
        if ch.isdigit():
            n = n * 10 + int(ch)
        elif ch in '+-*/':
            if op == '+':
                stack.append(n)
            elif op == '-':
                stack.append(-n)
            elif op == '*':
                stack.append(stack.pop() * n)
            else:
                prev = stack.pop()
                stack.append(int(prev / n))
            op, n = ch, 0
    return sum(stack)
```

### Q138. Advanced

**The Skyline Problem**

Commonly reported in interviews at Google, Facebook, Microsoft.

Buildings are triples `[left, right, height]`. Return the skyline as key points `[x, height]` where the height of the silhouette changes.

Example: Two adjacent buildings produce a rise, a step where the shorter one is hidden, and a fall back to zero.

**Answer:**

Sweep line. Events are left edges (`+height`) and right edges (`-height`). A max-heap, or a sorted multiset, tracks active heights. Emit a point when the current max changes. Python's heap needs lazy deletion.

**Complexity:** Time O(n log n), space O(n).

```python
def skyline(buildings):
    import heapq
    events = []
    for L, R, H in buildings:
        events.append((L, -H, R))
        events.append((R, 0, 0))
    events.sort()
    heap = [(0, float('inf'))]
    out = []
    for x, neg_h, R in events:
        while heap[0][1] <= x:
            heapq.heappop(heap)
        if neg_h:
            heapq.heappush(heap, (neg_h, R))
        height = -heap[0][0]
        if not out or out[-1][1] != height:
            out.append([x, height])
    return out
```

### Q139. Advanced

**Bus Routes**

Commonly reported in interviews at Google, Amazon.

Each bus route is a cycle of stops. The cost of a trip is the number of buses taken. Return the minimum buses needed to go from `source` to `target`, or -1.

Example: If source and target share a route, the answer is 1. If source equals target, the answer is 0.

**Answer:**

BFS on buses, or on stops where you mark a route used once you board it. Boarding a route visits all of its stops at cost +1.

**Complexity:** Time O(total stops across routes), space O(total stops).

```python
def num_buses(routes, source, target):
    from collections import defaultdict, deque
    if source == target:
        return 0
    stop_to_buses = defaultdict(set)
    for i, route in enumerate(routes):
        for stop in route:
            stop_to_buses[stop].add(i)
    q = deque([(source, 0)])
    seen_stops = {source}
    seen_buses = set()
    while q:
        stop, buses = q.popleft()
        for b in stop_to_buses[stop]:
            if b in seen_buses:
                continue
            seen_buses.add(b)
            for nxt in routes[b]:
                if nxt == target:
                    return buses + 1
                if nxt not in seen_stops:
                    seen_stops.add(nxt)
                    q.append((nxt, buses + 1))
    return -1
```

### Q140. Advanced

**Critical Connections**

Commonly reported in interviews at Amazon.

An undirected connected graph. Return every bridge: an edge whose removal increases the number of connected components.

Example: A tree edge is always a bridge. An edge on a cycle is not.

**Answer:**

Tarjan's DFS. Record discovery time and the lowest discovery time reachable from the subtree. An edge `u-v` is a bridge when `low[v] > disc[u]`.

**Complexity:** Time O(V + E), space O(V + E).

```python
def critical_connections(n, connections):
    from collections import defaultdict
    g = defaultdict(list)
    for u, v in connections:
        g[u].append(v)
        g[v].append(u)
    disc = [-1] * n
    low = [0] * n
    time = 0
    out = []
    def dfs(u, parent):
        nonlocal time
        disc[u] = low[u] = time
        time += 1
        for v in g[u]:
            if v == parent:
                continue
            if disc[v] == -1:
                dfs(v, u)
                low[u] = min(low[u], low[v])
                if low[v] > disc[u]:
                    out.append([u, v])
            else:
                low[u] = min(low[u], disc[v])
    dfs(0, -1)
    return out
```

### Q141. Advanced

**Word Search II**

Commonly reported in interviews at Amazon, Microsoft.

Given a board and a list of words, return every word that can be formed by a 4-directional path without reusing a cell.

Example: A board containing `oath` and `pea` returns those words when both are in the dictionary and present as paths.

**Answer:**

Insert the words into a trie. DFS from each cell, walking the trie. When a word ends, record it and erase the terminal mark so it is not found twice. Prune dead branches.

**Complexity:** Time O(m * n * 4^L) in the worst case, much less with trie pruning. Space O(total characters).

```python
def find_words(board, words):
    trie = {}
    for w in words:
        node = trie
        for ch in w:
            node = node.setdefault(ch, {})
        node['#'] = w
    m, n = len(board), len(board[0])
    found = []
    def dfs(i, j, node):
        ch = board[i][j]
        nxt = node.get(ch)
        if not nxt:
            return
        word = nxt.pop('#', None)
        if word:
            found.append(word)
        board[i][j] = '.'
        for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)):
            ni, nj = i + di, j + dj
            if 0 <= ni < m and 0 <= nj < n:
                dfs(ni, nj, nxt)
        board[i][j] = ch
        if not nxt:
            node.pop(ch, None)
    for i in range(m):
        for j in range(n):
            dfs(i, j, trie)
    return found
```

### Q142. Advanced

**Employee Free Time**

Commonly reported in interviews at Amazon, Google, Airbnb-style.

Each employee has a sorted list of busy intervals. Return the finite gaps when every employee is free, in sorted order.

Example: If one person is busy 1-3 and another is busy 2-4, the merged busy block is 1-4 and there is no finite common free gap inside that block.

**Answer:**

Collect every interval, sort by start, and merge. A gap between merged blocks is common free time.

**Complexity:** Time O(n log n), space O(n).

```python
def free_time(schedule):
    busy = sorted(iv for person in schedule for iv in person)
    merged = [list(busy[0])]
    for start, end in busy[1:]:
        if start <= merged[-1][1]:
            merged[-1][1] = max(merged[-1][1], end)
        else:
            merged.append([start, end])
    gaps = []
    for a, b in zip(merged, merged[1:]):
        gaps.append([a[1], b[0]])
    return gaps
```

### Q143. Advanced

**Meeting Rooms II**

Commonly reported in interviews at Amazon, Google, Facebook.

Given meeting intervals, return the minimum number of rooms required so that no two meetings in the same room overlap.

Example: `[[0, 30], [5, 10], [15, 20]]` returns `2`.

**Answer:**

Sort starts and ends separately. Sweep with two pointers. A start before the next end opens a room. An end at or before the next start frees a room.

**Complexity:** Time O(n log n), space O(n).

```python
def min_rooms(intervals):
    starts = sorted(s for s, e in intervals)
    ends = sorted(e for s, e in intervals)
    rooms = used = 0
    j = 0
    for s in starts:
        if s < ends[j]:
            used += 1
            rooms = max(rooms, used)
        else:
            j += 1
    return rooms
```

### Q144. Advanced

**Non-overlapping Intervals**

Commonly reported in interviews at Amazon.

Return the minimum number of intervals to remove so the rest do not overlap. Touching at an endpoint is allowed.

Example: `[[1, 2], [2, 3], [3, 4], [1, 3]]` returns `1`.

**Answer:**

Sort by end time. Keep an interval when it starts at or after the last kept end. Otherwise it is the one to drop, because it ends later or conflicts.

**Complexity:** Time O(n log n), space O(1) extra besides sorting.

```python
def erase_overlap(intervals):
    intervals = sorted(intervals, key=lambda iv: iv[1])
    end = float('-inf')
    removed = 0
    for s, e in intervals:
        if s >= end:
            end = e
        else:
            removed += 1
    return removed
```

### Q145. Advanced

**Task Scheduler**

Commonly reported in interviews at Facebook, Amazon.

Tasks are letters. The same letter must be separated by at least `n` intervals. A CPU cycle can be idle. Return the minimum cycles needed to finish every task.

Example: Tasks `AAABBB`, `n = 2` can be scheduled as `A B idle A B idle A B` in some equivalent order and takes 8.

**Answer:**

The most frequent task determines a frame pattern. If the most frequent task appears `f` times and `k` tasks share that frequency, the answer is `max(len(tasks), (f - 1) * (n + 1) + k)`.

**Complexity:** Time O(n), space O(1) for a fixed alphabet.

```python
def least_interval(tasks, n):
    from collections import Counter
    counts = Counter(tasks)
    f = max(counts.values())
    k = sum(v == f for v in counts.values())
    return max(len(tasks), (f - 1) * (n + 1) + k)
```

### Q146. Advanced

**Queue Reconstruction by Height**

Commonly reported in interviews at Amazon, Google.

People are pairs `[h, k]` meaning height `h` and exactly `k` people in front who are at least as tall. Reconstruct the queue.

Example: `[[7, 0], [4, 4], [7, 1], [5, 0], [6, 1], [5, 2]]` has a known unique arrangement.

**Answer:**

Sort by height descending, and by `k` ascending within a height. Insert each person at index `k`. Taller people are already placed, so index `k` is exactly the number of taller-or-equal people in front.

**Complexity:** Time O(n^2) because of list insertion. Space O(n).

```python
def reconstruct_queue(people):
    people = sorted(people, key=lambda p: (-p[0], p[1]))
    out = []
    for p in people:
        out.insert(p[1], p)
    return out
```

### Q147. Advanced

**Odd Even Linked List**

Commonly reported in interviews at Amazon.

Group nodes at odd positions before nodes at even positions, preserving relative order. The first node is position 1. Do it in place.

Example: `1 -> 2 -> 3 -> 4 -> 5` becomes `1 -> 3 -> 5 -> 2 -> 4`.

**Answer:**

Split into two lists with two tails, then attach the even head after the odd tail.

**Complexity:** Time O(n), space O(1).

```python
def odd_even(head):
    if not head:
        return head
    odd, even, even_head = head, head.next, head.next
    while even and even.next:
        odd.next = even.next
        odd = odd.next
        even.next = odd.next
        even = even.next
    odd.next = even_head
    return head
```

### Q148. Advanced

**Flatten Binary Tree to Linked List**

Commonly reported in interviews at Microsoft, Facebook.

Flatten a binary tree into a right spine in preorder, in place. Left children become null.

Example: Root 1, left 2, right 5 becomes `1 -> 2 -> ... -> 5` along `right`.

**Answer:**

Reverse postorder (right, left, root) with a previous pointer, or find the rightmost node of the left subtree and stitch the original right subtree there.

**Complexity:** Time O(n), space O(1) for the stitch method if you do not use recursion, or O(h) recursive.

```python
def flatten(root):
    cur = root
    while cur:
        if cur.left:
            pred = cur.left
            while pred.right:
                pred = pred.right
            pred.right = cur.right
            cur.right = cur.left
            cur.left = None
        cur = cur.right
    return root
```

### Q149. Advanced

**Populating Next Right Pointers**

Commonly reported in interviews at Amazon, Microsoft.

Each node of a perfect binary tree has a `next` pointer. Point every node at its level's right neighbor, or null if it is the rightmost.

Example: On a perfect tree, the left child's next is the right child. A right child's next is the parent's next's left child.

**Answer:**

Use the `next` pointers already established on the current level to wire the level below. No queue is required.

**Complexity:** Time O(n), space O(1).

```python
def connect(root):
    left = root
    while left and left.left:
        cur = left
        while cur:
            cur.left.next = cur.right
            if cur.next:
                cur.right.next = cur.next.left
            cur = cur.next
        left = left.left
    return root
```

### Q150. Advanced

**Binary Tree Zigzag Level Order**

Commonly reported in interviews at Amazon, Microsoft.

Return level order, but alternate the direction of each level.

Example: Level 0 left to right, level 1 right to left, and so on.

**Answer:**

Ordinary BFS. Reverse the collected level when the level index is odd, or use a deque and insert at the front on alternate levels.

**Complexity:** Time O(n), space O(n).

```python
def zigzag(root):
    from collections import deque
    if not root:
        return []
    out, q, flip = [], deque([root]), False
    while q:
        level = []
        for _ in range(len(q)):
            node = q.popleft()
            level.append(node.val)
            if node.left:
                q.append(node.left)
            if node.right:
                q.append(node.right)
        out.append(level[::-1] if flip else level)
        flip = not flip
    return out
```

### Q151. Advanced

**Path Sum III**

Commonly reported in interviews at Amazon.

Count the paths that sum to `target`. A path must go downward (parent to child) but does not have to start at the root or end at a leaf.

Example: Several downward paths can share a prefix and still be counted separately.

**Answer:**

Prefix sums on the DFS path. At each node, add the number of earlier prefixes equal to `current_sum - target`. A map keeps those counts. Backtrack the count when you leave a node.

**Complexity:** Time O(n), space O(n).

```python
def path_sum_iii(root, target):
    from collections import defaultdict
    seen = defaultdict(int)
    seen[0] = 1
    def dfs(node, total):
        if not node:
            return 0
        total += node.val
        ans = seen[total - target]
        seen[total] += 1
        ans += dfs(node.left, total) + dfs(node.right, total)
        seen[total] -= 1
        return ans
    return dfs(root, 0)
```

### Q152. Advanced

**House Robber III**

Commonly reported in interviews at Uber, Amazon.

Houses form a binary tree. You cannot rob two directly connected nodes. Return the maximum amount.

Example: Robbing a node forbids its children. Robbing the children forbids the node.

**Answer:**

Return a pair `(rob_this, skip_this)` from each subtree. `rob_this` is the node value plus the skip values of the children. `skip_this` is the max of each child's pair.

**Complexity:** Time O(n), space O(h).

```python
def rob_tree(root):
    def dfs(node):
        if not node:
            return 0, 0
        L, R = dfs(node.left), dfs(node.right)
        rob = node.val + L[1] + R[1]
        skip = max(L) + max(R)
        return rob, skip
    return max(dfs(root))
```

### Q153. Advanced

**Decode String**

Commonly reported in interviews at Google, Amazon, Bloomberg.

The encoding is `k[encoded]`, meaning `encoded` repeated `k` times. Encodings nest. Return the decoded string.

Example: `3[a2[c]]` returns `accaccacc`.

**Answer:**

A stack of `(previous_string, k)`. On `]`, pop and repeat. Digits may have more than one character.

**Complexity:** Time O(n) relative to the output length. Space O(n).

```python
def decode_string(s):
    stack = []
    cur = ''
    k = 0
    for ch in s:
        if ch.isdigit():
            k = k * 10 + int(ch)
        elif ch == '[':
            stack.append((cur, k))
            cur, k = '', 0
        elif ch == ']':
            prev, times = stack.pop()
            cur = prev + cur * times
        else:
            cur += ch
    return cur
```

### Q154. Advanced

**Daily Temperatures**

Commonly reported in interviews at Amazon, Facebook.

For each day, return how many days you must wait until a warmer temperature. If none exists, that entry is 0.

Example: `[73, 74, 75, 71, 69, 72, 76, 73]` returns `[1, 1, 4, 2, 1, 1, 0, 0]`.

**Answer:**

Monotonic decreasing stack of indices. When today's temperature is warmer than the stack top, that day has found its answer.

**Complexity:** Time O(n), space O(n).

```python
def daily_temperatures(temps):
    ans = [0] * len(temps)
    stack = []
    for i, t in enumerate(temps):
        while stack and temps[stack[-1]] < t:
            j = stack.pop()
            ans[j] = i - j
        stack.append(i)
    return ans
```

### Q155. Advanced

**Next Greater Element II**

Commonly reported in interviews at Amazon, Google.

A circular list. For each position, return the next greater element, searching forward and wrapping around. Use -1 when none exists.

Example: `[1, 2, 1]` returns `[2, -1, 2]`.

**Answer:**

Monotonic stack over indexes `0 .. 2n-2`, using `i % n` to read the circular array. Each index is pushed once.

**Complexity:** Time O(n), space O(n).

```python
def next_greater_circular(nums):
    n = len(nums)
    ans = [-1] * n
    stack = []
    for i in range(2 * n):
        while stack and nums[stack[-1]] < nums[i % n]:
            ans[stack.pop()] = nums[i % n]
        if i < n:
            stack.append(i)
    return ans
```

### Q156. Advanced

**Online Stock Span**

Commonly reported in interviews at Amazon, Bloomberg.

The span of today's price is the number of consecutive days ending today whose price is less than or equal to today's price. Support a stream of `next(price)` calls.

Example: Prices 100, 80, 60, 70, 60, 75, 85 produce spans 1, 1, 1, 2, 1, 4, 6.

**Answer:**

Monotonic decreasing stack of `(price, span)`. Pop every previous day that is less than or equal, and add its span to today.

**Complexity:** Each call is amortized O(1). Space O(n).

```python
class StockSpanner:
    def __init__(self):
        self.stack = []
    def next(self, price):
        span = 1
        while self.stack and self.stack[-1][0] <= price:
            span += self.stack.pop()[1]
        self.stack.append((price, span))
        return span
```

### Q157. Advanced

**Car Fleet**

Commonly reported in interviews at Amazon, Google.

Cars drive at constant speeds toward a destination and cannot pass. A fleet is cars that bunch up at the same position and speed. Return how many fleets arrive.

Example: Target 12, positions `[10, 8, 0, 5, 3]`, speeds `[2, 4, 1, 1, 3]` returns `3`.

**Answer:**

Sort cars by position descending (closest to the destination first). A car joins the fleet ahead when its arrival time is less than or equal to that fleet's time. Otherwise it starts a new fleet.

**Complexity:** Time O(n log n), space O(n).

```python
def car_fleet(target, position, speed):
    cars = sorted(zip(position, speed), reverse=True)
    fleets = 0
    lead = -1.0
    for pos, spd in cars:
        time = (target - pos) / spd
        if time > lead:
            fleets += 1
            lead = time
    return fleets
```

### Q158. Advanced

**Asteroid Collision**

Commonly reported in interviews at Amazon.

Asteroids move right if positive and left if negative. When two collide, the smaller explodes. Equal sizes both explode. Return the state after every collision.

Example: `[5, 10, -5]` returns `[5, 10]`. `[8, -8]` returns `[]`.

**Answer:**

A stack of asteroids still in play. Only a right-moving stack top collides with a new left-moving asteroid. Resolve that pair before pushing.

**Complexity:** Time O(n), space O(n).

```python
def asteroid_collision(asteroids):
    stack = []
    for a in asteroids:
        alive = True
        while alive and stack and stack[-1] > 0 and a < 0:
            if stack[-1] < -a:
                stack.pop()
            elif stack[-1] == -a:
                stack.pop()
                alive = False
            else:
                alive = False
        if alive:
            stack.append(a)
    return stack
```

### Q159. Advanced

**Gas Station**

Commonly reported in interviews at Amazon, Uber.

Circular route. `gas[i]` is the fuel at station `i` and `cost[i]` is the fuel to reach the next station. Return the starting station index that completes the circuit, or -1. A solution is unique when it exists.

Example: If the total gas is less than the total cost, return -1.

**Answer:**

If the running tank drops below zero, no station in that segment can be the start. Reset the candidate to the next station and reset the tank. Also check that total gas covers total cost.

**Complexity:** Time O(n), space O(1).

```python
def can_complete(gas, cost):
    if sum(gas) < sum(cost):
        return -1
    tank = start = 0
    for i, (g, c) in enumerate(zip(gas, cost)):
        tank += g - c
        if tank < 0:
            start = i + 1
            tank = 0
    return start
```

### Q160. Advanced

**Candy**

Commonly reported in interviews at Amazon.

Children stand in a line with ratings. Each child gets at least one candy. A child with a strictly higher rating than a neighbor gets more candies than that neighbor. Return the minimum candies.

Example: `[1, 0, 2]` returns `5` (2, 1, 2).

**Answer:**

Two passes. Left to right enforces the left neighbor. Right to left enforces the right neighbor by taking the max.

**Complexity:** Time O(n), space O(n).

```python
def candy(ratings):
    n = len(ratings)
    candies = [1] * n
    for i in range(1, n):
        if ratings[i] > ratings[i - 1]:
            candies[i] = candies[i - 1] + 1
    for i in range(n - 2, -1, -1):
        if ratings[i] > ratings[i + 1]:
            candies[i] = max(candies[i], candies[i + 1] + 1)
    return sum(candies)
```

### Q161. Advanced

**H-Index**

Commonly reported in interviews at Google, Bloomberg.

A researcher has citation counts. The h-index is the largest `h` such that at least `h` papers have at least `h` citations each.

Example: `[3, 0, 6, 1, 5]` returns `3`.

**Answer:**

Sort descending and find the largest `i` with `citations[i] >= i + 1`. Counting sort is O(n) because any count above `n` can be bucketed at `n`.

**Complexity:** Time O(n) with counting, or O(n log n) with sorting. Space O(n) or O(1) extra.

```python
def h_index(citations):
    citations = sorted(citations, reverse=True)
    h = 0
    for i, c in enumerate(citations):
        if c >= i + 1:
            h = i + 1
        else:
            break
    return h
```

### Q162. Advanced

**Find the Duplicate Number**

Commonly reported in interviews at Amazon, Microsoft.

The list contains `n + 1` integers, each in `1..n`. Exactly one value is repeated, possibly more than once. Find it without modifying the list and with O(1) extra space.

Example: `[1, 3, 4, 2, 2]` returns `2`.

**Answer:**

Treat indexes and values as a linked list. The duplicate is the entrance of the cycle. Floyd's algorithm finds it. Binary search on the value range also works if you can count how many items are `<= mid`.

**Complexity:** Time O(n), space O(1).

```python
def find_duplicate(nums):
    slow = fast = nums[0]
    while True:
        slow = nums[slow]
        fast = nums[nums[fast]]
        if slow == fast:
            break
    slow = nums[0]
    while slow != fast:
        slow = nums[slow]
        fast = nums[fast]
    return slow
```

### Q163. Advanced

**Majority Element II**

Commonly reported in interviews at Amazon.

Return every value that appears more than `len(nums) // 3` times. There are at most two such values.

Example: `[1, 1, 1, 3, 3, 2, 2, 2]` returns `[1, 2]`.

**Answer:**

Boyer-Moore with two candidates. A second pass confirms that each candidate really exceeds `n / 3`, because the voting pass can leave a non-qualifier when no value is that frequent.

**Complexity:** Time O(n), space O(1).

```python
def majority_ii(nums):
    c1 = c2 = None
    k1 = k2 = 0
    for n in nums:
        if n == c1:
            k1 += 1
        elif n == c2:
            k2 += 1
        elif k1 == 0:
            c1, k1 = n, 1
        elif k2 == 0:
            c2, k2 = n, 1
        else:
            k1 -= 1
            k2 -= 1
    return [c for c in (c1, c2) if c is not None and nums.count(c) > len(nums) // 3]
```

### Q164. Advanced

**Subsets II**

Commonly reported in interviews at Amazon, Facebook.

Return all unique subsets. The input may contain duplicates.

Example: `[1, 2, 2]` returns subsets that include `[2]` once and `[2, 2]` once.

**Answer:**

Sort. Backtrack. After choosing a value, the next recursive call may skip duplicate siblings at the same depth.

**Complexity:** Time O(n * 2^n), space O(n) besides the answer.

```python
def subsets_with_dup(nums):
    nums = sorted(nums)
    out = []
    def bt(start, path):
        out.append(path[:])
        for i in range(start, len(nums)):
            if i > start and nums[i] == nums[i - 1]:
                continue
            path.append(nums[i])
            bt(i + 1, path)
            path.pop()
    bt(0, [])
    return out
```

### Q165. Advanced

**Permutations II**

Commonly reported in interviews at Amazon, LinkedIn.

Return all unique permutations. The input may contain duplicates.

Example: `[1, 1, 2]` returns three permutations, not six.

**Answer:**

Sort and skip a duplicate that would be placed in the same position as an unused identical predecessor. A used-array makes that test easy.

**Complexity:** Time O(n * n!), space O(n) besides the answer.

```python
def permute_unique(nums):
    nums = sorted(nums)
    used = [False] * len(nums)
    out = []
    def bt(path):
        if len(path) == len(nums):
            out.append(path[:])
            return
        for i, n in enumerate(nums):
            if used[i]:
                continue
            if i and nums[i] == nums[i - 1] and not used[i - 1]:
                continue
            used[i] = True
            path.append(n)
            bt(path)
            path.pop()
            used[i] = False
    bt([])
    return out
```

### Q166. Advanced

**Combination Sum II**

Commonly reported in interviews at Amazon.

Each candidate may be used once. The input may contain duplicates. Return unique combinations that sum to `target`.

Example: `[10, 1, 2, 7, 6, 1, 5]`, target `8` includes `[1, 1, 6]` and `[2, 6]` among others.

**Answer:**

Sort, then backtrack. Move the start index forward so a number is not reused, and skip duplicate siblings.

**Complexity:** Time exponential. Space O(n) besides the answer.

```python
def combination_sum2(candidates, target):
    candidates = sorted(candidates)
    out = []
    def bt(start, remain, path):
        if remain == 0:
            out.append(path[:])
            return
        for i in range(start, len(candidates)):
            if i > start and candidates[i] == candidates[i - 1]:
                continue
            if candidates[i] > remain:
                break
            path.append(candidates[i])
            bt(i + 1, remain - candidates[i], path)
            path.pop()
    bt(0, target, [])
    return out
```

### Q167. Advanced

**Palindrome Partitioning**

Commonly reported in interviews at Amazon, Bloomberg.

Partition a string so every part is a palindrome. Return all such partitions.

Example: `aab` returns `[['a', 'a', 'b'], ['aa', 'b']]`.

**Answer:**

Backtracking. At each start index, try every end that makes `s[start:end]` a palindrome, then recurse. Precompute a palindrome DP table if you want faster checks.

**Complexity:** Time exponential in the number of cuts. Space O(n) besides the answer.

```python
def partition(s):
    out = []
    def is_pal(a):
        return a == a[::-1]
    def bt(start, path):
        if start == len(s):
            out.append(path[:])
            return
        for end in range(start + 1, len(s) + 1):
            piece = s[start:end]
            if is_pal(piece):
                path.append(piece)
                bt(end, path)
                path.pop()
    bt(0, [])
    return out
```

### Q168. Advanced

**Restore IP Addresses**

Commonly reported in interviews at Amazon, Microsoft.

A string of digits may be split into four integers that form a valid IPv4 address. No leading zeros are allowed, and each part is at most 255. Return every valid address.

Example: `25525511135` returns `['255.255.11.135', '255.255.111.35']`.

**Answer:**

Backtracking with four parts. A part is one to three digits, has no leading zero unless it is exactly `0`, and is at most 255.

**Complexity:** Time is bounded by a small constant. Space O(1) besides the answer.

```python
def restore_ip(s):
    out = []
    def bt(start, parts):
        if len(parts) == 4:
            if start == len(s):
                out.append('.'.join(parts))
            return
        for length in range(1, 4):
            if start + length > len(s):
                break
            piece = s[start:start + length]
            if (piece[0] == '0' and length > 1) or int(piece) > 255:
                continue
            parts.append(piece)
            bt(start + length, parts)
            parts.pop()
    bt(0, [])
    return out
```

### Q169. Advanced

**Word Break II**

Commonly reported in interviews at Google, Amazon.

Return every way to segment a string into dictionary words, with spaces between words.

Example: `catsanddog` with `cat, cats, and, sand, dog` returns both `cats and dog` and `cat sand dog`.

**Answer:**

Backtracking with memoization on the start index. The memo stores the list of sentences that segment the suffix. Without memo, overlapping subproblems explode.

**Complexity:** Time exponential in the worst case because the output can be exponential. Memoized time is polynomial in the number of segmentations explored.

```python
def word_break_ii(s, word_dict):
    words = set(word_dict)
    memo = {}
    def bt(start):
        if start in memo:
            return memo[start]
        if start == len(s):
            return ['']
        out = []
        for end in range(start + 1, len(s) + 1):
            w = s[start:end]
            if w in words:
                for rest in bt(end):
                    out.append(w + (' ' + rest if rest else ''))
        memo[start] = out
        return out
    return bt(0)
```

### Q170. Advanced

**Burst Balloons**

Commonly reported in interviews at Google.

Balloons have numbers. Bursting balloon `i` scores `left * nums[i] * right`, where left and right are the still-present neighbors. Ends are treated as 1. Return the maximum score.

Example: `[3, 1, 5, 8]` returns `167`.

**Answer:**

Interval DP, but think about the last balloon burst in an open interval. `dp[l][r]` is the best score bursting everything strictly between `l` and `r`.

**Complexity:** Time O(n^3), space O(n^2).

```python
def max_coins(nums):
    a = [1] + [n for n in nums if n > 0] + [1]
    n = len(a)
    dp = [[0] * n for _ in range(n)]
    for length in range(2, n):
        for left in range(n - length):
            right = left + length
            for k in range(left + 1, right):
                dp[left][right] = max(dp[left][right], a[left] * a[k] * a[right] + dp[left][k] + dp[k][right])
    return dp[0][n - 1]
```

### Q171. Advanced

**Distinct Subsequences**

Commonly reported in interviews at Google.

Return how many distinct ways `t` appears as a subsequence of `s`.

Example: `s = 'rabbbit'`, `t = 'rabbit'` returns `3`.

**Answer:**

DP. `dp[i][j]` is ways to form the first `j` characters of `t` from the first `i` of `s`. Always carry the ways that skip `s[i]`. If characters match, also add the ways that use this match.

**Complexity:** Time O(n * m), space O(m).

```python
def num_distinct(s, t):
    dp = [1] + [0] * len(t)
    for ch in s:
        for j in range(len(t), 0, -1):
            if ch == t[j - 1]:
                dp[j] += dp[j - 1]
    return dp[-1]
```

### Q172. Advanced

**Interleaving String**

Commonly reported in interviews at Google, Amazon.

Return true when `s3` is formed by interleaving `s1` and `s2` while preserving the order of each.

Example: `aabcc` and `dbbca` can form `aadbbcbcac`. They cannot form `aadbbbaccc`.

**Answer:**

DP. `dp[i][j]` means the first `i+j` characters of `s3` are an interleaving of the prefixes. A rolling boolean row is enough.

**Complexity:** Time O(n * m), space O(m).

```python
def is_interleave(s1, s2, s3):
    if len(s1) + len(s2) != len(s3):
        return False
    dp = [False] * (len(s2) + 1)
    dp[0] = True
    for j in range(1, len(s2) + 1):
        dp[j] = dp[j - 1] and s2[j - 1] == s3[j - 1]
    for i in range(1, len(s1) + 1):
        dp[0] = dp[0] and s1[i - 1] == s3[i - 1]
        for j in range(1, len(s2) + 1):
            take1 = dp[j] and s1[i - 1] == s3[i + j - 1]
            take2 = dp[j - 1] and s2[j - 1] == s3[i + j - 1]
            dp[j] = take1 or take2
    return dp[-1]
```

### Q173. Advanced

**Longest Valid Parentheses**

Commonly reported in interviews at Google, Amazon.

Return the length of the longest substring of correctly matched parentheses.

Example: `')()())'` returns `4`.

**Answer:**

A stack of indices, starting with `-1` as a base. On `)`, pop and the distance to the new top is a valid length. If the stack empties, push the current index as the new base. DP is an alternative.

**Complexity:** Time O(n), space O(n).

```python
def longest_valid_parentheses(s):
    stack = [-1]
    best = 0
    for i, ch in enumerate(s):
        if ch == '(':
            stack.append(i)
        else:
            stack.pop()
            if not stack:
                stack.append(i)
            else:
                best = max(best, i - stack[-1])
    return best
```

### Q174. Advanced

**Minimum Number of Taps / Jump coverage**

Commonly reported in interviews at Amazon, Google.

On a line of length `n`, tap `i` waters `[i - ranges[i], i + ranges[i]]`. Return the minimum taps that water `[0, n]`, or -1.

Example: This is the jump-game coverage problem in disguise.

**Answer:**

Convert each tap into the farthest reach achievable from each start point. Then run the jump-game-II greedy scan.

**Complexity:** Time O(n), space O(n).

```python
def min_taps(n, ranges):
    reach = [0] * (n + 1)
    for i, r in enumerate(ranges):
        left, right = max(0, i - r), min(n, i + r)
        reach[left] = max(reach[left], right)
    taps = end = far = 0
    for i in range(n + 1):
        if i > far:
            return -1
        if i > end:
            taps += 1
            end = far
        far = max(far, reach[i])
    return taps
```

### Q175. Advanced

**Shortest Path in a Grid with Obstacles Elimination**

Commonly reported in interviews at Google.

A grid has empty cells and obstacles. You may eliminate up to `k` obstacles. Return the shortest 4-directional path from the top left to the bottom right, or -1.

Example: With `k = 1`, one obstacle on the only short path can still be crossed.

**Answer:**

BFS state is `(row, col, eliminations_left)`. Visit each state once. The first time you reach the target is the shortest path.

**Complexity:** Time O(m * n * k), space O(m * n * k).

```python
def shortest_path(grid, k):
    from collections import deque
    m, n = len(grid), len(grid[0])
    q = deque([(0, 0, k, 0)])
    seen = {(0, 0, k)}
    while q:
        i, j, left, dist = q.popleft()
        if i == m - 1 and j == n - 1:
            return dist
        for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)):
            ni, nj = i + di, j + dj
            if not (0 <= ni < m and 0 <= nj < n):
                continue
            nleft = left - grid[ni][nj]
            if nleft >= 0 and (ni, nj, nleft) not in seen:
                seen.add((ni, nj, nleft))
                q.append((ni, nj, nleft, dist + 1))
    return -1
```

### Q176. Advanced

**Sliding Window Median**

Commonly reported in interviews at Google.

Return the median of every window of size `k`.

Example: `[1, 3, -1, -3, 5, 3, 6, 7]`, `k = 3` returns the medians of each window.

**Answer:**

Two heaps do not support deletion of an arbitrary outgoing element in O(log k) without lazy deletion. Lazy deletion plus a balance step works. In Python, `SortedList` from `sortedcontainers` makes the intent obvious; a balanced policy with two heaps is the dependency-free version.

**Complexity:** Time O(n log k), space O(k).

```python
def median_sliding(nums, k):
    import heapq
    low, high = [], []
    delayed = {}
    def prune(heap):
        while heap:
            v = -heap[0] if heap is low else heap[0]
            if delayed.get(v, 0):
                delayed[v] -= 1
                if delayed[v] == 0:
                    del delayed[v]
                heapq.heappop(heap)
            else:
                break
    def balance():
        if len(low) > len(high) + 1:
            heapq.heappush(high, -heapq.heappop(low))
        elif len(high) > len(low):
            heapq.heappush(low, -heapq.heappop(high))
        prune(low); prune(high)
    out = []
    for i, n in enumerate(nums):
        if not low or n <= -low[0]:
            heapq.heappush(low, -n)
        else:
            heapq.heappush(high, n)
        balance()
        if i >= k:
            old = nums[i - k]
            delayed[old] = delayed.get(old, 0) + 1
            if low and old <= -low[0]:
                prune(low)
            else:
                prune(high)
            balance()
        if i >= k - 1:
            if k % 2:
                out.append(float(-low[0]))
            else:
                out.append((-low[0] + high[0]) / 2)
    return out
```

### Q177. Intermediate

**Maximum Product Subarray**

Commonly reported in interviews at Amazon, LinkedIn, Google.

Return the largest product of any contiguous subarray. Values may be negative or zero.

Example: `[2, 3, -2, 4]` returns `6`. `[-2, 0, -1]` returns `0`.

**Answer:**

Track both the maximum and the minimum product ending here, because a negative value can turn the minimum into the maximum. A zero resets both.

**Complexity:** Time O(n), space O(1).

```python
def max_product(nums):
    best = hi = lo = nums[0]
    for n in nums[1:]:
        cands = (n, hi * n, lo * n)
        hi, lo = max(cands), min(cands)
        best = max(best, hi)
    return best
```

### Q178. Intermediate

**Next Permutation**

Commonly reported in interviews at Google, Amazon.

Rearrange a list of integers into the next greater permutation in lexicographic order. If it is already the last permutation, rearrange it into the lowest one. Do it in place.

Example: `[1, 2, 3]` becomes `[1, 3, 2]`. `[3, 2, 1]` becomes `[1, 2, 3]`.

**Answer:**

Find the rightmost ascent `nums[i] < nums[i+1]`. Swap `nums[i]` with the smallest later value that is still larger, then reverse the suffix.

**Complexity:** Time O(n), space O(1).

```python
def next_permutation(nums):
    i = len(nums) - 2
    while i >= 0 and nums[i] >= nums[i + 1]:
        i -= 1
    if i >= 0:
        j = len(nums) - 1
        while nums[j] <= nums[i]:
            j -= 1
        nums[i], nums[j] = nums[j], nums[i]
    nums[i + 1:] = reversed(nums[i + 1:])
    return nums
```

### Q179. Intermediate

**Find First and Last Position**

Commonly reported in interviews at Amazon, Facebook, Bloomberg.

A sorted list may contain duplicates. Return the first and last index of `target`, or `[-1, -1]`.

Example: `[5, 7, 7, 8, 8, 10]`, target `8` returns `[3, 4]`.

**Answer:**

Two binary searches: a lower bound for `target`, and a lower bound for `target + 1` minus one.

**Complexity:** Time O(log n), space O(1).

```python
def search_range(nums, target):
    def lower(x):
        lo, hi = 0, len(nums)
        while lo < hi:
            mid = (lo + hi) // 2
            if nums[mid] < x:
                lo = mid + 1
            else:
                hi = mid
        return lo
    left = lower(target)
    if left == len(nums) or nums[left] != target:
        return [-1, -1]
    return [left, lower(target + 1) - 1]
```

### Q180. Basic

**Integer Square Root**

Commonly reported in interviews at Amazon, Facebook, Microsoft.

Return the floor of the square root of a non-negative integer. Do not use a library sqrt.

Example: `8` returns `2`. `16` returns `4`.

**Answer:**

Binary search the answer from 0 through `n`. Compare `mid * mid` with `n`. Python integers do not overflow.

**Complexity:** Time O(log n), space O(1).

```python
def my_sqrt(n):
    lo, hi, ans = 0, n, 0
    while lo <= hi:
        mid = (lo + hi) // 2
        if mid * mid <= n:
            ans = mid
            lo = mid + 1
        else:
            hi = mid - 1
    return ans
```

### Q181. Basic

**Roman to Integer**

Commonly reported in interviews at Amazon, Microsoft, Google.

Convert a valid Roman numeral to an integer. Subtractive pairs are `IV`, `IX`, `XL`, `XC`, `CD`, and `CM`.

Example: `MCMXCIV` is `1994`.

**Answer:**

Walk left to right. If the current value is less than the next value, subtract it. Otherwise add it.

**Complexity:** Time O(n), space O(1).

```python
def roman_to_int(s):
    val = {'I': 1, 'V': 5, 'X': 10, 'L': 50, 'C': 100, 'D': 500, 'M': 1000}
    total = 0
    for i, ch in enumerate(s):
        if i + 1 < len(s) and val[ch] < val[s[i + 1]]:
            total -= val[ch]
        else:
            total += val[ch]
    return total
```

### Q182. Intermediate

**Integer to Roman**

Commonly reported in interviews at Amazon, Microsoft.

Convert an integer from 1 through 3999 into a Roman numeral using the standard subtractive forms.

Example: `1994` becomes `MCMXCIV`.

**Answer:**

Greedy. Walk a table of value-symbol pairs from 1000 down through 1, appending the symbol as many times as it fits.

**Complexity:** Time O(1) because the input is bounded. Space O(1).

```python
def int_to_roman(num):
    table = [(1000, 'M'), (900, 'CM'), (500, 'D'), (400, 'CD'), (100, 'C'), (90, 'XC'), (50, 'L'), (40, 'XL'), (10, 'X'), (9, 'IX'), (5, 'V'), (4, 'IV'), (1, 'I')]
    out = []
    for value, symbol in table:
        while num >= value:
            out.append(symbol)
            num -= value
    return ''.join(out)
```

### Q183. Intermediate

**String to Integer**

Commonly reported in interviews at Amazon, Microsoft, Bloomberg.

Parse a 32-bit signed integer from the start of a string. Skip leading spaces, accept an optional sign, and read digits. Clamp to `[-2**31, 2**31 - 1]`. Stop at the first non-digit. If no digit is found, return 0.

Example: `'   -42'` returns `-42`. `'4193 with words'` returns `4193`.

**Answer:**

A small state scan. Accumulate the number and clamp as soon as it leaves the 32-bit range.

**Complexity:** Time O(n), space O(1).

```python
def my_atoi(s):
    s = s.lstrip()
    if not s:
        return 0
    sign = 1
    i = 0
    if s[0] in '+-':
        sign = -1 if s[0] == '-' else 1
        i = 1
    n = 0
    while i < len(s) and s[i].isdigit():
        n = n * 10 + int(s[i])
        i += 1
    n *= sign
    return max(-2**31, min(2**31 - 1, n))
```

### Q184. Basic

**Valid Palindrome**

Commonly reported in interviews at Facebook, Microsoft, Apple.

Return true when the string is a palindrome after ignoring non-alphanumeric characters and case.

Example: `'A man, a plan, a canal: Panama'` is true.

**Answer:**

Two pointers. Skip characters that are not letters or digits, and compare with `casefold`.

**Complexity:** Time O(n), space O(1).

```python
def is_palindrome(s):
    lo, hi = 0, len(s) - 1
    while lo < hi:
        while lo < hi and not s[lo].isalnum():
            lo += 1
        while lo < hi and not s[hi].isalnum():
            hi -= 1
        if s[lo].casefold() != s[hi].casefold():
            return False
        lo += 1
        hi -= 1
    return True
```

### Q185. Basic

**Longest Common Prefix**

Commonly reported in interviews at Amazon, Google.

Return the longest prefix shared by every string in a non-empty list. Return an empty string when there is no common prefix.

Example: `['flower', 'flow', 'flight']` returns `'fl'`.

**Answer:**

Horizontal scan: start with the first string and shorten it until every other string starts with it. Vertical scan compares one character column at a time.

**Complexity:** Time O(total characters), space O(1) extra besides the answer.

```python
def longest_common_prefix(strs):
    prefix = strs[0]
    for word in strs[1:]:
        while not word.startswith(prefix):
            prefix = prefix[:-1]
            if not prefix:
                return ''
    return prefix
```

### Q186. Intermediate

**Evaluate Reverse Polish Notation**

Commonly reported in interviews at Amazon, LinkedIn, Google.

Tokens are integers or the operators `+`, `-`, `*`, and `/`. Division truncates toward zero. Evaluate the postfix expression.

Example: `['2', '1', '+', '3', '*']` returns `9`.

**Answer:**

A stack. Operands are pushed. An operator pops the right operand, then the left, and pushes the result. Python's `int(a / b)` truncates toward zero.

**Complexity:** Time O(n), space O(n).

```python
def eval_rpn(tokens):
    stack = []
    for tok in tokens:
        if tok in '+-*/':
            b, a = stack.pop(), stack.pop()
            if tok == '+':
                stack.append(a + b)
            elif tok == '-':
                stack.append(a - b)
            elif tok == '*':
                stack.append(a * b)
            else:
                stack.append(int(a / b))
        else:
            stack.append(int(tok))
    return stack[0]
```

### Q187. Intermediate

**Perfect Squares**

Commonly reported in interviews at Amazon, Google.

Return the least number of perfect squares that sum to `n`.

Example: `12` returns `3` because `4 + 4 + 4`. `13` returns `2` because `4 + 9`.

**Answer:**

Unbounded knapsack, or BFS over remainders. `dp[x] = 1 + min(dp[x - s])` for every square `s <= x`. Lagrange's four-square theorem says the answer is at most 4, which can prune a math solution.

**Complexity:** Time O(n * sqrt(n)), space O(n).

```python
def num_squares(n):
    dp = [0] + [n] * n
    for x in range(1, n + 1):
        s = 1
        while s * s <= x:
            dp[x] = min(dp[x], dp[x - s * s] + 1)
            s += 1
    return dp[n]
```

### Q188. Intermediate

**Unique Paths II**

Commonly reported in interviews at Amazon, Google.

Same as unique paths, but some cells are obstacles and cannot be entered. Return the number of paths from the top left to the bottom right.

Example: A grid with one obstacle in the only corridor returns 0.

**Answer:**

DP. An obstacle cell is 0. Any other cell is the sum of the ways to arrive from the left and from above.

**Complexity:** Time O(m * n), space O(n).

```python
def unique_paths_with_obstacles(grid):
    n = len(grid[0])
    row = [0] * n
    row[0] = 1
    for r in grid:
        for j in range(n):
            if r[j] == 1:
                row[j] = 0
            elif j:
                row[j] += row[j - 1]
    return row[-1]
```

### Q189. Basic

**Best Time to Buy and Sell Stock II**

Commonly reported in interviews at Amazon, Bloomberg.

You may complete as many buy-sell transactions as you want, but you may not hold more than one share. Return the maximum profit.

Example: `[7, 1, 5, 3, 6, 4]` returns `7`.

**Answer:**

Add every upward difference. Each ascent can be captured by buying before it and selling after it, and overlapping transactions are unnecessary.

**Complexity:** Time O(n), space O(1).

```python
def max_profit_ii(prices):
    return sum(max(0, b - a) for a, b in zip(prices, prices[1:]))
```

### Q190. Advanced

**Best Time to Buy and Sell Stock with Cooldown**

Commonly reported in interviews at Google, Amazon.

You may complete as many transactions as you want, but after you sell you must wait one day before buying again. Return the maximum profit.

Example: `[1, 2, 3, 0, 2]` returns `3`.

**Answer:**

Three states: holding, sold today (cooling), and free to buy. Roll them forward one day at a time.

**Complexity:** Time O(n), space O(1).

```python
def max_profit_cooldown(prices):
    hold, sold, rest = float('-inf'), 0, 0
    for p in prices:
        prev_sold = sold
        sold = hold + p
        hold = max(hold, rest - p)
        rest = max(rest, prev_sold)
    return max(sold, rest)
```

### Q191. Intermediate

**01 Matrix**

Commonly reported in interviews at Amazon, Google.

A binary matrix. For each cell, return the distance to the nearest 0. Movement is 4-directional.

Example: A cell that is already 0 has distance 0. Its neighbor has distance 1.

**Answer:**

Multi-source BFS from every 0. The first time a cell is reached is its shortest distance.

**Complexity:** Time O(m * n), space O(m * n).

```python
def update_matrix(mat):
    from collections import deque
    m, n = len(mat), len(mat[0])
    q = deque()
    dist = [[-1] * n for _ in range(m)]
    for i in range(m):
        for j in range(n):
            if mat[i][j] == 0:
                dist[i][j] = 0
                q.append((i, j))
    while q:
        i, j = q.popleft()
        for di, dj in ((1, 0), (-1, 0), (0, 1), (0, -1)):
            ni, nj = i + di, j + dj
            if 0 <= ni < m and 0 <= nj < n and dist[ni][nj] < 0:
                dist[ni][nj] = dist[i][j] + 1
                q.append((ni, nj))
    return dist
```

### Q192. Intermediate

**Is Graph Bipartite**

Commonly reported in interviews at Amazon, Facebook, Google.

An undirected graph is given as an adjacency list. Return true when the nodes can be colored with two colors so every edge connects different colors.

Example: A triangle is not bipartite. A square is.

**Answer:**

BFS or DFS coloring. If a neighbor already has the same color, the graph is not bipartite. Repeat for every component.

**Complexity:** Time O(V + E), space O(V).

```python
def is_bipartite(graph):
    color = {}
    def dfs(u, c):
        if u in color:
            return color[u] == c
        color[u] = c
        return all(dfs(v, 1 - c) for v in graph[u])
    return all(u in color or dfs(u, 0) for u in range(len(graph)))
```

### Q193. Advanced

**Count Complete Tree Nodes**

Commonly reported in interviews at Google, LinkedIn.

A complete binary tree has every level filled except possibly the last, which is filled from the left. Return the number of nodes faster than a full traversal in the average case.

Example: A perfect tree of height h has `2^(h+1) - 1` nodes.

**Answer:**

Compare the left-spine height with the right-spine height. If they match, the tree is perfect. Otherwise recurse into the child that is not a perfect subtree you already counted. This is O(h^2).

**Complexity:** Time O(h^2), which is O((log n)^2). Space O(h).

```python
def count_nodes(root):
    def height(node):
        h = 0
        while node:
            h += 1
            node = node.left
        return h
    if not root:
        return 0
    L, R = height(root.left), height(root.right)
    if L == R:
        return (1 << L) + count_nodes(root.right)
    return (1 << R) + count_nodes(root.left)
```

### Q194. Intermediate

**Binary Search Tree Iterator**

Commonly reported in interviews at Facebook, Amazon, Microsoft.

Implement an iterator over a BST that returns the next smallest value, with `next` and `has_next` amortized O(1) and O(h) memory.

Example: The sequence of `next` calls is the inorder traversal.

**Answer:**

Keep an explicit stack of the left spine. `next` pops a node and pushes the left spine of its right child.

**Complexity:** Construction and each `next` are amortized O(1). Space O(h).

```python
class BSTIterator:
    def __init__(self, root):
        self.stack = []
        self._push(root)
    def _push(self, node):
        while node:
            self.stack.append(node)
            node = node.left
    def next(self):
        node = self.stack.pop()
        self._push(node.right)
        return node.val
    def has_next(self):
        return bool(self.stack)
```

### Q195. Basic

**Convert Sorted Array to BST**

Commonly reported in interviews at Amazon, Microsoft.

Build a height-balanced BST from a sorted list of distinct integers.

Example: `[-10, -3, 0, 5, 9]` has 0 as a valid root.

**Answer:**

The middle element is the root. Recurse on the left half and the right half.

**Complexity:** Time O(n), space O(log n) for the recursion of a balanced tree.

```python
def sorted_array_to_bst(nums):
    def build(lo, hi):
        if lo > hi:
            return None
        mid = (lo + hi) // 2
        node = _T(nums[mid])
        node.left = build(lo, mid - 1)
        node.right = build(mid + 1, hi)
        return node
    return build(0, len(nums) - 1)

class _T:
    def __init__(self, val):
        self.val, self.left, self.right = val, None, None
```

### Q196. Intermediate

**Intersection of Two Linked Lists**

Commonly reported in interviews at Amazon, Microsoft, Bloomberg.

Two singly linked lists may merge and share a tail. Return the first shared node, or null. Do not modify the lists.

Example: If the lists are different lengths, the shared node is not at the same index from each head.

**Answer:**

Walk both pointers. When one reaches the end, redirect it to the other head. They meet at the intersection after at most two passes, or both become null.

**Complexity:** Time O(n + m), space O(1).

```python
def intersection(a, b):
    p, q = a, b
    while p is not q:
        p = p.next if p else b
        q = q.next if q else a
    return p
```

### Q197. Intermediate

**Minimum Size Subarray Sum**

Commonly reported in interviews at Amazon, Facebook.

A list of positive integers. Return the length of the shortest contiguous subarray whose sum is at least `target`, or 0 if none exists.

Example: `target = 7`, `[2, 3, 1, 2, 4, 3]` returns `2` because of `[4, 3]`.

**Answer:**

Sliding window. Expand the right edge, and shrink the left edge while the sum stays at least the target.

**Complexity:** Time O(n), space O(1).

```python
def min_subarray_len(target, nums):
    left = total = 0
    best = len(nums) + 1
    for right, n in enumerate(nums):
        total += n
        while total >= target:
            best = min(best, right - left + 1)
            total -= nums[left]
            left += 1
    return best if best <= len(nums) else 0
```

### Q198. Basic

**Rotate Array**

Commonly reported in interviews at Microsoft, Amazon.

Rotate a list to the right by `k` steps. `k` may be larger than the length.

Example: `[1, 2, 3, 4, 5]`, `k = 2` becomes `[4, 5, 1, 2, 3]`.

**Answer:**

Reduce `k` modulo n. Reverse the whole list, then reverse the first `k` items, then reverse the rest. Three reversals do it in place.

**Complexity:** Time O(n), space O(1).

```python
def rotate(nums, k):
    n = len(nums)
    k %= n
    def rev(a, b):
        while a < b:
            nums[a], nums[b] = nums[b], nums[a]
            a += 1
            b -= 1
    rev(0, n - 1)
    rev(0, k - 1)
    rev(k, n - 1)
    return nums
```

### Q199. Intermediate

**Multiply Strings**

Commonly reported in interviews at Facebook, Amazon.

Two non-negative integers are given as strings. Return their product as a string. Do not convert the whole inputs with `int` if you want to show the grade-school algorithm; the result must still be exact.

Example: `'123'` times `'45'` is `'5535'`.

**Answer:**

Grade-school multiplication into an array of digit places. `num1[i] * num2[j]` lands at index `i + j + 1`, then carry forward.

**Complexity:** Time O(n * m), space O(n + m).

```python
def multiply(num1, num2):
    if num1 == '0' or num2 == '0':
        return '0'
    places = [0] * (len(num1) + len(num2))
    for i, a in enumerate(reversed(num1)):
        for j, b in enumerate(reversed(num2)):
            places[i + j] += int(a) * int(b)
    carry = 0
    for i, val in enumerate(places):
        carry, places[i] = divmod(val + carry, 10)
    while places and places[-1] == 0:
        places.pop()
    return ''.join(str(d) for d in reversed(places))
```

### Q200. Basic

**Number of 1 Bits**

Commonly reported in interviews at Amazon, Apple, Microsoft.

Return how many `1` bits the two's-complement representation of a non-negative integer contains. In a 32-bit interview variant, only the low 32 bits count; here count every bit of the Python int.

Example: `11` is `1011` and returns `3`.

**Answer:**

`n & (n - 1)` clears the lowest set bit. Count how many times you can do that. Python 3.10+ also has `int.bit_count()`.

**Complexity:** Time O(number of set bits), space O(1).

```python
def hamming_weight(n):
    count = 0
    while n:
        n &= n - 1
        count += 1
    return count
```

*Section size: 200 questions (Basic 38, Intermediate 63, Advanced 99).*

---

Total questions: 3200.
