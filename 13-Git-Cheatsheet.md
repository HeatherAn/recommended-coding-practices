# Git Cheatsheet

## Configuration

`git config --global user.name "your name"` : set your user name for all your repositories as a user.  

`git config --global user.email "your email address"` : set your email for all your repositories as a user.      

`git config --local user.name "your name"` : set your user name for the repository you are in.  

`git config --global core.editor “name editor“` : set the default text editor. For example:    

- For **Kate** (Linux):  `git config --global core.editor "kate"`  

- For **Gedit** (Linux, Windows):  `git config --global core.editor "gedit --wait --new-window"`   

- For **Vim** (all): `git config --global core.editor "vim"`   

- For **VSCode** (all): `git config --global core.editor "code --wait"`   

- For **Emacs** (all):  `git config --global core.editor "emacs"`    

`git config --system --list` :  list the `--system` settings which apply to every user on the system/device and all their repositories.  

`git config --global --list` : list the `--global` settings that are stated in the `~/.gitconfig` file (or `~/.config/git/config` file if applicable) and that specify settings for all the repositories you have as a user.  

`git config --local --list` : list the `--local` settings that are stated in the `./.git/config` file and that specify settings for the specific repository you are in.   

## Repository basics

`git init` : initialize a new Git repo.   

`git status` : show changed files (what is un-tracked, what is not staged yet, what is staged and ready to be committed).    

`git add file` : stage a file called `file`.  

`git restore file` : discard changes made to a file called `file` that has not been yet added to the staging area. 

`git restore --staged file` : un-stage a file called `file`.   

`git commit -m "message"` : commit changes with a message in "message".   

`git reset --soft commit_hash` : delete commit of hash `commit_hash` but keep changes staged.  

`git reset --mixed commit_hash` : delete commit of hash `commit_hash`, un-stage the changes but do not discard the changes.  

`git reset --hard commit_hash` : delete commit of hash `commit_hash`, un-stage the changes and discard the changes.  

`git commit --amend` : edit the last commit message.  

`git cherry-pick commit_hash` : apply the commit of hash `commit_hash` to the current branch.  

`git blame file` : see who changed each line of the file called `file`.  

`git log` : show commit history.  

`git log --oneline` : show commit history in short.  

`git rm file` : delete file called `file` and stages the deletion.   

`git mv file1 file2` : rename file called `file1` as `file2`.   

## Branches  

`git branch --all` : list all branches of a git repo.  

`git switch -c name_branch` : create new branch called `name_branch` and move into it right away.  

`git switch -c name_branch commit_hash` : create new branch called `name_branch` at the state of the commit `commit_hash`, and move into it right away.  

`git checkout name_branch` : switch to branch called `name_branch`.  

`git merge name_branch` : merge changes from the branch called `name_branch` into the current branch. 

`git branch -d name_branch` : delete branch called `name_branch`.  

`git branch -D name_branch` : force delete branch called `name_branch` (e.g., for deleting an un-merged branch).  

`git rebase name_branch` : rebase the branch called `name_branch` into the current branch (this changes the hash of the (new) commits made in the current branch).  
  
## Remotes

`git clone ssh_url` : create a copy of a Github repository, including its commit history and related metadata.  

`git remote -v` : list remotes associated with a git repo.  

`git remote add origin ssh_url` : assign an ssh url `ssh_url` to the **origin**.  

`git push origin <name_branch1>:<name_branch2>`: push the changes from *local* branch called `<name_branch1>` to the **origin** *remote* `name_branch2`. Same for `git pull`.  

`git push origin main` : push the changes from *local* `main` to the **origin** *remote* `main`. Same for `git pull`.  

`git push origin <name_branch>` : push the changes from *local* `main` to the **origin** *remote* `name_branch`. Same for `git pull`.  


________________________

Want to check some of the commands in more details? Start by checking the [Setting Up Git](https://github.com/HeatherAn/recommended-coding-practices/blob/main/07-Setting-Up-Git.md) section.

______________________

[Previous : 12 - Cloning and Forking](https://github.com/HeatherAn/recommended-coding-practices/blob/main/12-Cloning-and-Forking.md)  
[Next : 14 - Project Structure](https://github.com/HeatherAn/recommended-coding-practices/blob/main/14-Project-Structure.md)  

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)


