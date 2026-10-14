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

