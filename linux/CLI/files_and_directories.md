# Directories and Files

## Navigation and Structure Information
3. **ls, pwd, cd**
  - `cd -` (change to previous directory)
  - Absolute Path: `/usr/bin/...`
  - Relative Path: `./bin/...`
4. - mkdir - make directory
   - remove files "rm"; remove directories `rm -rf`
     - `rm -f` - forcefully, `rm -i` - interactively
   - mv & cp
5. **touch** to create files (without content),
  - `touch {en-US, de-DE}.json`
  - touch can be used to modify timestamp of an (existing) file ("change when it is touched")

## Finding Files and Text
`find . -name src -type d` find within the current dir all folders (d) with name src
- find has many useful flags
  - eg, -mtime (time modified)
  - -type can be d (dir), f (file)
  - it also has -exec which can specify what to execute when find that files but you need to research how to do that properly (has some funny syntax at the end)
    - `find . -name "*.tmp" -exec rm {} \;`
  - fd is upgraded version of find (ignores git structure and colors the output)

check locate and updatedb
  - they can be really useful if you are using some files consistently (and you are doing exactly that)

`grep -R foobar` will search for foobar in all files in current dir
- check also its (newer) alternative "rg" or "ripgrep"
