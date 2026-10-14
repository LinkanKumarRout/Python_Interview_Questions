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

