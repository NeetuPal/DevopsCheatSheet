# CheatSheet

### Check disk usage of your home directory
```sh
du -sh ~
```
### Check total + free space available
```sh
df -h ~
```
### Check large files
```sh
du -ah ~ | sort -rh | head -20
```

# git reset
## Works at the commit level and sometimes staging.

### Moves the file out of staging back to working directory, without losing changes.
```sh
git reset HEAD <file>
```

### Removes the commit but keeps all changes staged.
```sh
git reset --soft HEAD~1
```

### Removes commit, moves changes back to working directory (unstaged).
```sh
git reset --mixed HEAD~1   
```

### Completely removes the last commit and all its changes.
```sh
git reset --hard HEAD~1
```

## git restore(Undo) → affects working directory and staging area.

### Restores the file from HEAD (last commit).
```sh
git restore <file>
```
### Removes it from staging area, but your changes stay in the file.
```sh
git restore --staged <file>
```
### rings src/app.py content from commit abc123.
```sh
git restore --source=abc123 src/app.py
```
### Discards all local modifications (not staged).
```sh
git restore .
```
### Completely wipes out local modifications and unstages everything.
```sh
git restore --staged --worktree .
```
## Case Rebase: You created feature branch from main, then both got new commits

### First stash the changes then rebase so that new changes reflect in local from remote the stash pop to bring back to working directory then
```sh
git rebase main
```
### Always start with: Fetch(to see what changed)
```sh
git fetch origin
```
### Shows all configured remotes with their fetch/push URLs.
```sh
git remote -v
```
### You can check the installed AWS CLI version with this command:
```sh
aws --version
```
### Confirms installation path.
```sh
which aws
```





