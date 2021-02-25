# Directories and Files
  - Absolute Path: `/usr/bin/...`
  - Relative Path: `./bin/...`

## Navigation and Structure Information
3. **pwd, cd**
  - `cd -` (change to previous directory)
  - Directory History: `pushd`, `popd`, `dirs`
  - enables you to do `cd -2`
  - https://www.howtogeek.com/659146/how-to-use-pushd-and-popd-on-linux/
4. - mkdir - make directory
   - remove files "rm"; remove directories `rm -rf`
     - `rm -f` - forcefully, `rm -i` - interactively
   - mv & cp
   - `mv` behaves similarly like cp
	- the point is that the oriignal file/dir is gone after the action
`mkdir -p a/b/c/d`
	- creates all directories (if a also does not exist)
- `z`
- `ls`
- `tree` - gives the tree structure of the directory
	- `tree -d` gives only directories (only files)

## Finding Files and Text
`find . -name src -type d` find within the current dir all folders (d) with name src
- find has many useful flags
  - find path -name filename
    - `find . -name index.js`
  - eg, -mtime (time modified)
  - find files of particular type
    - `find . -name "*.js"`
  - -type can be d (dir), f (file)
  - it also has -exec which can specify what to execute when find that files but you need to research how to do that properly (has some funny syntax at the end)
    - `find . -name "*.tmp" -exec rm {} \;`
  - `find . -maxdepth 3 -name '*ui.sh'`
  - fd is upgraded version of find (ignores git structure and colors the output)

- [fzf](https://github.com/junegunn/fzf)
- [fd](https://github.com/sharkdp/fd) - simple and fast alternative to find
	- check how to color the output
	- [fd vs find](https://search.app.goo.gl/GQ2Nsqx)

check `at` & `locate` & `updatedb` commands
  - they can be really useful if you are using some files consistently (and you are doing exactly that)

1. **touch** to create files (without content),
  - `touch {en-US, de-DE}.json`
  - touch can be used to modify timestamp of an (existing) file ("change when it is touched")
