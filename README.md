# GIT-cheat-sheet

## Ignore versioned files
`git rm -r --cached path/ignore/dir`

## Convert last commit to unstaged changes (uncommit)
`git reset HEAD^`

## Rename branch
`git branch -m [old_name] new_name`
## Rebase to specific commit
`git rebase --onto <new-parent> <old-parent>`
## Merge 2 commits
Say the history is

`git log --pretty=oneline`

> a931ac7c808e2471b22b5bd20f0cad046b1c5d0d c

> b76d157d507e819d7511132bdb5a80dd421d854f b

> df239176e1a2ffac927d8b496ea00d5488481db5 a

That is, A was the first commit, then B, and finally C.
Running `git rebase --interactive HEAD~2` gives you an editor with

> pick b76d157 b
> pick a931ac7 c

Changing c's pick to squash will result in the commit merging with it's predecessor

> pick b76d157 b
> squash a931ac7 c

and save-quitting your editor, you'll get another editor. When you save and quit, the contents of the edited file become commit message of the new combined commit.
## Set editor
`export EDITOR=vim`
## Rebase to current remote master
`git pull --rebase origin master`
## Create a branch from specific commit in different branch
`git checkout -b <branch_name> <commit>`
## Reset branch to given commit
`git reset --hard COMMIT_ID`
## Delete branch
`git branch -d branch_name`
## Undo “git commit --amend” done instead of “git commit”
1. `git reset --soft HEAD@{1}`
2. `commit properly`
 
## Accept all remote changes in all conflicts

`grep -lr '<<<<<<<' . | xargs git checkout --theirs`

`git add .`

`git rebase --continue`

## Removing an entire commit
`git rebase -p --onto SHA^ SHA`
## Recursively converting files from dos line endings to unix line endings
 `find . -name "*" -type f -exec dos2unix {} \;.`

