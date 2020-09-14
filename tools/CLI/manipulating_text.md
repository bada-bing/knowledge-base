# Manipulating Text Tools
1. grep [Global RegEx Print]
   - search for patterns in file(s)
   - ```grep [flags] 'pattern' file```
     - e.g., ```grep -i '[^.!?]*apple[^.!?]*[.]' some_file.txt```
     - this command should print all lines which contain word apple in the file **some_file.txt**
       - probably not completely correct but will work in most cases
     - regex pattern goes into ''
   - looks for patterns in lines, and prints each line that matches the pattern
     - lines are separated with "\n" newline characters
  - http://www.robelle.com/smugbook/regexpr.html

  Flags
  | Flag         |                                                                                                                             Description |
  | ------------ | --------------------------------------------------------------------------------------------------------------------------------------: |
  | -i           |                                                                                                                    case **i**nsensitive |
  | -v           |                                                                                         invert matches (lines which do not match regex) |
  | -c [--count] | General Output **C**ontrol (supress normal output, instead print the count of lines which match the regex, i.e., number of occurencies) |
  | -o | only point the matching part of the line, not the whole line |
  | -E [aka egrep] | escape special characters |
  | -F | ❔ don't treat the match string as regex |
  | -r [recursive] | search all files in a directory |
  | -f | only show filenames of the files that matched |
  | -A [after-context] NUM | prints NUM of lines which follow the matched pattern |
  | -B [before-context] NUM | prints NUM of lines which come before the matched pattern |
  | -C [context] NUM | prints NUM of lines which surround the matched pattern |
  | -a  | search binaries (treat binary data as text, instead of ignoring it) |

-E enables to use special characters such as ".+" (one or more of any character); without this flag you would have to escape +, i.e., ```.\+```

Alternatives to grep (better for searching code):
- ack, ag, ripgrep
- zgrep: grep for gzip files [gzip command](https://www.geeksforgeeks.org/gzip-command-linux/)
- pgrep: https://linuxize.com/post/pgrep-command-in-linux/
2. sed [Stream Editor]
  - Used for string manipulation using regex
  - ```sed options 'command' file```
    - command: e.g, - ```s/<PATTERN>/<REPLACEMENT>/<FLAGS>``` (s - *substitute*)
    e.g., cat readme.md | sed 's/apple/XXXX/gi'
      's' - the s at the beginning of the pattern is specific to PERL, SED and VIM and specifies that we are performing substitution
      Flags:
      - g - global
      - i - (case)-insensitive
      - m - treat strings as multiple lines
      - s - treat string as a single line

  - meta-characters if no flag is specified, need to be escaped
    - "+" needs to be escaped like this "\+" (and ? as well \? )
    - interestingly, "*" don't need to be escaped e.g., "ap*le" (will match&replace apple and apppppple)
  - How to use sed
    - ```echo 'hello beep boop' ``` | sed 's/b..p/XXXX/g

		CAPTURE GROUPS - https://stackoverflow.com/questions/4609949/what-does-1-in-sed-do

		(External) Flag -i (not part of the pattern)
		"sed -i" does the inline substitution of a file (changes and saves automatically for you)
