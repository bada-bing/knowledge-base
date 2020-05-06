[Course Link](https://frontendmasters.com/courses/git-in-depth/)
[Code and Slides](https://github.com/nnja/advanced-git)

# Useful Commands
`git config --global core.editor <YOUR_EDITOR>`
## Log
`git log` uses pager to display list of commits (shows the history of your repository)
- by default it is set to **less** (use --no-pager flag (needs to be in front of `log`))
- log has many useful flags which can be combined
- `git log --since="2 weeks ago"`
- `git log --name-status --follow -- <file>` (log files that have been moved or renamed, git tracks that file and how it was changing)
- `git log -grep <regexp>` - search for commit messages that match a regular expression
- `git log --diff-filter=R --stat` - include/exclude files based on what kind of modification was done (A) - added, (D) - deleted, (M) - modified
- `git log --grep=mail --author=miki --since=2.weeks`
- How to reference Commits
  - ^ or ^n (1st or nth parent commit) (e.g., in merges you usually have 2 parents, but you can have even more, and this is how you reference them)
  - ~ or ~n (1st commit back following 1st parent and n commits back following only 1st parent)
  - ~ and ^ can be combined
![How to reference commits](assets/git-reference-commits.png)

## Show
`git show <commit>`
`git show <commit> --stat` show files changed in commit
`git show <commit>:<file>` look at file from another commit

## Diff - shows you changes
  - `git diff` - unstaged changes (what could be in next commit )
  - `git diff --staged` - staged changes (what will be in next commit)
  - important: git diff A B is not the same as git diff B A
  - you can use diff for branches
    - git branch --merged master -  check which branches are merged with dev/master and maybe they can be cleaned up
    - git branch --no-merged master


# Fixing Mistakes
- checkout
  - pulls data from repo to staging area (switching branches), but also from staging area to working area
  - 1.) Update HEAD pointer; 2.) copies the commit snapshot to Staging Area; 3.) copies the content to working area
  - `git checkout -` checkouts the previous branch
  - `git checkout -f <branch-name>` will force the checkout and overwrite existing changes (be careful)
  - `git checkout -- file` - replace the working area with the version from the current staging area (i.e., it will discar unsaved changes and apply content from the last commit)
    - these "--" signify the end of the command operation and start of positional parameters
    - `git checkout <commit> -- file` will update the staging area to match the commit and then update the file in working area
      - this is extremely useful for restoring deleted files!
      - `git checkout <deleting_commit>^ -- <file_path>` (^ references the parent commit) - we find the commit where we deleted the file, then we find its parent and from there we retrieve the deleted file and put it back to staging and working areas
- reset (important command... do research)
  - works differently for paths and for commits
  - soft, mixed and hard
  - for commits: moves the head pointer and modifies file
    - soft: moves HEAD and the current branch
    - mixed: soft + reset staging area
    - hard: mixed + reset working area
- revert
  - fixes mistakes by creating opposite changes from the specified commit
  - the original commit stays in the repository
- clean
  - will remove untracked files
  - `--dry-run` to see what will be deleted
  - `-f` to do deletion
  - `-d` will clean dirs

- amend
  - this does not really rewrite previous commit, it actually creates a copy of it (and changes something) and moves pointer to that commit


