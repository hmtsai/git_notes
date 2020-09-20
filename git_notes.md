
##################################################################################
# [main/submodules] working directory are clean:
# and you wish update from remote origin to your local [main/submodules] working directory
##################################################################################
$ git pull --rebase && git submodule foreach 'git pull --rebase'

##################################################################################
# check [main/submodules] status
# check [main/submodules] diff
##################################################################################
$ git status && git submodule foreach 'git status'
$ git diff --submodule=diff
(if only git diff, you will see hash value different)

##################################################################################
# you completed your task, and the task modified files in main and submodules
# now you want to commit the changes of them
##################################################################################

1. go to submodules directories, commit each of them first
$ git commit -a -m 'sumodules modify'

2. go to main, check status, you will see (new commit, the new hash of submodule), again commit each of them.
$ git commit -a -m 'main modify and hash of submodule'

3. push main and submodules simultaneously
$ git push --recurse-submodules=on-demand

##################################################################################
# branch
##################################################################################
- show all branches
$ git branch

- create new branch and checkout on the branch
$ git checkout -b [branch_work]

- working on branch_work;
  - finished the work; commit the work
- change back to master
$ git rebase [branch_work];
$ git push --recurse-submodules=on-demand

if on branch, work not yet finish; commit the temp work (WIP) for record.

######################################################
# if you are on a branch, which is branch from master;
# and you wish on this branch to push to origin
# git push origin [local branch]:[remote branch]
# or
# git push origin HEAD:[remote branch]
######################################################
$ git push origin develop:master
$ git push origin HEAD:master

Note: if develop or HEAD leave empty, would delete [remote branch] !!!

######################################################
setup a remote for others clone/pull/push
######################################################

at /path/project, init git; set remote origin; push origin
$ git init .
$ git add .
$ git commit -m 'init commit'
$ git remote add origin /path/project/.git
$ git push origin master

at /path/test
$ git clone /path/project/.git project

at /path/test/project/
work and modify
$ git push
######################################################



######################################################
GitHub: create a git repo at Git Hub
######################################################
echo "# git_notes" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M master
git remote add origin https://github.com/hmtsai/git_notes.git
git push -u origin master
######################################################





