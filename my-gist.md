# Regex Tutorial

Introductory paragraph (replace this with your text)

## Summary

To create a tutorial that explains how a specific regular expression, or regex, functions by breaking down each part of the expression and describing what it does.


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Credits](#credits)

## Regex Components
A regular expression is a pattern that the regular expression engine attempts to match in input text. A pattern consists of one or more character literals, operators, or constructs. For a brief introduction, see .NET Regular Expressions.

Each section in this quick reference lists a particular category of characters, operators, and constructs that you can use to define regular expressions.

We've also provided this information in two formats that you can download and print for easy reference:
<br>

### Anchors

Anchors, or atomic zero-width assertions, specify a position in the string where a match must occur. When you use an anchor in your search expression, the regular expression engine does not advance through the string or consume characters; it looks for a match in the specified position only. For example, ^ specifies that the match must start at the beginning of a line or string. Therefore, the regular expression ^http: matches "http:" only when it occurs at the beginning of a line. The following table lists the anchors supported by the regular expressions in .NET.

```
Anchor	Description
^	By default, the match must occur at the beginning of the string; in multiline mode, it must occur at the beginning of the line. For more information, see Start of String or Line.
$	By default, the match must occur at the end of the string or before \n at the end of the string; in multiline mode, it must occur at the end of the line or before \n at the end of the line. For more information, see End of String or Line.
\A	The match must occur at the beginning of the string only (no multiline support). For more information, see Start of String Only.
\Z	The match must occur at the end of the string, or before \n at the end of the string. For more information, see End of String or Before Ending Newline.
\z	The match must occur at the end of the string only. For more information, see End of String Only.
\G	The match must start at the position where the previous match ended. For more information, see Contiguous Matches.
\b	The match must occur on a word boundary. For more information, see Word Boundary.
\B	The match must not occur on a word boundary. For more information, see Non-Word Boundary.
```

<br>

### Quantifiers

Regular expressions use quantifiers to generate unbounded matching possibilities and other matching amount specifications. An atom can optionally be followed by one of these quantifiers:
```
 *   representing 0 or more occurrences of the atom,
 +   representing 1 or more occurrence of the atom,
 ?   representing 0 or 1 occurrences of the atom,
 ```
the bound {n}   representing exactly n occurrences of the atom,
the bound {m,n}   representing between m and n occurrences of the atom.
The quantifier can optionally be followed by "?" indicating that the match be minimal (non-greedy, reluctant) as opposed to the default maximal (greedy) match.

<br>

### Grouping Constructs

Grouping constructs delineate the subexpressions of a regular expression and capture the substrings of an input string. You can use grouping constructs to do the following:

Match a subexpression that is repeated in the input string.

Apply a quantifier to a subexpression that has multiple regular expression language elements. For more information about quantifiers, see Quantifiers.

Include a subexpression in the string that is returned by the Regex.Replace and Match.Result methods.

Retrieve individual subexpressions from the Match.Groups property and process them separately from the matched text as a whole.

The following table lists the grouping constructs supported by the .NET regular expression engine and indicates whether they are capturing or non-capturing.

```
Grouping construct	Capturing or noncapturing
Matched subexpressions	Capturing
Named matched subexpressions	Capturing
Balancing group definitions	Capturing
Noncapturing groups	Noncapturing
Group options	Noncapturing
Zero-width positive lookahead assertions	Noncapturing
Zero-width negative lookahead assertions	Noncapturing
Zero-width positive lookbehind assertions	Noncapturing
Zero-width negative lookbehind assertions	Noncapturing
Atomic groups	Noncapturing
```


<br>

### Bracket Expressions

A bracket expression is either a matching list expression or a non-matching list expression. It consists of one or more expressions: ordinary characters, collating elements, collating symbols, equivalence classes, character classes, or range expressions. The <right-square-bracket> ( ']' ) shall lose its special meaning and represent itself in a bracket expression if it occurs first in the list (after an initial <circumflex> ( '^' ), if any). Otherwise, it shall terminate the bracket expression, unless it appears in a collating symbol (such as "[.].]" ) or is the ending <right-square-bracket> for a collating symbol, equivalence class, or character class. The special characters '.', '*', '[', and '\\' ( <period>, <asterisk>, <left-square-bracket>, and <backslash>, respectively) shall lose their special meaning within a bracket expression.

The character sequences "[.", "[=", and "[:" ( <left-square-bracket> followed by a <period>, <equals-sign>, or <colon>) shall be special inside a bracket expression and are used to delimit collating symbols, equivalence class expressions, and character class expressions. These symbols shall be followed by a valid expression and the matching terminating sequence ".]", "=]", or ":]", as described in the following items.

<br>

### Character Classes

A character class defines a set of characters, any one of which can occur in an input string for a match to succeed. The regular expression language in .NET supports the following character classes:

Positive character groups. A character in the input string must match one of a specified set of characters. For more information, see Positive Character Group.

Negative character groups. A character in the input string must not match one of a specified set of characters. For more information, see Negative Character Group.

Any character. The . (dot or period) character in a regular expression is a wildcard character that matches any character except \n. For more information, see Any Character.

A general Unicode category or named block. A character in the input string must be a member of a particular Unicode category or must fall within a contiguous range of Unicode characters for a match to succeed. For more information, see Unicode Category or Unicode Block.

A negative general Unicode category or named block. A character in the input string must not be a member of a particular Unicode category or must not fall within a contiguous range of Unicode characters for a match to succeed. For more information, see Negative Unicode Category or Unicode Block.

A word character. A character in the input string can belong to any of the Unicode categories that are appropriate for characters in words. For more information, see Word Character.

A non-word character. A character in the input string can belong to any Unicode category that is not a word character. For more information, see Non-Word Character.

A white-space character. A character in the input string can be any Unicode separator character, as well as any one of a number of control characters. For more information, see White-Space Character.

A non-white-space character. A character in the input string can be any character that is not a white-space character. For more information, see Non-White-Space Character.

A decimal digit. A character in the input string can be any of a number of characters classified as Unicode decimal digits. For more information, see Decimal Digit Character.

A non-decimal digit. A character in the input string can be anything other than a Unicode decimal digit. For more information, see Decimal Digit Character.

<br>

### The OR Operator

* `|` Acts like a boolean OR. Matches the expression before or after the |.
It can operate within a group, or on a whole expression. The patterns will be tested in order. Just as in java will match either set of characters. It will look for this OR that.

<br>

### Flags

Expression flags change how the expression is interpreted. Flags follow the closing forward slash of the expression.

* `i` Ignores case
* `g` Global search retain the index of the last match, allowing subsequent searches to start from the end of the previous match. Without the global flag, subsequent searches will return the same match.
* `m` Multiline flag When the multiline flag is enabled, beginning and end anchors (^ and $) will match the start and end of a line, instead of the start and end of the whole string.
* `u` Unicode
* `y` The expression will only match from its lastIndex position and ignores the global (g) flag if set. Because each search in RegExr is discrete, this flag has no further impact on the displayed results.
* `s` Dot (.) will match any character, including newline.



### Grouping and Capturing
* `(ABC)` Capturing groups multiple tokens together and creates a capture group for extracting a substring or using a backreference.
* `(?<name>ABC)` named capturing group captures groups of a specific name.
* `\1` is a numeric Referance
* `(?:ABC)` Groups multiple tokens together without creating a capture group.

<br>

### Character Escapes

The backslash (\) in a regular expression indicates one of the following:

The character that follows it is a special character, as shown in the table in the following section. For example, \b is an anchor that indicates that a regular expression match should begin on a word boundary, \t represents a tab, and \x020 represents a space.

A character that otherwise would be interpreted as an unescaped language construct should be interpreted literally. For example, a brace ({) begins the definition of a quantifier, but a backslash followed by a brace (\{) indicates that the regular expression engine should match the brace. Similarly, a single backslash marks the beginning of an escaped language construct, but two backslashes (\\) indicate that the regular expression engine should match the backslash.

<br>

## Author

By Corey Nance

* [My Github](https://github.com/coreyNance)
* [Regex Tuturial](https://github.com/coreyNance/Regex_Tutorial)

## Credits

Microsoft Docs
<br>
https://docs.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-options