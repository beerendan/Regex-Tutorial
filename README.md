# Regex Tutorial

Regex make up a small part of the total code written for a wide variety of applications, yet play a very important role in overall functionality. What is a regex? 

## Summary

A **regex**, or regular expression, is a particular sequence of characters used to define specific search patterns. They are mostly used to validate input, however they can be used for a wide variety of additional applications. These include but are not limited to; finding character patterns in a string, find or replace one or more characters in a sequence, or to find and extract types of characters or sequences in strings. This tutorial will help explain regex by breaking down and explaining the components of the expression. To accomplish this, we will use a regex used to verify a URL. The expression is as follows:

                   
                   /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
                   
 
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

The basic structure of a regex begins with its components being wrapped in forward slash (/) characters on either side. This is because it is considered a literal and would not function as intended otherwise. Once that is done, the rest of the expression can be built of from there using the component criteria as follows:

### Anchors
`^`,`$`

Anchors refers to characters used in regex that are implemented by the user to find matches the beginning or end of data strings. In this case, `^` would be used to find data that beginning in the character(s) denoted in the regex. Inversely, `$` is used to find data **ending** in the desired character or string. In each of these cases, the regex is case-sensitive and will only return exact matches, for example `hOtDoG$` would only return a match with matching case, not `hotdog` or `HotDog`. To broaden the search, the format `"hOtDoG$"` can be used with added quotation marks to loosen search parameters.
In our URL verifying expression we are using as an example, the anchors are shown below as the portions without highlight:

`                   
/`**^**`(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?`**$**`/                    
`
 
### Quantifiers
`*`,`+`,`?`,`{}`,`()*`

A quantifier is the component of the expression that is used to determine the limits of the string that the regex is trying to match. Depending on the character used, either the contents of the string itself can be matched, or length of the string by exact length or by a range of characters lengths. The string to be matched is written before the quantifier character, and is known as the **anterior**. Their applications are as follows:
* `*` is used to match a pattern that contains the anterior any number of times.
* `+` is used to match a pattern that contains the anterior a minimum of 1 time.
* `?` is used to match a pattern that contains the anterior either once or not at all.
* `{}` are used to set limits in 3 different ways:
  * `{ n }` where n is the exact number of times the pattern can match.
  * `{ n, }` where the pattern matches a minimum of n times.
  * `{ n, x }` where n is the minimum number of times the pattern matches and x is the maximum.

All of these quantifiers, by default, will attempt to make as many matches as possible. That is known as a quantifier being **greedy**. The inverse would be for a quantifier to be **lazy**, such that it will attempt as few matches as possible. A quantifier can be made lazy by adding `?` after it.

### Grouping Constructs
`()`

Grouping constructs are used to seperate parts of the regular expression into smaller expressions. The goal of this is to make it such that multple distinct parts of a string can be matched to determine their respective functions. Parentheses (`()`) are used to distinguish the various component expressions of the regex, and the results called the **capture group**. Inserting `?:` into the paratheses disables the capture group, whereas inserting `?<>` names the group.

### Bracket Expressions
`[]`

Sometimes, a range of characters to be matched in a string is a more appropriate method of matching. To accomplish this, **bracket expressions** are used, where any character in a string inside the brackets can be used to match individually. For example: `[abc]` would match `abc`,`a`,`b`,`c`,`ab`,`ac` and `bc`. To narrow these parameters, the bracket expression can have a `$` added, `[]$` to match only the entire string inside the brackets. The component can also be modified to work inversely to a regular bracket expression by adding `^` inside the brackets, such that it will only match characters that are NOT inside the brackets`[^]`.

### Character Classes
`\.`,`\d`,`\w`,`\s`

To further narrow the parameters of the regex, **character classes** can be added to match specific character types within the string. They are also case sensitive, which affects the characters they will match. This is defined below:
  * `\.` is used to match any character type
  * `\d` is used to match a single integer
  * `\w` is used to match a single alphabetic character
  * `\s` is used to match a space, or ' '
  * `\D` is used to match any single non-integer character
  * `\W` is used to match any non-alphabetic character
  * `\S` is used to match any non-space character

### The OR Operator
`|`

In cases where it is simpler to not have the contents of a bracket expression meet seperate requirements, the **OR Operator** can be used between two characters of the regex, so that the result searches for instances of the union between those two characters instead of anything containing those to characters. For example, `[xy]` would match `yzx`, but with `x|y`, the only result would be `xy`.

### Flags
`g`,`m`,`i`

There are extra paramaters that can be added to the regex. These **flags** affect how matching takes place by modifying search behavior using select **alpha characters**. They function as follows:
* `g` is for Global search, whereby the function does not return after just the first match and continues to seek additional matches throughout the whole string
* `m` is for Multi-line, where Anchors will match the start and end of a single line, as opposed to an entire string.
* `i` is for Insensitive, meaning that all criteria are no longer subject to parameters are case (UPPER or lower).

### Character Escapes
`\`

The issue with having these different characters defining different components, is that sometimes it is those specific characters that are being searched for to be matched. If they are inserted into a regex, they would cause errors as they would be considered components. To strip a character of its particular designation, a backlash (`\`) is inserted before the character to **escape** it, or to render it no more than another regular character to facilitate search and matching.
## Author

Written by Brendan Bowen, a student in the 2023 Carleton University FullStack Coding Bootcamp. For more information, visit https://github.com/beerendan

https://gist.github.com/beerendan/4d3dcb7654d74db8ba0cab485bbb5860
