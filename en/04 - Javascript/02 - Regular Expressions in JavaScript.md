
# Regular Expressions in JavaScript

Regular expressions (regex) are powerful tools used for pattern matching, validation, and manipulation in strings. This course covers advanced regex topics and demonstrates how to use them effectively in JavaScript.

## Table of Contents
1. [Introduction to Regular Expressions](#introduction-to-regular-expressions)
2. [Basic Syntax and Patterns](#basic-syntax-and-patterns)
3. [Special Characters: `.`, `^`, `$`, `[]`, `()`, `|`](#special-characters-.,-^,-$,-[],-(),-|)
4. [Quantifiers: `*`, `+`, `?`, `{n,m}`](#quantifiers-,-+,--,-{n,m})
5. [Character Classes: `\d`, `\w`, `\s`, etc.](#character-classes-\d,-\w,-\s,-etc)
6. [Anchors: `^`, `$`, `\b`, `\B`](#anchors-^,-$,-\b,-\B)
7. [Groups and Capturing](#groups-and-capturing)
8. [Assertions: Lookahead and Lookbehind](#assertions-lookahead-and-lookbehind)
9. [Flags: `g`, `i`, `m`, `s`, `y`](#flags-g,-i,-m,-s,-y)
10. [Using `RegExp` Constructor vs Literal Notation](#using-regexp-constructor-vs-literal-notation)
11. [Testing Patterns with `test()` and `exec()`](#testing-patterns-with-test-and-exec)
12. [Replacing with `replace()` and Capturing Groups](#replacing-with-replace-and-capturing-groups)
13. [Matching Multiple Occurrences](#matching-multiple-occurrences)
14. [Regex Performance Considerations](#regex-performance-considerations)

---

## Introduction to Regular Expressions
Regular expressions are patterns used to match character combinations in strings. They are widely used for searching, validation, and manipulation of text.

Example:
```javascript
let regex = /world/;
let result = regex.test("Hello, world!");  // true
```

---

## Basic Syntax and Patterns
Regex patterns are defined by enclosing them between forward slashes (`/pattern/`). Basic patterns match exact character sequences.

Example:
```javascript
let regex = /abc/;
console.log(regex.test("abcdef"));  // true
console.log(regex.test("defabc"));  // false
```

---

## Special Characters: `.`, `^`, `$`, `[]`, `()`, `|`
Special characters have special meanings. These include the dot `.` (any character), `^` (start of string), `$` (end of string), square brackets `[]` (character classes), parentheses `()` (grouping), and pipe `|` (alternation).

Example:
```javascript
let regex = /^a.b$/;  // Matches a string starting with 'a', followed by any character, and ending with 'b'
console.log(regex.test("axb"));  // true
console.log(regex.test("ab"));   // false

let altRegex = /cat|dog/;
console.log(altRegex.test("dog"));  // true
```

---

## Quantifiers: `*`, `+`, `?`, `{n,m}`
Quantifiers define how many times an element in the pattern should occur. `*` means 0 or more, `+` means 1 or more, `?` means 0 or 1, and `{n,m}` means between `n` and `m` occurrences.

Example:
```javascript
let regex = /a{2,4}/;  // Matches 'aa', 'aaa', or 'aaaa'
console.log(regex.test("aaa"));  // true
console.log(regex.test("a"));    // false
```

---

## Character Classes: `\d`, `\w`, `\s`, etc.
Character classes define a set of characters to match. `\d` matches digits, `\w` matches word characters, and `\s` matches whitespace characters.

Example:
```javascript
let regex = /\d+/;  // Matches one or more digits
console.log(regex.test("12345"));  // true
console.log(regex.test("abc"));    // false
```

---

## Anchors: `^`, `$`, `\b`, `\B`
Anchors are used to match positions in strings. `^` matches the start, `$` matches the end, `\b` matches word boundaries, and `\B` matches non-word boundaries.

Example:
```javascript
let regex = /^hello/;  // Matches 'hello' at the start of a string
console.log(regex.test("hello world"));  // true
console.log(regex.test("world hello"));  // false

let wordBoundaryRegex = /\bcat\b/;
console.log(wordBoundaryRegex.test("my cat is cute"));  // true
```

---

## Groups and Capturing
Parentheses `()` are used to group patterns. Capturing groups store matched content for later use.

Example:
```javascript
let regex = /(\d{3})-(\d{2})-(\d{4})/;
let result = regex.exec("123-45-6789");
console.log(result[1]);  // 123 (first captured group)
```

---

## Assertions: Lookahead and Lookbehind
Assertions allow matching a pattern only if it is followed (lookahead) or preceded (lookbehind) by another pattern, without consuming characters.

Example:
```javascript
let lookaheadRegex = /(?=\d{3})\d+/;  // Positive lookahead for a three-digit number
console.log(lookaheadRegex.test("12345"));  // true

let lookbehindRegex = /(?<=@)\w+/;  // Positive lookbehind for '@'
console.log(lookbehindRegex.test("user@example.com"));  // true
```

---

## Flags: `g`, `i`, `m`, `s`, `y`
Flags modify regex behavior. `g` is for global matches, `i` for case-insensitive, `m` for multiline, `s` for dot-all (matches newline), and `y` for sticky matches.

Example:
```javascript
let regex = /hello/i;  // Case-insensitive search
console.log(regex.test("Hello"));  // true
```

---

## Using `RegExp` Constructor vs Literal Notation
You can create regex patterns using literals (`/pattern/`) or the `RegExp` constructor (`new RegExp("pattern")`).

Example:
```javascript
let regexLiteral = /abc/;
let regexConstructor = new RegExp("abc");

console.log(regexLiteral.test("abc"));  // true
console.log(regexConstructor.test("abc"));  // true
```

---

## Testing Patterns with `test()` and `exec()`
The `test()` method returns `true` if the pattern matches, and `false` otherwise. The `exec()` method returns an array of matched results or `null`.

Example:
```javascript
let regex = /\d+/;

// Using test()
console.log(regex.test("abc123"));  // true

// Using exec()
let result = regex.exec("abc123");
console.log(result[0]);  // "123"
```

---

## Replacing with `replace()` and Capturing Groups
The `replace()` method allows you to replace matched patterns with new text. You can also use captured groups to reference parts of the match.

Example:
```javascript
let regex = /(\d{3})-(\d{2})-(\d{4})/;
let replaced = "123-45-6789".replace(regex, "$1.$2.$3");
console.log(replaced);  // "123.45.6789"
```

---

## Matching Multiple Occurrences
The `g` flag allows you to match multiple occurrences of a pattern in a string.

Example:
```javascript
let regex = /\d+/g;
let result = "The numbers are 123, 456, and 789.".match(regex);
console.log(result);  // ["123", "456", "789"]
```

---

## Regex Performance Considerations
Regex performance can vary depending on the complexity of the pattern. Avoid overly complex patterns or unnecessary backtracking, and consider using non-greedy quantifiers.

Example:
```javascript
let regex = /.*a.*b/;  // May cause excessive backtracking on large strings
console.log(regex.test("aaabbb"));  // true
```

---

## Conclusion

### Key Takeaways:
1. Regular expressions are powerful for pattern matching and text manipulation.
2. Special characters and quantifiers define how patterns are matched in strings.
3. Assertions, flags, and capturing groups enhance regex functionality.
4. The `test()` and `exec()` methods are essential for pattern matching.
5. Always consider performance when writing complex regex patterns.

### Practical Exercise:
1. Write a regex to validate a phone number in the format `(XXX) XXX-XXXX`.
2. Use `replace()` to format dates from `MM-DD-YYYY` to `YYYY/MM/DD`.
3. Create a regex to match valid email addresses and use `test()` to validate an email string.
