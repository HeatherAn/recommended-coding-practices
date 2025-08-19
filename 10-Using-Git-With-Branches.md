# Using Git With Branches

So far you have a *local main* branch (in `~/Documents/Project_Z`) and a *remote main* branch (`Project_Y` in the Github).  

Up to this point -where you have been working by yourself on a repo- **branching** can be understood as creating a **separate "copy"** of a repository at a given point in time, for a separate use. So that each branch is a different line of development.  

Now, branches are useful not only when you are working on a code by yourself, but also when coding in collaboration with others. When working individually on a code, you could for example have a branch called `testing` (for testing some functionality in the code) or a branch called `issue_X` to solve a specific issue with the code. When collaborating with others, each collaborator in charge of a specific task can work in a separate branch (each called `task_id`, with `id` being an identifier for the specific task), and merge to the *remote main* only after testing such task.     

## How can I create more branches? 

You can create as many branches as you need to, starting from whichever commit from whichever branch!  

To create a new *local* branch, go to the directory where the *local* **main** branch is (i.e., where Git has been initialized with `git init`) and type:  

```
git switch -c name_branch
```
Where `name_branch` is the name of the new *local* branch to be created. This will create a new branch called **name_branch** starting from your **main** *local* branch and starting from the `HEAD` commit, and it will switch to that branch right away. When being in the `name_branch`, you will see the same files as in the **main** branch. But all changes made while being on the `name_branch` will "stay" there, and they will be independent from the changes made to the same files in the *local* **main** branch.  

If you want to create a branch from your *local main* but from how the *local main* was -for example- two commits ago, you have to speficy the commit *hash* as `git switch -c name_branch commit_id` (or use `HEAD~2` as `commit_id`).   

## Switching between branches

To know in which branch you are currently working in you can do `git branch`. The output will be a list of all *local* branches related to that repository. The one next to the asterisk `*` is the one you are currently in. 

If you use the `--all` option (so `git branch --all`) you will see a list of all *local* and *remote* branches. Again, the branch next to the asterisk `*` is the one you are currently in. 

To **switch from the current branch to another** we saw before you can use `git switch name_branch`, where `name_branch` is the name of the branch you want to move into. This instruction actually works for Git versions later than 2.23. You can also switch from the current branch to another one called `name_branch` by doing `git checkout name_branch`. Does `git checkout` sound familiar? Yes! We have already used it to restore a specific version of a file before in [Using Git For The Nth Time](https://github.com/HeatherAn/recommended-coding-practices/blob/main/09-Using-Git-For-The-Nth-Time.md). The `checkout` command is a very versatile one! See more by looking at the manual with `git checkout --help`.

____________________

### Important: switching branches changes files!

Keep in mind that **when you work in a given branch, Git will show you the versions you last committed in that branch**. This means that when switching branches, files in your working directory will change. Do not panic! It is just because you are working in a different branch! 
____________________

## How to delete branches?

You can delete *local* and *remote* branches by adding the `-d` flag:  

- `git branch -d name_branch` : to delete a *local* branch called `name_branch`.

- `git branch -rd name_branch` : to delete a *remote* branch called `name_branch`. Keep in mind this will only remove the pointer to the remote branch `name_branch` (so you will not see it anymore when doing `git branch --all` for example). But the remote branch will still exist in Github. If you want to delete the remote branch in Github then you can do: `git push origin --delete name_branch`  

To know all *remote* branches you are tracking, use `git branch -r` (the `-r` flag refers to "remote").  

_________________

### Parenthesis

We had seen before that `git log` allows you to see the history of commits. When having different branches, `git log` **does not show all branches** all the time. By default `git log` only shows the commit history of the branch **you are currently in**. If you want to see the commit history of a specific branch you have to specify it as: `git log name_branch` (where `name_branch` is the name of the branch you want to see its history of commits). If you want to see the commit history of all branches do: `git log --all`.
_________________

## Common branch aliases

- When working on a code by **yourself**, aside the *local main* and the **origin** (actually **origin/main** branch as seen when doing `git branch --all`), you can create other branches for specific tasks related to the development of the code. When creating new branches, choose short names, such as **testing** (to perform the testing of code), **issue_X** (with **X** being the number of a specific issue), etc.  

- When working in **collaboration** with others, there will be a main repository (usually referred to as the **upstream** *remote* Github repository). And each collaborator will have its own "copy" of this main repository *locally* (the **main** branch in each collaborator's *local* directory where Git has been initialized). Each collaborator can create other branches *locally* and *remotely*; and some of those branches can even be accessed by more than one collaborator (in case they work together on a specific task). The team should make a proper design of what branches will be created as a team, what branches will be worked on individually, and even define responsibilities to which team member will be accepting merges between branches.

________________ 

### Parenthesis

When having more branches than a *local main* and a *remote main*, keep in mind the following commands:  

- `git remote add name_remote ssh_key` : to add a new remote called `name_remote` with the url `ssh_key`. This is how we have defined the **origin** before (see [Using Git For The First Time](https://github.com/HeatherAn/recommended-coding-practices/blob/main/08-Using-Git-For-The-First-Time.md)). You can use such instruction to define other *remote* repositories. For example, an **upstream** *remote* repo.  
- `git remote remove name_remote` : very useful command to remove the "link" to an already defined *remote*.  
- `git remote set-url name_remote new_ssh_key` :  in case a *remote* has been moved, you can change the url of the remote with alias `name_remote`, by specifying the new url of the *remote* repository in `new_ssh_key`.  
- `git remote rename old_name new_name`: changes the alias of the *remote* from the `old_name` to a `new_name`.  
_________________

## Pushing and Pulling

When having more branches you can explicitly tell Git what you want to push/pull to/from where. 

`git push origin main:name_branch` : pushes the changes from your local `main` to the **origin** remote `name_branch`. Same for `git pull`.  

______________________

[Previous : 09 - Using Git For the Nth Time](https://github.com/HeatherAn/recommended-coding-practices/blob/main/09-Using-Git-For-The-Nth-Time.md)  
[Next : 11 - Merging or Rebasing Branches](https://github.com/HeatherAn/recommended-coding-practices/blob/main/11-Merging-Or-Rebasing-Branches.md)  

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)
