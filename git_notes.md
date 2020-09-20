# Git Notes
### Clone git repo [and submodules if any]
```
git clone [--recurse-submodules] [/path/to/xxx.git] [local branch name (xxx)]
```
### Pull new commits from remote origin and submodules
```
$ git pull --rebase [&& git submodule foreach 'git pull --rebase']
```
### check working directory status, diff
```
$ git status && git submodule foreach 'git status'
$ git diff --submodule=diff
(if only git diff, you will see hash value different)
```
### You completed your task, including changes in main and submodule working directory, now you want to commit the changes of them.

> 1. go to submodules directories, commit each of them first
```
$ git commit -a -m 'sumodules modify' 
```
> 2. go to main, check status, you will see (new commit, the new hash of submodule), again commit each of them.
```
$ git commit -a -m 'main modify and hash of submodule'
```
>3. push main and submodules simultaneously
```
$ git push --recurse-submodules=on-demand
```
## Git branch
branch is just a tag (label) point to the hash object. master is the default (usually) branch of a git repo.

 - show all branches
```
$ git branch
```
- create new branch and checkout on the branch
```
$ git checkout -b [branch_work]
```
- working on [branch_work];
  - finished the work; commit the work
  -  change back to master, rebase the [branch_work] commits on master.
```
      $ git rebase [branch_work];
      $ git push --recurse-submodules=on-demand
```
> *if the work not yet finish on a branch, and you are interrupted; you can commit the temp work (WIP) for record. later come back to continue.*

> if you are on a branch, which is branch from master;  and you wish on this branch to push to origin
> git push origin [local branch]:[remote branch]
> or
>  git push origin HEAD:[remote branch]
```
$ git push origin develop:master
$ git push origin HEAD:master
```
***Note: if develop or HEAD leave empty, would delete [remote branch] !!!***

## Setup a remote for others clone/pull/push
Suppose you are now at /path/project, init git; set remote origin; push origin
```
$ git init .
$ git add .
$ git commit -m 'init commit'
$ git remote add origin /path/project/.git
$ git push origin master
```
go to /path/test, clone the project.
```
$ git clone /path/project/.git project
```
go to /path/test/project/, work and commit. finally push to to project upstream
```
$ git push
```






