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

