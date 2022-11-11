# 17. Regex User Manual

A regex, which is short for regular expression, is a sequence of characters that defines a specific search pattern. When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. They are also frequently used to validate input. This Regex User Manual will show how we can use Regex throughout the code development.

## Summary

RegEx is a tool that may be used to define a search term parameter, and can be applied in many differnt circumstances, accross multiple coding languages. 

For example, the following regular expression can be used to verify that user input is a valid email address:
```
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components
- Please reference the below URL for detailed explanation.
- [https://regexr.com/](https://regexr.com/)

### Anchors
Anchors are unique in that they match a position within a string, not a character.
* `^abc$`	-^beginning / $end of the string
    * `^` Matches the beginning of the string, or the beginning of a line if the multiline flag (m) is enabled. This matches a position, not a character.
    * `$` Matches the end of the string, or the end of a line if the multiline flag (m) is enabled. This matches a position, not a character.

* `\b\B`	-word boundary, not-word boundary
    * `\b` Matches a word boundary position between a word character and non-word character or position (start / end of string). See the word character class (w) for more info.
    * `\B` Matches any position that is not a word boundary. This matches a position, not a character.

### Quantifiers

Quantifiers matches the specified quantity of the previous token.

* `n*n+n?`	-0 or more, 1 or more, 0 or 1
    * "+" Matches 1 or more of the preceding token.
    * "*" Matches 0 or more of the preceding token.
    * "?" Matches 0 or 1 of the preceding token, effectively making it optional.
    * "?" Makes the preceding quantifier lazy, causing it to match as few characters as possible. By default, quantifiers are greedy, and will match as many characters as possible.

* `n{1}n{3,}`	 -Matches for exactly one, three or more
* `{1,6}`  	    -Matches characters between one & six characters.
* `ab|cd`	    -Acts like a boolean OR. Matches the expression before or after the |.

### OR Operator

`|` Acts like a boolean OR. Matches the expression before or after the |.
* `ab|cd`	    -Acts like a boolean OR. Matches the expression ad or cd.

### Character Classes

Character classes match a character from a specific set. There are a number of predefined character classes and you can also define your own sets.

* `[ABC]` Characters inside brakets will match any character in the set.
* `[^ABC]` Adding a caret will match any character that is not in the set.
* `[A-Z]` Add a dash between two characters will select a Range.
* `.` Will Match any characters expect linebreaks. Its like a wildcard and will accpet any input.
* `[\s\S]` A character set that can be used to match any character, including line breaks, without the dotall flag. An alternative is [^] carrot in brackets, but it is not supported in all browsers.
* `\w` Matches any word character (alphanumeric & underscore). Only matches low-ascii characters (no accented or non-roman characters).
* `\W` Matches any character that is not a word character (alphanumeric & underscore).
* `\d` Matches any digit character (0-9)
* `\D` Matches any character that is not a digit character (0-9). Equivalent to [^0-9].
* `\p{Ll}` Matches a character in the specified unicode category.
* `\P{Ll}` Matches any character that is not in the specified unicode category. Requires the u flag.

### Flags
Expression flags change how the expression is interpreted. Flags follow the closing forward slash of the expression (ex. /.+/igm ).

* `i` Ignores case; Makes the whole expression case-insensitive.
* `g` Retain the index of the last match, allowing subsequent searches to start from the end of the previous match.Without the global flag, subsequent searches will return the same match.
* `m` When the multiline flag is enabled, beginning and end anchors (^ and $) will match the start and end of a line, instead of the start and end of the whole string.
* `u` When the unicode flag is enabled, you can use extended unicode escapes in the form \x{FFFFF}.
* `y` The expression will only match from its lastIndex position and ignores the global (g) flag if set. Because each search in RegExr is discrete, this flag has no further impact on the displayed results.
* `s` Dot (.) will match any character, including newline.

### Grouping and Capturing
* `(ABC)` Capturing groups multiple tokens together and creates a capture group for extracting a substring or using a backreference.
* `(?<name>ABC)` Creates a capturing group that can be referenced via the specified name.
* `\1` Matches the results of a capture group. 
* `(?:ABC)` Groups multiple tokens together without creating a capture group.

### Bracket Expressions
* A bracket expression (an expression enclosed in square brackets, "[ ]" ) is an RE that shall match a specific set of single characters, and may match a specific set of multi-character collating elements, based on the non-empty set of list expressions contained in the bracket expression.

### Greedy and Lazy Match
* Greedy matches the longest possible string.
    A Greedy quantifier tells the engine to match as many instances of its quantified token or subpattern as possible. This behavior is called greedy. In the greedy mode (by default) a quantified character is repeated as many times as possible.

* 'Lazy' means matching the shortest possible string.
    A lazy quantifier tells the engine to match as few of the quantified tokens as needed. Laziness is only enabled for the quantifier with ?.

### Boundaries
* The `\b` is an anchor like the caret `^` and the dollar sign `$`. It matches a position that is called a “word boundary”. The word boundary match is zero-length.

* Exactly which characters are word characters depends on the regex flavor you’re working with. In most flavors, characters that are matched by the short-hand character class `\w` are the characters that are treated as word characters by word boundaries. Java is an exception. Java supports Unicode for `\b` but not for `\w`.

*  Since digits are considered to be word characters, `\b4\b` can be used to match a 4 that is not part of a larger number. This regex does not match 44 sheets of a4. So saying “`\b` matches before and after an alphanumeric sequence” is more exact than saying “before and after a word”.

### Back-references
* Backreferences match the same text as previously matched by a capturing group. Suppose you want to match a pair of opening and closing HTML tags, and the text in between. By putting the opening tag into a backreference, we can reuse the name of the tag for the closing tag.

### Look-ahead and Look-behind
* `(?=ABC)` is a lookahead and it asserts that what immediately follows the current position in the string is ABC
* `(?!ABC)` is a negative lookahead and it asserts that what immediately follows the current position in the string is not ABC

* `(?<=ABC>)` is a lookbehind and asserts that what immediately precedes the current position in the string is ABC
* `(?<!ABC)` is a negative lookbehind and asserts that what immediately precedes the current position in the string is not ABC


## Author

Jongwon (Michael) Choi, current Columbia University Coding Boot Camp Student.

Github URL: [https://github.com/](https://github.com/)

* Reference
    * [https://regexr.com/](https://regexr.com/)
    * [https://www.rexegg.com/](https://www.rexegg.com/)
    * [https://www.regular-expressions.info/tutorialcnt.html](https://www.regular-expressions.info/tutorialcnt.html)