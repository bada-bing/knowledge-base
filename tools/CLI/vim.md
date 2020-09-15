The most important tool to learn Vim is vimtutor

- [4 week Vim plan](https://medium.com/actualize-network/how-to-learn-vim-a-four-week-plan-cd8b376a9b85)
	- https://thoughtbot.com/blog/the-vim-learning-curve-is-a-myth
	- https://danielmiessler.com/study/vim/
	- https://wrongsideofmemphis.com/2013/03/27/vim-speed-is-not-really-the-point/
	- https://yannesposito.com/Scratch/en/blog/Learn-Vim-Progressively/
- [best book to learn vim](https://pragprog.com/book/dnvim/practical-vim)

[Vim Cheatsheet](https://www.fprintf.net/vimCheatSheet.html) [Consider Printing it]

Extensions
- https://opensource.com/article/20/1/vim-email-calendar
- https://opensource.com/article/19/11/vim-plugins?utm_campaign=intrel

• Check in more details what are ANSI codes
Vim (and other CLI tools) use ANSI codes
• these codes are used to manipulate the cursor and the text output
• this is how you get the std output in different colors

On some systems in order to have syntax highlighting you need to install vim-common
`sudo apt-get install vim vim-common`


:set number relativenumber
	- show the actual number of the current line
	- show relative numbers of the lines which surround it

:set complete=., …, kspell
	- set complete specifies where vim will look for auto-completion suggestions
	- kspell is the dictionary but only if the "spell" (spelchecking) is enabled in vim
		○ you set spelling with ":set spell"
	- otherwise to always look for it set "k" instead of kspell
	- kspell is better … because you want to have this option enabled only in some cases
		○ eg, you write commit message, you write email, …


check what are cnext and cprevious

What are registers in VIM?
	- the guy uses them to store some text (like in clipboard)
	- CTRL-a/b (select a/b register)
	- dot register holds the text which you entered last time you were in the INSERT mode

ctrl+r insert text from a register
ctrl+a last inserted text
