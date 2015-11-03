# Git: Tips And Tricks
Git Cheatsheet with a few nifty tips and tricks

### Git log (Pretty graph view)
```git log --graph ``` 
This displays your commits in a nice tree form.

By making the following alias you get:
* colors
* graph of commits
* one commit per line
* abbreviated commit IDs
* dates relative to now
* commit references
* author of the commit
* And the alias is:

```git config --global alias.lg "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative"```

And every time you need to see your log, just type in

```git lg```

or, if you want to see the lines that changed

```git lg -p```

### Stash
```git stash```								                  : Stash current changes

```git stash save "appropriate caption here"```	: Name stashed changes

```git stash apply```							              : Apply the last stashed item

```git stash pop```							                : Apply and drop most recent stash

```git stash list```							              : List all stashes

```git stash clear```							              : Clear all entries in stash

### Cherry pick and apply to current branch

```git cherry-pick ###SHA-1##```

In cases picking one single commit is not enough and you need, let's say three consecutive commits - rebase is the right tool, not cherry-pick. 

### Forget added files in git

```git rm -r --cached .```

```git add .``` 

### Git Aliases

```git config --global alias.<handle> <command>```
 
```git config --global alias.st status```

### Deleting a branch both locally and remotely

##### Locally:

```git branch -D local_branch_name```

```-D``` force deletes, ```-d``` will give you a warning if it’s not already merged in.

##### Remotely:
 
```git push origin --delete remote_branch_name```

(or)

```git push origin :remote_branch_name```

### Keeping a forked repo in sync with the main repo

```git remote add upstream <path-to-the-main-repo>```

```git fetch upstream```

```git rebase upstream/master```

### Different branch name for local and remote

Branch out locally:

```git checkout -b local_branch_name```

Checkout branch with an easy to remember local_branch_name

Push to remote & set upstream:

```git push -u origin local_branch_name:remote_branch_name```

Push the local branch to remote repo with a different descriptive name remote_branch_name

```git branch --set-upstream-to=origin/remote_branch_name```

Set your push.default to upstream to push branches to their upstreams (which is the same that pull will pull from), rather than pushing branches to ones matching in name (which is the default setting for push.default, matching).

```git config push.default upstream```

### Squash PR commits into one

Fetch from upstream (when merging clone to main upstream branch) or origin (when merging branch to master)

```git fetch upstream```

```git checkout mybranch```

```git merge upstream/master```
     
If necessary, resolve conflicts and git commit...
     
```git reset --soft upstream/master```

```git commit -am 'Some cool description for a single commit'```

```git push -f```

Note that it's super important that you merge before resetting, and that the argument is the same master branch. Otherwise you risk messing up your local history.

The --soft parameter tells Git to reset HEAD to another commit, but that’s it. If you specify --soft Git will stop there and nothing else will change. What this means is that the index and working copy don’t get touched, so all of the files that changed between the original HEAD and the commit you reset to appear to be staged.

### Git aliases

``git config --global alias.l "log --oneline --graph"``

### Keeping a forked repo in sync with the main repo

``git remote add upstream <path-to-the-main-repo>``

``git fetch upstream``

``git rebase upstream/master``

### Deleting last commit from git

If you already pushed, use ``git revert``

If no one else is using your branch:

``git reset —hard HEAD~1 (or) git reset —hard <sha1-commit-id>``

``git push origin HEAD —force``
