# regex-tutorial

In this tutorial, we will be taking a look at what Regex (regular expressions) are and how they are used. 

## Summary

Regex (short for regular expression) is a string of text that allows you to create search patterns that match, manage, and locate text. An example code snippet of regex shows as following:
```
/[\w._%+-]+@[\w.-]+\.[a-zA-z]{2,4}/
```
* A regular expression used to match an e-mail address

Regular expressions can also be used from the command line and within text-editors to find text within a file. 

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

In regular expressions, we use anchors to check if the matching symbol is thestarting symbol or ending symbol of the input string. Anchors are of two types:The first type is the caret `^` that checks if the matching character is the firstcharacter of the input and the second type is the dollar sign `$` which checks if a matchingcharacter is the last character of the input string.

Examples of Anchors:
* `^` - matches any string that start with the anterior word
* `$` - matches a string that end with preceeding word before the character
* Examples:
```
^Hello          matches any string starting with `Hello`
World$          matches any string ending with `World`
^Hello World$   matches exact string
goodbye         matches any string that has the exact text `goodbye` in it
```
### Quantifiers

In regular expressions, quantifiers are used to specify the number of times that a character or a group of characters can be repated. 

* `*` - matches a string that has the anterior followed by zero or more of the last character
* `+` - matches a string that has the anterior followed by one or more of the last character
* `?` - matches a string that has the atnerior follwoed by zero or one of the last character
* `{}` -  matches a string that has the anterior followed by how ever many the number in the brackets of the last character in the string
* `()*` - matches a string that has any anterior characters followed by zero or more copies of the string within the brackets
* Examples:
```
xyz*        matches a string that has xy followed by zero or more z
xyz+        matches a string that has xy followed by one or more z
xyz?        matches a string that has xy followed by zero or one z
xyz{2}      matches a string that has xy followed by 2 z
xyz{2,}     matches a string that has xy followed by 2 or more z
xyz{2,5}    matches a string that has xy followed by 2 up to 5 z
x(yz)*      matches a string that has x followed by zero or more copies of the sequence yz
x(yz){2,5}  matches a string that has x followed by 2 up to 5 copies of the sequence yz
```

### Grouping Constructs

Grouping unifies a pattern or string so that it is matched in a complete block

Examples of Grouping:
* `()` - parentheses creates a capture group
* `(?:)` - using `?:` disables the capturing group
* `(?<>)` - using `?<>` puts a name to the group
* Examples:
```
x(yz)           parentheses create a capturing group with value yz
x(?:yz)*        using ?: we disable the capturing group
x(?<bar>yz)     using ?<bar> we put a name to the group
```

### Bracket Expressions

Bracket Expressions are characters enclosed by a bracket `[]` matching any single character within the brackets. 
*note: if the first character within the brackets is a `^` then it signifies any chracter **not** in the list, and is unspecified whether it matches an encoding error. 

Examples of Bracket Expressions: 
* `[]` - matching any single character within the brackets
* `[]%` - matching the string inside the brackets before the `%`
* `[^]` - matching any string that has not a letter from within the brackets (negation of expression)
* Examples:
```
[xyz]         matches a string that etiher has x or x y or x z (same as x|y|z)
[x-y]         similar to case above
[u-zU-Z0-9]   a string that represents a single hexadecimal digit, case insensitively
[0-9]%        a string that has a character from 0-9 before a %
[^a-zA-Z]     a string that has not a letter from a to z or from A to Z
```

### Character Classes

Character Classes (Character Set) tells the regex engine to match only one out serveral specific characters, such as digits, words, or whitespace

Examples of Character Classes:

* `\d` - matches a single character that is a digit
* `\w` - matches a word character (any alphanumeric character plus underscore)
* `\s` - matches a whitespace character (including tabs and line brakes)
* `.` - matches any character
* the capital case for any aformentioned characters will inverse the match
* Examples:
```
\d    matches a single any digit 0-9
\w    matches a single any character that is a-z
\s    matches ` `
.     matches any character
\D    matches a single non-digit character
\W    matches a single any non-character that is a-z
\S    matches a single non-` `
```

### The OR Operator

OR Operators (Alternation Operator) matches on of a choice of regular expressions: if you put the character(s) representing the alternation operator between any two characters in the regular expression, the result matches the union of the strings that those two characters match.

Examples of OR Operators:

* `(|)` - matches a string that has any anterior characters followed by the characters on the left or right of the vertical bar
* `[]` - matches a string that has any anterior characters without any characters within the brackets
* Examples: 
```
x(y|z)  matches a string that has x followed by y or z (and captures y or z)
x[yz]   matches a string that has x, but without capturing b or c
```

### Flags

Flags are optional parameters that we can add to a plain expression to make it search in a different way. Each flag is denoted by a single alphabetic character, and serves different purposes in modifying the expression's searching behavior.

Examples of Flags:
* `g` - Global, does not return after the first match, which restarted any subsequest searches from the end of the previous match (Makes the expression search for all occurences)
* `m` - Multi-line, when enabled the Anchors (^ $) will match the start and end of a line, rather than the whole string
* `i` - Insensitive, makes the entire expression case-insensitive
* Examples:
```
/Hello/g   matches all `Hello` in the test
/Hello/m   matches the beginning and ending of each line with `Hello`, rather than the whole string `Hello` itself
/Hello/i   matches all `hello` despite case (Hello, hEllo, heLlo, hellO, hello, HELLO all match)
```

### Character Escapes

A backslash `\` is used in regular expressions to escape the next character. This
allows us to include reserved characters such as `{ } [ ] / \ + * . $ ^ | ?` as matching characters. To use one of these special character as a matching character, prepend it with `\`.

For example, the regular expression `.` is used to match any character except anewline. Now, to match `.` in an input string, the regular expression`(f|c|m)at\.?` means: a lowercase `f`, `c` or `m`, followed by a lowercase`a`, followed by a lowercase `t`, followed by an optional `.`character.

## Author

Github: https://github.com/bEbOuNdLeSs
