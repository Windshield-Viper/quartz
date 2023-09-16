# Updating a feature branch
**(From GitHub)**

First we'll update your local master branch. Go to your local project and check out the branch you want to merge into (your local master branch)

```shell
$ git checkout master
```

Fetch the remote, bringing the branches and their commits from the remote repository. You can use the -p, --prune option to delete any remote-tracking references that no longer exist in the remote. Commits to master will be stored in a local branch, remotes/origin/master

```shell
$ git fetch -p origin
```

Merge the changes from origin/master into your local master branch. This brings your master branch in sync with the remote repository, without losing your local changes. If your local branch didn't have any unique commits, Git will instead perform a "fast-forward".

```shell
$ git merge origin/master
```

Check out the branch you want to merge into

```shell
$ git checkout <feature-branch>
```

Merge your (now updated) master branch into your feature branch to update it with the latest changes from your team.

```shell
$ git merge master
```

Depending on your git configuration this may open vim. Enter a commit message, save, and quit vim:

1. Press `a` to enter insert mode and append text following the current cursor position.
2. Press the **esc** key to enter command mode.
3. Type `:wq` to write the file to disk and quit.

This only updates your local feature branch. To update it on GitHub, push your changes.

```shell
$ git push origin <feature-branch>
```