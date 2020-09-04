[SSH Subsection](./ssh.md)

# Remote
- git repository stored remotely (github)
- origin is the default name of the server you cloned from
- `git remote` will list all the remotes which are known to this GIT repo
- `git remote add origin ..`
- `git remote -v`
- `git clone <url> <local-folder-name>` clone - copy of repo on your local machine to the <local-folder-name>
- fork is - copy of repo on your github account
- `git clone --shallow` - will clone only the last snapshot; this will be much faster but will not include all commits and all branches

`git branch --set-upstream-to=origin/master`

what is difference between origin and upstream
- I think that `origin` is just a (commonly-accepted) name, and upstream is the concept itself... origin is upstream, origin2 is also upstream

- In order to stay up-to-date with new changes, you need to set up upstream
- you can check out a remote branch, with tracking
  - `git checkout -t origin/feature`
- tell git which branch to track the first time you push
  - `git push origin master:master` (map local `master` branch to remote `master` branch)
  - `git push -u origin feature`
- `git branch --v`
  - tells you which branch are you tracking on your local branch
- `git branch --vv` -- tell about branches in very verbose way
- `git fetch` - get info from the server without pushing or pulling (pulls down all changes which happend on the server, but does not change local repo)
  - once you fetch changes you can do `git merge` (to include changes from remote to your local repo)
- `git pull` (under the hood it is `git fetch` && `git merge`)
  - `git pull --rebase` - fetch & update your local branch to copy the upstream branch, then replay any commits you made via rebase
- `git push` - you can only push if there will be no conflict
  - to see which commits are not yet pushed upstream use `git cherry -v`
