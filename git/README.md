[whats-inside-the-git-directory](https://blog.safia.rocks/post/171558325240/whats-inside-the-git-directory) [article]
[Deep Dive into Git](https://www.youtube.com/watch?v=fBP18-taaNw) [Must watch conference talk about GIT]
[ProGit Book](https://git-scm.com/book/en/v2)
[Understanding Git - Branching](https://hackernoon.com/understanding-git-branching-2662f5882f9)
[Collection of useful .gitignore templates](https://github.com/github/gitignore)

The section about git VCS
1. [Frequently Used Commands](#Commands)
2. [.git Directory](#.git)
3. [Data Model](#Data-model)
4. [Hints](#Hints)
5. [Configuration](#configuration)
6. [SSH](./ssh.md)

# Commands
- The Git commands are just leaky abstractions over the data storage
- Essentially, a branch is just a text file (inside of .git/refs/) containing a checksum of the last commit on that branch, i.e., a pointer to the commit.

|Command | Description|
| ------------- |-------------:|
|git branch | |
|git branch -D branch_name | remove branch|
|git checkout -b new_branch_name | create new branch|
|git checkout branch_name | switch to existing branch|
|git checkout | switch to previous branch|
|git reset --hard <sha-id>| take your code base to the state it was at time of some commit |
|git cherry-pick <sha-id>| borrow code from some commit |
|git reflog | helps to recover your project history |
|git gc | preserves all commits of all reflogs |

# Configuration
You need to make sure that your commit credentials are stored in GitLab/GitHub as well
	- e.g., I had an issue that in my local git config I was using e-mail address mpetkovic@wps-management.de but in gitlab user-settings there was only mpetkovic@wescale.com and therefore my commits were not properly recognized
	- you can manage these settings in Gitlab here `GITLAB_SERVER/profile/emails` (e.g., https://gitlab.wescale.io/profile/emails)
    [link from the source of the answer](https://gitlab.com/gitlab-org/gitlab-foss/issues/21578)

# .git
- Structure of the .git Directory:
  - objects/
    * contains objects/files which contain info about commits, files, directories
  - refs/
    * this is where git stores branch pointers
      - e.g., each branch points to its latest commit
  - HEAD points to currently active branch (or headless commit)

# Data-model
*[Understanding GIT - Data Model](https://hackernoon.com/https-medium-com-zspajich-understanding-git-data-model-95eb16cc99f5)* [ARTICLE]
- GIT generates 40-chars checksum hash for every object
  - first 2 chars are used for dir/ name and the rest (38 chars) for object file name
- 3 Types of Objects
  - BLOB Objects: contain a snapshot of the files and their checksum header
  - TREE Objects: contain a list of files with pointers to BLOB objects assigned to them
    - this is how git associates which file has which content at a given time
    - TREE Objects can be nested (they can point to other tree objects)
      - Think about it this way: Every BLOB represents a file and every TREE object represents a directory, so if we have nested directories we will have nested TREE Objects
  - COMMIT Objects: contain a reference to their TREE Objects

## 3 Areas where code changes reside from GIT's point of view
*[Understanding GIT - Index](https://hackernoon.com/understanding-git-index-4821a0765cf)* [ARTICLE]
[Watch this YT lecture for better understanding](https://www.youtube.com/watch?v=xbLVvrb2-fY)
- Working Directory/Area
  - *project/*
  - All the changes you make will remain in the WD until you add them to the staging area (- git add ...)
- Staging Directory/Area (i.e., Index)
  - project/.git/index
  - preview area of the next commit
  - /index file keeps track of file changes which are related to staging area
    - this file is storing info about each file in the repository
      - mtime, file, wdir, stage, repo
- Repository
  - project/.git/objects
  - after the commit, the changes are saved as commit, blob and tree objects

## Hints
- When using git clone to to clone the project (from GitHub/GitLab) always use the small button *"copy URL"*
  - if you copy the URL manually, it often happens that it will include some empty space or something similar and the git clone command will fail
- Git Hooks https://githooks.com/
  - [How to use JS in git hooks](https://medium.com/@Sergeon/using-javascript-in-your-git-hooks-f0ce09477334)
- Git Secret
  - used for encryption of sensitive data in the repository (e.g., passwords, db-connection-strings)
  - [article](https://www.techrepublic.com/article/how-to-install-and-use-git-secret/)
### Common Problems
- [How to push to GitHub through HTTPS when you have 2-factor authentication enabled?](https://mycyberuniverse.com/how-fix-fatal-authentication-failed-for-https-github-com.html)
  - This happens once 2-factor authentication is enabled.
  - TL;DR; The solution is to create personal access token which will be used instead of the password to authenticate your account
  - **Even Better: Use only SSH.**

- Line Endings
  - ⭐[Mind the end of your line](http://web.archive.org/web/20150912185006/http:/adaptivepatchwork.com:80/2012/03/01/mind-the-end-of-your-line/)
    - article about how to configure git to handle line endings LF - CRLF
  - [SO - Force LF EOL in git repo and working copy](https://stackoverflow.com/questions/9976986/force-lf-eol-in-git-repo-and-working-copy)
    - read the first answer till the end! actually the config from the second answer is used
  - [.gitattributes](https://git-scm.com/docs/gitattributes)
  - If a file is unspecified then Git falls back to the core.autocrlf setting and you are back in the old system.
		* you added .gitattributes to prevent LF conversion to CRLF and especially to prevent that CRLF enters into repo
		* Set your global configuration file
			* git config --global core.autocrlf input
	* Additionally use .editorconfig (and related plugins) to ensure that LF is always used over CRLF