- rebase
  - give a commit a new parent (i.e., new base commit)
  - extremely powerful, research
    - here is one link [yt link](https://www.youtube.com/watch?v=f1wnYdLEpgI)
      - important, he does not use it really well, but comments are really good


- git branch creates new branch (but does not check it out)
# Git Foundations
Git - Distributed VCS
- resembles key-value store
- value is the data, key is the hash of the data (sha1; 40-digit hexadecimal number)
  - hash returns the same output for the same input every time
    - therefore, you can't really change commits (since if you change any of the content it will give you different sha1)
    - this is really important to prevent all sorts of corupption problems
  - under the hood git hash is produced by `git hash-object` function

Where does Git store its data?
- `.git` dir
- `git init` will set up .git dir for new repository
  - in .git/objects it is where we store 3 types of git objects (blob)
    - inside each dir starts with 2 characters which are first 2 characters of hash (key) of each git object

-❗ You can't store empty dirs in GIT
-❗ In git identical content is only stored once (and that is where git trees (as type of git objects) take the main role)
-❗ GIT objects are compressed (can't be direclty observed)
  - `git cat-file -t "hash-of-the-object"` (returns you the type of the object)
  - `git cat-file -p "hash-of-the-object"` (-p as pointer; returns you the content of the object)

Git stores the data in 3 types of objects
1. Blob (stores compressed data (i.e., source code), along with some metadata in a header)
2. Tree - contains pointers (using sha1) to blobls and to other trees (because dirs can be nested)
   - Git stores filenames and directory structures info about blobs in a **tree**
   - additional metadata, mode (executable file, symbolic link, ...), type of pointer (blob or tree), filename or dir_name
     - trees are directed graphs; snapshots of the repository (point at files and dirs)
3. Commit - points to a tree and contains metadata: author, date, message, parent commit
   - Commit is a code snapshot (combination of the changes from the staging area and the previous commit)

# References - Pointers to Commits
- stored in .git/refs
  - .git/refs/heads is where branches live (files there point to last commits of respective branches)
3 Types (tags, branches, HEAD - a pointer to the current branch/commit)
  - HEAD determines what will be the parent of the next commit (head usually points to the name of the current branch)
  - switching branches in git is fast because, it is essentially just changing the pointer
  - tags are like bookmarks (pointers to commits)
    - they can be lightweighted and annotated `git tag -a` (annotations add metadata like authors, ...)
    - tags are not automatically pushed to remote (you need to do it manually `git push --tags` (or something similar))
- Branch pointer moves with each new commit to the branch
  - tag is a snapshot, it does not change where it points to
  - tags are used for releases (e.g., v1.0, ...)
- Detached Head happens when we checkout some commit (which is not pointer to branch) and we make commits after them (now because they don't have the branch they are in detached head)
  - if we don't create branch for these commits they will become dangling commits once we checkout something else

# Repository
- When you clone remote repository (i.e., from gitlab, github) it checkouts by default the default branch (i.e., master or development)
- Where code lives:
  - Working Area - untracked files - files/changes not handled by git or not in your staging area
  - Staging Area (i.e., Cache, Index) - what changes will be in the next commit
    - Clean staging area is not empty! but it is rather an exact copy of your last commit
    - it is a binary file in .git/
    - ⭐ Git knows that some file is changed, because its SHA1 is now changed (i.e., sha1 of the new file is not the same as sha1 of the file in repo)
    - use `git ls-files -s` to see what is in staging area
  - Repository - files that Git knows about and it contains all your commits
- Stash - save un-commited work (safe from destructive operations)
  - useful for switching between branches while you are in the middle of work
  - by default git stashes only tracked files, if you want to include untracked you must specify it with flag `git stash --include-untracked`
    - `git stash --all` (kepp all files, even ignored)
  - useful commands
    - `git stash`; `git stash list`
    - `git stash show stash@{0}` - show the content
    - `git stash apply` apply the latest stash; `git stash apply stash@{0}` apply a specific stash;
    - `git stash save "some name"`
    - ❓❓❓ you can start branch from stash
    - `git checkout <stash-name> -- <filename>` grab single file from stash
    - `git stash pop` - remove the last stash and apply changes
    - `git stash drop` - remove the last stash; `git stash drop` stash@{n} - remove the nth stash;
    - `git stash clear` - removes all stashes
    - `git stash -p` to partially apply stash (similar to `git add -p`)
# Git Workflow
- `git add <file>`
- `git rm <file>` - remove file in the next commit (this is like removing the file and staging that change)
- `git mv <file>` - rename a file in the next commit
- 🌟 `git add -p` - partial staging - allows you to stage commits in chunks and interactively (useful when you did to many changes for one commit)


## Merge and Fast-Forward
- merge commits are commits which have more than one parent (i.e., usually 2 parents development and feature branch)
  - merge commit is a marker when a new feature is merged into master/development
  - `git cat-file -p <sha1-of-commit>`
- fast-forward happens when there is a clear path how to update one branch to include changes from the other
  - by updating the pointer of the other branch to the pointer of the second branch they will have same commits and changes
    - `git merge --no-off` enforces merge commit, even when it is not necessary (it will not use fast-forward)
- ❓ research on how "git merge" works and how merge conflicts appear
- git rerere - Reuse Recorded Resolution (git saves how you resolve a merge conflict and next time reuse the same resolution)


How to write commit messages
- Add the body of the message after new line when the commit is bigger (not just the first line using -m "...")
- Commit message is in **future tense**. 'Fix' vs 'Fixed'
  - That is a short subject followed by a blank line
  - After that follows a description of the current behavior, a short summary of why the **fix** is needed. Mention side-effects
  - Description should be broken into 72 char lines

# Remote
- git repository stored remotely (github)
- origin is the default name of the server you cloned from
- `git remote -v`
- clone - copy of repo on your local machine
- fork is - copy of repo on your github account

what is difference between origin and upstream

- In order to stay up-to-date with new changes, you need to set up upstream
- you can check out a remote branch, with tracking
  - `git checkout -t origin/feature`
- tell git which branch to track the first time you push
  - `git push -u origin feature`
- git branch --v
  - tells you which branch are you tracking on your local branch
- `git fetch` - get info from the server without pushing or pulling (pulls down all changes which happend on the server, but does not change local repo)
- `git pull` (under the hood it is `git fetch` && `git merge`)
  - `git pull --rebase` - fetch & update your local branch to copy the upstream branch, then replay any commits you made via rebase
- `git push` - you can only push if there will be no conflict
  - to see which commits are not yet pushed upstream use `git cherry -v`


How to recover Lost Work
- ORIG_HEAD (commit where HEAD was pointing before reset or merge)
  - `git reset --merge ORIG_HEAD`
- If you need to go back in time and find a commit that is no longer referenced (i.e., dangling commit) you can look in reflog
  - it has slightly different syntax: HEAD@{2} means "the value of HEAD 2 moves ago"

research on github and gitlab shortcuts especially for code browsing
