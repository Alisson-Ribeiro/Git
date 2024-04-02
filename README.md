# Git commands with description for later reference
### Research purposes only

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
### Shows changes between commits, branches, files and others

* git diff ---> shows the changes made (and were not commited) since the last commit by default

* git diff branch1 branch2 ---> shows a comparison between the 2 specified branches

* git diff 'commit-hash' 'commit-hash' ---> shows the difference between the 2 specified hash commits

* git diff --color-words ---> highlight the changes made with red (deletion), green (insertion) and white (not touched by any change)

## Tag
### A known checkpoint for your project

* git tag ---> lists the existent tags

* git tag -A 'tag' -m "message" ---> creates a tag with a message, 'tag' generally is like a release format 'v1.0'

* git tag -d v1.0 ---> deletes the specified tag

### Sharing of tags is similar to branches. By default, 'git push' does not send tags to remote. Tags demand a explicit 'git push' ---> example: 'git push origin v1.0'

## Stash
### Store your code for later use (it's not a commit). Archives (or stashes) changes you made to the working copy, so you can work anywhere else, and then return to the stashed point.
### Hint: never commit a not working patch! Stash it instead!
### Attention: 'git stash' command does not stashes changes made to untracked and ignored files.

* git stash ---> stashes changes for later use
### Obs: Stashes are local to your repository, stashes are not sent to remote when pushing (git push)
### Obs¹: It does not include untracked and ignored files

* git stash pop ---> brings out of the stash and apllies to the working copy, removing from stash
### Obs: Brings out of the stash the most recent by default
### Obs¹: You can choose which stash to bring by informing its id as last argument ---> example: 'git stash pop stash@{2}'

* git stash apply ---> brings out of the stash and apllies to the working copy, keeping the copy in stash... it's useful if you may apply the same stash to more branches

* git stash -u (or --include-untracked) ---> stashes changes for later use, including untracked files but not the ignored ones

* git stash -a (or --all) ---> stashes changes for later use, includes untracked and ignored files

* git stash save "message" ---> adds a message to your stash, useful when more stashes are created so you don't get lost

* git stash show ---> shows a summary, or you can add as an option -p (or --patch) to visualize the full stash comparison

* git stash drop stash@{n} ---> deletes the stash informed in brackets, for a single drop

* git stash clear ---> to delete all stashes

## Alias
### Alias is not a command in git, but a tool you can configure to obtain efficiency and productivity. Aliases are created using the 'git config' command. See these examples:

* git config --global alias.co ---> checkout

* git config --global alias.br ---> branch

* git config --global alias.st ---> status

### It creates shortcuts with global storage for the given command

## Log
### See what and where is anything in your project. The 'git log' and its variations add so many visualizations for you to handle the info you need.

* git log ---> shows every commit in current branch (no filter)

* git log --oneline ---> a summary of git log

### The 'git log' command includes many options to show comparisons with each commit. The most commom ones are: '--stat' and '-p'.

### The '--stat' option shows the number of insertions e deletions for each changed file by each commit. It's useful for a brief summary of changes made by each commit. For example: the following commit added 67 lines to the file 'file.py' and removed 38 lines.

### If you want to see the changes introduced by each commit, you can use the option '-p' in 'git log'. Howerver, for commits with many changes, the output can be long and hard to handle

* git shortlog ---> is a special version of 'git log', groups each commit by author and shows the first line of each commit message. It's a easy way to see where someone is working at.

* git log --graph ---> draws a ASCII graphic representing the branch structure of the commit history, it's usually used with '--oneline' and '--decorate' options. It's a good tool for simple repository with few branches, but for larger projects with many branches you'd rather use a tool called 'Sourcetree'. Link: [https://www.atlassian.com/br/software/sourcetree]

* git log -n ---> filter and shows only the n last commits

* git log --after="2024-1-1" ---> filter and shows only the commits created after the specified date. Also works with '--before="2024-1-1"'

* git log --after="2024-1-1" --before="2024-1-2" ---> filters and shows the commits created between the specified dates

* git log --author="Jose" ---> filters and shows commits created by a specific user. You can also add arguments to the filter, for example: '--author="jose\\|Maria"' ---> this will return commits created by Jose or Maria

* git log -S"Hello, World!" ---> filters and shows commits that introduced a specific line

* git log main..feature ---> shows the commits present in feature branch, but not in main branch. It's the progress the feature branch has achieved since it was separated from main

## Collaborative workflows
## How to sincronize (git remote) || the 'git remote' command is an interface to manage a list of remote entries to the repository

## How to view git remote settings

* git remote ---> lists the remote connections you have with other repos

* git remote -v ---> lists the remote connection with other repos with the URL included for each connection

### Shows where you are (fetch)ing from and where you (push)ing to

## How to inspect a remote

* git remote show 'remote-connection' ---> Gives a detailed output about the remote settings. This output contains a list of related branches to remote and also to the attached terminals to fetch and push