# Email Validator - Regular Expressions

Regex, shorthand for Regular Expression, is a way for developers to identify types of text such as, phrases, numbers, emails, and many other types of different text. They use a pattern of certain characters to identify a given piece of text and are often modular, with each component responsible for identifying different parts of text. In this example, I will be going over a regular expression that is commonly used to valiate email adresses. 
## Summary

The following expression: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ , is often used to identify email adresses. It's components consist of identifiers than can find lowercase letters and digits, the @ symbol, a period, and a domain. To learn more about each component of this regex, continue reading where you will find a table of contents on each component of the regex! 

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
Here we have the regex as a whole, which represents a generic template for emails.
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

The components of this regular expression are as follows: 
- First component:
    - it is important to note that the regular expression begins with / and is followed by a ^. the ^ indicatex where the input will begin, and is where we will begin to decyoher the regular expression.
    - in this regular expression, the first component ( ([a-z0-9_\.-]+)@ ) is surounded by a pair of prenthesis. The brackets  encapsulate the following search patterns:
        - 'a-z' : This character set matches any lowercase letter
        - '0-9': This character set matches any digit 1-9
        - '_' : Represents an underscore
        - '\.': represents a period. When a backslash is present before any special character, it is indicative that the special character should be treated litteraly, therefore \. indicates that the expression should match a period in the text.
        - '-' : When a hyphen is at the end of the brackets, it indicates to litterally match for a hyphen
        - The + on the outside of the square bracket indicates that there must be one more of these characters present

- Second component 
    -  The second component of the regex follows the @ symbol from the previous component, ([\da-z\.-]+)\. , and breaks down as follows:
        - '\d' : Represents any Aarabic numeral ( is equivalent to [0-9])
        - 'a-z' : matches any lowercase letter
        - '\.' : (notice there are two in this segment of the expression) represents a period. When a backslash is present before any special character, it is indicative that the special character should be treated litteraly, therefore \. indicates that the expression should match a period in the text.
        - '-' : When a hyphen is at the end of the brackets, it indicates to litterally match for a hyphen
        - '+' : Indicates a + sign 

- Third component
    - The third component is : ([a-z\.]{2,6}) and breaks down as follows:
        - 'a-z' : Any lowercase letter 
        - '\.' : a period or . symbol 
        - {2,6} : This component in a regular ecpression can be represented as X{n,m}, where X is the item or expression that will be evaluated and "n" is 0 or a positive integer, "m" is a positive integer, and m > n. this means that the expression (X) must match at least "n" and at most "m" occurrences of the preceding item "x". In the case ofn this component, X is [a-z\.], and the expression must match any of the characters represented in the bracket at least 2 times, and at most 6, which is the length of most domains ( .com, .net, .ct, etc)



### Anchors
Anchors are used to indicate where in the string a set of characters will be matched. Some common anchors used in regex are the '^' and '$' symbol. The carot (^) points to the beggining of a string or line and is also written at the beggining of the expression, while  the dollar sign ($) points to the end of a string or line and is written at the end of the expression. For example, in our expression for email validator:
 /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/,

 the carot symbol is found at the start of the expression and indicates that a search for the first two components will start at the beggining of the string, while the dollar sign is found at the end of the expression, indicating the search for the third component must be matched at the end of the string. 

### Quantifiers
These sets of characters indicate the number of characters or expressions that will be natched. common quantifiers include: 
- '*'
- '+'
- '?'
- '{n,m}'

### OR Operator
The or opperator is | and indicates to match a character set before or after the operator. For example n|m indicates to match either n or m. 

### Character Classes
Regular expressions only care about 3 character classes, digits, special characters, or leters. All which can be found in any body of text! 

### Flags
Flags are optional parameters that can change the the behavior of a search. These flags are typically represented as a sinlge lower case letter. In Java Script there are 6 flags: 
- i : ignores casing 
- g : means global, searches for all occurences in a global scope of the string. If used, the regex search engine will continue to search for the indicated set after the first match is found ( like command + f in the browser! ) 
- s : Dot All, makes the wild character . match newlines as well.
- m : multiline, makes the boundary characters ^ and $ match the beginning and ending of every single line instead of the beginning and ending of the whole string.
- y : sticky, makes the expression start its searching from the index indicated in its lastIndex property 
- u : Unicode, makes the expression assume individual characters as code points, not code units, and thus match 32-bit characters as well.

### Grouping and Capturing
Grouping and Capturing in regular expressions is the practice of grouping multiple characters within parenthesis in order to create single units of search criteria, for example, (ab) represents a group where "a" "b" is the search criteria. 
    Capturing groups can be numbered and are numbered by counting the number of open paranthesis from left to right. In the example, ((A)(B(C))), there are four groups: 
- ((A)(B(C)))
- (A)
- (B(C))
- (C)
### Bracket Expressions
Bracket expressions create what we call metacharacters, which differ from litteral characters ( which represent the literal representation of the symbol that is being used). A metacharacter can be a set of characters or a single character and is definded as a pair of square brackets encapsulating a set of characters tht you want to match. 
### Greedy and Lazy Match
Greedy matches ( the default ) and Lazy matches are different ways to search about a string. A greedy match will search as much of the string as possible, back tracking itself in an iterable manner, untill all matching sets are found,  while a Lazy match will search through each character of a string one, by one, collecting the matching sets as the search takes place. 
### Boundaries
The boundary characters are ^ and $ and they indicate where a search should take place within a given string or body of text. The ^ indicates a search should start at the beggining of the string while the $ indicates that a search should begin at the end of a string, line or text. 
### Back-references
A back-reference is the portion of a string that is matched to the capturing group. After a set is matched, it is stored in memory for later recall as a back-reference. A back-reference is specified in the regular expression as a backslash (\) and can be followed by a digit that indicates the number of the group to be recalled. For example, the expression (\d\d) defines one capturing group matching two digits in a row, which can be recalled later in the expression via the backreference \1. To match any 2 digits, followed by the exact same two digits, you would use (\d\d)\1 

### Look-ahead and Look-behind
Look-ahead and Look-behind are similare search techniques but function in opposite ways. The syntax for a lookahead expression looks like this: X(?=Y) , where X is the expression to be matched, but only if followed by Y, so an expression like '30(?=@) will match the number 30, but only of it is followed by @ in a string. regex can also perform a negative Lookahead, where a set is only matched if it is not followed by a specified criteria. A negative lookahead looks like this : The syntax is: X(?!Y)
On the contrary, a Lookbehind matches a set only if it is preceeded by a specified criteria, that is, a match will only be captured if a specified criteria is found before it. The syntax for a Lookbehind looks like this: (?<=Y)X, matches X, but only if there’s Y before it. a negative lookbehind: (?<!Y)X, matches X, but only if there’s no Y before it.

#### Sources: 
- https://docs.oracle.com/javase/tutorial/essential/regex/groups.html
- https://www.codeguage.com/courses/regexp/flags#:~:text=A%20flag%20is%20an%20optional,a%20single%20lowercase%20alphabetic%20character.
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Character_classes
- https://javascript.info/regexp-greedy-and-lazy
## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
Thank you for reading my RegEx tutorial! My name is Jacob Garcia and I am an aspiring Software engineer. I am currently taking a course that will enhance my learning and help improve my skills in the developer world. In my free time I like to stay active by working out at the gym, exploring mountains or canyons or learning about software development! To see some of my projects check out my [Github profile](https://github.com/DevJake99?tab=repositories)
