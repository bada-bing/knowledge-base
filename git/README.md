The section about git VCS
1. [Frequently Used Commands](#Commands)
1. [.git Directory](#.git)
1. [Data Model](#Data-model)

# Commands
- The Git commands are just leaky abstractions over the data storage
- Essentially, a branch is just a text file (inside of .git/refs/) containing a checksum of the last commit on that branch, i.e., a pointer to the commit.

|Command | Description|
| ------------- |-------------:|
|git branch | |
|git checkout -b new_branch_name | create new branch|
|git checkout branch_name | switch to existing branch|
|git checkout | switch to previous branch|

# .git
- Structure of the .git Directory:
  - objects/
    * contains objects/files which contain info about commits, files, directories
  - refs/
    * this is where git stores branch pointers
      - e.g., each branch points to its latest commit
  - HEAD points to currently active branch (or headless commit)

# Data-model


## 3 Areas where code is stored
- Working Area
- Staging Area (i.e., Index)
- Repository
