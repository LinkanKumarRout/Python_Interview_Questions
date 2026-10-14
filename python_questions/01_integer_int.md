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

