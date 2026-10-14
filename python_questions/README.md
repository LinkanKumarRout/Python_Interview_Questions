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

