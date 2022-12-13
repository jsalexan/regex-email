# Regex - Matching an Email Address

A Regex (regular expression) is a handy tool developers can use to define search patterns in blocks of data, large and small. One of the more common uses is in validating email addresses, as their specifications can be quite complex. In this tutorial, we'll look at one such regular expression and breakdown its components to see how it works. 

## Summary

Here is an example of a regex to match an email address: <br><br>
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`<br><br>
This may look complicated, but you won't need an [Enigma machine](https://en.wikipedia.org/wiki/Enigma_machine) to crack this code. Keep reading to learn all the components and get a better understanding of how and why it works.

## Table of Contents

- [Introduction to Components](#introduction-to-components)
- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
<br><br>
## Regex Components

### Introduction to Components
In JavaScript, there are two ways to create a regex object. The example in this gist uses *literal notation*, wrapping the pattern in forward slash characters (**/**). But you could also write it as a *RegExp constructor*, which is instead wrapped in quotation marks.

Also note, regex is *case sensitive*. This will be important!<br><br>

### Anchors
Anchors identify the start and end of the regular expression. Here is what they look like: <br>
`^ or $`<br>
The carrot (`^`) denotes a string that *begins* with the characters that follow it. `/^([a-z0-9_\.-]`<br>
On the other end, the dollar sign (`$`) denotes where the regex ends and which characters should precede it. `([a-z\.]{2,6})$/`<br>
Emails begin and end with a very specific pattern, so anchors assist in verifying the structure.
In the next sections you'll learn more about how those characters are specified.
<br><br>

### Quantifiers
Quantifiers set the limits on how many times a character, or group of characters, must be found to match the pattern you're looking for. They include characters such as: <br><br>
```*``` - Match zero or more times.<br>
```+``` - Match one or more times.<br>
```{n}``` - Match exactly "n" times (replace with the number of your choosing).<br><br>
In our example, the ```+``` adds the components together: **email name + email carrier or service + .com** 
The ```{}``` contain the quantity for which we're searching. In our example, we want the last part of the email to contain only 2-6 characters from the following set: `[a-z\.]` (between a-z and `.`). Therefore we write `([a-z\.]{2,6})`<br><br>

### Grouping Constructs
The grouping constructs allow you to check smaller sections of a string to see if they meet your requirements. In our example, we use `()` to enclose these short phrases as sub-expressions, like `([a-z\.]{2,6})`. This allows us to define the structure of the email name, email carrier or service, and the ".com" separately. <br><br>

### Bracket Expressions
We've already explored two uses of brackets in regex (quantifier and grouping), but another that's used in our example is `[]`. These square brackets define a set of characters to match. From our example: <br>
`[a-z0-9_\.-]` - any character a-z, 0-9, or `_`  `.`  `-` in the email name. <br><br>
`[\da-z\.-]` - any single digit number, character a-z or `.`  `-` in the email carrier/service name. (See below for the meaning of `\d`)<br><br>
`[a-z\.]` - any character a-z or `.`. This part of the regex would be seeking the equivalent of the .com part of an email address. <br><br>The backslash is used to escape a special character (see [character escapes](#character-escapes). <br><br>

### Character Classes
A Character Class defines a set of characters, such as the [bracket expressions](#bracket-expressions) mentioned above. Another common character class used in our example is the `\d`. This denotes we're looking for any single digit number. In our example `[\da-z\.-]`, it is looking for single digit numbers, any letter a-z or the characters `.`  `-` .<br><br>

### The OR Operator
The bracket expressions allow you to specify that you are searching for any letter **OR** number **OR** character within your set parameters, without using a special **OR Operator**. But if you wanted to specify 'OR' outside of a bracket expression, you could use the character `|`. For example, you could write [abc] or a|b|c. They both mean 'a or b or c'. (This operator is not used in our example.)<br><br>

### Flags
In regular expressions, you may use optional flags that allow you to add advanced search features. For example, adding `g` after the slash at the end of your regex would change the search to "global", meaning it would return all instances, not just the first found. Including `i` would flag the search as case-insensitive. There are six flag types in total. You can learn more about them [here](https://javascript.info/regexp-introduction).<br><br>


### Character Escapes
When you need to include any special character *literally*, you can 'escape' it by including a backslash in front of it. We described this functionality above in the [Bracket Expressions](#bracket-expressions) section, where we wanted to include a literal `.` in our regex. Without a backslash before it, the `.` would indicate a wildcard in regex, so escaping is very important to get the results you want. <br><br>
For more information on regex, check out this handy [cheat sheet](https://www.keycdn.com/support/regex-cheat-sheet).

## Author

[Jennifer Alexander-Hill](https://github.com/jsalexan) 🦆
