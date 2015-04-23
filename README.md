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