Regular Expression is a pattern matching language
- really good reference on your system of regex is the documentation for perl ```perldoc perlref```

* ⭐[Page to learn&debug RegEx](https://regex101.com/)
* [Additional Page about RegEx](https://www.regexpal.com/)

### Tips
1. RegEx will try to expand the pattern to match the biggest character set it can match - Greedyiness of RegEx
   - in other words it will not stop once it finds the first match, if the next character could also belong to a match
   - there are also non-greedy RegExes
2. RegExes should be simple!
   - often it is better to solve something with multiple simple regex than to create one complex big one
     - especially if you are searching for something (or want to ensure that something exists)
     - e.g., test if a certain password is longer than 8 chars, contains a special character, contains at least one big letter and at least one small letter
       - this is better done with 4 small than with one really complex regex
3. When you use -r or -E you actually don't need to escape metacharcters!
4. Sed and grep are oriented around lines - line mode operations
	- that means that regex tries to matches within a single line (and that for each line)
		- probably need to specify some flag if you want it to search accross multiple lines


### RegEx in JS
  - check [MDN page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp) and [W3schools](https://www.w3schools.com/js/js_regexp.asp)
    - str.split(re)
    - str.match(re)
    - str.replace(re)
    - re.test(str)
    - re.exec(str)

[6 Handy RegEx for Every Frontend Dev](https://blog.bitsrc.io/6-handy-regular-expressions-every-front-end-developer-should-know-ac9e0c514b71)

Test Regex: https://www.regexpal.com/

System Tools with Regex:
- grep, sed, perl, vim, less

1. An Example how to replace a string in node.js
```javascript
'1 two three'.replace(/1/, 'one');
```
2. Find (Whole) Sentences that contain a Specific Word:
```javascript
str.match(/[^.!?]*\bapple\b[^.!?]*.?/gi);
```
- [^.!?] - matches any character which is not ., ! or ?
- \* matches zero or more sequences of the *preceding* item
- "\b" Matches a Word-boundary position such as whitespace, punctuation, or the start/end of the string.
- apple - the showcase word to search for in the sentence
- "." - matches any character that is not a line-break character

## Meta-Characters

### Quantifiers
- `?` - zero or one time
- `*` - zero or more times
- `+` - one or more times
- `{..}`., {2, }, { ,4}, {2,4}
		- for this in sed you need to provide enhanced mode
  		- e.g.```sed -r 's/o{2,4}/XXXX/g'```
      - or -E (instead of -r) try both

### Character Classes
- `.` - a character class that matches anything

- [] - Character Class Ranges
  - set of different characters that can be matched e.g., "[abc]" or not matched "[^abc]"
- (a|b) - match a or b
---
- \b - Word-boundary
- \w - Word `[A-Za-z0-9_]`
- \W - non-Word Char `[^a-zA-Z0-9_]`
- \s - Whitespace `[\t\r\n\f]`
- \S - non-Whitespace `[^\t\r\n\f]`
- \d - Digit `[0-9]`
- \D - non-digit `[^0-9]`

### Anchors
- ^ - anchor at the beginning
  - e.g. for string "cool beans. cool" ----> sed 's/^cool/Cool/' would replace the cool at the beginning of the sentence
  - not to be confused for the negation in character classes [^...]
- $ - anchor to the end


### Capture Groups
	- Groups
	- '(...)' - Capture Groups
		○ check what are capture groups in regex
		○ this tells the regex engine to save the matched text and make it available for later
		○ every result of the matched capture groups is saved under integer
			§ e.g., $1 for the first match (or for the first capture group)
		○ back-references
			§ use capture groups again in your regex itself
			§ e.g., search for words that are repeated twice
			§ echo 'the the dog dog ' | sed -E 's/(\w+) \1/\1/gi'
				□ here first \1 refers to repetition of the matched word in regex
				□ second \1 refers to replacing the whole match with only one word
				□ result: it will print 'the dog'
					® if you have the the dog dogo
						◊ it will still end with "the dogo" - not sure if that is desired
						◊ that is easy to fix... just end " " after first  and second \1
						◊ echo 'the the dog dog ' | sed -E 's/(\w+) \1 /\1 /gi'
	• (?:) - Non-Capture Groups


## Flags
- g - Global
  - match all occurencies (do not stop at first one)
- i - Insensitive
  - case-insensitive



