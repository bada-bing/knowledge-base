# Regular Expressions and Search Patterns
Regular expressions are text strings used for matching a specific pattern, or to search for a specific location, such as the start or end of a line or a word. Regular expressions can contain both normal characters or so-called meta-characters, such as * and $.

Many text editors and utilities such as vi, sed, awk, find and grep work extensively with regular expressions. Some of the popular computer languages that use regular expressions include Perl, Python and Ruby. It can get rather complicated and there are whole books written about regular expressions; thus, we will do no more than skim the surface here.

These regular expressions are different from the wildcards (or meta-characters) used in filename matching in command shells such as bash (which were covered in Chapter 7: Command-Line Operations). The table lists search patterns and their usage.
`.`	Match any single character
`a|z`	Match a or z
`*`	Match preceding item 0 or more times

`$`	Match end of string
`^`	Match beginning of string

`strings` is used to extract all printable character strings found in the file or files given as arguments.
It is useful in locating human-readable content embedded in binary files; for text files one can just use `grep`.

For example, to search for the string my_string in a spreadsheet: `$ strings book1.xls | grep my_string`

text utilities that you can use for performing various actions on your Linux files, such as changing the case of letters or determining the count of words, lines, and characters in a file.

`tr`
-  translates specified characters into other characters or deletes them.
- The general syntax is as follows: `$ tr [options] set1 [set2]`

The items in the square brackets are optional. tr requires at least one argument and accepts a maximum of two. The first, designated set1 in the example, lists the characters in the text to be replaced or removed. The second, set2, lists the characters that are to be substituted for the characters listed in the first argument. Sometimes these sets need to be surrounded by apostrophes (or single-quotes (')) in order to have the shell ignore that they mean something special to the shell. It is usually safe (and may be required) to use the single-quotes around each of the sets as you will see in the examples below.

For example, suppose you have a file named city containing several lines of text in mixed case. To translate all lower case characters to upper case, at the command prompt type cat city | tr a-z A-Z and press the Enter key.

## Command	Usage
`$ tr abcdefghijklmnopqrstuvwxyz ABCDEFGHIJKLMNOPQRSTUVWXYZ`	Convert lower case to upper case
`$ tr '{}' '()'` < inputfile > outputfile	Translate braces into parenthesis
`$ echo "This is for testing" | tr [:space:] '\t'`	Translate white-space to tabs
`$ echo "This   is   for    testing" | tr -s [:space:]` Squeeze repetition of characters using -s
`$ echo "the geek stuff" | tr -d 't'`	Delete specified characters using -d option
`$ echo "my username is 432234" | tr -cd [:digit:]`	Complement the sets using -c option
`$ tr -cd [:print:] < file.txt`	Remove all non-printable character from a file
`$ tr -s '\n' ' ' < file.txt`	Join all the lines in a file into a single line

tee takes the output from any command, and, while sending it to standard output, it also saves it to a file. In other words, it "tees" the output stream from the command: one stream is displayed on the standard output and the other is saved to a file.

For example, to list the contents of a directory on the screen and save the output to a file, at the command prompt type ls -l | tee newfile and press the Enter key.

`cut`
cut is used for manipulating column-based files and is designed to extract specific columns. The default column separator is the tab character. A different delimiter can be given as a command option.

For example, to display the third column delimited by a blank space, at the command prompt type ls -l | cut -d" " -f3 and press the Enter key.
