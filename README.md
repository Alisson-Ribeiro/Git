# Git commands with description for later reference
### Research purposes only

## Main branches commands
###  Efficient use of branches is crucial for collaborative and organized development.

* git branch branch-name ---> creates a new branch with the specified name

* git checkout branch-name ---> switches to the specified existent branch

* git checkout -b branch name ---> creates and switches to the specified branch in a single command

* git branch ---> lists every existent branches in repository

* git branch -d branch-name ---> deletes a local branch

* git branch -m new-branch-name ---> renames a local branch

* git push origin branch-name ---> sends a new branch to remote repository

* git fetch origin branch-name ---> brings (download) a remote branch to your local repository

* git merge branch-name ---> merges a branch into your current branch, creates a merge commit and keeps the whole commit history from both branches. If you use the command 'git log', you will be able to see every commit from both branches now in a single branch. The 'git merge' command doesn't delete the merged branch, you can still checkout to the merged branch and keep working and committing to the branch, if you do so, these commits are not added automatically, so you'll need to 'git merge' again. Git merge is often more used for shared branch work where more people are working together.

* git branch -v ---> lists the existent branches in repository, along with last commit info of each branch