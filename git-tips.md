# Some git tips

# Move all uncommitted changes to a new branch and revert the existing branch to HEAD.

```bash
# get into the master branch
git checkout master

# create a new branch for the changes and check it out
git checkout -b dev_branch

# stash the changes until we revert master
git stash

# go back to master
git checkout master

# reset to the last commit
git reset --hard HEAD

# go back to dev_branch
git checkout dev_branch

# re-apply the stashed changes and you are good to go
git stash apply
````

