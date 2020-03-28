# Move uncommitted changes to a new branch and revert the existing branch to HEAD.

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

# Git pull specific folder

```
To add to this comment (particularly if you want to turn this series of commands into a script), I would amend it as follows:

mkdir <dir>
cd <dir>
git init
git remote add origin -f <URL>
git config core.sparseCheckout true # enable this

echo "/absolute/path/to/folder" > .git/info/sparse-checkout # if you don't start with root you are liable to download multiple folders wherever the name you specified is matched.

git pull origin master
```
* https://github.community/t5/How-to-use-Git-and-GitHub/How-can-I-download-a-specific-folder-from-a-GitHub-repo/td-p/88#

