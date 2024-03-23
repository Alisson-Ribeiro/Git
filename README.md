Every git command (or most of them) have arguments which add many possibilities and features to the given command, in this repository you will find the most usual ones. For the Official documentation refer to: [https://git-scm.com/docs]

## A standalone individual developer does not exchange patches with other people, and works alone in a single repository, using the following commands:
(obs: some of these commands will not have a description in this repository)

* git init
* git log
* git clone
* git config
* git alias
* git reset
* git revert
* git checkout
* git switch
* git branch
* git add
* git diff
* git status
* git commit
* git restore
* git merge
* git rebase
* git tag

# Git commands with description for later reference
### Research purposes only

## Main branches commands
### Efficient use of branches is crucial for collaborative and organized development.

* git branch branch-name ---> creates a new branch with the specified name

* git checkout branch-name ---> switches to the specified existent branch

* git checkout -b branch name ---> creates and switches to the specified branch in a single command

* git checkout 'commit-hash' ---> travels along the development timeline to the specified commit

* git branch ---> lists every existent branches in repository

* git branch -d branch-name ---> deletes a local branch

* git branch -m new-branch-name ---> renames a local branch

* git push origin branch-name ---> sends a new branch to remote repository

* git fetch origin branch-name ---> brings (download) a remote branch to your local repository

* git merge branch-name ---> merges a branch into your current branch, creates a merge commit and keeps the whole commit history from both branches. If you use the command 'git log', you will be able to see every commit from both branches now in a single branch. The 'git merge' command doesn't delete the merged branch, you can still checkout to the merged branch and keep working and committing to the branch, if you do so, these commits are not added automatically, so you'll need to 'git merge' again. Git merge is often more used for shared branch work where more people are working together instead of 'git rebase' due to maintaining commit history regardless of project complexity

* git branch -v ---> lists the existent branches in repository, along with last commit info of each branch

## Switch
### Introduced in version 2.23, we have the git switch command, which we can use to switch between branches. Ok, and what about the 'git checkout' command?

### The 'git checkout' command is a versatile one, it can (among other things) restore especific files or even commits, while the new 'git switch' command is used only to switch between branches. futhermore, the 'git switch' command checks for additional consistencies that 'git checkout' doesn't, for example the 'git switch' would abort the operation if it would lead to loss of local changes.

* git switch branch-name ---> switches to the specified branch-name

* git switch - ---> switches back to previous branch, similar to 'cd -'

* git switch --create branch-name ---> creates and switches to the name-specified branch

## Restore
### Introduced in version 2.23, 'git restore' we can use to restore a file to the last committed version of it.

* git restore --staged file.py ---> Undo changes made to a file, equivalent to 'git reset file.py'

## Diff
### Shows changes between commits

* git diff 'commit-hash'..'commit-hash' ---> shows the difference between the 2 specified hash commits

## Tag
### A known checkpoint for your project

* git tag ---> lists the existent tags

* git tag -A 'tag' -m "message" ---> creates a tag with a message, 'tag' generally is like a release format 'V0.1.0'

## Stash
### store your code for later use (it's not a commit). Archives (or stashes) changes you made to the working copy, so you can work anywhere else, and then return to the stashed point. Hint: never commit a not working patch! Stash it instead! Attention: 'git stash' command does not stashes changes made to untracked and ignored files.

* git stash ---> stashes changes for later use
Obs: Stashes are local to your repository, stashes are not sent to remote when pushing (git push)
Obs¹: It does not include untracked and ignored files

* git stash pop ---> brings out of the stash and apllies to the working copy, removing from stash

* git stash apply ---> brings out of the stash and apllies to the working copy, keeping the copy in stash... it's useful if you may apply the same stash to more branches

* git stash -u (or --include-untracked) ---> stashes changes for later use, including untracked files but not the ignored ones

* git stash -a (or --all) ---> stashes changes for later use, includes untracked and ignored files