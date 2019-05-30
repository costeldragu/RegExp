# RegExp

This file will contain useful information's about how RegExp work

| Type                          | Example                        | RexExp |
|-------------------------------|--------------------------------|--------|
| Digit                         | 1                              | \d     |
| whiteSpace                    | (Tab, space, new line)         | \s     |
| Word character                | Alphanumeric or underscore (_) | \w     |
| Anything but a Digit          | a                              | \D     |
| Anything but a whiteSpace     | 1                              | \S     |
| Anything but a Word character | -                              | \W     |

####Quantifiers:

* \* = 0 or more
* \+ = 1 or more
* ? = 0 or 1
* {m,n} at least m and at most n


| Quantifier | Meaning          | Example  |
|------------|------------------|----------|
| *          | 0 or more        | \d*      |
| +          | 1 or more        | \s+      |
| ?          | 0 or 1           | \w?      |
| {m}        | Exactly m reps   | \w{3}    |
| {m, }      | At least m reps  | \s{2, }  |
| {m, n}     | From m to n reps | \d{3,5}  |
| {0, n}     | At most n reps   | \s{0 ,5} |


####Greedy Backtracking
 As Many As Possible (longest match).
By default, a quantifier tells the engine to match as many instances of its quantified token or subpattern as possible. 

| Quantifier Mode  | Meaning                     | Example                                                     |
|------------------|-----------------------------|-------------------------------------------------------------|
| (default) Greedy | Match as much as possible   | \d* - as many digits as possible                            |
| ? Lazy           | Match as little as possible | \s+? - As few spaces as possible                            |
| + Possessive     | Like Greedy but no back off | \w*? – As many word characters as possible, but no back-off |


####Named Capture Groups
(?<spaces>\s+)<?<text>\w+)(?<digits>\d+)
    
####Case Insensitive Flag    

* (?i)
* ((?i)my-pattern)
* ((?i)my-(-?i)pattern)
* ((?id)my-pattern) groupCount=1
* (?i:my-pattern) groupCount=0
   
####Boundaries
* \btom - will match fist tom from tom-tom
* tom\b - will match last tom from tom-tom  
* \btom\b - will match last tom from tom but not tom-tom 

####Look-around

Rich (?=Man) - will match Rich is the second work is Man 


| Anchor/Boundary | Meaning                                                     |
|-----------------|-------------------------------------------------------------|
| ^               | Beginning of a line                                         |
| $               | End of a line                                               |
| \b              | The position of, or after, a word character                 |
| \B              | The position of, or after, a non-word character             |
| \A              | The beginning of the input string                           |
| \G              | The end of the previous match                               |
| \Z              | The end of the input except for possibly a final terminator |
| \z              | The end of the input                                        |

| Syntax     | Meaning                  | Explanation                                                                              |
|------------|--------------------------|------------------------------------------------------------------------------------------|
| (?<=regex) | Look-behind              | Asserts that the regex pattern immediately precedes the current capture position         |
| (?=regex)  | Look-ahead               | Asserts that the regex pattern immediately follows the current capture position          |
| (?<!regex) | Negative look-behind     | Asserts that the regex pattern does not immediately precede the current capture position |
| (?!regex)  | Negative look-ahead      | Asserts that the regex pattern does not immediately follow the current capture position  |
| (?>regex)  | Atomic non-capture group | Does not capture or backtrack                                                            |

Anchors & Boundaries

Both describe a position in an expression,
but don’t capture any characters.
“Anchors” refer to positional patterns, only
needing to check a single character such as
end of line or end of input.
“Boundaries” refer to word boundaries,
checking the character before and after.

##Examples :

Search in logs : (\d{4}-\d{2}).*?WARN -

| Type          | Example                                | RexExp                         |
|---------------|----------------------------------------|--------------------------------|
| Phone         | 212-345-6789 or (212)-345-6789         | \(?\d{3}\)? [-\s]?\d{3}-?\d{4} |
| Date          | 2019-07-2 or 2019/7/2 But not 2019/7-2 | \d{4}([ -/])?\d{1,2}\1\d{1,2}  |
| Zip Code      | 11223 or 11223-4567                    | \d{5}(-\d{4})?                 |
| Non - numeric | Victor_Grazi                           | [\w&&[^\d]]+                   |
| Alphabetic    | AaBbCc                                 | [A-Za-z]+                      |