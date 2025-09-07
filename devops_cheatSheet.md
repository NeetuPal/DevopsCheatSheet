# Cloud shell cheat sheet

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
### Brings src/app.py content from commit abc123.
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
### when pushing the first time->Sets upstream (tracking branch) → Git now knows the link.
```sh
git push -u origin main
```
### If you forgot -u the first time, you can set it afterward:
```sh
git branch --set-upstream-to=origin/main main
```
### rename branch to main
```sh
git branch -M main
```
### to check the latest 3 versions of Terraform
```sh
gh release list --repo hashicorp/terraform --limit 3
```
```sh
gh release list --repo aws/aws-cli --limit 3
```
```sh
gh release list --repo cli/cli --limit 3
```

### Linux often does store git credentials here
```sh
~/.git-credentials
```
### If you see osxkeychain → Git is storing credentials in macOS Keychain.
```sh
git config --get credential.helper
```

### Paste the token when prompted.
```sh
gh auth login --with-token
```
### The flag --with-token does not take the token directly on the command line.
Instead, it tells gh to read the token from standard input (stdin).
That’s why your terminal is just sitting there waiting.
```sh
echo "ghp_..." | gh auth login --with-token
```
### check the GitHub CLI (gh) status
```sh
gh auth status
```
### Kill (Ctrl + C) if you don’t need the process anymore. <br>EOF (Ctrl + D) if a program is waiting for input and you’re done.<br>Pause (Ctrl + Z) if you want to stop for now and maybe come back later.

 ### Show current shell    
 ```sh
echo $SHELL
```

### Show parent process (to see which shell launched)
```sh
ps -p $$
```
### In AWS CloudShell, sometimes you don’t have root privileges (sudo). If timedatectl fails, you can still force your session to use IST by setting the environment variable:
```sh
export TZ="Asia/Kolkata"
```
### Clean result — only one time, in 12-hour format. the reason for the second $() and the cut is to remove the duplicate time from uptime.
```sh
echo "$(date +"%I:%M:%S %p") $(command uptime | cut -d" " -f4-)"
```
### %F: Short for %Y-%m-%d (Year-Month-Day)- Alternative Date Formats:
```sh
$(date +%Y%m%d_%H%M%S)
```
```sh
$(date +%Y-%m-%d_%H-%M-%S)
```
```sh
$(date +%s)
```
### Remove the longest matching pattern that ends with a forward slash from the beginning of the string
```sh
local filename="${1##*/}"
```
### basename returns  → "/" for below cmd
```sh
"$(basename '/')"
```
### If Git saved your GitHub credentials in Keychain, running this will output your password or Personal Access Token (PAT)
```sh
security find-internet-password -s github.com -w
```
### List your repos
```sh
gh repo list <your-username> --limit 10
```
### Short reusable alias (like git set-origin aws_user)
```sh
git config --global alias.set-origin '!f() { git remote set-url origin https://github.com/$(gh api user --jq .login)/$1.git; }; f'
```
### To check specifically for origin
```sh
git remote get-url origin
```
### These details will be attached to your commits, but ⚠️ they don’t confirm GitHub authentication yet.
```sh
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```
### Check your Git identity
```sh
git config --global --list
```
### This will show the first 5 lines. Confirm your line 1 edit is really there.
```sh
head -n 5 create-aws-user.sh
```
### Use PAT directly in the remote URL
```sh
git remote set-url origin https://<USERNAME>:<PAT>@github.com/<USERNAME>/<REPO>.git
```
### Verify if CLI has credentials
```sh
aws sts get-caller-identity
```
### Create repo from Mac Terminal
```sh
mkdir secret_setup
```
```sh
git branch -m main
```
```sh
echo "# secret_setup" > README.md
```
```sh
cd secret_setup
```
```sh
echo "# secret_setup" > README.md
```
```sh
git init
```
```sh
git add README.md
```
```sh
git commit -m 'add' README.md
```
```sh
gh repo create secret_setup --public --source=. --remote=origin --push
```
### Push a file to git repo
```sh
mkdir new_folder
```
```sh
cp "/c/Users/Naresh Pal/Downloads/project-bolt-sb1-vqfzyeew/project/delete-aws-users-by-tag.sh" .
```
```sh
git init
```
```sh
git remote add origin https://github.com/NeetuPal/aws_user.git
```
```sh
git config --global user.email "you@example.com"
```
```sh
git config --global user.name "Your Name"
```
```sh
git branch -M main
```
```sh
git branch --set-upstream-to=origin/main main
```
```sh
git pull --rebase origin main
```
```sh
 git pull origin main
```
```sh
git push origin main
```

### step for changing master → main
```sh
git branch -m master main
```
```sh
git push -u origin main
```
Go to GitHub → Your Repository → Settings → Branches.

Under Default branch, select main instead of master.

Click Update.
```sh
git push origin --delete master
```
