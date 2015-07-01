# Git: Tips And Tricks
Git Cheatsheet with a few nifty tips and tricks

### Git log (Pretty graph view)
```git log --graph; ``` 
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

### Forget added files in git

```git rm -r --cached .```

```git add .``` 

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
