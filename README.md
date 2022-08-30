# Git Tasks

1. Create your own repository with a filled file(s).
   -  Push your repository to GitLab/GitHub/Bitbucket.
2. Create a master branch and protect it.
   - Create your work branch. 
   - Add any files and edit some records in existing files. 
3. Add your changes from the work branch to the master branch. 
   - (Make a merge-request/pull-request from your branch and close it. Cope with conflicts if there are.)
4. Back repository to someone's old commit. 

# Solution

### :one: Task

#### Create directory (Github) with file README.md
```
mkdir /home/$USER/Github && touch README.md
```
#### Initialization of directory to Git
```
git init -b main
```
#### Generating SSH key and using it for GitHub (place mail which are registered on github repo) and adding SSH key to ssh-agent
```
ssh-keygen -t rsa -b 4096 -C "rybitskyiy@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```
#### Copy public key into GH account and save it

#### Initial commit, auth. in GitHub, create remote repository (name Github, public)
```
git add README.md
git commit -m "Initial commit"
sudo apt install gh && gh auth login && gh repo create Github --public --source=. --remote=upstream --push
```

### :two: Task

#### To protect main branch its necessary to perfrom some actions on GitHub: Seeting - Branches - Add branches protection rule - Branch name - And define rule for pull request

#### Create worker branch and set push option
```
git checkout -b worker && git push --set-upstream origin worker
```
#### Create file and push it
```
sudo lshw -short > system.txt
git add system.txt && git commit -m "added file system.txt" && git push
```
### :three: Task

#### Carry out merge worker branch into main
```
git checkout main && git merge worker
```
#### To execute of pull-request - following step-by-step on GitHub repository

### :four: Task

#### Before we continue, small hint: to have git log in a pretty format it nacily to use provided below git alias. After that to lookup in git log, write - git logline 
```
git config --global alias.logline "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```
#### Just for a looking for an old commit, use next:
```
git checkout commithash
```
#### If we want to roll-back with discarding any changes made after that commit, use next:
```
git reset commithash 
```
#### And if we want to take previous commit and add new commit after that, keeping log in tact, use next:
```
git revert commithash 
```
