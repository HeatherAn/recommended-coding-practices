When using more than one branch per repository, there are 3 concepts that you have to keep in mind: **branches**, **merging** and **conflicts**. 

# Branches

**Branching** refers to creating a **separate "copy"** of a repository for private use. So that each branch is a different line of development. They are useful not only when you are working on a code by yourself, but also when coding in collaboration with others. When working individually on a code, you could for example have a branch called `testing` (for testing), or a branch to solve a specific issue with the code (called `issue_X`). When collaborating with others, each collaborator could be in charge of a specific task being worked on a specific branch.

## How are branches used? 

Branches are usually used for **bug fixing** and **testing**.

## The *master* branch: the *local* and the *remote* **master**

When a repository is initialized in your local work laptop/station, the `git init` command will create the *local* **master** branch. This is the default name of the first branch that is created associated to the (in this case *local*) repository. In principle you could change this alias, and "rename" that branch. However it is recommended not to do that, specially if you are not fully used to Git (yet). 

When a *local* repository is "linked" to a *remote* repository, `git clone` defines the *remote* repository as the **origin**. As we have seen before, this **origin** also has its own **master** (because a repository has been initialized remotely). Then strictly speaking, there is the *local* **master** branch, and the *remote* **master** branch (which is actually recognized as **origin/master** in your local system). If there is only one branch in the **origin**, then you can refer to it only by using the **origin** alias (that is why we have been using `git pull origin master` and `git push origin master` to pull and push changes). 

When you are working with more branches, then you have to keep in mind *which* *local* branch will be connected to *which* *remote* branch (using the respective alias).

## How can I create more branches? 

You can create more *local* branches, as well as more *remote* branches.

To create a new *local* branch, go to the directory where the *local* **master** branch is (i.e., where Git has been initialized with `git init`) and type:  

* `git branch name_branch` : where `name_branch` is the name of the new *local* branch to be created.  

To create a new *remote* branch *locally* (from your work laptop/station), go to the directory where the *local* **master** branch is (i.e., where Git has been initialized with `git init`) and type:

* `git branch name_branch` : where `name_branch` is the name of the new *local* branch to be created. You have to create it first *locally* and then push it to the *remote*.
* `git switch name_branch` : leave the current branch and switch to the `name_branch`. Since we are assuming this is the first branch you are creating, then you will be moving from the *local* **master** to the `name_branch`. When being in the `name_branch`, you will see the same files as in the **master** branch. But all changes made while being on the `name_branch` will "stay" there, and they will be independent from the changes made to the same files in the *local* **master** branch.
* `git push origin name_branch` : by doing this you will create the *remote* branch. This *remote* branch will be a separate branch from the *remote* **master** and will be referred to as **origin/name_branch**. 

## Switching between branches

To know in which branch you are currently working in you can do `git branch`. The output will be a list of all *local* branches related to that repository. The one next to the asterisk `*` is the one you are currently in. 

To **switch from the current branch to another** we saw before you can use `git switch name_branch`, where `name_branch` is the name of the branch you want to move into. This instruction actually works for Git versions later than 2.23. You can also switch from the current branch to another one called `name_branch` by doing `git checkout name_branch`. Does `git checkout` sound familiar? Yes! We have already used it to restore a specific version of a file before in [Using Git for the Nth Time](Using-Git-for-the-Nth-Time). The `checkout` command is a very versatile one! See more by looking at the manual with `git checkout --help`.

In Git versions later than 2.23, you can also create a new branch and switch to it in a single line of commands by typing: `git switch -c name_branch`, where the `-c` flag refers to create a new branch (called `name_branch`).
____________________
### Important to keep in mind: switching branches changes files!

Keep in mind that **when you work in a given branch, Git will show you the version of files you last committed in that branch**. This means that when switching branches, files in your working directory will change. Do not panic! It is just because you are working in a different branch! 

_________________


## How to delete branches?

You can delete *local* and *remote* branches by adding the `-d` flag:  

- To delete a *local* branch, use: `git branch -d name_branch` (where `name_branch` is the *local* branch to be deleted).

- To delete a *remote* branch use: `git branch -rd name_branch` (where `name_branch` is the *remote* branch to be deleted).

To know all *remote* branches you are tracking, use `git branch -r` (see we are using a `-r` flag to refer to "remote").

_________________
### Parenthesis

We had seen before that `git log` allows you to see the history of commits. When having different branches, `git log` **does not show all branches** all the time. By default `git log` only shows the commit history of the branch **you are currently in**. If you want to see the commit history of a specific branch you have to specify it as: `git log name_branch` (where `name_branch` is the name of the branch you want to see its history of commits). If you want to see the commit history of all branches do: `git log --all`.
_________________

## A bit on common branch aliases

- When working on a code by **yourself**, aside the *local* **master** and the **origin** (actually **origin/master** branch), you can create other branches for specific tasks related to the development of the code. When creating new branches, choose short names, such as **testing** (to perform the testing of code), **issue_X** (with **X** being the number of a specific issue), etc. These branches can also be linked to *remote* Gitlab repositories within the **origin** project.

