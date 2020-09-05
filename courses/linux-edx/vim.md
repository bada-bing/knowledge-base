`echo "some text" > some_file` (will print "some text" to some_file, and overwrite existing content if it exists)
`echo "additional text" >> some_file` (will append "some text" to some_file)
# Text Editors
## Vim
`vim -r myfile` (edit in a recovery mode from a system crash)

vim has three modes: Command, Insert, and Line.

### Cheat Sheets
- https://www.linuxtrainingacademy.com/vim-cheat-sheet/
- https://www.fprintf.net/vimCheatSheet.html
- https://vimsheet.com/
- https://phoenixnap.com/kb/vim-commands-cheat-sheet
- https://vim.rtorr.com/

`:r file2` read in file2 and insert in current position
`:w ` write to the file
`:w myfile` write out the file to myfile
`:w! file2` overwrite file2
`:x or :wq` exit vim and write out modified file
`:q!` quit even though modifications are not saved


`:0 or 1G`	To move to beginning of file
`:n or nG`	To move to line n
`:$ or G`	To move to last line in file
CTRL-F or Page Down	To move forward one page
CTRL-B or Page Up	To move backward one page
^l	To refresh and center screen


a	Append text after cursor; stop upon Escape key
A	Append text at end of current line; stop upon Escape key
i	Insert text before cursor; stop upon Escape key
I	Insert text at beginning of current line; stop upon Escape key
o	Start a new line below current line, insert text there; stop upon Escape key
O	Start a new line above current line, insert text there; stop upon Escape key
r	Replace character at current position
R	Replace text starting with current position; stop upon Escape key
x	Delete character at current position
Nx	Delete N characters, starting at current position
dw	Delete the word at the current position
D	Delete the rest of the current line
dd	Delete the current line
Ndd or dNd	Delete N lines
u	Undo the previous operation
yy	Yank (copy) the current line and put it in buffer
Nyy or yNy	Yank (copy) N lines and put it in buffer
p	Paste at the current position the yanked line or lines from the buffer.

Typing `: sh` or maybe `: sh command` opens an external command shell. When you exit the shell, you will resume your vi editing session.

Typing `:!` executes a command from within vi. The command follows the exclamation point. This technique is best suited for non-interactive commands, such as : `! wc %`. Typing this will run the wc (word count) command on the file; the character **%** represents the file currently being edited.

in vim check:
1. what is leader key
2. plugins and dotfiles
3. vim macros
4. marks (works like bookmarks)
5. `:earlier` will give you the erlier version of the same file

# 3. VIM
Missing Semester [lecture notes](https://missing.csail.mit.edu/2020/editors/)

Complex key combinations are usually labeled in docs in 3 exchangable ways
1. `^V`
2. `Ctrl-V`
3. `<C-V>`
- they all mean the same "CTRL + V"

## Split Panes and Buffers
[vim splits move faster and more naturally](https://thoughtbot.com/blog/vim-splits-move-faster-and-more-naturally)
- in VIM "open files" are called "open buffers"
- VIM has tabs and windowses (like in tile managers)

- `0` goes to the beginning of the line
- `^` goes to first not empty char on the line (not space char)

similar to k and l, use `^U` and `^D` to go up and down (but 10 lines up or down)

## Visual Mode
`Shift-V` (❓) puts you in Visual-Line mode (selects the whole line for you) which you can then copy or do whatever you want
- y - to copy/yank

`~` (tilda) changes the case of selected characters