- When working in **collaboration** with others, there will be a main repository (usually referred to as the **upstream** *remote* Gitlab repository). And each collaborator will have its own "copy" of this main repository *locally* (the **master** branch in each collaborator's *local* directory where Git has been initialized). Each collaborator can create other branches *locally* and *remotely*; and some of those branches can even be accessed by more than one collaborator (in case they work together on a specific task). The team should make a proper design of what branches will be created as a team, and what branches will be worked on individually.

________________
### Parenthesis

When having more branches than a `master` and an `origin` one, keep in mind the following commands:  

- `git remote add name_remote https_key` : to add a new remote called `name_remote` with the https address `https_key`. This is how we have defined the **origin** before (see [Using Git for the First Time](Using-Git-for-the-First-Time)). You can use such instruction to define other *remote* repositories. For example, an **upstream** *remote* repo.  
- `git remote remove name_remote` : very useful command to remove the "link" to an already defined *remote*.  
- `git remote set-url name_remote new_https_key` :  in case a *remote* has been moved, you can change the url of the remote with alias `name_remote`, by specifying the new url of the *remote* repository in `new_https_key`.  
- `git remote rename old_name new_name`: changes the alias of the *remote* from the `old_name` to a `new_name`.  

________________

# Merging

**Merging** refers to **applying the changes** from one file to another in order to **update** it. When working with different branches you will need to merge features from one branch into another.

Merging occurs when you do `git pull`. In fact `git pull` does a lot of things between the *local* and the *remote* branches, among which it calls the `merge` command which actually does the merging of files.

Specially when working collaboratively, it is recommended not to use `git pull` to update the *local* branch with the *remote* changes. It is recommended to do `git fetch` and then `git merge` instead. In this way, you can see what others have done and foresee what type of conflicts might arise when merging. 

__________________
### Parenthesis

We saw `git merge branch_name` allows you to merge the changes of the branch called `branch_name` with the branch you are currently working in. You can always undo this merging by doing `git merge --abort`. So do not worry! You can always undo things!

__________________

Thus when working collaboratively, the workflow for each collaborator should be: 

- **fetch** to get the *remote* changes in the *local* branch, but without merging them (e.g., if you are working between the *remote* **origin** and the *local* **master** do `git fetch origin master`)  
- **merge** the *remote* changes with the respective *local* branch (e.g., if you are working between the *remote* **origin** and the *local* **master** do `git merge origin`)  
- solve conflicts (**add** and **commit**)  
- work (**add** and **commit**)  
- **push** all work done *locally* to the respective *remote* branch (e.g., if you are working between the *remote* **origin** and the *local* **master** do `git push origin master`)  

Keep in mind each collaborator may have also their *own branches* or *shared branches* to fix issues, perform specific testing, etc. In such a case, each collaborator will have to be aware in *which local branch* they are currently working in, and with *which remote branch* they should merge such branches with. 


# Conflicts

When branches are merged, **conflicts** will surely arise. Conflicts occur:

- when two or more collaborators **change the same lines of the same file** or,   
- when a file has been **deleted** by one collaborator, but it has been **edited** by another collaborator. 

In general, when conflicts appear Git will show very descriptive messages of *where* the conflict is and *what a solution could be*. Whenever a conflict arises, you must **solve it**. 

## How to solve conflicts?

When merging branches Git will **fetch** the changes, detect conflicts (if any), and if there are conflicts, it will **refuse to merge** the two copies of the repository (and the conflict(s) will be pointed out).

## How does Git point out a conflict?  

When you see the file where a conflict has been detected, the changes **you made** will be preceded by `<<<<<<< HEAD`. Your changes will be then followed by a `=======`. Then the changes added by **your collaborator(s)** will appear followed by a `>>>>>>>`. The very long string afterwards is the **identifier** of the commit.

In order to **fix** this, you just have to **modify** the file, **add** the change, **commit** it and **push** it. This will update the *remote* repository with the conflict fixed by you.

Take a look at [this video](https://youtu.be/xNVM5UxlFSA) to see what a conflict looks like. In this video the presenter uses **VSCode** as the editor and he is working in a terminal within **VSCode**. But you can see the Git commands he uses to solve the conflict with the `content.txt` file. 

# Remember when working collaboratively with others:

- If the Gitlab repository has already been created, the **owner** of the project must first **give access** to the collaborators. This can be done via the `Settings` and `Manage access` tab. Collaborators must **accept** the access to the repository.   
- Once given access, collaborators must **clone** the repository by typing in the terminal:    
    `git clone https_key dir1`: where `https_key` is the https address of the Gitlab repository, and `dir1` is the name of the directory in their *local* work laptop/station where they want to "copy" the Gitlab repository's content. When the repository is cloned, the cloned repository is identified by the **origin** alias.  
- Collaborators and the owner can make changes to the project files by *fetching* and *merging* (or *pulling*), *adding*, *committing* and *pushing*.  
- Everyone should **fetch and merge** (or **pull**) from the **upstream** branch frequently, in order to avoid conflicts.  
- Establish responsibilities clarifying the tasks for each collaborator. Use branches to segregate the work (e.g., one branch per task).  
- Make smaller commits, by segmenting large tasks into smaller sub-tasks or establishing step-wise tasks.
- Communication! If you want to go beyond the task you were given, go for it! But tell your collaborators in advance (before they start modifying the code by themselves, creating more conflicts!).
- Follow a code convention (in terms of the use of tabs/spaces, name of variables and functions, mandatory and optional hyperparameters, etc.).

Do you want to see more about Git branches, check the Git documentation [here](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

In the next section we will look at summarizing examples on how to use the Git commands we have seen so far.

________________________

[Previous : Using Git for the Nth Time](Using-Git-for-the-Nth-Time)  
[Next : Git Examples](Git-Examples)  

[Go back to Purpose](Purpose)
